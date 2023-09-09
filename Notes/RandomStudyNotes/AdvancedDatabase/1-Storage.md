There are two ways:
1) RAID technology is collection of hard discs grouped together grouped with software that helps for data recovery
2) network storage architecture: similar to normal networks, the nodes will be hard discs

Databases aim to get results quickly, following factors are part of efficient data access:
## Efficient Data Access: How?
### 1) Data buffering for reading data
-  reading data ahead of request (buffering): CPU does not directly accesses the hard disc, but the RAM, whenever CPU wants to read a block of data, it checks the buffer first, if data is not available, then checks the hard drive. the buffer manager anticipates what data will be read next, buffer is an area in the RAM.
- buffering is most useful in processes run in parallel concurrency, this is possible by special hardware, i.e. multiple CPU processors exist.
- double buffering: 
- techniques for filling and flushing the buffer (buffer replacement strategies):
	- least recently used (LRU):  if it in the buffer for a long time, then unlikely we will need it
	- FIFO: opposite to LRU, we just processed it (occupied longest by a page), so don't need it anymore, so override it
### 2) Placement of data on hard disc: 
#### placement of blocks on the hard disc:
- if contiguous allocation, on the track, in sector 1, sector 2 etc. arrange blocks one after the other. ; linked allocation: if scattered over multiple blocks,
- we fixed length records, and variable length records, where it corresponds
- during formatting, OS allocates size of blocks in hard drive.
- in database, we call sectors, blocks. it has a capacity.
- blocking factor: number of records that can be stored in a block
#### placement of records on a block:
- spanned records: 
	- I want to fill the block to max capacity. this will have effect that a record may be stored in different blocks. So the cut-off record is divided, but is joined to the second block by having a pointer to the next block. We don't lose storage space in this (no empty space in blocks).
- un-spanned records: 
	- We prefer that a whole record is stored in a single block. this may leave some empty space in the block. For database perspective, we prefer un-spanned.
- BLOBs are stored as: inside table we store a pointer to the image or media
#### Placement of records in files:
- File is something abstract by the operating system, so a file is not stored on the hard disc, but the actually the records are stored physically on the hard disc.
- 2 types of arrangement of records in a file:
	1) unordered records
		- Called heap file
		- insertion is fast
		- cost in O(n)
	2) ordered records
		-  
		- sometimes sequential search is better than binary for ordered records
		- hashing is only for equality conditions (meaning that it will only return the specific record we want, not a range) so is not suitable for range queries, so not useful for databases

index is another file used to speed up the processes for another file
### Types of tech for storing data:
- We have RAID and SAN technologies: allows fast data access and allows data recovery
- Instead of a hard disc: does not have movable parts (read/write heads), We can also use an SSD
- sequential access: magnetic tape storage devices, used for backups

