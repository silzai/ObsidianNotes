- IP addresses are in dot decimal notation 
- See how to convert from decimal to binary and back (do it quickly)
	- there are some tricks:
	- to convert from decimal to binary: 155
		1) take the decimal value, then compare it with the MSB, and if greater then, will put 1 in the MSB position, otherwise 0
		2) Then subtract the decimal value with the MSB, and the compare the result of the subtraction with the bits before the MSB and if lower than them, then add 0s
		3) Then put 1 where the result is greater than that bit position
		4) then minus and repeat from 1).

# IPv4 Subnet Mask:
- The host part being 0 in an IP address identifies the network part of the IP address
- An IP address of a network can contain addresses from $network \ address +1$ to $broadcast \ address - 1$ 
- also a subnet mask has a property that it always starts with 1s and ends with 0s, i.e. there is no in between number for the subnet mask
- to find number of devices that a network can contain: $$Number \ of \ hosts=2^n-2$$
	- $where \ n = \text{number of bits in host part}$
	- and we are subtracting 2 because (broadcast and network addresses) are not included in this
- directed broadcast: need to broadcast message to a remote network.
- limited broadcast: broadcast to local network only
- multicast address: each multicast group has a unique multicast address (how are all these assigned), to send to specific addresses
- DHCP:
	- dynamic host configuration protocol
	- when we join the network, the network will have a pool of available IP addresses, the DHCP server will give us one of these IP addresses
	- then when leave the network, it takes the address away, and give another one on next connection
- 