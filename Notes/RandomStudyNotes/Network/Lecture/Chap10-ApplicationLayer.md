# Application Layer Protocols for Email
- From last server to destination:
	- POP3: 
		- post office protocol 3
		- whole email is downloaded from server to the device, and the email is not found in the server
	- IMAP:
		- Internet Message Access Protocol
		- we can download parts of the email, and get the whole email, but also keep a copy of the email in that server
# Application Layer Protocol for Domain Name Resolution
- DNS server will get the actual IP address, and will be sent to the browser, which will contact the destination
## DNS Message Format

## Recursive DNS
- DNS client will send to local DNS server, which will send to top level domain servers if those servers dont know the domain name
## Iterative DNS
- DNS client will point you to another DNS server, and we will again go and ask another server, and this will continue until a domain name is found
# Application Layer Protocol for Dynamic Host Configuration

# Application Layer for FTP
- Control Connection: Need one control connection, need port 21
- Data Connection: But can do any number of data connections
- SMB (not standardized):
	- it was proprietary, but was widely used
	- can log in remotely to a server and use its resources, 