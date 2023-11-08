- Chap-20
- Goal is to create 
	- concurrency manager
	- recovery manager
- This chapter is about the theory of transactions only, next chapter is the implementation of concurrency for transactions
- We have 2 types of DBMS:
	1) Single-user DBMS
	2) Multi-user DBMS
# What is a Transaction: 
> [!info] Transaction:
> A transaction is a unit of work, possibly consisting of multiple data accesses and updates that must commit or abort as a single atomic unit.

> [!info] Commit
> When a transaction commits, all updates it performed on the database are made permanent and visible to other transactions.

> [!info] Abort
> If a transaction aborts, then all of its updates are removed from the database, and the database is restored to the state it would have been if the aborting transaction was never performed.

- Concurrency of queries is important as serial execution of multiple queries is too slow.
- Our ***goal*** is to enable multiple transactions to execute without clashes at the same time, this allow concurrency in DBMS. This is possible when transactions maintain the ACID property:
# ACID Property of a Transaction:
## A: 
- "Atomicity" is the “all or nothing” guarantee for transactions — either all of a transaction’s actions commit or none do.
## C: 
- "Consistency"; the database remains good even after any transaction i.e. there is no insecure transaction (Consistency is an application-specific guarantee, so a transaction can only commit if it leaves the database in a consistent state) (integrity constraints may ensure this property)
## I:
- "Isolation" is a guarantee to application writers that two concurrent transactions will not see each other’s in-flight (not yet-committed) updates. As a result, applications need not be coded “defensively” to worry about the “dirty data” of other concurrent transactions; they can be coded as if the programmer had sole access to the database.
- It is implemented via a locking protocol.
## D:
- "Durability" is a guarantee that the updates of a committed transaction will be visible in the database to subsequent transactions independent of subsequent hardware or software errors, until such time as they are overwritten by another committed transaction (transaction must be saved permanently on disc)

- DBMS aim to ensure the A, I and D while C is managed during run-time/on the application side.
# ==watch video on Teams and complete notes==
- In concurrency control, the concurrency control manager can lock (using locking protocol) some data (for short amount of time) to not be operated on concurrently when there are multiple queries by users. Locking must be done because update and read statements may conflict, so want to write first then read the latest table.
- ***granularity***: to specify the size of the data to be locked, we can use the term granularity. we can specify which level to lock i.e. on records, or attributes of a record, or disk blocks.

- buffer is usually in control of the OS, but DBMS does not trust the OS to allocate the buffers, so DBMS allocates its own cache buffers, 

- Concurrency control manager should prevent these problems:
	- lost update problem: 
	- Temporary update problem: 
	- Incorrect Summary Problem: 

# ==may need to move scheduling/serialization before Recovery==
# Recovery:
- The Recovery Manager guarantees "Atomicity" & "Durability"
- if there is an interruption, then recovery manager will go to the log file, and do either undo or redo
- Log file (which is a sequential file) used for data recovery (and auditing, but not discussed here)
- recovery data is written before the modifiable data
- Recovery is handled by two operations undo and redo
	- We don't need any more operations than undo and redo to do recovery
	- redo: maybe there is a failure and we doubt that the transaction maybe not written to disk, so we need to do redo. From recovery information from log file, we rewrite the transaction.
	- undo: Some transaction may not have been committed, so we can ==??==
- commit point:
- Force writing log file from buffer to disc
	- DBMS buffer replacement policies, not generally used by OS:
		- LRU
		- hot set: pages that are used a lot, so keep storing them in the buffer, and not replace these ones
		- DBMIN: similar to hot set



- DBA has option to apply different levels of isolation in order to create a snapshot isolation, where the different levels prevents dirty reads and no lost updates, and the levels build upon each other, there are 4 levels, 4th level is called serializable. (we can even relax some isolations for the sake of testing, so they execute quickly)

- Conflict can occur if changing the order of transactions give different outcomes
- Conflicts of transactions can occur from these:
	- RW
	- WW
	- 
# Scheduling:
- we are good if any interleaved transactions are also serializable
- if transaction $T2$ relies on transaction $T1$, then $T1$ should committed before $T2$ otherwise will have dirty read problem
- if we have a schedule: $$w1(X) ;\ r2(X)$$
- then $c1$ should be done before $c2$ to make it recoverable
- cascading rollback (is bad): the failure of one transaction may lead to the failure of the other transaction 
	- if T1 has to abort, then T2 should also be aborted, (even though it may not have errors)
	- can apply cascadeless schedule: your read should not read items from uncommitted records
- String schedule: the transaction neither read or write until last item is committed.

- result equivalence: not safe
- conflict equivalence: safe
- view equivalence: safe, better than conflict equivalence (but check is expensive)

- Conflict serializability:
	- difference between serial and serializable:
		- serial: first t1 finished executing then t2 executes (is always correct, but not practical, we would like interleaved execution)
		- serializable: is an interleaved schedule, but is equivalent to some serial schedule and we know that serial execution is always correct (meaning I could find a serial schedule for the interleaved schedule, since the result would be the same)
	- if there is a cycle in the precedency graph then the transactions are not serializable, once we design protocols such as 2 phase looking protocol (in chap 21), we need to enforce the transaction always be serializable
- To enforce serializability:
	- transactions must always have serial conflict schedule
- view serializability allows blind writes (writing without reading), is better than conflict serializable because allows more schedules. but is NP hard (complete?) to ensure correctness, so not implemented commercially.
- conflict serializable schedules is a subset of view serializable.

- To check for serializability:
	- 1 condition to check for conflict serializability: check for circle in precedency graph
	- 3 conditions to check for view serializability: conditions given in document

- as concurrency increases, the errors (dirty read etc.) decreases and vice versa. 

- debit-credit transaction: is also correct, but we dont use it, as expensive to check the actual functions
___
# References
- [Concurrency and Recovery paper, WashingtonU](https://courses.cs.washington.edu/courses/cse544/11wi/papers/franklin97.pdf)
- [“Architecture of a Database System.”, stonebraker](https://dsf.berkeley.edu/papers/fntdb07-architecture.pdf)