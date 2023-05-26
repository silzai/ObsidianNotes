##### Theory for Abstract Classes:
> Meaning of Abstract thing: Anything general; not specific, for ex: A shape, not specified which shape.
- Abstract classes do not allow instantiation.
- Have to create SubClass to instantiate the *AbstractClass*.
- Methods in the *AbstractClass* are left empty and specified in the SubClass, So the *AbstractClass* is like a *template*.
- A SubClass cannot extend an *AbstractClass* unless it has all the methods that are declared as *abstract* in the *AbstractClass*.
##### Implementation:
- in the AbstractClass, the methods can be either abstract or not.
- if the method is abstract, then it will be left empty.
#### Interface:
- It is a template but everything is abstract and not every *implementation* is interconnected.
- For example: a `payable` can be *implemented* by BOTH an Employee Class and an Invoice Class, even though they are not connected, but both are *payables*.
