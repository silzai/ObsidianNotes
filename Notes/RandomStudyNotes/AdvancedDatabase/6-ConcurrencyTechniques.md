- Chap 21
- Implementation of what we studied in chap 20
- To implement conflict serializability, we can do the following:
- Concurrency control protocols that ensure serializability:
	1) Two phase locking protocol
		- is a classic protocol
	2) timestamp based protocol
		- there is ordering of transactions based on the time
	3) multi-version concurrency control (MVCC)
		- will allow multiple transactions
## lock manager is responsible for locking: 
- special kind of metadata, lock table specifies items that have locks
- is a variable that can hold values: `"write locked" or "read locked" or "unlocked"`
- granting lock = granting access
- if locked (`lock=1`), transaction cannot access the unit (except the current one)
- since read and read is safe to do concurrently in any way, then can allow multiple/all transactions hold the lock.
- in case of writing, only 1 transaction can hold the lock 
# Two phase locking protocol:
- n=number of transactions
- lock conversion:
	- wants us to allow us to increase n,
- upgrading:
	- while a transaction, is reading only, then let other transactions read also, but after reading and modifying the value, upgrade the lock to write lock, and block others. 
- downgrading:
	- downgrade this lock to shared lock
- two phase locking:
	- there are two phases:
		1) expanding
		2) shrinking
	- strict condition: should first obtain all locks (expand), then in the second phase, it releases all locks (shrink)
	- lock and unlock not allowed to be interleaved
	- any transaction that wants to read an item should obtain 
	- any transaction that wants 

- Critics say locking has overhead, so need more efficient method to handle concurrency and serializability.
- Locking is a pessimistic technique because its based on the assumption that transactions are likely to interfere with each other, and so it takes measures accordingly, an alternative is ***optimistic concurrency control*** which has ==????==

# Timestamp Ordering (TO):
- achieve concurrency using the time the transactions enter the system
- There are no deadlocks, the later transaction will be forced to rollback.
- every transaction passes a test, otherwise transaction is rolled back
- This ensures conflict serializability
- There are 3 types:
	1) Basic TO
	2) but with this, there can be too many rollbacks, so we have 2nd alternative, "strict TO", to reduce number of rollbacks
		- If have a transaction that modified X, T enters and tries to modify X
	3) 3rd alternative Thomas's write rule (not important):
		- can have more read/writes
## Basic TO protocol:
- It has 2 variables:

>[!info] $read\_TS(X)$:
>The latest time a read operation was performed on $X$

>[!info] $write\_TS(X$):
>The latest time a write operation was performed on $X$
- before executing a transaction $T$, will first perform a test where we will compare $read\_TS/write\_TS$ to the $TS(T)$ (time stamp of $T$)
- So, whenever there is a transaction $T$, we will check these conditions:

> [!important] if there is a $write(X)$ for transaction $T$
> 1) if $read\_TS(X) > TS(T)$ OR $write\_TS(X) > TS(T)$, then reject $T$
> 2) Otherwise execute $write(X)$ and set $write\_TS=TS(T)$  

> [!important] if there is a $read(X)$ for transaction $T$
> 1) if $write\_TS(X) > TS(T)$, then reject $T$ and rollback.
> 2) Otherwise if $write\_TS(X)\le TS(T)$ then execute $read(X)$ and set $read\_TS(X)=max(TS(T),current \ read\_TS(X))$

| T1    | T2    | read_TS(x) | write_ts(x) |
| ----- | ----- | ---------- | ----------- |
| 1     | 2     | 0          | 0           |
| readx |       | 1          |             |
|       | readx | 2           |             |
|writex       |       |            |             |

- initially T1 enters the system then T2 enters, so T1 has timestamp of 1, and T2 has 2, while readts(x) and writets(x) are 0

- The dependent transaction to another transaction will also rollback (cascading rollback)
	- if want to prevent this then, will change from basic TO, to strict TO
	- this ensures schedules are strict (cascade-less) and conflict serializable
- read_ts
- write_ts

# Multi-version Concurrency Control (MVCC):
- It is implemented either by locking, timestamp or 
- MVCC by timestamping:
	- f
- MVCC by locking:
	- we have 3 locks: read, write and certify
- We keep multiple versions of the items, and allow different transactions to interact on different version of the same item.

# Validation techniques (optimistic)
- during read/write there is no checking done (they are free), we can allow multiple transactions to execute.
- but since we want to maintain, updates are not directly passed to the database storage
- before we allow permanent storage, first it has to be validated, if it correct then, we can allow it to commit

# Snapshot Isolation
- There is no read lock, but there are write locks
- does not ensure serializability, if there are errors in transactions, it is not responsibility of the concurrency control manager but the application programmer (human)

# Granularity
- There is a hierarchy in the database to grant locks, where the root or 1st node in the hierarchy is the whole database
- If a parent node has a lock, then the child node will also have a lock
- transaction doing sequential scan of whole file, will need to lock the whole table
- if transaction is on one key in the table, then can only lock the attribute
## multiple Granularity level locking protocol
- Locks are applied intuitively
- Using this, we can achieve that when a current node has shared locked, its descendant node can still obtain an exclusive lock
- A child cannot be locked unless its parent is locked with either IX or SIX

# Locks in Indexes
- The transaction should acquire exclusive lock on the index when writing
- But this is severe (inefficient), as other transaction would have to wait
- Indexes are sensitive for query optimization, and we do not keep the locks for long
- keeping nodes half-full helps in following conservative and optimistic approaches.
- conservative approach:
	- lock the root
	- maintain the root until we lock the child
	- once the child is locked, the root is unlocked
	- then the locked child will reach its child node, and lock it the grandchild, and then unlock the parent, will do this until 
- optimistic approach:
	- shared lock is enough
	- only need to lock the leaf

- b-link tree approach:
	- The siblings will be connected
	- solves the problem of ???

# Issues in concurrency
- 
- Phantom problem:
- Interactive transactions:

