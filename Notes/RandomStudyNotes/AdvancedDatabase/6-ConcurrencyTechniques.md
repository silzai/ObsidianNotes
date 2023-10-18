- Chap 21
- Implementation of what we studied in chap 20
- To implement serializability, we can do the following:
- Have concurrency control protocols that ensure serializability:
	1) Two phase locking protocol
		- is a classic protocol
	2) timestamp based protocol
		- there is ordering of transactions based on the time
	3) multi-version concurrency 
		- will allow multiple transactions

## lock manager is responsible for locking: 
- special kind of metadata, lock table specifies items that have locks
- is a variable that can hold values: `"write locked" or "read locked" or "unlocked"`
- granting lock = granting access
- if locked (`lock=1`), transaction cannot access the unit (except the current one)
- since read and read is safe to do concurrently in any way, then can allow multiple/all transactions hold the lock.
- in case of writing, only 1 transaction can hold the lock 
## Two phase locking protocol:
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

Critics say locking has overhead, so need more effiecient method to handle concurrency and serializablity.

# Timestamp
- There are no deadlocks, the later transaction will be forced to rollback.
- every transaction passes a test, otherwise transaction is rolledback
- This ensures conflict serializablility
- TO: Timestamp Ordering
## Basic TO protocol:
- before executing, will perform test where first will check the read/write_ts table
- in case read_ts in correct, then the later transaction 
- For write_item(x):
	- if write_item(x) then ==??==
- For read_item(x):
	- 

- The dependant transaction to another transaction will also rollback (cascading rollback)
	- if want to prevent this then, will change from basic TO, to strict TO
	- this ensures schedules are strict (cascade-less) and conflict serializable
- read_ts
- write_ts

