# CPU Scheduling
# Types of Scheduling
response time = time from arrival time up to when the process is first executed
# Non-preemptive
## Waiting time
$$\text{waiting time = response time = start time - arrival \ time}$$
## Turnaround time
$$\text{turnaround = end \ time - arrival \ time}$$
- OR $$\text{turnaround = waiting \ time + burst \ time}$$
# Preemptive
## Waiting time
$$\text{waiting \ time = turnaround \ time - burst \ time}$$
- OR $$\text{waiting \ time = arrival \ time + start \ time + (anything\  in \ the \ middle)}$$
# Multilevel Queue Scheduling
- Usually we had just one ready queue, in this the ready queue is split into multiple level queues
- those ready queues will have their own scheduling algorithm
- starvation can happen:
	- the lower queue has to wait for the processes in the upper queue to finish
	- so we can do time slicing to solve this:
## Multilevel Feedback Queue
- This is implemented in Linux
- special case of multilevel queue: multi-feedback Queue:
- the queue will have priorities
- feedback: 
	- if a process from a certain queue is preempted (interrupted), then instead of going to the tail of the same queue, insert it to the next queue
- 