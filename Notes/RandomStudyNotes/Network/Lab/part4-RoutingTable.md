- To see the the routing table for router:
```
router# show ip route
```
- Need to enable the interface for the routers:
- as soon as we enable the interface by `no shutdown`, the router identifies that this router interface is directly connected

# To set static routing:
- in global configuration mode, do:
```
router(config)# ip route < (from) ip-address with .0 at the end> <subnet mask> < (to) next hop ip address>
```
for example:
```
router(config)# ip route 10.1.1.0 255.255.255.0 209.165.200.225
```
# Why set static routing?
- If 2 hosts are on different networks (they have different routers), then they do not know where each other is and cannot communicate, so need to set the static routing in the router.

# IPv6:
- enable IPv6 on router (so it can forward packets):
```
R1(config)# ipv6 unicast-routing
```
- To assign IPv6 address:
```
R1(config-if)# ipv6 address <ipv6 address>/subnet
```
- To assign 