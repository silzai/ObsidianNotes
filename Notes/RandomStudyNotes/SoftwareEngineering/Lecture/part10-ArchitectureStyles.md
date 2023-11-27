- arc is big field
- soft architect is a critical person, and gets the highest salary
- architectural patterns/styles are macro level patterns (as opposed to design patterns that are micro level)

- architectural styles show high level design choices
- We can use UML (or rarely ADL) to show architectural designs/styles 
# Elements of Architectural Styles
- There are 3 components, sometimes called 3C
1) Component:
	1) Has a subset of the system functionality
	2) to access it, we need interfaces
2) Connector:
	1) Used to allow components to communicate with each other
	2) are application independent i.e. we can reuse them
	3) For example: pipe, stream, message passing, procedure calls, service bus
3) Configuration:
	1) We select several components and connectors and combine them in a way to provide a functionality called a configuration

>[!note]
>architectural styles are a collection of architectural design decisions

>[!note] Architectural Design Definition
>We know that these worked before, and provide beneficial qualities in a system, while following specific development constraints
# 1) Call and Return Style
- Used a lot for 40 years
## Layered Style:
- disadvantage: Cannot be applied to too many software systems
- There can be cross cutting layer/concern that is shown as a vertical box along side the main layers, there can be several cross-cutting layer

- To deploy a layered style application:
	- every layer can be deployed to 1 machine only or to different machines, or a mixture of both

- Random difference between web and application server:
>[!note] Web server
>Web server is a subset of application server

>[!note] Application Server
>application server is used to enable interaction between end-user clients and server-die application code

# 3) Data Flow
## Pipe and Filter
## Batch Sequential

- Pipe and filter VS batch sequential
- 

# 4) Virtual Machines (Its a architectural style, not like our usual VMs)
## Interpreters
- We have 
## Rule-Based Systems
- also called knowledge based systems
- inference engine will look at knowledge base 
# 5) Data-Centric Systems
## Blackboard Style:
- the data store is responsible to notify parties of change
- 
## Repository Style:
- the parties check the data-store for changes