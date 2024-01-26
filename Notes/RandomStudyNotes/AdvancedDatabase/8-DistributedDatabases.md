- chap-23
>[!info] Distributed Computing
>- Nodes are connected by a network
>- A task is split to different nodes (computers/processors) and they will execute and then a master node will collect the solution from the participating sites. (there may not necessarily be a master)
>- This allows to handle big data quickly
# What makes distributed computing?
- We have nodes that are actually DBMSs and are connected by a network
- they must be logically inter-related (i.e. each nodes belongs to a university or hospital only) 
- there may be absence of homogeneity: different types of DBMS (i.e. relational DBMS, object DBMS etc.) may be implemented on different nodes.
- A distribute DBMS system manages the distributed database
- Networks may be over a LAN or WAN
# Properties of distributed databases:
- Transparency: 
	- The client should think that he is using a simple DBMS, so hiding the fact that it is distributed, otherwise, it will add complexity to the client. There are different types of transparencies.
- availability:
- reliability:
- scalability:
	- horizontal scalability: Expanding the number of nodes in a distributed system
	- vertical scalability: Expanding capacity of the individual nodes
- partition tolerance: 
	- System should have the capacity to continue operating while the network is partitioned
- Autonomy:
	- how much freedom each node has to handle its data
# Techniques for Distributed System:
## Policies of Data Fragmentation:
- fragments are logical units of databases
	- horizontal fragmentation: (also called sharding)
		- divide data through the rows
		- (a shard is a subset of the tuples)
	- vertical fragmentation:
		- divide data through the columns
	- hybrid (both vertical and horizontal)

- we have a metadata that stores information related to fragmentation called *fragmentation schema*
- *allocation schema*: describes the allocation of the fragments to nodes of the distributed database
## Policies for Replication and Allocation:
- *allocation schema*: describes the allocation of the fragments to nodes of the distributed database
- Replication:
- How many copies of data do nodes keep:
	- fully replicated:
		- replication of whole database at every site in distributed system (increases availability, but updates are slow)
	- non-redundant allocation:
		- 1 fragment at each site
	- Commercial systems do partial replication
- Technique:
	- if this particular element is accessed multiple times, then we can keep copies all out
## Concurrency Control in Distributed Systems:
- each item has many copies, but one copy is called distinguished copy
- A lock is only applied to this distinguished copy, so need to acquire lock on this copy
- primary site: all distinguished copies are stored at the same site (node) (locks are targeted at this site)
	- so sometimes need a backup site, in case the primary site fails
- distributed concurrency control using "Voting":
	- no distinguished copy
	- each copy has its own lock
	- A node wants a lock, so a broadcast is sent to all nodes, and by "voting", the opposing nodes (low in number of votes) that also want the lock, will have their transactions aborted to give the lock to the node wanting it.
## Recovery in Distributed Systems:
- The log is kept at a place based on the design decision.
- uses distributed commit
- There are two protocols:
### two phase commit protocol:
- there is a controller that sends message to all nodes, and when receives reply that all are committed 
- then controller tells them to send 
### Three phase commit protocol:
- commit issues a prepare commit message to all nodes
- at failure we can safely assume, that any transaction that replied to prepare to commit has succeeded, and vice versa.

# Types of distributed systems
- federated databases are a "boom" in medical systems because of the privacy with it.

,السلام علیكم

I am Basil and I study CS at Qatar University (I'm in my 3rd year). I got your contact from my father who took it from your brother as he works in the same company (QAFAC).

If you have the time, then I would like to meet on phone or physically (on the time and place of your choice as I have winter holidays).

I wanted advice about the general job market here in Qatar, how to apply to companies and internships in the upcoming summer.

thnkss a lot.