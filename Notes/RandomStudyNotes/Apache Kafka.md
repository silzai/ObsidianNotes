# what is it?
- Kafka is a distributed event store and stream-processing platform.
- event streaming is capturing data in real-time from event sources like databases, sensors, mobile devices, cloud services, and software applications in the form of streams of events.
> note:
> there exists an open source python library called `Quix` [whose docs can be found here](https://quix.io/docs/get-started/welcome.html)can be used to manage topics, and make producers/consumers/streams fully in python, but I will be using the more matured `javadocs` for all the examples below.
## creating broker/kafka server
- to create a broker/kafka server, we can get the docker image

```sh
$ docker pull apache/kafka
```

- and start the kafka docker container

```sh
$ docker run -p 9092:9092 apache/kafka -name kafka
```
## creating a topic
- simply run the following command in the terminal, but for docker, may have to add additional commands/options:
```sh
bin/kafka-topics.sh --create --topic <topic-name> --bootstrap-server localhost:9092
```
- they can also be created using the docker config files
- additionally, topics can be auto-created using from code in java, and even in `Quix` for python using `auto_create_topics=True`.
## Kafka APIs
### The [Producer API](https://kafka.apache.org/documentation.html#producerapi)
- to publish (write) a stream of events to one or more Kafka topics, or A Kafka client that publishes records to the Kafka cluster.
- The idempotent producer strengthens Kafka's delivery semantics from at least once to exactly once delivery. meaning producer retries will no longer introduce duplicates. *this is enabled by default*, but it is imperative to avoid application level re-sends since these cannot be de-duplicated.
- Here is an example of using the `Producer` to send records with strings containing sequential numbers as the key/value pairs.
 ```java
Properties props = new Properties();
props.put("bootstrap.servers", "localhost:9092");
props.put("linger.ms", 1);
props.put("key.serializer", "org.apache.kafka.common.serialization.StringSerializer");
props.put("value.serializer", "org.apache.kafka.common.serialization.StringSerializer");
 
 Producer<String, String> producer = new KafkaProducer<>(props);
for (int i = 0; i < 100; i++)
	producer.send(new ProducerRecord<String, String>("my-topic", Integer.toString(i), Integer.toString(i)));
	
 producer.close();
```
- To use the transactional producer API, we need to assign a `transactional.id` id and use the following functions: `producer.beginTransaction()`, `producer.commitTransaction()`, and `producer.abortTransaction()`, here is an example:
```java
 Properties props = new Properties();
 props.put("bootstrap.servers", "localhost:9092");
 props.put("transactional.id", "my-transactional-id");
 Producer<String, String> producer = new KafkaProducer<>(props, new StringSerializer(), new StringSerializer());

 producer.initTransactions();

 try {
     producer.beginTransaction();
     for (int i = 0; i < 100; i++)
         producer.send(new ProducerRecord<>("my-topic", Integer.toString(i), Integer.toString(i)));
     producer.commitTransaction();
 } catch (ProducerFencedException | OutOfOrderSequenceException | AuthorizationException e) {
     // We can't recover from these exceptions, so our only option is to close the producer and exit.
     producer.close();
 } catch (KafkaException e) {
     // For all other exceptions, just abort the transaction and try again.
     producer.abortTransaction();
 }
 producer.close();
```
- When the `transactional.id` is specified, all messages sent by the producer must be part of a transaction.
- All messages sent between the [`beginTransaction()`](https://kafka.apache.org/37/javadoc/org/apache/kafka/clients/producer/KafkaProducer.html#beginTransaction()) and [`commitTransaction()`](https://kafka.apache.org/37/javadoc/org/apache/kafka/clients/producer/KafkaProducer.html#commitTransaction()) calls will be part of a single transaction. 
### The [Consumer API](https://kafka.apache.org/documentation.html#consumerapi)
- to subscribe to (read) one or more topics and to process the stream of events produced to them.
#### Consumer Groups
- _consumer groups_ allow a pool of processes to divide the work of consuming.
- These processes can either be running on the same machine or they can be distributed over many machines
- All consumer instances sharing the same `group.id` will be part of the same consumer group.
- to subscribe to a topic (Subscribe to the given list of topics to get dynamically assigned partitions):
```java
consumer.subscribe(Arrays.asList("foo", "bar"));
```
- an example that demonstrates a simple usage of Kafka's consumer api that relies on automatic offset committing:
```java
Properties props = new Properties();
// notes on bootstrap.servers: `bootstrap.servers` provides the initial hosts that act as the starting point for a Kafka client to discover the full set of alive servers in the cluster, be they may 100 or 1000 nodes.
props.setProperty("bootstrap.servers", "localhost:9092");
props.setProperty("group.id", "test");
// Setting `enable.auto.commit` means that offsets are committed automatically
props.setProperty("enable.auto.commit", "true"); props.setProperty("auto.commit.interval.ms", "1000");
props.setProperty("key.deserializer",
 "org.apache.kafka.common.serialization.StringDeserializer");
props.setProperty("value.deserializer", "org.apache.kafka.common.serialization.StringDeserializer");

// In this example the consumer is subscribing to the topics "foo" and "bar" as part of a group of consumers called "test" as configured with `group.id`.
KafkaConsumer<String, String> consumer = new KafkaConsumer<>(props);
consumer.subscribe(Arrays.asList("foo", "bar"));

while (true) {
	 ConsumerRecords<String, String> records = consumer.poll(Duration.ofMillis(100));
	for (ConsumerRecord<String, String> record : records)
		 System.out.printf("offset = %d, key = %s, value = %s%n", record.offset(), record.key(), record.value());
}
```
- To consume in batches:
```java
Properties props = new Properties();
props.setProperty("bootstrap.servers", "localhost:9092");
props.setProperty("group.id", "test");
props.setProperty("enable.auto.commit", "false");
props.setProperty("key.deserializer", "org.apache.kafka.common.serialization.StringDeserializer");
props.setProperty("value.deserializer", "org.apache.kafka.common.serialization.StringDeserializer");

KafkaConsumer<String, String> consumer = new KafkaConsumer<>(props);
consumer.subscribe(Arrays.asList("foo", "bar"));
final int minBatchSize = 200;
List<ConsumerRecord<String, String>> buffer = new ArrayList<>();

while (true) {
ConsumerRecords<String, String> records = consumer.poll(Duration.ofMillis(100));
	for (ConsumerRecord<String, String> record : records) {
		 buffer.add(record);
	}
	if (buffer.size() >= minBatchSize) {
		// this example is about batching then inserting into a database
		insertIntoDb(buffer);
		// we will manually commit only after the database insertion is done 
		consumer.commitSync();
		buffer.clear();
	}
}
```
- `commitSync()`:
	-  If we allowed offsets to auto commit, records would be considered consumed after they were returned to the user in `poll`. It would then be possible for our process to fail after batching the records, but before they had been inserted into the database.
	- To avoid this, we will manually commit the offsets only after the corresponding records have been inserted into the database.
### The [Kafka Streams API](https://kafka.apache.org/documentation/streams)
- to implement stream processing applications and i.e. do transformations on the data.
- `Streams` processes *do not* execute on the brokers, they are executed on the application (the application that uses the brokers)
- `Quix` can also be used for a full pythonic implemenation.
- 
### The [Kafka Connect API](https://kafka.apache.org/documentation.html#connect)
- to build and run reusable data import/export connectors that consume (read) or produce (write) streams of events from and to external systems and applications so they can integrate with Kafka
- The Connect API allows implementing connectors that continually pull from some source data system into Kafka or push from Kafka into some sink data system.
- kafka connect is run on a separate server to ingest or give data
- its just some `JSON` config files, that says get data from this "place" and stream it into "this" topic.
### The [Admin API](https://kafka.apache.org/documentation.html#adminapi)
- to manage and inspect topics, brokers, and other Kafka objects.
- additionally, to create a topic using the `Admin API`:
```java
 Properties props = new Properties();
 props.put(AdminClientConfig.BOOTSTRAP_SERVERS_CONFIG, "localhost:9092");

 try (Admin admin = Admin.create(props)) {
   String topicName = "my-topic";
   int partitions = 12;
   short replicationFactor = 3;
   // Create a compacted topic
   CreateTopicsResult result = admin.createTopics(Collections.singleton(
     new NewTopic(topicName, partitions, replicationFactor)
       .configs(Collections.singletonMap(TopicConfig.CLEANUP_POLICY_CONFIG, TopicConfig.CLEANUP_POLICY_COMPACT))));

   // Call values() to get the result for a specific topic
   KafkaFuture<Void> future = result.values().get(topicName);

   // Call get() to block until the topic creation is complete or has failed
   // if creation failed the ExecutionException wraps the underlying cause.
   future.get();
 }
```
