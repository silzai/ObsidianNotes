Databases aim to get results quickly, following factors are part of efficient data access:
## Efficient Data Access: How?
### 1) Use data buffering for reading data
-  reading data ahead of request (buffering): CPU does not directly accesses the hard disc, but it accesses the RAM, a buffer is an area in the RAM.
- Whenever the CPU wants to read a block of data, it checks the buffer first, if data is not available, then checks the hard drive. the buffer manager anticipates what data will be read next.
- buffering is most useful in processes that run in parallel concurrency, this is possible by special hardware, i.e. multiple CPU processors exist.
- ***double buffering:*** The CPU can start processing a block once the blocks transfer to main memory is completed; at the same time, the disk I/O processor can be reading and transferring the next block into a different buffer.
#### techniques for filling and flushing the buffer (buffer replacement strategies):
1) ***least recently used (LRU):***  if the data is in the buffer for a long time, then unlikely we will need it, so override it with different data that we may need.
2) ***FIFO:*** It is opposite to LRU, so if we just processed some data (occupied longest by a page), so we don't need it anymore, so override it with different data that we may need.
### 2) Placement of data on hard disc: 
#### placement of blocks on the hard disc:
- During formatting, OS allocates how big the size of blocks in hard drive will be.
- In database terminology, we call sectors, blocks. they have a capacity.
- We have two types of arrangements of blocks on disc:
	1) ***contiguous allocation***: data is arranged on the one track of the hard disc i.e. in sector 1, sector 2, meaning blocks are arranged one after the other.
	2) ***linked allocation***: if data scattered over multiple blocks over the hard disc
#### placement of records on a block:
- ***blocking factor:*** number of records that can be stored in a block
- ***spanned records:***
	- I want to fill the block to max capacity. this will have effect that a record may be stored in different blocks. So the cut-off record is divided, but is joined to the second block by having a pointer to the next block. We don't lose storage space in this (no empty space in blocks).
- ***un-spanned records:***
	- We prefer that a whole record is stored in a single block, this means that the record has to be fixed length and should be smaller than the block size. This may leave some empty space in the block. For database perspective, we prefer un-spanned.
- BLOBs are stored as: inside table we store a pointer to the image or media
#### Placement of records in files:
- A File is a sequence of records.
- [Files don't actually exist as separate entities on disk](https://en.wikibooks.org/wiki/Operating_System_Design/File_Systems/Abstraction). (try clicking on the link)
- a File is something abstract by the operating system, so a file is not stored on the hard disc, but the actually the records are stored physically on the hard disc.
- 2 types of arrangement of records in a file:
	1) ***unordered records***
		- Called heap file
		- insertion is fast
		- cost in $O(n)$ for searching a record
	2) ***ordered records***
		- sometimes sequential search is better than binary search for ordered records when you want to obtain a large number of records.
		- hashing is only for equality conditions (meaning that it will only return the specific record we want, not a range) so is not suitable for range queries

- index is another file used to speed up the processes for both ordered and unordered files, to find more about it, see the indexing file I sent.
### Types of tech for storing data:
1) RAID technology is collection of hard discs grouped together grouped with software that helps for data recovery, and SAN technologies allow fast data access and allows data recovery
2) network storage architecture: similar to normal networks, the nodes will be hard discs
3) Instead of a hard disc: does not have movable parts (read/write heads), We can also use an SSD
4) sequential access: magnetic tape storage devices, used for backups

