# 3 Types of Transport Layer Types of Questions:
## A regular problem about segmenting in the transport layer:
- Question: 
- The given will be:
	- The total data size from the application layer
	- the size of a segment
	- the size of the segment header (when no additional options are used) = 20 bytes always
	- So, the $$number \ of \ segments \ needed = \ ceiling(\frac{total \ datasize \ from \ the \ app \ layer}{size \ of \ a \ segment}) $$
	- And, the size of the data sent to network layer: $$size = number \ of \ segments * (segment \ size + 20)$$ ==???==
	- And, the size of the last segment size =  total  data size from the application layer 
## A regular problem about multiplexing in the transport layer:
- Question: 
- The given will be:
	- suppose we have 3 different applications
	- We have a throughput capacity, and if all the capacity will go to one app, then will slow down, so the transport layer has to do multiplexing to distribute to all apps
	- TCP standard header (no options used) = 20 bytes
	- The size of a segment of each app will be given (i.e. email segment size, web segment size, chat segment size)
	- How much data do we need to carry within one iteration of sending
## A regular problem about error handling and flow control in transport layer:
- Question: Time needed to be delivered correctly to the destination.
- The given will be:
	- The total data size from the application layer
	- packet error probability = so, 5% of initial packets are lost
	- assumption: 
		- each packet is sent only once after error
		- no retransmission
		- each segment is mapped to one network layer packet
		- 
