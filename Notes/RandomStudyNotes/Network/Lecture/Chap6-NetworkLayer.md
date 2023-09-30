## Features of IP:
- connectionless: when sending data, sender doesn't need to ask the receiver if he wants packet or not, but just sends it
- best effort: packet will maybe reach or maybe not, because error checking is already present in transport layer and data link layer
- media independent: Can use IP protocol through any medium, but only the IP header is adjusted
## IPv4 Packet:
- time-to-live: at each router, this value is decremented by 1, and when reaches 0, packet is thrown away, this avoids the packet roaming around the network indefinitely

- Router can also fragment a packet into fragmented packets if the medium cannot handle that size, then will use some features in the IP header to identify the fragmented packets.