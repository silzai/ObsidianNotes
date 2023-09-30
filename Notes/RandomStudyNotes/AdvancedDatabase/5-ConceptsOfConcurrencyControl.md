- Chap-20
- We have 2 types of DBMS:
	1) Single-user DBMS
	2) Multi-user DBMS
- Multi-user DBMS have concurrent queries being executed (when multiple queries are running at the same time)
- Responsible for making sure that concurrent/parallel are executed without conflicts
- interleaved processing: the CPU will process processA for some time then stops executing it and processes processB and repeats the cycle (once the operation does not contain data in the buffer, then that process is suspended and cpu moves to the next process)
- Parallel processing: if we have multi-core computer, then can actually process operations at the same time

- Transaction: 

- ***granularity***: in concurrency control, the concurrency control manager can lock (using locking protocol) some data (for short amount of time) to not be operated on concurrently when there are multiple queries by users. Locking must be done because update and read statements may conflict, so want to write first then read the latest table.
- to specify the size of the data to be locked, we can use the term granularity. we can specify which level to lock i.e. on records, or attributes of a record, or disk blocks.

- `read_item(x)` where x can be any size of data, record or block
- `write_item(x)` where x can be any size of data, record, or block

- buffer is usually in control of the OS, so DBMS does not trust the os to allocate the buffers, so dbms allocates its own cache buffers, 

- lost update problem: 