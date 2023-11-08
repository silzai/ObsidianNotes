# The network layer consists of:
- Addressing end devices
- Encapsulation
- Routing
- De-encapsulation
# Features of IP:
## 1) connectionless:
- when sending data, sender doesn't need to ask the receiver if he wants packet or not, but just sends it
## 2) best effort (unreliable):
- packet will maybe reach or maybe not, IP does not care
- If out-of-order or missing packets create problems for the application using the data, then upper layer services, such as TCP, must resolve these issues. This allows IP to function very efficiently.
- Leaving the reliability decision to the transport layer makes IP more adaptable and accommodating for different types of communication.
## 3) media independent:
- Can use IP protocol through any medium, but only the IP header is adjusted
- Each medium has a different MTU (maximum transmission unit i.e. what size of a packet can be transmitted through that medium)
- In some cases a router, must split up a packet when forwarding it from one medium to a medium with a smaller MTU, this is called ***fragmentation***
# IPv4 Packet:
- need to memorize the whole packet header arrangement
- There are 12 main fields
- header length is 20 bytes 60 bytes (where optional fields and padding can be added) 

| IPv4 Header                                                        | /                                           | /                                                                                                                                                 | /                                                                       | /                                                           | /                                                                                  |
| ------------------------------------------------------------------ | ------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------- | ----------------------------------------------------------- | ---------------------------------------------------------------------------------- |
| Version (4 bits): IPv4 or IPv6?                                    | IHL (4 bits): length of header              | Differentiated Services (8 bits): For QoS; there are 2 parts; DSCP (priority of packet), ECN (notify destination router that there is congestion) | Total Length (2 bytes): total length of entire packet (header and data) | Identification (2 bytes): Will identify the fragment number | Flags: used to recover fragments of the packet (there are some incoming fragments) |
| Fragment Offset: The pointer of this fragment in the entire packet | TTL (8 bits): How long packet will be alive | Protocol (8 bits): identify protocol on the higher layer                                                                                          | Header Checksum: check integrity of the packet (check for error)                                                         | Source IP (32 bits)                                         | Destination IP (32 bits)                                                           |

>[!note]
>time-to-live (TTL): at each router, this value is decremented by 1, and when reaches 0, packet is thrown away, this avoids the packet roaming around the network indefinitely

>[!note]
>Since IHL is only 4 bits, and maximum length of header is 60 bytes, then how can we represent the length in only 4 bits? * To find the actual length, a calculation is done as follows:* $$length \ of \ header \ (in \ bytes) = IHL \times 4$$
# IPv6 Packet:
- need to memorize the whole packet arrangement
- header is 128 bits (16 bytes)

| IPv6                                                                            | /                                                               | /                                                                           | /                                                           |
| ------------------------------------------------------------------------------- | --------------------------------------------------------------- | --------------------------------------------------------------------------- | ----------------------------------------------------------- |
| Version: IPv6 or IPv4?                                                          | Traffic Class: (corresponds to differentiated services in IPv4) | Flow Label (20 bits): identify end to end flow, to provide fine grained QoS | Payload length: (corresponds to total length field in IPv4) |
| Next Header: indicates protocol in higher layer (also to any other next header) | Hop limit: (corresponds to TTL in IPv4)                         | Source IP (32 bits)                                                         | Destination IP (32 bits)                                              |

>[!note] Next Header
 Next header contains a pointer to any extension headers/protocols if there are any, otherwise it will just point to the TCP header (the next header naturally). this allows encapsulation of any protocol inside an IPv6 packet.

>[!note] Traffic Class
>Traffic class field is related to QoS, it sends congestion notification in case of traffic jams
## Has fewer fields than IPv4 header
- This makes IPv6 packet more simpler, and improves packet handling and efficiency on the router
- Got rid of fragmentation but has extension headers, where in some cases the router will look at the extension header (but usually the extension header is accessed at the destination) (not included in course)
- IPv6 eliminated NAT:
	- as it violates end to end connectivity
	- violates IP uniqueness
	- violates rules of the protocol stack
- removed unnecessary headers/fields:
	- eliminated IHL
	- fixed size of bytes
- IPv6 provides security as such:
# Host Routing:
- For IPv4
- There are 3 types of host routing:
	1) to itself
	2) to a local host
	3) to a remote host

> [!important] Routing Table
> A PC needs a routing table to see what to do with the packet, i.e. send to itself or send elsewhere on the NIC
- to get the routing table on windows, do:
```
netstat -r
```
## To find destination for packet in routing table of PC:
- This is a routing table:

| Network Destination | Netmask       | Gateway      | Interface     | Metric |
| ------------------- | ------------- | ------------ | ------------- | ------ |
| 0.0.0.0             | 0.0.0.0       | 192.168.10.1 | 192.168.10.10 | 25     |
| 127.0.0.0           | 255.0.0.0     | on-link      | 127.0.0.1     | 306    |
| 192.168.10.0        | 255.255.255.0 | on-link      | 192.168.10.10 | 281       |

- We will take the IP address to be explored, and do AND with the "netmask" column, and compare it with the "Network Destination" column in the same line we did the mask with, and if the "anded" value matches with the "Network Destination", then we will use the "Interface" column on that line to send the packet through that interface of the host PC.
>[!warning] when more than one line/entry matches the network destination
>when more than one line matches, then we use the line where the subnet mask has greatest number of ones, if two match, then use the line with the lowest "metric" (the route with the least cost in the physical layer)

>[!important] Netmask
>- netmask is a value that is used to obtain the network part from any IP address (or we can get the whole IP address also by keeping the subnet mask as 255.255.255.255), we do logical AND of IP address with netmask, and the part where netmask is 0 at the end will separate the IP address from the network address.
>- IP address slash a number: the number indicates the number of bits used in the network part

>[!note]
>The IP address where the host part is all 0 is reserved for the whole network, and no specific device on the network can have that address.
# Router Routing:
- There are two types of entries in a router routing table:
	1) Directly connected routes
	2) Remote routes
## Directly Connected Routes:
- The entries can be grouped as follows in this example of directly connected routes:

| Route Source (how the network was learned by router) | Destination Network (destination network, and how it is connected) | Outgoing Interface |
| ---------------------------------------------------- | ------------------------------------------------------------------ | ------------------ |
| C                                                    | 192.168.10.0/24 is directly connected,                             | GigabitEthernet0/0 |
| L (link local route identifies the router itself)                                                    | 192.168.10.1/32 is directly connected,                             | GigabitEthernet0/0 |

>[!note] Route Source
>Route source can have other values, for example,
>-  "S" which indicates a static route that was manually created by an administrator to reach a specific network
>- "D" Identifies that the route was learned dynamically from another router using the Enhanced Interior Gateway Routing Protocol (EIGRP).
>- "O" identifies that the route was learned dynamically from another router using the Open Shortest Path First (OSPF) routing protocol.
## Remote Routes:
- The entries can be grouped as follows in this example of remotely connected routes:

| Source Route | Destination Network | Administrative Distance (trustworthiness) | metric | next hop IP address | elapsed time since last update | 
| ------------ | ------------------- | ----------------------------------------- | ------ | ------------------- | ------------------------------ |
| D            |                     |                                           |        |                     |                                |

> [!note] Next Hop
> It is the next IP address of the networking device (router) that will receive the packet and forward it further

> [!note] Elapsed Time
> if this time is elapsed, then this row/entry will be removed from the routing table, it indicates how fresh the routing line is.