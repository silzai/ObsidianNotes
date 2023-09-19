- Started as LAN which evolved to WAN then the internet
- There are 3 network components:
	1) Devices:
		- end devices
		- intermediary network devices: devices that enable communication between end devices.
	2) Media:
		- copper wires: DSL (digital subscriber line) wires, can also use coaxial cables
		- fiber optic
		- Wireless
	3) Services: the software

- Types of networks:
	- LAN: connection in a certain local geographic area
	- WAN: If we connect 2 LANs then it is called a WAN.
 - extranet: allows external entities, people to access our intranet

### A Reliable Network:
1) Fault tolerance: There are 2 type of networks:
	- circuit switched: is old type of network, advantage is that the connection is reserved for you, other people cannot access it when you are using it, so it is reliable.
		- if the connection goes down, we cannot do anything
	- packet switched: People can share the same connection, each packed has (source address, destination address, sequence number)
		- If the connection goes down, then we can just use another line
2) Quality of service: 
	- need a certain level of performance to be satisfied of the network, to do this, priority decisions should be considered for time-sensitive communication eg. for video calls against emails
3) Scalable: Tier-1 ISPs (eg. Verizon) will give subscription to Tier-2 ISPs, then they will give subscription to Tier-3 ISPs (local)
4) Security: 
	- external threats:
		- trojan horse: looks like a useful software, but also actually contains malicious things
		- spyware: software sending our info to outside sources
		- zero-day attacks: there is a new virus, so anti-virus software cannot catch it
		- DoS attack: Too much bogus requests/traffic that legitimate users cannot access the service (we also have distributed DoS)
		- identity theft:
	- Solutions:
		- antivirus
		- firewall filtering
		- access control lists (who can access what in an organization regarding internal threats)
		- intrusion prevention systems
		- virtual private networks (we are actually in a public network, but makes it seem like we are in a private network)

Network Trends:
- BYOD
- Online collaboration
- Video communication
- Cloud computing
- powerline networking: can also use our power line (a building's electrical system as the transmission medium and regular wall outlets as connecting points) for data transfer
- wireless broadband