1) Scanner: that identifies the tokens in our query, tokens are the keywords, table names etc.
2) parser: responsible for checking the syntax, makes sure whether the statement is correct in terms of syntax
3) validation: if the table/attributes even exists that is queried for, and I have the privileage to access it
4) Query tree: mapping, your select statement to a procedural statement that uses relational algebra expressions, after declarative statement, it maps it into a tree
5) query optimizer: makes the execution plan and plans a good (not optimal, otherwise too much time) execution strategy

## Nested Queries:
- Semi join and Anti join used to un-nest nested queries
- Optimizer does not like nested queries as the inner query may be executed many times
- query optimizer converts nested query into a join using a semi join if used for the operations `EXISTS`, `IN`, `ANY`
	- new query will search in the table and stop searching at the first match
- converts query into anti join : it is used for `NOT EXISTS`, `NOT IN`, `ALL`
	- new query will 
##  Sorting:
- Used when query has `ORDER BY` clause
- Sorting and then joining is more efficient
- to execute `UNION`, `INTERSECT` operations

- In databases, external sorting is done as the data is not able to fit in the RAM, sorting is done in the DBMS cache in RAM
- nR: number of runs/partitions
- nB: number of pages allocated to buffer in a DBMS
- How many runs will be generated, how many passes we need, what will be the cost?
- cost: number of blocks written or read

### Algorithms for `SELECT` operations:
- Query optimizer will choose a from a collection of algorithms to fetch records
- DBMS can use the statistics in the catalog, and based on these statistics of the attributes of the records, and the query optimizer can choose a suitable algorithm 
- two types of `SELECT`:
	- Conjunctive:
		- individual index:
		- composite index: indexes are available on both select conditions
		- intersection of record pointers: get the records from indexes of both conditions then intersect them both to get the record(s)
	- Disjunctive (OR): 
		- get the records from indexes of both conditions then make union of them both to get the record(s)
### Selectivity (for `SELECT`): 
- is the ratio of number of records that are to be selected to the total number of records in whole file
- Why important: the algorithm to be used for selecting/searching records is chosen based on the selectivity.
	- for example: if the selectivity is 1, we simply use linear search

### Joins:
- Will use 2 way joins i.e. joins on 2 tables, because it can be generalized for multiple tables also
- equi-join: If there is an equality condition (=)
- $\theta$ join: If there is range (greater than, less than)
- natural join: Same as equi-join, but will not contain duplicates (in oracle, will use keyword `DISTINCT`)
- Algorithm options: 
	- J1: Nested-loop join: comparable to sequential search
		- will make the smaller table as the outer table
		- will take one block from the outer table, then search and compare it with all of the block of the second table, cost will be $B_r\times B_s$
		- Give more space in buffer to the outer table, so can make the outer table in buffer even smaller
	- J2: index based nested loop join
		- will take a table, then instead of searching all of the blocks of the second table, it simply searching the index of the second table
	- J3: merge-sort join
		- This one is used mostly
		- R `JOIN` on S on A=b
		- 2 pointers, one on first record of 1 table, and the other pointer on first record of $S$
		- if the value of $S$ less than $R$ then will simply move the pointer of $S$ down and check again, if there is equality, then will write that both records of $R$ and $S$ as 1 record on the new join table 
		- if $S$ is less, then will move pointer of $R$
#### Different operations make use of `JOIN`, such as:
- Project ($\pi$):
- Set Operations, have a precondition, that both tables have equal attributes:
	- Union ($\cup$):
		- Result $T$ will contain tuples that are in either $R$ or $S$.
		- R and S are initially sorted, then $T$ will be built using a kind of a merge sort algorithm, by just adding tuples from both tables to $T$
	- Intersection ():
		- Result T will contain tuples that are in R AND S
		- Inter
		- if equal, then output to T
	- Minus ($-$):
		- Result T will contain that are in R but not in S
		- while sorting, if less than, then output to T

- Partition hash join: first partition then probe
- hybrid hash-join: while partitioning, will probe also at the same time

- Aggregate function (`MIN, MAX, COUNT, AVERAGE, SUM`):
	- Some of the operations can be executed using the index only (don't need to go to the original data file) using a dense index, but for sparse index, an additional frequency of values column may be needed in the index file, or can use b-trees.
	- otherwise will scan the table and perform those 

- Inner join: join on matching tuples
- outer join: just need a modification of the J3 algorithm for different outer joins
	- left outer join: 

- pipelined evaluation of query tree executes the next statement even while the previous statement has not finished execution. This evaluation is opposed to the materialized evaluation of the query tree.

- see parallel algorithms for databases (18.8) in slides.
- 