# Use the router for DHCP configuration in Bahrain and Kuwait routers
- First configuring the default gateway of the LAN interface to apply DHCP to:
```
Router>enable
Router#config terminal
Router(config)#int fa0/0
Router(config-if)#ip address 192.168.1.1 255.255.255.0
Router(config-if)#no shutdown
Router(config-if)#exit
```
- Now adding DHCP property:
```
Router(config)#
Router(config)#ip dhcp pool MY_LAN
Router(dhcp-config)#network 192.168.1.0 255.255.255.0
Router(dhcp-config)#default-router 192.168.1.1
```
- Can exclude addresses in the DHCP pool like this:
```
Router(config)#ip dhcp excluded-address 192.168.1.1 192.168.1.10
```
- Finally will need to enable DHCP in all hosts (PCs).
# Use only 1 server in Saudi and UAE with DHCP relay agent
- First add DHCP pools to the server with proper names
- To do this, will first need to set the routing of the routers (static or OSPF, any will do)
- then simply write in the router of network that needs DHCP:
```
Router(config-if)# ip helper-address <IP address of DHCP server>
```
