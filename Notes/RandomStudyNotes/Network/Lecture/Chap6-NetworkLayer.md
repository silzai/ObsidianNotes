- NAT (network address translation): The router converts the IP addresses by changing the IP address in layer 3 (network layer) and the port number in layer 4 (Transport layer)
## Features of IP:
- connectionless: when sending data, sender doesn't need to ask the receiver if he wants packet or not, but just sends it
- best effort: packet will maybe reach or maybe not, because error checking is already present in transport layer and data link layer
- media independent: Can use IP protocol through any medium, but only the IP header is adjusted, but the packet will be fragmented depending on the type of medium
## IPv4 Packet:
- ==need to memorize the whole packet arrangement==
- time-to-live: at each router, this value is decremented by 1, and when reaches 0, packet is thrown away, this avoids the packet roaming around the network indefinitely

- Router can also fragment a packet into fragmented packets if the medium cannot handle that size, then will use some features in the IP header to identify the fragmented packets.

## IPv6 Packet:
==need to memorize the whole packet arrangement==
- traffic class field has related to QoS, sends congestion notification in case of traffic jams
- Got rid of fragmentation but has extension headers, where in some cases the router will look at the extension header (but usually the extension header is accessed at the destination) (not included in course)
- ***next header*** will have a pointer to extension headers/protocols if there are any, otherwise it will just point to the TCP header (the next header naturally)
- there is flow label where if given, then all packets will follow same path between routers
- We eliminate NAT, 
	- as it violates end to end connectivity
	- violates IP uniqueness
	- violates rules of the protocol stack
- removes unnecessary headers/fields:
	- eliminate IHL
	- fixed size of bytes
- IPv6 provides security as such:
	- has flow label

## Host Routing:
- For IPv4
- Loopback address: 127.0.0.1 (or any address starting from 127.0.0.1)
- to get the routing table on windows, do:
```
netstat -r
```
- pc needs the routing table to see what to do with the packet, i.e. send to itself or send elsewhere
- netmask is a value that is used to separate any ip address and get the network part (or we can get the whole ip address also by keeping the subnet mask as 255.255.255.255), we do logical AND with Netmask , the part where netmask is 0 at the end will separate the IP address from the network address.
- ip address slash a number: the number indicated the number of bits used in the network part
- We take the IP address to be explored, and do AND with the subnet mask, and compare it with the "network destination" in the same line we did the mask with, if the values match, then we will use that interface==??==
- when more than one line matches, then use the line where the subnet mask has greatest number of ones, if two match, then use the line with the lowest "metric" (the route with the least cost in the physical layer)
- the interface column then routes the packet to the desired.==??==

## Router Routing: