## Cisco Packet Tracer
- Packet tracer allows simulation of networks such as testing, configuration
- we can create or recreate predefined topologies and configure switches, routers
### Creating a simple network:
- Need at least 2 end devices (computers or servers)
- connect them both using a switch with any media of our choice, a switch is used to forward a packet
- different medias can be used to connect routers such as fiber optic, cables, waves

- to choose a specific port to use, we will use the third cable in the "connections" tab, gigabit ethernet is faster
- console is used to access the switch
- side-note: RS-232 is a serial port (serial ports are used for any purpose)

- For end devices, if we click on the device, and go to the "desktop" tab and go to "ip configuration"
- in "ip configuration":
	- ipv4 address: we put our own ip address
	- subnet mask: we put our own subnet mask
- For servers we will do the same also

- Switches/routers have an operating system called IOS (internetworking operating system)
	- to access it, we need connections to it using a "console cable" (can also use SSH port to access it remotely) that will connect to the "console" port of a switch and computer
	- We can use a terminal program such as "TerraTerm" to play with the operating system of switch using an end-device (computer)

- TerraTerm:
	- select serial
	- can write "show version" to see the version details
	- 

To verify the connection, to check if the network is working, we can do 2 things
Use the "command prompt" of a device:
- we will go to "desktop" tab
- then go to "command prompt"
- will type the command "ping (destination address)"
- this command will send 4 packets to the destination,
	- sometimes checking with only 4 packets is not reliable, so we can set the number of packets to send by ping
- if these packets are sent to the destination, destination device will send an acknowledgment/reply to the sender device
Use the "Add simple PDU":
- on the top left tab, we can select "add simple PDU"
- click the devices that we want to send the packet to and from

- Routers have the capacity of routing the traffic
- Routers need to know the IP address to work, and it is initially disabled, so we need to turn it on
- any device on the internet has a unique address, IP address
- we also have a subnet mask that identifies the network as a whole

- Once we are done with the logical aspect, we have to rearrange the components in the physical aspect

- There is real-time (faster) and simulation (slower), simulation shows the movements of packets (PDU) from one location to another