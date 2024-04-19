# Synchronization
- concurrent processes -> shared resource -> need synchronization
# Bounded Buffer (producer/consumer):
- problems:
	1) busy waiting in the while loop of insert and delete methods
		- solved by `wait/notify`
	2) The problem may occur if either a writer overwrites data in the buffer before it is consumed by the reader, or a reader consumes the duplicate data. (problem of not having mutual exclusion)
- thats why we need synchronization
# Java Synchronization
- all threads are added to a queue 
- have an entry set, represents all thread in runnable state waiting to acquire a lock
- to put mutex (mutual exclusion) to an object:
```java
Object x = new Object(); 
synchronized(x) {
// code to execute while lock is held on x
// this is the critical section
}
```
- furnace policy
- spinning:
	- thread yield: stop the thread, put it back into ready queue
		- to give turn to other threads
	- problem: doesn't release the lock, so only good for object that doesn't have locks
	- to solve `yield()` will use `wait/notify()`: 
		- if blocked then, will make `wait()` , this will put thread in `waiting set`
		- `notify()` will move from `waiting set` to `entry set` to make it runnable
		- can use `notifyAll()` to move all threads in wait set to `entry set`
- Recursive Lock:
	- method with lock on object can run in another synchronized method
- nested lock:
	- if manipulating different objects, then will have nested locks
# Semaphores
- is a synchronization mechanism
- usually implemented on buffers
- does not require busy waiting
	- only thing need to solve is mutual exclusion aka synchronization
- binary semaphore:
	- if number of resources is 1, then will have this
	- behaves like a normal locking mechanism
	- 