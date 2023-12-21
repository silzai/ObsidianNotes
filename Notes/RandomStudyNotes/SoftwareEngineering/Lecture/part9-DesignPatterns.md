- Will do following design patterns:
	1) Factory Method (creational design pattern)
	2) Singleton (creational design pattern)
	3) Proxy (structural design pattern)
	4) Adapter (structural design pattern)
	5) Façade (structural design pattern)

>[!info] Before You Proceed
>It is good to know the difference between a "creational" design pattern and a "structural" design pattern:
>- Creational Design Pattern: Code used to "create" objects in a certain way
>- Structural Design Pattern: Code used to "use/access" the objects in a certain way
>
>Note: There are also Behavioral Design Patterns that are not in our syllabus
# Factory Method:
- It is a creational design pattern
- By applying this, we can create objects without exposing creation logic to the client

# Singleton:
- creational design pattern
```mermaid
---
title: Singleton
---
classDiagram
    note "From Duck till Zebra"
    Animal <|-- Duck
    note for Duck "can fly\ncan swim\ncan dive\ncan help in debugging"
    Animal <|-- Fish
    Animal <|-- Zebra
    Animal : +int age
    Animal : +String gender
    Animal: +isMammal()
    Animal: +mate()
    class Duck{
        +String beakColor
        +swim()
        +quack()
    }
    class Fish{
        -int sizeInFeet
        -canEat()
    }
    class Zebra{
        +bool is_wild
        +run()
    }
```

```java
Public class Singleton {

	private static 

}
```
# Proxy:
- It is a Structural design pattern
- don't let the client directly access an object, make the client use the object through a proxy
- The proxy will instantiate the realSubject object then the realSubject will do the actual operations, the methods of realSubject will be called inside the proxy

# Adapter:
- adapter will provide a bridge class between a class that uses the bridge class's interface, but want to perform the operations of the adaptee.
# Façade:
- Provide an interface to multiple classes

>[!note] Adapter and Façade
>Adapter and Façade are similar to what we call wrapper classes (i.e. they provide interfaces)

>[!info] Difference Between Adapter and Façade
>- Adapter uses the old interface, while Façade provides a new interface
>- Adapter adapts one element, Façade adapts multiple elements