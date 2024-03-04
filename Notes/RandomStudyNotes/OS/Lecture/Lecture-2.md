# RAM
## SRAM
- maybe on-chip of CPU or off-CPU
- used by cache
- few MB
## DRAM

# At which stage are code instructions binded to the memory?
## Absolute code
- In this code, binding to physical memory locations happens at compilation time, every instruction is defined by a specific address that programmer has to define, is written in low level language, such as assembly
## Relocatable code 
- high level language is first compiled to a binary file, and that is when the OS assigns the instructions to the memory, called dynamic binding
	- OS does not produce the physical addresses for the instructions but uses logical addresses
	- physical allocation is done on execution time
	- MMU (memory management unit) uses a relocation register to do mapping from logical address to physical address
	
>[!info]
>Slide10: Logical and physical addresses are the same in Compile-time and Load-time address-binding schemes; logical and physical addresses differ in execution-time address-binding scheme.

- Dynamic Loading???
- Overlays:
	- to allocate a process a certain amount of memory that is less than its size

- question by P=NP
	- what happens when logical memory address does not map to physical address? then we will replace the physical memory block with the new code
	- can also do swapping
# Swapping
- A process can be swapped temporarily out of memory to a backing store, and then brought back into memory for continued execution
- backing store on disc represents a copy (image) of every process under execution, and used for recovery
- if memory is completely full, and user runs high priority process, then will do roll-out, roll-in

- All below is done by MMU, and for absolute code, this is not needed:
	- for single partition contiguous memory allocation:
		- for a certain process relocation address : 5000, the limit: 500
			- first physical address starts from 5000
			- will go upto 499
			- only contain processes that will be loaded into memory
		- the limit: To know the ending address
		
		- if logical address is within the limit:
			- first will compare with the limit, so the address is valid
	- for multiple partition allocation:
		- OS keeps track of all holes and and allocation partitions
- # Dynamic Storage Allocation Problem
- First fit:
	- advantage: fast
	- disadvantage: resource wastage if the first one is very big than the process
- Best-fit:
	- advantage: resource allocation is most optimized
	- disadvantage: slow
- worst fit:
	- advantage: some processes may expand in their execution, so will use this
	- disadvantage: wasting resources, slow
	
- fragmentation: wasted memory
	- external frag: total memory of all holes (total memory that can be used to satisfy a request)
		- can solve/reduce it by compaction:
			- merge all holes to single big partition
			- Shuffle memory contents to place all free memory together in one large block. 
			- Compaction is possible only if relocation is dynamic, and is done at execution time.
	- internal frag: memory allocated for process (difference of allocated memory and process size) $$Internal\ fragmentation=allocated\ memory - process\ size$$
		- cannot solve this
- Because of fragment issues, we need 
# Non-contiguous memory allocation schemes:
## Paging:
- memory is divided into fixed blocks called frames with values of powers of 2
	- this is from memory perspective
- but from process's (logical) ==??== perspective, we have pages of same size:
- OS keeps track of all free and allocated frames
	- these frames are non-contiguous
- Page table:
	- it is per process
	- have page number and mapping frame to it 
	- translates logical address to physical address
- example:
	- logical address space of process has 100 addresses: 0-99
	- divided to page size of 10
	- so need 10 pages
	- CPU wants to execute instruction at address 17 from logical address space
		- first will see where the address will be in the pages, page numbers start from 0, so 17 will be in page 1
		- then see which frame this page maps to
		- suppose this maps to frame 200
		- so will just add 200 to 17, and will allocate physical address
- Disadvantage:
	- internal fragmentation will be worse if last frame is not completely full, so worst case will be: $allocated\ memory - 1$
- Address Translation scheme:
	- CPU generates logical address with 2 parts: `<page number, page offset>`
	- if logical address is m bits, then if n bits are the offset, then m-n is the page number where this address exists
	- 
## Segmentation:
- another way to generate logical addreses
- in paging we divided program into fixed sized blocks, in segmentation same is done but blocks are of different sizes called segments
- we don't have frames and pages, only segments
- there is no internal fragmentation
- consists of: `<segment number, offset>`
- segment tables:
	- shows num of entries 
	- entries are equal to num of instructions process has
	- each entry has base and limit
	- STLR stores the number of segments this process consists of.
		- segment number `s` is legal if `s < STLR`
		- offset should be less than the limit
	- tip: to get the size of the whole process from segment table, can add all the limits 
- 