# 1. Deadlock Prevention :  
Deadlock prevention means to block at least one of the four conditions required for deadlock to occur. If we are able to block any one of them then deadlock can be prevented. 

The [four conditions](https://www.geeksforgeeks.org/deadlock-prevention/) which need to be blocked are:- 

1. Mutual Exclusion
2. Hold and Wait
3. No Preemption
4. Circular Wait

[Spooling](https://www.geeksforgeeks.org/difference-between-spooling-and-buffering/) and non-blocking synchronization algorithms are used to prevent the above conditions. In deadlock prevention all the requests are granted in a finite amount of time. 

# 2. Deadlock Avoidance :   
In Deadlock avoidance we have to anticipate deadlock before it really occurs and ensure that the system does not go in unsafe state. In deadlock avoidance the maximum number of resources of each type that will be needed are stated at the beginning of the process.