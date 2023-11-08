- These are "structural diagrams" (as opposed to behavioral diagrams i.e. sequence diagram)
# Package diagram:
- idea is that we want to decompose large software system into different elements.
- packages are logical structures
- but we are not binded by the diagram, the implementation may be different
## Rules:
- Names are unique in a package
- 
# Component diagram: 
- idea of this is that components are easily replaceable (component based software engineering)
- can be a class, or more than a class, can be a jar file
- a component may have several interfaces
- has provided interfaces: which provides an interface
- has required interfaces: it needs that interface to function
- not mandatory to show ports
- So a component can only be reached through its components
# Deployment Diagram:
- need these diagrams for complex software systems, which have multiple hardware components, no need to make for small desktop application.
- shows how to map software components into hardware components
- Consists of:
	- nodes (hardware): represented as 3d cube
	- connection: defines the communication path
	- dependency
	- location
- while components and packages were logical representations, an artifact is a physical element in the system, and the artifact is a manifestation of a component which it is dependent of.
	- but no need to show the the manifestation dependency if not needed.