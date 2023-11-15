- Internet at layer 3 at each router processed data, but layer 4 is end-to-end, between sender and receiver in the communication

- On the same device, there are different applications sending and receiving packets, so multiplexing is done through segmentation.

# Transport Layer Protocols:
## TCP:
- connection-oriented protocol
- first establishes TCP session:
	- does 3 way handshake
- has flow control:
	- issue is with the receiver
	- there is a limit to how many segments a receiver can process, so it drops them, but tells the sender to slow down sending segments
	- The receiver tells the sender that it can accommodate "this" number of segments at a time, so the sender send that amount.
	- We will not overwhelm the receiver
- has congestion control:
	- issue with the network (as opposed to receiver)
	- if there is no problem in flow control, and segments are arriving
	- so TCP handles the 
- reliable, delivers packets in order
- if packet not received, will retransmit
- viewing websites or email is required to be error free, so used in this
- TCP segment:

| Source Port | Destination Port | Sequence Number | Acknowledgment number | 
| ----------- | ---------------- | --------------- | --------------------- |

- acknowledgment number:
	- the first byte the receiver is expecting to receive from sender
- sequence number:
	- it is the position/number of the byte the thing sender is sending
	- the initial sequence number is selected randomly by the sender
- Control bits:
	- there are 6 bits, for 6 flags
	- acknowledgment bit: it tell about dummy data or not
	- urgent bit: if urgent bit is 0, then ignore urgent field
	- syn flag: 
- Window:
	- how many bytes the receiver can process without being overwhelmed
	- the window value is what a receiver tells the sender how many bytes the it can process at a given time
	- 
## UDP:
- connection-less protocol
- There is no acknowledgment by receiver
- best effort, if data not received, will not retransmit, but the application layer takes care of this
- is faster/light-weight, used in applications that are more "real-time" (i.e. for videos etc.)
- The UDP header does not have many fields because of the above mentioned differences:

| Source Port | Destination Port | Length | Checksum | Application layer data | 
| ----------- | ---------------- | ------ | -------- | -------------- |

# Ports:
| Port Number Range | Port Group                         |
| ----------------- | ---------------------------------- |
| 0 to 1023         | well-known ports                   |
| 1024 to 49151     | Registered ports                   |
| 49152 to 65535                  | private ports and/or dynamic ports |

>[!info]
>well known ports are always provided *from the server*, the server can be an actual web server or even a pc. 

# Session Establishment:
## TCP Connection (3-way Handshake):
- Need the 6 flags from control bits to make TCP session:

>[!important] SYN
>packets used to initiate a connection

>[!important] ACK
>packets used to confirm the data packets ahave been received, and incremented by 1 for ACK reply

>[!important] FIN
>Indicate connection is being torn down, both sender and receiver send the FIN packets to gracefully terminate session.

# ==need to complete how to establish connection from example of mobile pic== 

- need to establish a connection as follows(as opposed to UDP which is connectionless)
- A sends SYN to B
- B sends an acknowledgment for the first segment, and also increments the ack to tell that this is the segment with the SEQ number that it is expecting
- 
- After 3-way handshake and after sending the data, we need to terminate the session
## Terminate TCP Session: 
- any of the 2 host can initiate termination of session
1) A will send FIN to B
2) B sends ACK to A
3) then finally A send an ACK to B to terminate the session