>[!warning]
>These notes are mixed up and incomplete
# Cross over cable
- we use different type(standard)
- A at one end and B at other end.
# Straight through cable:
- same standard at both ends
# Types of Connectors:
- RJ-11 end is for telephone lines
- RJ-45 is used for networks

- DCE controls the speed of data transfer
- DCE-Male
- DTE-Female

- In lab we will use serial cables to connect to 2 routers
- In real life we use ISP to connect 2 routers

- `ipconfig` in cmd to get all the info.
# Routing: lab 7
- How can a routing table help us decide which is right way to contact the destination?
- type `show ip route` in the command prompt in the router to after enabling
```
 Router>enable
 Router# show ip route
 Router#conf t (global configuration mode "configure terminal")
```
- Then enter configuration commands, one per line.
- note: to terminate the process, press Ctrl/z.
```
Router(config)# interface gi 0/0/0
Router(config-if)# ip address 192.168.1.1 255.255.255.0
Router(config-if)# no shutdown --> to save or enable the router interface
```

- the router table is created when we enable the interface (`no shutdown`)


in global configuration mode; type the following:
## for R1:
```
Router(config)# ip route 10.1.1.0 255.255.255.0 209.165.200.226
Router(config)# ip route 10.1.2.0 255.255.255.0 209.165.200.226
```
## for R2
```
Router(config)# ip route 192.168.10.0 255.255.255.0 209.165.200.225
Router(config)# ip route 192.168.11.0 255.255.255.0 209.165.200.225
```
# Lab 8:
- Finding number of hosts
- Will use only these values to build subnet mask:
0         00000000
128     10000000
192     11000000
224     11100000
240     11110000
248     11111000
252     11111100
254     11111110
255     11111111

### Example 1:
- IP address length = 32 bits
- 10.1.8.200/26
- 255.255.255.192 --> 192 bcz we need 26 1's 
- Network part = 26 bits
- Host Part = 32 - 26 = 6

- Network address (anding the device IP address with subnet mask): 10.1.8.192
- Broadcast address: 10.1.8.255

10.1.8.11001000 --> binary of 200
         .11000000
### Example 2:
- IP address = 32 bits
- 172.16.117.77/20
- 255.255.240.0
- Network part = 20 bits
- Host Part = 32 - 20 = 12 

Network address : 172.16.112.0
Broadcast address : 172.16.127.255 ????

172.16.01110101.01001101
          .11110000.00000000
          .01110000.00000000
- To find the number of hosts that an IP address can contain:
$$number \ of \ host = 2^{12}-2$$		

### Example 3
- IP address = 32 bits
- 172.16.128.48  --> how many bits?
- 255.255.255.240 
- Network part = 28 bits
- Host Part = 32 - 28 = 4 

Network address : 172.16.128.48
Broadcast address : 172.16.128.63

172.16.128.01001101
                .11110000
                .00110000
$$number\ of\ host\ bits = 2^{4}-2 =14\ hosts$$	

- example 4 
Ip address = 32 bits
192.168.33.63 --> how many bits?--> we count number of 1s
255.255.255.192
Network part =26  bits
Host Part = 32 - 26 = 6 

Network address : 172.16.112.0
Broadcast address : 172.16.127.255 ????

192.168.00100001.00111111
            .11110000.00000000
            .11110000.00000000
number of host bits = 2^6-2 = hosts



Example lab 8 ch 9 pdf:

Ip address = 32 bits
10.1.113.75/19 
255.255.224.0
Network part =19  bits
Host Part = 32 - 19 = 13

Network address : 10.1.96.0
Broadcast address : 10.1.127.255

for network:
10.1.01110001.01001011
      .11100000.00000000
      .01100000.00000000
for host:
10.1.01111111.11111111 --> 13 bits all 1s

number of host bits = 2^13-2 = hosts


# Legacy:

- too many host per network --> impractical
- imagine there are 2 labs each with 100 hosts but there is a single network. should we add another network? No because the host number is not too big so what we can do is divide the network into two instead of adding a new network
## Example 1:
- 192.168.1.0/24 
- Network part =24  bits
- Host Part = 32 - 24 = 8
/25 (borrowing 1 bit from host part to make new subnet)
number of host = $2^8-2 = 254$

## To find how many bits to borrow?
- First see how many subnets you want
- then do $$bits \ to \ borrow = log_2(NumberSubnetsNeeded)$$

- ...Continuing previous example here:
- Will borrow 1 bit like this:
192.168.1.00000000
              .10000000

network#0 : 192.168.1.0
network#0 : broadcast : 192.168.1.127 $\rightarrow$ last 8 bits changed to 1

192.168.1.11111111
network#1 : 192.168.1.128
network#1 : broadcast: 192.168.1.255

## Example 2:
Host ip address:172.16.77.120 
Original subnet mask: 255.255.0.0 /16
New subnet mask: 255.255.240.0 / 20
4 bits--> how many host we can have(question for Basil)
172.16.01001101.01111000 
          .11110000.00000000
          .01000000.00000000
172.16.64.0
network#0 : 192.168.1.0
network#0 : broadcast : 192.168.1.127 --> last 8 bits changed to 1

192.168.1.11111111
              .10000000
network#1 : 192.168.1.128
network#1 : broadcast: 192.168.1.255

- is there direct method to find subnet mask from slash notation?

# To divide a network into subnets
- handling smaller networks is easier than one large one
- to minimize the broadcast domain

- each router interface connection to another router belongs to a different subnet

## Example:
- To divide 192.168.200.0/24 to 4 subnets
- to make subnets, will need to see how many subnets the network is divided into, and how many hosts those subnets need
- Here we need 4 subnets, so we need to borrow bits from the host side, so to see how many bits to borrow, do: $$log_2(4)=2$$
- This means we need 2 bits from the host side to make 4 subnets

- Another example:
- 172.16.128.0/17 and need 9 subnets
- so will do $log_2(9)=3.2 \approx 4$ so we need to borrow 4 bits
- so $17+4=21$, so subnet mask for the subnets will be: $255.255.248.0$
- Now, by doing: $256-248=8$, so we will have subnet network addresses by increments of $8$
- So, the last value of network addresses of each subnet will be:

| 0   | 8   |
| --- | --- |
| 9   | 17  |
| 18  | 26  |
| 34  | 42  |
