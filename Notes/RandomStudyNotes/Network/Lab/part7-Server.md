- A server has a "services" tab, where we can assign the server any role.
# To make a server a DHCP server
- Will choose DHCP service, and "enable" the service
- will set the default gateway (this will be set as the default gateway for any host)
- Then input the start IP address (inclusive)

>[!note] Static IP Addresses
>Some devices need static IP address such as printers or switches, because these will remain here, and changing the IP address for these does not make 

>[!important] DHCP Relay Agent
>Need "DHCP relay agent" to allow DHCP messages to go through a router, so can put only 1 DHCP server, instead of a server for each subnet. 

# To make a server a DNS server
- If this is not working, we cannot go to a website using its website name (only its IP address)
- There is a hierarchy for DNS services
	- The organization connects to the ISP DNS servers
	- The ISP connects to the other DNS servers
	- That finally connects to the main DNS server
- If a domain name is not found in the local servers, then will move up the hierarchy to look for the domain name
>[!info]
DHCP server also has a parameter to configure the DNS server

- can see DNS servers services in windows as following:
```
User> nslookup
```

TFTP: cisco trivial file transfer protocol, only used by cisco devices
FTP: 

- to save the running config config to TFTP:
```
Router# copy run tftp
```