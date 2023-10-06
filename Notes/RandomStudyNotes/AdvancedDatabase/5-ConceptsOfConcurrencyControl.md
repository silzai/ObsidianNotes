- Chap-20

- Goal is to create 
	- concurrency manager
	- recovery manager

- This chapter is about theory only, next chapter is the implementation
- We have 2 types of DBMS:
	1) Single-user DBMS
	2) Multi-user DBMS

- Transaction: 
	- is a group of read or writes or both
	- Transaction processing systems are large databases that enable high concurrency, availability and response time
	- concurrency of queries is also important, otherwise is serial execution of multiple queries by different queries is too slow.

- Our goal is to enable multiple transactions to execute at the same time, to allow concurrency in DBMS.

- Multi-user DBMS have concurrent queries being executed (when multiple queries are running at the same time)
- Responsible for making sure that concurrent/parallel are executed without conflicts
- Multi-programming is done in two ways:
	- interleaved processing: the CPU will process processA for some time then stops executing it and processes processB and repeats the cycle (once the operation does not contain data in the buffer, then that process is suspended and CPU moves to the next process)
	- Parallel processing: if we have multi-core computer, then can actually process operations at the same time on different processors

- ***granularity***: in concurrency control, the concurrency control manager can lock (using locking protocol) some data (for short amount of time) to not be operated on concurrently when there are multiple queries by users. Locking must be done because update and read statements may conflict, so want to write first then read the latest table.
- to specify the size of the data to be locked, we can use the term granularity. we can specify which level to lock i.e. on records, or attributes of a record, or disk blocks.

- `read_item(x)` where x can be any size of data, record or block
- `write_item(x)` where x can be any size of data, record, or block

- buffer is usually in control of the OS, so DBMS does not trust the OS to allocate the buffers, so DBMS allocates its own cache buffers, 

- Concurrency control manager should prevent these problems:
	- lost update problem: 
	- Temporary update problem: 
	- Incorrect Summary Problem: 
## Recovery:
- if there is an interruption, then recovery manager will go to the log file, and do either undo or redo
- Log file (which is a sequential file) used for data recovery (and auditing, but not discussed here)
- recovery data is written before the modifiable data
- Recovery is handled by two operations undo and redo
	- We don't need any more operations than undo and redo to do recovery
	- redo: maybe there is a failure and we doubt that the transaction mabey not written to disk, so we need to do redo. From recovery information from log file, we rewrite the transaction.
	- undo: Some transaction may not have been committed, so we can ==??==
- commit point:
- Force writing log file from buffer to disc
	- DBMS buffer replacement policies, not generally used by OS:
		- LRU
		- hot set: pages that are used a lot, so keep storing them in the buffer, and not replace these ones
		- DBMIN: similar to hot set

- ACID properties of transactions
	- A: atomicity: transaction is executed fully, or not at all
	- C: consistency preservation: the database remains good even after any transaction i.e. there is no insecure transaction
	- I: isolated: 
	- D: transaction must be saved permanently on disc
- DBA has option to apply different levels of isolation in order to create a snapshot isolation, where the different levels prevents dirty reads and no lost updates, and the levels build upon each other, there are 4 levels, 4th level is called serializable. (we can even relax some isolations for the sake of testing, so they execute quickly)

- conflict can occur if changing the order of transactions give different outcomes
- Conflicts of transactions can occur from these:
	- RW
	- WW
	- 
## Scheduling:
- if transaction $t2$ relies on transaction $t1$, then $t1$ should commited before $t2$ otherwise will have dirty read problem
- if we have a schedule: $w1(X)$; $r2(X)$, then $c1$ should be done before $c2$ to make it recoverable
- cascading rollback (is bad): the failure of 1 transaction may lead to the failure of the other transaction 
	- if t1 has to abort, then t2 should also be aborted, (even though it may not have errors)
	- can apply cascadeless schedule: your read should not read items from uncommitted records
- String schedule: the transaction neither read or write until last item is committed.
- difference between serial and serializable:
	- serial: first t1 finished executing then t2 executes (is always correct, but not practical, we would like interleaved execution)
	- serializable: is a interleaved schedule, but is equivalent to some serial schedule, and we know that serial execution is always correct (meaning i could find a serial schedule for the interleaved schedule)
		- 