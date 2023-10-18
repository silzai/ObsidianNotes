## Rules of Communication:
### Message Encoding:
- Messages are converted into bits by the sending host, then they are encoded into a pattern of sounds, light waves, or electrical pulses depending on the network media, then are decoded by the receiver.
### Message Formatting and Encapsulation:
- message is encapsulated in a Frame where it provides the source and destination hardware addresses.
### Message Size:
- Segmenting: It is when size restrictions of frames require the source host to break a long message into individual pieces that meet both the minimum and maximum size requirements.
- Each segment is encapsulated in a separate frame with the address information, and is sent over the network. At the receiving host, the messages are de-encapsulated and put back together to be processed and interpreted.
- Using segmenting, we can do multiplexing:
	- If we have it, then 2 users can send data "concurrently" so both wait for same time for data delivery
	- If do not have it, then PDU will be delivered in order of sending, meaning 1 user will have to wait for the other to complete delivering
- segmenting/multiplexing is reliable, but creates more complexity/is time consuming. 
### Message Timing, there are 3 factors: 
#### Access Method:
- Two computer cannot "speak" at the same time, so it is necessary for computers to define an access method. Hosts on a network need an access method to know when to begin sending messages and how to respond when errors occur.
#### Flow Control:
- A sending host can transmit messages at a faster rate than the destination host can receive.
- Source and destination hosts use flow control to agree on correct timing for successful communication.
#### Response Timeout:
- Hosts on the network also have rules on how long to wait for responses and what to do if a response timeout occurs.
### Message Delivery Options:
- Unicast
- multi-cast
- broadcast
- Additionally, in some message delivery options, hosts need acknowledgement while some do not.
## TCP/IP:
 - There are 4 layers:
1) Application Layer
2) TCP: 
	- takes the data, divides it into parts and marks them, called segments and it establishes the end-to-end connection between devices
3) Internet Layer (IP): 
	- encapsulates the segments into packets and giving them an address, and delivering them across the best path to the destination host.
4) Network Access (has 2 components):
	1) communication over a data link: Data-link management protocols take the packets from IP and format them to be transmitted over the media.
	2) physical transmission of data: The standards and protocols for the physical media govern how the signals are sent and how they are interpreted by the receiving clients.

- Protocol Suite: Any protocols from the layers in TCP/IP can work in combination with different layers, and the combination of these different protocols is called protocol suite.

- In OSI model, don't go into details, its only a "reference model", if we want to implement it, we will use a "protocol model", called a "TCP/IP Model", it simplifies the first 3 layers from OSI into "Application", and also the other layers are grouped into total of 4 layers of TCP/IP.

- For OSI:
	- Session manages the data transfer, but on the application level
	- Router operates up to the network layer, 
	- Each layer communicates the same layer on another device: 
		- routers don't care what happens in the layers below, it just looks at the packet, so it gives the impression that each layer is communicating with the same layer on any different device, by doing this separation, we can do anything without troubling the other layers
	- Data link, IP address can change according to the network we are in, here we are talking about the MAC address
	- Physical are the actual bits that are being transmitted


- How to know IP address? The http protocol will go to the DNS and there they have servers that can find the IP address of the domain name
## How to know MAC address of another device? 
There are 2 scenarios:
### 1) devices connected to the same LAN:
pc1 knows the IP address of the pc2, but does not know its MAC address,
- Uses ARP (address resolution protocol), will send a broadcast message to the LAN, telling what the IP address is of the pc2, the other devices will look at it, and if not their IP address, then will not reply, but pc2 (that is the owner of that IP address), then server will reply to sender by sending its MAC address.
### 2) devices are on different networks: 
- The last part of the IP address identifies the unique device e.g. In the IP address "192.168.1.110", here "192.168.1" identifies a network, and "110" identifies the device
1) First sees if device is in the same network, then the device will send and ARP
2) if not, then since the device is connected to a gateway router, we get its address
3) So if the other device is not in our local network, then we will use the MAC address of the gateway router
4) So in the encapsulated PDU, the data link frame header will contain MAC addresses of my device and the MAC address of the gateway router, but the Network layer IP packet header will contain my IP address, but the destination will be the actual servers IP address that is on another network

___
References:
[Intro to networks-LoyolaUni](http://intronetworks.cs.luc.edu/1/html/intro.html)

