- Polymorphism: 
	- overloading: methods that have same name but different parameters/function in the same class
	- overriding: methods that have same name but different parameters/function in the sub-class inheriting from a super class

- Domain model:
	- is like a visual dictionary, 
	- is similar to class diagrams from UML, but we don't show methods:
	- There are 4 types of elements:
		1) Conceptual class, will be a noun
		2) associations between conceptual classes
		3) attributes of conceptual classes
		4) multiplicity, same as cardinality in ER diagrams, put them in associations


- aggregation:
	- hollow diamond
	- attach the diamond to the whole (class), not the part (class)
	- part class may exist without the whole
- composition:
	- filled diamond
	- life cycle of the part depends on the whole

## More on class relationships in design class diagram:

- Will an actor be a class in a class diagram?
	- If we will manipulate the data of the actor in the system, then actor will be a class
	- if information of an actor is used in the system, then it will be a class, otherwise if there is no information of an actor being used, then it will not be a class.

- A use case need to consist of several different functions for it to be a use case, not there should not be just one simple function in it

### Messages
- [messages by mit](https://web.mit.edu/java_v1.0.2/www/tutorial/java/objects/messages.html)
### Collection/Container Class
- No need to show that the class is a collection in class diagram

### Class Stereotypes in UML
- Used to make UML extensible
- example with stereotypes for MVC:
	- `<<boundary>>` (view)
		- refers to the view (the UI) in MVC
	- `<<controller>>`
		- information to the controller will come from the boundary
		- it is the control class in MVC
	- `<<entity>>`
		- it is the model class in MVC