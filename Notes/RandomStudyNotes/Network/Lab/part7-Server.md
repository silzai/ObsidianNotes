- A server has a "services" tab, where we can assign the server any role.
# To make a server a DHCP server
- Will choose DHCP service, and "enable" the service
- will set the default gateway (this will be set as the default gateway for any host)
- Then input the start IP address (inclusive)

>[!note] Static IP Addresses
>Some devices need static IP address such as printers or switches, because these will remain here, and changing the IP address for these does not make 

>[!important] DHCP Relay Agent
>Need "DHCP relay agent" to allow DHCP messages to go through a router, so can put only 1 DHCP server, instead of a server for each subnet. 