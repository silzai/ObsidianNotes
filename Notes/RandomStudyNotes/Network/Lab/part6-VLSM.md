# How to do it?
- Suppose you have an IP address: 112.30.0.0/20
- And the network it is on has 6 networks (based on 6 interfaces of the router)
- And suppose that each 6 networks have a different number of hosts, and the number of hosts differ by a significant amount in number
- so that means, by subnetting, giving a fixed number of hosts to each network based on the biggest network will waste addresses in the smaller networks

- So to start variably subnetting to avoid wasting addresses, we will do:
	1) We will first identify the maximum number of hosts each network needs
	2) Then we will identify the network with the biggest number of hosts, and make a subnet of it
	3) The biggest subnet, has the lowest number of subnet masks
	4) Then from *that biggest* subnet, we will make *another* subnet to 
	5) Then will 
	6) always leave unused IP addresses at the end of the ranges


# another example: 145.45.0.0/21

# 145.45.0000 0001.0

| Network | hosts needed              | subnet addresses/mask | host range | broadcast address | default gateway |
| ------- | ------------------------- | --------------------- | ---------- | ----------------- | --------------- |
| 0       | 111 (7 bits for host)/25  |   145.45.1.0                    |            |                   | 0.0             |
| 1       | 166 (8 bits for host)/24  |  145.45.0.0/24                     |            |                   |   1.0              |
| 2       | 33 (7 bits for host)/26   |  145.45.1.128/26                     |            |                   |   2.0              |
| 3       | 16   (7 bits for host)/27 |   145.45.1.192/26                      |            |                   |    3.0             |
| 4       | 24   (7 bits for host)/27 |    145.45.1.224/26                     |            |                   |   4.0              |
| 5 (WAN) | 2    (7 bits for host)/30 |    145.45.2.0/26                     |            |                   |    5.0             |

unused range : 145.45.2.4 - 145.45.2.255

