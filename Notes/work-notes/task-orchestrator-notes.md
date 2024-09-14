technologies to research about (TOC):
- Docker
- Kubernetes
- Apache Kafka
- Apache Airflow
- Apache Spark
- Celery
# Docker
## what is it?
- basically we can package (containerize) a whole applications environment (including all dependencies) and run the container in (loose) isolation from the host machine's file system.
- Instead of virtualizing an entire physical machine like in virtual machines, containers virtualize the host operating system only, so it is lighter/memory efficient to use containers.
- we can run many containers simultaneously on a given host
- in the end, its easier to deploy/share code basically.
## its architecture
- docker client sends web api requests to docker daemon, which then executes the commands such as fetching from registry, running container etc.
## there are 3 main components in docker
- we will play with these 3 components throughout (i guess): docker image, docker container, and registry
### docker image
- a docker image contains all of the configurations needed to run a container
- to create an image, we need a `Dockerfile`
#### to create a `Dockerfile` of an app, do the following
- navigate to the root directory of the app and do:
```shell
touch Dockerfile
```
- add the configurations as following in the `Dockerfile`:
```Dockerfile
# FROM will instruct the builder that you wanted to start from the `starting-image` image, such as alpine:latest, this will provide a starting point for the image
FROM starting-image
# `RUN`, `CMD`, `ADD`, `COPY`, and `ENTRYPOINT` commands will be executed in the specified working directory (WORKDIR)
WORKDIR /app
# can initialize variables using ARG
ARG FILENAME="hello"
# syntax is `COPY <source> <destination>`, where source is in your local filesystem and the destination is inside your image.
COPY . .
# `ADD` can do COPY from the internet as the source
ADD https://example.com/file .
# `RUN` executes a command inside the container shell.
# a good practice is to remove unnecessary files at the end of RUN command to make the image less bloated
RUN commands separated with && \ (if linux)
# `CMD` specifies the default command to run when starting a container from this image, cmd runs after run
CMD ["node", "src/index.js"]
# `EXPOSE` is used to indicate the port that needs to be published.
EXPOSE 3000
```
- and to make the image *executable*, append the following to the `Dockerfile`:
```Dockerfile
ENTRYPOINT ["executable", "parameter1", "parameter2"]
```
- and then inside the root directory, build the image using:
```shell
docker build -t app-dir-name .
# with -t option (tag), we can give a name to the image/file generated 
# app-dir-name is the name given when using -t option
# . will tell the command to look for the Dockerfile in the current dir
```
> note:
> when using the `-t` option, we can also an additional name that suggests the version among various things for the image, for example: `app-dir-name:0.1`
### container
- is a runnable instance of a docker image, we can:
 - create and start:
```shell
docker container run --detach --publish 8080:80 <image-name>
# --detach will make it so that the container is detached from the terminal it ran from
# --publish <host port>:<container port>, this means that any request to port 8080 on the host will be forwarded to port 80 in the container
```
- create but don't start:
```shell
docker container create --publish 8080:80 fhsinchy/hello-dock
```
- stop:
```shell
docker container stop <container-name>
```
- and to continue running when stopped or not running:
```shell
docker container start <container identifier>
```
- to restart:
```shell
docker container restart hello-dock-container-2
```
- and delete stopped containers using the cli:
```shell
docker container rm <container identifier>
```
#### Volume
- its just a folder on the host machine
- its used so that containers can share data
- to create it:
```sh
docker volume create <volume-name>
```
- then to connect/mount a container to a volume:
```sh
docker run --mount source=<volume-name>,target=<location-of-volume>
```
- now multiple can mount this volume and access the same files, and the files will persist even if the containers are closed
#### networking
- to see networks in system:
```shell
docker network ls
```
- to get ip address of a container:
```shell
docker container inspect --format='{{range .NetworkSettings.Networks}} {{.IPAddress}} {{end}}' notes-api-db-server
```
- but using ip address like this is dangerous, so will use a **user-defined bridge network** as opposed to the default one, so to make it, will do the following:
- first create our own network:
```shell
docker network create <network name>
```
- then to connect a container to the network, run the container with the following option:
```shell
docker network connect <network identifier> <container identifier>
```
- ==then what??==

