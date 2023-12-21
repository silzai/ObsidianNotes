>[!quote] Chap-20
>This chapter is about the theory of transactions only, next chapter is the implementation of concurrency for transactions

>[!success] For transaction processing, goal is to create:
>- concurrency manager
>- recovery manager
# What is a Transaction: 
> [!info] Transaction:
> A transaction is a unit of work, possibly consisting of multiple data accesses and updates that must commit or abort as a single atomic unit.

> [!info] Commit
> When a transaction commits, all updates it performed on the database are made permanent and visible to other transactions.

> [!info] Abort
> If a transaction aborts, then all of its updates are removed from the database, and the database is restored to the state it would have been if the aborting transaction was never performed.

- Concurrency of queries is important as serial execution of multiple queries is too slow.
 >[!tip]
 >Our ***goal*** is to enable multiple transactions to execute without clashes at the same time, this allows concurrency in DBMS. This is possible when transactions maintain the ACID property:
# ACID Property of a Transaction:
## A: 
- "Atomicity" is the “all or nothing” guarantee for transactions — either all of a transaction’s actions commit or none do.
## C: 
- "Consistency"; the database remains good after any transaction i.e. there is no insecure transaction
- (Consistency is an application-specific guarantee, so a transaction can only commit if it leaves the database in a consistent state)
- (integrity constraints may ensure this property)
## I:
- "Isolation" is a guarantee to application writers that two concurrent transactions will not see each other’s in-flight (not yet-committed) updates. As a result, applications need not be coded “defensively” to worry about the “dirty data” of other concurrent transactions; they can be coded as if the programmer had sole access to the database.
- It is implemented via a locking protocol.
## D:
- "Durability" is a guarantee that the updates of a committed transaction will be visible in the database to subsequent transactions independent of subsequent hardware or software errors, until such time as they are overwritten by another committed transaction (transaction must be saved permanently on disc)

>[!info]
>DBMS aim to ensure the A, I and D, while C is managed during run-time/on the application side.
# Scheduling:

>[!important] Difference between serial and serializable:
>- Serial: first t1 finished executing then t2 executes (is always correct, but not practical, we would like interleaved execution)
>- Serializable: is an interleaved schedule, but is equivalent to some serial schedule and we know that serial execution is always correct 
>- (meaning I could find a serial schedule for the interleaved schedule, since the result would be the same)

- We are good if any interleaved transactions are also serializable
- if transaction $T2$ relies on transaction $T1$, then $T1$ should committed before $T2$ otherwise will have dirty read problem
- if we have a schedule: $$w1(X) ;\ r2(X)$$
- then $c1$ should be done before $c2$ to make it recoverable
- cascading rollback (is bad): the failure of one transaction may lead to the failure of the other transaction 
	- if $T1$ has to abort, then $T2$ should also be aborted, (even though it may not have errors)
	- can apply cascade-less schedule: your read should not read items from uncommitted records
- String schedule: the transaction neither read or write until last item is committed.
# When are two schedules considered equivalent?
>[!important] Result Equivalence: 
>Two schedules are called result equivalent if they produce the same final state of the database. However, two different schedules may accidentally produce the same final state.
>- so, result equivalence: not safe

>[!important] Conflict Equivalence: 
>Two schedules are said to be conflict equivalent if the relative order of any two conflicting operations is the same in both schedules.
>- conflict equivalence: safe

>[!info] Quick Check: What is a conflict?
> Two operations in a schedule are said to conflict if they belong to different transactions, and access the same database item, and either both are write_item operations or one is a write_item and the other a read_item.
- view equivalence: safe, better than conflict equivalence (but check is expensive)

- Now that these definitions are clear, we will move on to discuss things that actually matter:
# Testing For Conflict serializability:
- Above, we discussed how different schedules can be equivalent, but for a particular schedule to be correct, we need it to be serializable, so:
>[!important] Conflict Serializable
>A schedule is serializable if it is (conflict) equivalent to some serial schedule

>[!warning] Testing for Serializability
>There is a simple algorithm for determining whether a particular schedule is (conflict) serializable or not. Most concurrency control methods do not actually test for serializability. Rather protocols, or rules, are developed that guarantee that any schedule that follows these rules will be serializable (i.e. Locking Protocols)

- There is only 1 check to find if schedule is (conflict) serializable.
- Algorithm to draw the precedency graph:
	1) For each transaction $T_i$ participating in schedule $S$, create a node labeled $T_i$ in the precedence graph. 
	2) For each case in $S$ where $T_j$ executes a read_item(X) after $T_i$ executes a write_item(X), create an edge ($T_i$ → $T_j$) in the precedence graph
	3) For each case in $S$ where $T_j$ executes a write_item(X) after $T_i$ executes a read_item(X), create an edge ($T_i$ → $T_j$) in the precedence graph.
	4) For each case in $S$ where $T_j$ executes a write_item(X) after $T_i$ executes a write_item(X), create an edge ($T_i$ → $T_j$) in the precedence graph.
	5) (All these points basically tell us to make an edge between the nodes when an operation is done on the same attribute/item and at least one of the operations is a write_item())
	6) The schedule $S$ is serializable if and only if the precedence graph has no cycles.
	
- if there is a cycle in the precedency graph then the transactions are not serializable, once we design protocols such as 2 phase looking protocol (in chap 21), then these automatically enforce the transactions to always be serializable.
## view serializability
- Allows blind writes (writing without reading), is better than conflict serializable because allows more schedules. but is NP hard to ensure correctness, so not implemented commercially.
- conflict serializable schedules is a subset of view serializable.

- To check for serializability:
	- 1 condition to check for conflict serializability: check for circle in precedency graph
	- 3 conditions to check for view serializability: conditions given in document

- as concurrency increases, the errors (dirty read etc.) decreases and vice versa. 

- debit-credit transaction: is also correct, but we don't use it, as expensive to check the actual functions
# What happens if a schedule is not serializable?
- These are the things that may happen:
1. Lost update Problem
3. Dirty read (or temporary update problem). A transaction T1 may read the update of a transaction T2, which has not yet committed. If T2 fails and is aborted, then T1 would have read a value that does not exist and is incorrect.
4. Incorrect Summary Problem
5. Nonrepeatable read. A transaction T1 may read a given value from a table. If another transaction T2 later updates that value and T1 reads that value again, T1 will see a different value.
6. Phantoms. A transaction T1 may read a set of rows from a table, perhaps based on some condition specified in the SQL WHERE-clause. Now suppose that a transaction T2 inserts a new row r that also satisfies the WHERE-clause condition used in T1, into the table used by T1. The record r is called a phantom record because it was not there when T1 starts but is there when T1 ends. T1 may or may not see the phantom, a row that previously did not exist. If the equivalent serial order is T1 followed by T2, then the record r should not be seen; but if it is T2 followed by T1,then the phantom record should be in the result given to T1. If the system cannot ensure the correct behavior, then it does not deal with the phantom record problem
___
# References
- [Concurrency and Recovery paper, WashingtonU](https://courses.cs.washington.edu/courses/cse544/11wi/papers/franklin97.pdf)
- [“Architecture of a Database System.”, stonebraker](https://dsf.berkeley.edu/papers/fntdb07-architecture.pdf)