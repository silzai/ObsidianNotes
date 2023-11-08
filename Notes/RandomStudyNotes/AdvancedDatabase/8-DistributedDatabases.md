>[!info] Distributed Computing
>- Nodes are connected by a network
>- A task is split to different nodes (computers/processors) and they will execute and then a master node will collect the solution from the participating sites.
>- This allows to handle big data quickly

# What makes distributed computing?
- We have a node that is actually a DBMS that are connected by a network
- they must be logically inter-related (i.e. each nodes belongs to a university or hospital only) 
- there may be absence of homogeneity: different types of DBMS (i.e. relational DBMS, object DBMS etc.) may be implemented on different nodes.
- A distribute DBMS system manages the distributed database
- Networks may over a LAN, or WAN
# Properties of distributed databases:
- Transparency: The client should think that he is using a simple DBMS, so hiding the fact that it is distributed, otherwise, it will add complexity to the client. There are different types of transparencies.
- availability:
- reliability:
- scalability:
	- horizontal scalability:
	- vertical scalability:
- partition tolerance:
- Autonomy:
# Techniques for distributed databases:
## Policies of Data Fragmentation:
- fragments are logical units of databases
- shards are a subset of the tuples
- horizontal fragmentation:
	- divide data through the rows
- vertical fragmentation:
	- divide data through the columns
- hybrid (both vertical and horizontal)
- we have a metadata that stores information related to fragmentation called *fragmentation schema*
- *allocation schema*: describes the allocation of the fragments to nodes of the distributed database
## Policies for Replication:
## Policies for Allocation:
- *allocation schema*: describes the allocation of the fragments to nodes of the distributed database

