- IP addresses are in dot decimal notation 
# To convert from decimal to binary and back (do it quickly)
- to convert from decimal to binary: 155
	1) take the decimal value, then compare it with the MSB, and if greater then, will put 1 in the MSB position, otherwise 0
	2) Then subtract the decimal value with the MSB, and then compare the result of the subtraction with the bits before the MSB and if lower than them, then add 0s
	3) Then put 1 where the result is greater than or equal to that bit position
	4) then minus and repeat from 1).

# IPv4 Subnet Mask:
- The host part being all 0 in an IP address identifies the network part of the IP address
- An IP address of a network can contain addresses from $size(network \ address) +1$ to $(broadcast \ address) - 1$ 
- also a subnet mask has a property that it always starts with 1s and ends with 0s, i.e. there is no in between number for the subnet mask
 >[!info] To find number of devices that a network can contain:
 > $$Number \ of \ hosts=2^n-2$$
$where \ n = \text{number of bits in host part}$
 and we are subtracting 2 because (broadcast and network addresses) are not included in this

# Side note:
- A network admin can either set the network configuration of devices manually (static assignment of IP addresses) or dynamically (DHCP)
- DHCP:
	- dynamic host configuration protocol
	- when we join the network, the network will have a pool of available IP addresses, the DHCP server will give us one of these IP addresses
	- then when leave the network, it takes the address away, and give another one on next connection
# Types of communications of hosts:
- directed broadcast: need to broadcast message to a remote network.
- limited broadcast: broadcast to local network only
- multicast address: each multicast group has a unique multicast address (how are all these assigned), to send to specific addresses

# Categories of IPv4 addresses:
- There are 6 kinds of IP addresses
## 2 main IP Addresses:
### 1) private:
- following network address ranges are private IP addresses:

| Starts from | Ends at        |
| ----------- | -------------- |
| 10.0.0.0    | 10.255.255.255 |
| 172.16.0.0  | 172.31.255.255 |
| 192.168.0.0 |        192.168.255.255        |
### 2) public:
- when we try to go out of the local network, will need to use addresses assigned by the ISP
## 4 special IP Addresses:
- 4 special IP addresses and their ranges:

|  IP Address Type   | Starts from |     Ends at     |
|:------------------:|:-----------:|:---------------:|
|  3) Loopback Address  |  127.0.0.0  | 127.255.255.255 |
| 4) Link Local Address | 169.254.0.0 | 169.254.255.255 |
|  5) TEST-NET Address  |  192.0.2.0  |   192.0.2.255   |
|    6) Experimental    |  240.0.0.0  | 255.255.255.254 |

>[!info] link local address: 
in case we don't have a DHCP server, we can use link local address, where the operating system of device assigns an IP address
## Legacy Classful IP Addressing:
- Nowadays we use classless addressing, since legacy classful addressing is obsolete
- RIR (Regional) these get chunks from AIANA and give to companies

- There are different classes (A, B, C, D, E) and the classes and their ranges are:

| Class | Starts from | Ends at |
|:-----:|:-----------:|:-------:|
|   A   |      0      |   127   |
|   B   |     128     |   191   |
|   C   |     192     |   223   |
|   D   |     224     |   239   |
|   E   |     240     |   255   |

# IPv6
## The IPv6 address has 2 parts:
- prefix: This is simply the network part of IPv4 address
- interface id: This is simply the host part of IPv4 address

- Since IPv6 supports more devices than IPv4 and is better than that, it is still not implemented fully because:
- The internet (and every component) right now is built on IPv4, and is not feasible to change everything to IPv6 to right away
- So in this intermediary stage, both are existing, upto the point where IPv4 will become obsolete
- But in this intermediary stage, to implement this at the moment, we can do
## Dual stack
- Devices will have both IPv6 and IPv4
## Tunneling
- will transmit IPv6 over IPv4 by encapsulating the IPv6 packet in a IPv4 packet (done in layer 3)
- The local networks will have IPv6 devices, while the tunnel will contain
## Translation
- Router will have a NAT64 table and will translate IPv6 to IPv4 and vice versa, so that packet can be transmitted.
# IPv6 Address representation using hextets
- IPv6 is represented in hexadecimal as opposed to dot decimal notation of IPv4.
- Will have 8 hextets
- remove leading 0s in each hextet
- use :: (double colons) for a sequence of 0 hextets (can only do it )
# Categories of IPv6 Addresses:
## Unicast
- There are 6 types:
	- global unicast
	- link-local (cannot pass the router)
	- loopback (all 0s except the LSB is 1)
	- unspecified address (all 0s)
	- unique local (can pass the router, but will only remain in the local network)
	- embedded IPv4
## Multicast
- same
## Anycast
- if it is destination, then any device that has that address can process that packet

# ???
## EUI-64:
- First take MAC address of device
- insert FFFE in the middle of OUI and host in the MAC address
- then flip the 7th bit

## Solicited Node Multicast address
- The prefixes are given: FF02 and ==???==
- If we have IPv6 address and need to do solicited multicast
# ICMP:
- ICMP is used with IPv4 or IPv6 for managing the 
- ICMP has messages
- ping uses ICMP

 >[!info] To find number of devices that a network can contain in IPv6:
 > $$Number \ of \ hosts=2^n-1$$
$where \ n = \text{number of bits in host part}$
 and we are subtracting only 1 because broadcast is not included in this as it has a different address

