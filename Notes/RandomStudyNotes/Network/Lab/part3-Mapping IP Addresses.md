- IP address need to be mapped to the MAC address of a device
- From the IP address we can identify which device to which network
- how to identify different computers on the same network (LAN)?
	- Use the MAC address
	- each computer has an ARP table to identify the MAC address of the other device on the network
	- A switch also has an ARP table
- To see the ARP table on windows computer:
```
arp -a
```
- To see ARP table on switch using IOS:
```
switch> show mac-address-table
```
- Need default gateway to communicate outside of a network (LAN).
- any router interface belongs to a different network, so each interface has a different IP address
- To configure a specific interface:
```
router(config)# interface fa0/0
```
- Then will be inside the interface like this, and will set the IP address of the interface and subnet mask like this:
```
Router(config-if)# ip address 192.168.1.1 255.255.255.0
```
- type `no shutdown` to enable the VLAN interface, otherwise the connection will not work.
- to disable the interface, type `shutdown`

- find MAC address of specific interface in router:
```
Router# show interfaces
```

- In switch, type:
```
switch# show ip interface brief
```