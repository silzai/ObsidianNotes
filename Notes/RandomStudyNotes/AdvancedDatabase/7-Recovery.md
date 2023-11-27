 >[!note]
 >A Recovery process restores the database to the most recent consistent state that was before the time of failure.
# Recovery strategies:
1) restore backed-up copy of database:
	- recommended for catastrophes, to restore data
2) Identify inconsistent operations and return the DB to a consistent state:
	- recommended for non-catastrophic (light) failure.
	- redo/undo
# Recovery Concepts:
## Deferred update technique:
- not practical as puts pressure on the buffer
- all modifications are kept in the buffer until transaction commits
- once commits, so then will write the data to disc
- (so we do not need undo/rollback)
- redo is needed
- the page written may be left in the buffer, so will redo that ???
>[!important]
>Need before image and
## Immediate update technique:
- A transaction can be written to disc before committing
- So we don't put pressure on the buffer
- failure can happen after T1 executes half its statements, so need to undo
- undo: all modified items by T1 are returned to their before image
- redo: commit the transaction
> [!important] 
> Only need before image for undo on immediate update technique
- Undo and redo should be idempotent, meaning executing operations multiple times, is equal to executing them once
	- every recovery should be idempotent
- buffering:
	- DBMS has its own buffers, but this can be configured if whether the DBMS can access those buffers itself directly, or through the operating system as a client.
	- how to know if a page is modified in the buffer so we can write it to disc?
		- there will be a dirty bit (flag) that will indicate this
	- how to know whether a page is between a process or not (so not to evict it)?
		- there will be a pin-unpin (flag) to indicate this
# Main Strategies:
- in-place updating:
	- 
- shadow paging:
	- don't need undo or redo
	- we have a directory in the RAM that the DBMS controls
	- This directory has entries that has pointers to the database page in disc
	- we then bring a shadow directory which stores the pointers of the old values, while the current directory 
	- if there is no crash, then the current directory is stored to disc
	- if there is a crash, then the shadow directory becomes the current directory
	- expensive, don't use it, not used commercially
# Logging
- Write-ahead logging protocol:
	- recovery data should be stored first, meaning:
	- log pages should go to the disc first
- need to keep 4 types of data in the log to recover (to perform undo and redo), and we don't need any other type of data
	1)  transaction starts: start T1
	2)  transaction commits: commit T1
	3) transaction reads: read T1
	4) transaction writes: write T1

>[!important] Checkpoints
>- A checkpoint record is written into the log periodically at that point when the system writes out to the database on disk all DBMS buffers that have been modified.
>- As a consequence of this, all transactions that have their (commit, T) entries in the log before a (checkpoint) entry do not need to have their WRITE operations redone in case of a system crash, since all their updates will be recorded in the database on disk during checkpointing.

- A log may grow very large, so we need checkpointing, to take a checkpoint:
	- temporarily suspend all transactions
	- force write all buffers that have been modified to disc
	- checkpoint will check if the pages in the buffer are all evicted to the disc
	- write a checkpoint record to log
	- resume normal transactions
- critics say that normal checkpointing will lose efficiency, so need fuzzy checkpointing, so to take fuzzy checkpoint:
	- we freeze the transactions only 

>[!important]
>we prefer immediate updating and in-place updating

# Policies (implementation): 
- These are the implementations of the recovery concepts above (immediate update etc.), buffer level deals with steal and no-steal
	- steal
		- it is implementation of immediate update
		- need undo and redo
	- no-steal 
		- It is implementation of deferred update
		- need only redo
	- force:
		- All pages modified in buffer should be evicted to disc before transaction commits
		- so don't need redo
	- no-force
		- buffer manager is free to evict any page
		- transaction may commit but the modified pages are still in buffer

>[!important]
>we prefer steal and no-force strategy (UNDO/REDO) (this is from immediate strategy)

- Redo is done on all items after the checkpoint
- Undo is done from the end item (before system crash) up to the checkpoint (log is scanned backwards)

# ARIES Recovery Algorithm
- Used in commercial systems such as IBMDB2
- It uses steal/no-force (UNDO/REDO)
- uses WAL
- has a marker that marks when a redo is done, and when we are doing recovery again, then it will not repeat the redo
- For this algorithm, the log has one more column called LSN (Log Sequence Number)

#### Recovery Algorithms:
- immediate 
- deferred
- Shadowing
- ARIES