We have 4 layers:
- TCP takes the data, divides it into parts and marks them, called segments: it establishes the end-to-end connection between devices
- then in IP we have packets (it is the address)
- then on the ethernet layer we call the data a frame (it is what is being done in between the end devices)

- In OSI model, don't go into details, its only a reference model, if we want to implement it, we will do a "protocol model", called a "TCP/IP Model", it simplifies the first 3 layers from OSI into "Application", and also the other layers are grouped into total of 4 layers of TCP/IP.

- For OSI:
	- Session manages the data transfer, but on the application level, such as 
	- Router operate up to the network layer, 
	- Each layer communicates the same layer on another device: 
		- routers don't care what happens in the layers below, it just looks at the packet, so it gives the impression that each layer is communicating with the same layer on any different device, by doing this separation, we can do anything without troubling the other layers
	- Data link, IP address can change according the network we are in, here we are talking about the MAC address
	- Physical are the actual bits that are being transmitted

- Protocol Suite: Any protocols from the layers in TCP/IP can work in combination with different layers, and the combination of these different protocols is called protocol suite.

- Multiplexing:
	- If do not have it, then PDU will be delivered in order of sending, meaning 1 user will have to wait for the other to complete delivering
	- If we have it, then 2 users can send data "concurrently" so both wait for same time for data delivery

- How to know IP address? The http protocol will go DNS and there they have servers that can find the IP address of the domain name
- How to know MAC address? The there are 2 scenarios, 
