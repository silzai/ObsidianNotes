# VLSM:
- Often assigning subnets in the classic way, we may waste many addresses.
- We can assign these efficiently as to not waste these extra addresses
- so we will pick any subnet from the extra/remaining subnets and borrow more bits from *that* subnet, so that *that* subnet will have more subnets inside it.

___
#### Side note: Addressing Schemes
- If we are a sysadmin, then assigning fixed devices like printers and servers etc., assigning these devices a fixed IP address (as opposed to using DHCP) using the same convention is important so that we may not get confused as the network grows or for troubleshooting.
- for example, we can make all routers to have the first IP address in that network, and assign all other devices from DHCP pool.