### registry:
- its a centralized place where you can upload your images and can also download images, popular is [dockerhub](https://hub.docker.com/)
	- we can also create our own private registry
	- and importantly, a local registry runs within your computer that caches images pulled from remote registries
- In order to share an image online, the image has to be tagged (using `-t` when building the image), further it must be tagged in this format: `<docker hub username>/<image name>:<image tag>`
- then after logging in, we can upload it using:
```shell
docker image push <image repository>:<image tag>
```
## Docker-Compose
- Compose is a tool for defining and running multi-container Docker applications. With Compose, you use a YAML file to configure your application’s services. Then, with a single command, you create and start all the services from your configuration.
- how it is done:
- will first create a `docker-compose.yml` in the root dir of project
- inside the `yml` we have `services` object, where each key in the object represents a different container
- can also define a `volumes` object and have a key called `volume` for a container so that this container can access it when needed, this is useful for databases.
- for example:
```yaml
version: "3.4"
services:
	python:
		build:
			context: . # look for yaml file in cur dir
		container_name: python
		image: username/python:1.0.0
		ports:
		- 5000:5000
```
- then to start the containers, type:
```sh
docker-compose up
```
- this will run every container defined in the `yml` automatically
- or to build an image:
```sh
docker-compose build <image-name>
```
# Kubernetes
- we don't usually run containers by themselves, they are run using orchestration software.
>Kubernetes:
>it is a platform, not an application, what that means is that end-users of an application do not use it. a platform is an environment in which applications are developed and run.
- orchestration tool for docker containers
- mainly used so that microservices can talk with each other, and the developer does not need to worry about deploying to which hardware and management of containers.
## what is it made up of?
- kubernetes master node hosts the Kubernetes Control Plane, which contains:
	- **api server**: exposes api to define our workload (users can talk to it using `kubectl`)
	- **scheduler**: assigns a worker node to each deployable component of your application
	- **controller manager**: replicating components, keeping track of worker nodes, handling node failures
	- **etcd**: datastore for the cluster
- kubernetes worker nodes:
	- kubelet
	- container runtime (the actual application)
	- kube-proxy

- content below was referenced from [this video](https://www.youtube.com/watch?v=DMpEZEakYVc&list=PLHq1uqvAteVvUEdqaBeMK2awVThNujwMd&index=3)
- manifest -> kubectl -> api on k8s master -> k8s master will start kubelet
## to set up a cluster
- to create a cluster, use `kubeadm` ==details???==
- for fast set up, we can either use minikube for local testing or cloud providers multi-node configuration
## `kubectl`
- `kubectl` is a CLI client that allows users to talk to the API server on the master node to configure/control the cluster.
### `config` file
- it contains: 
	- clusters: its a HTTP endpoint
	- users: these are credentials
	- contexts: tells which cluster to point to (cluster + user)
- to find out which context `kubectl` is pointing to:
```sh
kubectl config current-context
# output: <cluster name that is being pointed at by kubectl>
```
- to switch cluster :
```sh
kubectl use-context <cluster-name>
```
### `get` command
- used to retrieve different resources:
```sh
# examples:
kubectl get pods
kubectl get deployments
kubectl get namespaces
```
### `namespaces`
- resources are allocated to namespaces
- they are just a group of resources that are isolated from other resources
- to create a `namespace`:
```sh
kubectl create namespace <namespace-name>
```
- there is a default namespace in any cluster, so when running any command, `kubectl` will use the default namespace, to override this behavior and refer to another namespace when executing commands, do the following:
```sh
# for example, using the `get` command
kubectl get pods -n <namespace-name>
# -n means get the pods for this namespace
```
### `describe` command
- used to give detailed information about different objects such as pods, nodes, deployments, etc.
```sh
kubectl describe <object-type> <object-name> -n <namespace-name>
# object types: pod, node, etc.
```

> *all the topics below refer to configuration files of the same name, i.e. `Secret` refers to a configuration file called `Secret`*
## `ConfigMap`
- has `kind`, `metadata` sections and `data` section which contains the actual key-value pairs 
- `deployment.yaml` should reference a `configmap.yaml`, this will make kubernetes directly mount the config defined in the `configmap.yaml` file to the relevant pods
- here is an example of a `configmap.yaml`:
```yaml
apiVersion: v1
kind: ConfigMap
metadata:
	name: example-config # arbitrary name
data:
	config.json {
		"environment" : "dev"
	} # this is the config file to be passes to the application/container/pod
	url: <example-service> # this is an endpoint, will reference this in Deployment.yaml
```
## `Secret`
- used to store secret data such as credentials etc.
- similar to `ConfigMap` but stores data in `base64` format, however it is not encrypted, should have third party provider encrypt it
- again, `deployment.yaml` should reference a `secret.yaml`
```yaml
apiVersion: v1
kind: Secret
metadata:
	name: example-secret # arbitrary name
type: Opaque
data:
	username: <base64-encoded-username>
	password: <base54-encoded-pass>
```
## `Service`
- since all `deployment` need a `service`, so it makes sense to put them in one file, so refer to the `Deployment` section below. 
## `Deployment`
- used for stateless apps (use `StatefulSet` for stateful apps such as databases)
- [this video](https://www.youtube.com/watch?v=s_o8dwzRlu4&t=989s) said that using `statefulSet` is a pain in the neck, so databases are usually deployed separate from a kubernetes cluster, need to confirm ??????
### desired state
> when deploying, I would need a bunch of settings in my environment before deploying such as having a certain number of instances for availability, them being load balanced, and automatically scale when traffic increases, and roll out the deployment to another working infrastructure in case of failure, etc. that is the desired state.
- we can describe all of the above in a single file `deployment.yaml`, and kubernetes takes care of this automatically by comparing the actual state and converting it to the desired state if needed.
Additionally:
- a `Deployment` contains configuration on `pods` too
- a pod can be thought of as a server on a physical machine
- a pod can have multiple containers (usually just one)
- taking all of things said above into consideration, a `deployment.yaml` may contain the following things:
```yaml
apiVersion: apps/v1
kind: Deployment 
metadata:
	name: <example-name>
	labels:
		app: <example-app>
spec:
	replicas: 2 # number of instances to roll out
	strategy:
		type: rollingUpdate # meaning that we always want to have at least 2 replicas available
	template: # template is a blueprint/configuration for the pods
		# templates have their own metadata and spec
		metadata:
			labels:
				app: <example-app>
		spec: # this is the pod spec, we can have multiple containers in spec
			containers: 
			- name: <container-name>
				image: <image-name>
				ports:
				- containerPort: 5000 # port to expose the application
				livenessProbe:
					# check whether app is running, if not restart it etc.
				resources:
				# tell kubernetes the upper limit of ram and cpu that shoudld be used 
--- # from here, the Service configuration starts
apiVersion: v1
kind: Service
metadata:
	name: <example-service> # referencing the service defined in ConfigMap above 
spec: 
	selector:
		app: <example-name> # this will same as the name of the "label" in metadata section of the Deployment, meaning that this service belongs to the pod defined by that label.
	ports:
		protocol: TCP
		port: 80
		targetPort: 5000 # this should be the same as the containerPort as defined in template in Deployment
```
### now to deploy using `kubectl`
- simply enter the command:
```sh
kubectl apply -f <path-to-deployment.yaml>
```
# Apache Kafka
- used for distributed event streaming
- used for message queuing
- makes client-server application achieve scalability and high availability
> why Kafka is not just a message queue:
> - it works as a modern distributed system that runs as a cluster
> - it is a true storage system built to store data for as long as you might like
> - the stream processing capabilities in Kafka let you compute derived streams and datasets dynamically off of your streams.
## Components
### producers
- the producer API creates streams of data (`messages`) and produces them to specific `topics`
### brokers (kafka instances)
- A single Kafka server is called a broker
- he broker receives messages from producers, assigns offsets to them, and commits the messages to storage on disk
- It also services consumers, responding to fetch requests for partitions and responding with the messages that have been committed to disk.
- `messages` are stored on brokers in `topics`
- `topics` are divided into `partitions`
	- the `message` is appended into a `partition` in order
- Kafka brokers are designed to operate as part of a cluster
	- Within a cluster of brokers, one broker will also function as the cluster controller which is elected automatically and does administrative tasks such as assigning partitions to brokers and monitoring for broker failures.
- A partition is owned by a single broker in the cluster, and that broker is called the leader of the partition. A partition may be assigned to multiple brokers, which will result in the partition being replicated
	- This provides redundancy of messages in the partition, such that another broker can take over leadership if there is a broker failure. However, all consumers and producers operating on that partition must connect to the leader.
- retention:
	- Kafka brokers are configured with a default retention setting for topics, either retaining messages for some period of time (e.g., 7 days) or until the topic reaches a certain size in bytes (e.g., 1 GB).
	- once these limits are reached, messages are expired and deleted so that the retention configuration is a minimum amount of data available at any time.
	- individual topics can also be configured with their own retention settings
	- Topics can also be configured as log compacted, which means that Kafka will retain only the last message produced with a specific key.
### consumers
- consumer api subscribes to topics
- a consumer subscribes to one or more topics and reads the messages in the order in which they were produced
- consumer can subscribe to real time or can consume old data topics that are in a topic
- The consumer keeps track of which messages it has already consumed by keeping track of the *offset* of messages, which is a metadata by kafka, By storing the offset of the last consumed message for each partition, either in Zookeeper or in Kafka itself, a consumer can stop and restart without losing its place
- Consumer group:
	- Consumers work as part of a consumer group
	- The group assures that each partition is only consumed by one member
	- mapping of a consumer to a partition is often called *ownership* of the partition by the consumer.
	- n this way, consumers can horizontally scale to consume topics with a large number of messages. Additionally, if a single consumer fails, the remaining members of the group will rebalance the partitions being consumed to take over for the missing member.
## Apache Zookeeper
- Apache Kafka uses Zookeeper to store metadata about the Kafka cluster/broker, as well as consumer client details such as partition offsets
# Apache Airflow
## what is it?
- used for scheduling and creating pipelines (is a finite batch workflow orchestration platform), it also has a web interface that helps manage the state of your workflows.
- the framework contains operators to connect with many technologies
- Airflow is not used to *stream* data between tasks, that is the work of Apache Kafka or celery, its only used to schedule tasks in an order 
- Airflow workflows are defined in Python code.
## installation
- installation is simple using a `docker-compose.yaml` script given in [this link](https://github.com/soumilshah1995/Airflow-Tutorials-/tree/main/Tutorial2), and also, since we have to have a database for airflow, the same `docker-compose.yaml` also contains a postgres container. 
## the web interface
- shows a simple dashboard with a list of `DAG`
- Tree View:
	- shows the workflow
- Graph View:
	- shows border colors to see whether task is successful or failed (green for success).
## `DAG`
- A `DAG` collects [Tasks](https://airflow.apache.org/docs/apache-airflow/stable/core-concepts/tasks.html) together, organized with dependencies and relationships to say how they should run.
- to declare a `DAG`:
```python
 import datetime

 from airflow import DAG
 from airflow.operators.empty import EmptyOperator

 with DAG(
	 dag_id="my_dag_name",
	 start_date=datetime.datetime(2021, 1, 1),
	 schedule="@daily",):
	 
	 EmptyOperator(task_id="task")
``` 
- after declaring a `DAG`, we need to add `Tasks`
## `Tasks`
- A Task is the basic unit of execution in Airflow. Tasks are arranged into [DAGs](https://airflow.apache.org/docs/apache-airflow/stable/core-concepts/dags.html), and then have upstream and downstream dependencies set between them into order to express the order they should run in.
- `Operator` is a `Task` that is executes many types of things, such as shell scripts, python scripts, emails, etc. for example:
```python
with DAG("my-dag") as dag:
    ping = HttpOperator(endpoint="http://example.com/update/")
    email = EmailOperator(to="admin@example.com", subject="Update complete")

    ping >> email
```
### `Task` relationships/dependencies
- to add dependencies to tasks, we can use the `<<` or `>>` operator, depending on whether the relationship is `upstream` or `downstream`, for example:
```python
first_task >> [second_task, third_task]
third_task << fourth_task
```

# Apache Spark
- info below was taken from documentation from [this link](https://spark.apache.org/docs/latest/rdd-programming-guide.html)
## what is it?
- is a unified analytics engine for large-scale data processing
- It also supports a rich set of higher-level tools including [Spark SQL](https://spark.apache.org/docs/latest/sql-programming-guide.html) for SQL and structured data processing, [pandas API on Spark](https://spark.apache.org/docs/latest/api/python/getting_started/quickstart_ps.html) for pandas workloads, [MLlib](https://spark.apache.org/docs/latest/ml-guide.html) for machine learning, [GraphX](https://spark.apache.org/docs/latest/graphx-programming-guide.html) for graph processing, and [Structured Streaming](https://spark.apache.org/docs/latest/structured-streaming-programming-guide.html) for incremental computation and stream processing.
## how it works
- it has RDD (Resilient Distributed Dataset) API for unstructured data, RDDs support two types of operations: 
	- _transformations_, which create a new dataset from an existing one (`map()` is an example of transformation) [see docs](https://spark.apache.org/docs/latest/rdd-programming-guide.html#transformations)
	- _actions_, which return a value to the driver program after running a computation on the dataset (`reduce()` is an example of actions) [see docs](https://spark.apache.org/docs/latest/rdd-programming-guide.html#actions)
- it has `DataFrame` API for structured data 
- first we need to initialize Spark:
```python
from pyspark import SparkContext, SparkConf

# create a SparkContext object, which tells Spark how to access a cluster. To create a `SparkContext` you first need to build a SparkConf object that contains information about your application

# The `appName` parameter is a name for your application to show on the cluster UI.


conf = SparkConf().setAppName(appName).setMaster(master)
sc = SparkContext(conf=conf)
```
- we can also perform various machine learning tasks on both `RDD` and `DataFrames` (structured data), refer to [this documentation](https://spark.apache.org/docs/latest/ml-features.html#mllib-main-guide)
- we can also use spark to read/write to Kafka brokers, refer to [this documentation](https://spark.apache.org/docs/latest/structured-streaming-kafka-integration.html)
# Celery
## what is it?
- distributed system 
- Task queues are used as a mechanism to distribute work across threads or machines.
- A task queue’s input is a unit of work called a task. Dedicated worker processes constantly monitor task queues for new work to perform.
- it is used to:
	- send any job to the background. 
	- Which is any kind of processing of uploaded files, long running exports, data conversions, background scheduled jobs and for running tasks on a periodic basis using `celerybeat` and `crontab`
## how does it work?
- first of all, any script/source will enqueue a task (or more simply said, call a function that was defined on a module with the function/task definitions) to a message broker (such as rabbitMQ, etc.)
- so make sure that a broker service is running such as rabbitMQ.
- now to define a task, do the following in `tasks.py`:
```python
from celery import Celery
# the "broker" argument is the url of the rabbitMQ server, change this to use any broker service that is running
app = Celery('tasks', broker='amqp://localhost')

# this decorator is necessary to define a celery task
@app.task
def add(x, y):
    return x + y
```
- now we can then run the `worker` using:
```sh
# note that "tasks" is the name of the python file defined above
celery -A tasks worker
```
- *note: it is also possible to run the celery server using [Daemonization](https://docs.celeryq.dev/en/stable/userguide/daemonizing.html#daemonizing)*
- now celery server should be running and listening for tasks.
- Now, to enqueue a task to the broker to execute:
```python
from tasks import add # note that tasks is the name of the python file defined above

# delay function will enqueue the add(2, 3) task and then a celery worker will dequeue and execute it
add.delay(2, 3)
```
- so celery will dequeue/read from the message broker and perform the task automatically when you enqueue it using the `delay()` function
## setting up config for celery
- we can set up a config file `config.py` for celery to store results as follows:
```python
CELERY_RESULT_BACKEND = "database"
CELERY_RESULT_DBURI = "sqlite:///temp.db"
# using sqlite as the datastore for this example
```
- and in the worker file `tasks.py`, add the following:
```python
from celery import Celery

app = Celery('tasks', broker='amqp://localhost')
app.config_from_object('config') # this line is setting the config.py settings

# add the task definition here...
```
> additionally, an add-on to monitor celery workers is `Flower`
