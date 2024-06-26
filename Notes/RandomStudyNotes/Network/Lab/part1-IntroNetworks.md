# Cisco Packet Tracer
- Packet tracer allows simulation of networks such as testing, configuration
- we can create or recreate predefined topologies and configure switches, routers
# Creating a simple network:
- Need at least 2 end devices (computers or servers)
- connect them both using a switch with any media of our choice, a switch is used to forward a packet
- different medias can be used to connect routers such as fiber optic, cables, waves
### 1) To choose a specific port to use for end/network devices 
- we will use the third cable in the "connections" tab,
- gigabit ethernet is faster
- console port is used to access the switch
- side-note: RS-232 is a serial port (serial ports are used for any purpose)
### 2) To configure the IP address of the end-devices
- For end devices, if we click on the device, and go to the "desktop" tab and go to "IP configuration"
- in "IP configuration":
	- ipv4 address: we put our own IP address
	- subnet mask: we put our own subnet mask
### 3) To configure the networking devices
- Switches/routers have an operating system called IOS (internetworking operating system)
	- to access it, we need connections to it using a "console cable" (can also use SSH port to access it remotely) 
	- It will connect to the "console" port of a switch and computer
	- We can use a terminal program such as "TerraTerm" to play with the operating system of switch using an end-device (computer)
## TerraTerm:
- select "serial" option on start up
- can write "show version" to see the version details
- 
# To verify the connection and check if the network is working
- we can do 2 things
## 1) Use the "command prompt" of a device:
- we will go to "desktop" tab
- then go to "command prompt"
- will type the command "ping (destination address)"
- this command will send 4 packets to the destination,
	- sometimes checking with only 4 packets is not reliable, so we can set the number of packets to send by ping
- if these packets are sent to the destination, destination device will send an acknowledgment/reply to the sender device
## 2) Use the "Add simple PDU":
- on the top left tab, we can select "add simple PDU"
- click the devices that we want to send the packet to and from

- Routers have the capacity of routing the traffic
- Routers need to know the IP address to work, and it is initially disabled, so we need to turn it on
- any device on the internet has a unique address, IP address
- we also have a subnet mask that identifies the network as a whole

- Once we are done with the logical aspect, we have to rearrange the components in the physical aspect

- There is real-time (faster) and simulation (slower), simulation shows the movements of packets (PDU) from one location to another

### Uses of the IOS:
- Security: We can allow/block traffic/data, TCP/UDP packets using the IOS
- Routing: We can also do routing (which route to take for best path) 
- Addressing: switches and routers have many ports, so we can configure them
# Navigating around the IOS:
- To access the IOS CLI, we can use the console port of the networking device, and connect it to the computer using RS-232 port.
- Then will go to the terminal of the computer, and will see the prompt: 
```
//if we are working with a switch, will get this prompt:
switch>
```
## User mode
- (will see a greater than symbol for this in the prompt) 
- it is just used to check the current configuration, and we cannot the change the device configuration.

## privilege/enable mode 
- To change to `privilege/enable` mode, we will type:
```
switch> enable
```
- will see a hashtag for this in the prompt like this to confirm we are in privilege mode:
```
switch#
```
- now when we type `?` , we will see all the commands that are available in privilege mode.
## global configuration mode
- There is another sub-mode called "global configuration mode".
- Can only go here through "privilege mode". Have additional commands using this. to go to this, we will type:
```
switch# configure terminal
```
- Now, the prompt will show `switch(config)#` to confirm that we are in global configuration mode.

## line-interface
- There is another sub-mode after global configuration mode, called line-interface, will type:
```
switch(config)# line console 0
```
- To confirm that we are in line-interface, will have `switch(config-line)#` for the prompt
- To go back to privilege mode from global configuration mode or from a sub-mode backwards, will type `exit` 
#### For Help:
- can write `cl?` this will list all the commands that starts with `cl`, so `?` acts like a wildcard and lists all the commands that start with this.

# To change device name
- In global configuration mode, to name a device `sw-floor-1`, type:
```
switch(config)# hostname sw-floor-1
```
- if we close the terminal, is the name saved or not?
#### Then to save the name (saving the whole config actually)
- There are 2 types of configurations, running-config which is stored in temporary memory (to see this config file, will write `show run`) and startup-config which is stored in permanent memory or NVRAM (to see this config file, will write `show start`)
- so we need to save the running-config to the startup-config, 
- so When device starts, the device copies the startup-config to the running-config, that means we have to save everything to the startup-config if we want to save it permanently.
- to do this:
```
// go back to enable/privilege mode after renaming then write:
switch# copy run start
// Then press tab to autocomplete and press enter
```
- can `reload` in privilege mode to restart the networking device and see if the changes are saved.

# Securing the Device:
- To add a password to the networking device using the IOS:
- Port number always starts with 0 in a router, to add a password to this:
- will go to `line console 0` and type:
```
// This will set password to the intial entry to switch's console/terminal
// if want to set the password to "cisco":
switch(config-line)# password cisco
switch(config-line)# login
```
- will also need to save the password using the method we used to save the name.

-  Any user can open run file by typing `show run` and see all the passwords listed, so we will also set a password for enable mode:
```
// This will put password to enter privilege/enable mode
switch(config)# enable password cisco
// enable secret <string> command will override the enable password, and will encrypt the password in show run config file
```
#### To encrypt all passwords in run config:
- From global configuration mode, type:
```
switch(config)# service password-encryption
```

#### to add a banner message before the password:
- from global configuration mode, type:
```
switch(config)# banner motd # this is a banner message! type a password to enter!!! #
```

#### To remove the device name:
- go to global configuration mode and type:
```
router(config)# no hostname newrouter
```
#### To disable password:
- go to global configuration mode and type:
```
switch(config)# no enable secret
```

# IP address of a switch
- The idea of having an IP address on a switch is to do remote management
- Switch indicates that it is a LAN
- IP address of switch does not have physical interface, so we use VLAN for the interface, (v is for Virtual)
- router has physical interface
## Set IP address of a switch
- to go to the interface of the switch, type `switch(config)# interface vlan 1`
- `switch(config-if)#` in prompt means we are in the interface
- type `no shutdown` to enable the VLAN interface
- to disable the interface, type `shutdown`

- `show ip interface brief` will show all the device interfaces

# To change IP address of any device in windows:
- maybe first need to enable file sharing on windows computer to even ping other device
- change adapter settings
- click ethernet, then properties
- go to internet protocol version 4
- then mark the "use the following IP address"
- remember to configure the pc back to assign IP address automatically
- can also set the default gateway from there

# Set default gateway of switch

```
%Enter global configuration mode.

S1# configure terminal

%Configure the switch default gateway.

S1(config)# ip default-gateway 172.17.99.1

%Return to privileged EXEC mode.

S1(config)# end

%Save the running config to the startup config.

S1# copy running-config startup-config
```

>[!note] Default gateway for a PC
>The default gateway of a PC can be set easily by going to "Desktop" then "IP configuration" of that PC
