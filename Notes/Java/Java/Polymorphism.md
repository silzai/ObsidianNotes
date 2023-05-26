**We can create a SubClass object by instantiating the SuperClass:**
```java
Person e1 = new Employee();
```
- BUT the object `e1` will use methods from the subClass that are overridden.

##### example of application of polymorphism:
```java
public static double getPaintCost(Shape shape) {
	int PRICE = 5;
	return PRICE * shape.getArea();
}
```
- here in the method argument, we can send ANY subClass of Shape (ex: circle, square) and the method `shape.getArea()` will call the overridden method from the subClass.
- if we want to use methods in subClass that are not in superClass, we will have to down cast the object into the subClass.
	*NOTE: to downcast, we will first have to make a check i.e: `if (a instanceOf Employee)` *