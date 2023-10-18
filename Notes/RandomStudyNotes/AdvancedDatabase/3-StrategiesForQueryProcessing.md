 - This part is for Chap-18
- Chap-18 and Chap-19 go hand-in-hand like so:
	- This chapter shows with which algorithms, operations in the evaluation plans (trees) can be executed, chapter 19 will show how to pick the evaluation plan with the least cost (i.e. query optimization).
# Table of Contents:
- There are 4 steps in Query Processing:
==ask prof if order is correct==
1) Translating SQL to relational algebra expressions (making the evaluation plan/tree)
2) Selecting the evaluation plan with least cost (query optimization)
	- Heuristic based optimization
	- Cost-based optimization
3) Each node of the tree may have different ways of executing the queries, which also have different costs:
	- un-nesting `EXISTS`, `IN`, `ANY` using semi-join
	- un-nesting `NOT EXISTS`, `NOT IN`, `ALL` using anti-join
	- sorting
	- translating `SELECT`
	- translating various operations using `JOINS`
	- translating `PROJECT`
4) Methods to evaluate the evaluation plan (the tree) by the DBMS
	- materialization
	- pipelining
# 1) Translating SQL to relational algebraic expressions (making evaluation plan)
- An SQL query is first translated into an equivalent extended relational algebra expression—represented as a query tree data structure—that is then optimized to reduce cost (next chapter is for optimization).
- The tree is first made by listing all the tables and listing the cross products between them, this tree is called canonical tree, not optimized tree yet
- The final tree may be called an annotated tree, since it is optimized heuristically, and has labels or "annotations" on every node of the tree telling it "how" to execute the node (which algorithm to use from the ones we will study below)
# 2) Selecting the evaluation plan with least cost (query optimization)
- Will see this in chapter 19 (Query Optimizer).
# 3) Different ways to execute different queries:
## Nested Queries:
- query optimizer converts nested query into a join using a semi-join or anti-join
- ***Semi-join ($T1.X \ltimes T2.Y$)*** used to un-nest nested queries with `EXISTS`, `IN`, `ANY`
	- What does it do: A row of $T1$ is returned as soon as $T1.X$ finds a match with any value of $T2.Y$ without searching for further matches.
- ***anti-join ($T1.x \ \bar{\ltimes} \ T2.y$)*** are used to un-nest nested queries with `NOT EXISTS`, `NOT IN`, `ALL`
	- What does it do: A row of $T1$ is rejected as soon as $T1.x$ finds a match with any value of $T2.y$. A row of $T1$ is returned, only if $T1.x$ does not match with any value of $T2.y$.
- Optimizer does not like nested queries as the inner query may be executed many times (inefficient)
##  Sorting:
- Used when query has `ORDER BY` clause
- Sorting and then joining is more efficient
- to execute `UNION`, `INTERSECT`, and other operations.

- In databases, external sorting is done as the data is not able to fit in the RAM, sorting is done in the DBMS cache in RAM
- nR: number of runs/partitions
- nB: number of pages allocated to buffer in a DBMS
- How many runs will be generated, how many passes we need, what will be the cost?
- cost: number of blocks written or read
- **IMPORTANT**: If nB = x (meaning there are x pages available in RAM for sort-merge to use), then 1 page will be reserved for the output, and x-1 pages for the runs.

## Algorithms for `SELECT` operations:
- Query optimizer will choose a from a collection of algorithms to fetch records
- DBMS can use the statistics in the catalog, and based on these statistics of the attributes of the records, and the query optimizer can choose a suitable algorithm 
### We have two types of `SELECT`:
- Conjunctive (`AND`):
	- individual index:
	- composite index: indexes are available on both select conditions
	- intersection of record pointers: get the records from indexes of both conditions then intersect them both to get the record(s)
- Disjunctive (`OR`): 
	- get the records from indexes of both conditions then make union of them both to get the record(s)
### Selectivity (for `SELECT`): 
- is the ratio of number of records that are to be selected to the total number of records in whole file
- Why important: the algorithm to be used for selecting/searching records is chosen based on the selectivity.
	- for example: if the selectivity is 1, we simply use linear search

## Joins ($\bowtie$):
- Will study 2 way joins i.e. joins on 2 tables, because it can be generalized for multiple tables also
- Types of joins:
	- Equi-join: If there is an equality condition ($=$)
	- $\theta$ join: If there is range (greater than, less than)
	- natural join: Same as Equi-join, but will not contain duplicates (in oracle, will use keyword `DISTINCT`)
### Algorithm options: 
#### J1: Nested-loop join (or nested-block join):
- comparable to sequential search
- will make the smaller table as the outer table
- will take one block from the outer table, then search and compare it with all of the block of the second table, cost will be $B_r\times B_s$
- Give more space in buffer to the outer table, so can make the outer table in buffer even smaller
#### J2: index based nested loop join
- will take a table, then instead of searching all of the blocks of the second table, it simply searching the index of the second table
#### J3: merge-sort-join
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

## Aggregate Functions (`MIN, MAX, COUNT, AVERAGE, SUM`):
- Some of the operations can be executed using the index only (don't need to go to the original data file) using a dense index, but for sparse index, an additional frequency of values column may be needed in the index file, or can use b-trees.
- otherwise will scan the table and perform those 

- Inner join: join on matching tuples
- outer join: just need a modification of the J3 algorithm for different outer joins
	- left outer join: 

# 4) Evaluating The Evaluation Plan:
- Once the optimization is done, the query can be executed/evaluated in 2 ways:
- ***pipelined evaluation*** of query tree executes the next statement even while the previous statement has not finished execution. 
	- Avoids cost and time delay associated with writing intermediate results to disk
	- Being able to start generating results as quickly as possible
	- to look into the iterator model for pipelining, check the reference below
- ***materialized evaluation*** of the query tree executes individual operations one at a time, while storing the result of each evaluation/expression.

- see parallel algorithms for databases (18.8) in slides.

___
- References:
	- [Query Processing ucDavis](https://www.cs.ucdavis.edu/~green/courses/ecs165a-w11/8-query.pdf)
	- [Query Processing Paper, IndianaUni](https://clas.iusb.edu/computer-science-informatics/research/reports/TR-20080105-1.pdf)
	- [Query Processing CMU](https://15445.courses.cs.cmu.edu/fall2021/notes/11-queryexecution1.pdf) (helpful for "evaluating the evaluation plan")
	- [Query Processing CMUQ](https://web2.qatar.cmu.edu/~mhhammou/15415-s14/lectures/Lecture17-Query-Optimization-MHH-24March-2014.pdf)
	- [JOINs CMUQ](https://web2.qatar.cmu.edu/~mhhammou/15415-s15/lectures/Lecture18-Relational-Operators-29March-2015.pdf)
	- [helpful slides for all chapters](https://www.db-book.com/slides-dir/index.html)
	- [Cost of Select, UniSouthWales](https://www.cse.unsw.edu.au/~cs9315/16s1/notes/D/notes.html)

