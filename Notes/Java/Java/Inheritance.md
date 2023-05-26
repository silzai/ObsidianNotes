### To call the constructor of the superClass from sub-class:
```java
public Circle extends Shape { // For ex: subclass Circle from super class Shape
	public Circle(String color, int size, double radius){ 
		super(color, size) // Use super keyword to call constructor from super class
		this.radius = radius;
	}
}
```
## To override methods from the superClass
```java
//this is a method that is already inside a super class
@override
public String toString(){
	return super.toString() + "this text will be added to the toString of sub-class";
}
```
## To deny overriding the methods of superClass
- add `final` keyword to not let method be overridden. Make it `private`  to cancel all access to the method anywhere outside the SuperClass, this will not let the sub-classes to access the method.
```java
public final String toString(){}
OR
private String toString() {}
```
- Add `protected` to make super class accessible to sub-classes outside the package, but hidden to other classes outside the package.
```java
protected String toString(){}
```
- Make the class `final` to deny any sub-classes to inherit from it.NO SUBCLASSES.
```java
public final class ClassName(){}
```
### We can add subClass objects to SuperClass ArrayList
example: 
```java
Arraylist<Person> p1 = new ArrayList<Person>();
Employee e1 = new Employee();
p1.add(e1); // adding subClass object to SuperClass ArrayList
```
#### If we want to perform a specific action on the subClass object in the SuperClass ArrayList
- We have to cast the SuperClass into the subClass:
example: 
```java
for (Person person: p1) {
	if (person instanceOf Customer) { //KEYWORD: instanceOf
		Customer c = (Customer) person; // casting the Superclass into subclass
		c.//Call the method that you want for the SubClass
	}
}
```
*NOTE: Can also use [[Polymorphism]]*

