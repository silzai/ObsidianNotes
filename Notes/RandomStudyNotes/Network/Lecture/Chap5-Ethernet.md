- Ethernet has different flavors
- 802.3 MAC, 

- VLAN 
>[!info] broadcast
>put FF-FF-FF-FF-FF-FF (all 1s in binary format) in the destination MAC address in frame, and this will send frame to every device.

>[!info] multicast
>has 01-00-5E in the first part of the destination MAC address in frame, and this will send frame to multiple devices

>[!info] unicast
>otherwise if the destination MAC does not start with either of the values, it will be unicast to a specific device.

# Address Resolution Protocol (ARP):
- First send an ARP frame that is sent to everybody, which contains the IP of the destination, and that device will reply with a unicast directly to the sender, of the MAC address of the destination
- Then sender will send the actual data to destination
- After the initial request, the devices stores the MAC address of the destination in a table called ARP table/cache where it stores the MAC address of the devices that it has communicated with, and checks the table before sending an ARP in the future.

- if destination device is not in LAN, then need to send an ARP to receive reply from default gateway. ==need to check this in activity slides==

# Switching:
## Switches have a MAC address table:
- How do they build the switching table so a switch knows where to send a packet?
	1) switch will read the MAC address of the source and which port is connected to it (switch only records the source MAC address every time a frame is sent, never the destination)
	2) but then the switch does not know where to send it yet, so it will send the frame to all devices/ports, except to the device, called flooding
	3) the destination device will reply back to pc1 with a frame that will go through the switch's port, and the switch will record that this MAC address belongs to this port in the MAC table

## Two ways to forward frames in switches:
1) Store-and-forward: wait for whole packet to arrive
2) cut-through: has 2 subcategories
	- fast-forward:
	- fragment free:
## internal working of the switch, there is a buffer, 
- port-based memory: head line, a queue will occur if a frame is waiting for another frame to go through the same port
- shared-based memory: deposits all frames in a buffer with which all ports can access

- VLAN==????????????==
- Switches have IP addresses to work with them remotely, meaning switches do not have IP addresses to manage frames/packets but instead only for network administration.