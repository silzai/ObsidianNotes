- Comes under MDD (model driven development)
- It tells us about the functional requirements i.e. what the system should actually do, its goals/How the system will be used
- they are stories of using a system to meet goals
## Use-case:
- is a scenario of a system
- it does not represent one small step in the system, but many steps, so not reasonable to create a use-case called "add item" since that it is only one step. Better to create a "create entry" type use-case that will contain many steps. 
- For a use-case model, we also have use-case spec documents that tells
	- brief description
	- flow of events
## Actors:
- are external objects that produce/consumer data (human, organization, machine, external system, sensor etc.)
- should be external to the system
- will use nouns
- Does not represent positions but roles, so we can merge 2 positions to 1 role to represent an actor.
- Inherited actor should be below the generalized actor
## Associations:
- There are 3 types:
	1) Generalization
		1) hollow arrow
	2) include
		1) dashed arrow
		2) writing include with angular brackets
		3) not used/connected for actors, only other use-cases
		4) A use-case must invoke the use-case that is "included" with this association
	3) extend
		1) dashed arrow
		2) there is a condition
		3) is optional/exceptional system behavior 
		4) writing extend with angular brackets
		5) adding a note on when the condition is fulfilled
		6) not used/connected for actors, only other use-cases

## Use-case Specifications
- We have a use-case specifications table
- Structure:
	- Use case name: name of the use-case
	- brief description: what this use-case will do
	- Actors: List all actors that are connected to this use-case ONLY
	- Trigger: How/when the use case is executed/starts executing (i.e. customer pressed buy button)
	- preconditions: list of what conditions are already/met done for this use-case
		- all preconditions must be true before use case is executed
	- postconditions: list of what changes will happen when the use-case is executed
	- normal scenario: if everything goes perfect, what will happen
		- sequence of steps describing the interaction
		- is a table of "actor action" and "system response"
	- alternative flow: what happens when something goes wrong
		- exceptional/optional behavior during normal scenario
	- non-functional requirements: 