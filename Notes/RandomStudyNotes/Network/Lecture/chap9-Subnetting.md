>[!important] Kinds of Designs for Subnetting
>- based on number of hosts: will count from right to left and count the required bits to accommodate the number of hosts
>- based on number of subnets: will count from left to right and count the required bits to accommodate number of subnets
# VLSM:
- Often assigning subnets in the classic way, we may waste many addresses.
- We can assign these efficiently as to not waste these extra addresses
- so we will pick any subnet from the extra/remaining/any subnet and borrow more bits from *that* subnet, so that *that* subnet will have more subnets inside it.
## VLSM in IPv6:
- The following is a representation of a IPv6 packet with a **subnetting scheme**: 

| Global Routing Prefix | Subnet ID | Interface ID | 
| --------------------- | --------- | ------------ |
- The Subnet ID in IPv6 will be in multiple of 4 (i.e. one hextet)

>[!info] Side note: Addressing Schemes
>- If we are a sysadmin, then assigning fixed devices like printers and servers etc., assigning these devices a fixed IP address (as opposed to using DHCP) using the same convention is important so that we may not get confused as the network grows or for troubleshooting.
>- for example, we can make all routers to have the first IP address in that network, and assign all other devices from DHCP pool.

- 