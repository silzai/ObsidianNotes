- Chap-19
# There are 2 techniques for query optimization:
1) based on heuristic rules
2) based on cost estimation
# 1) based on *heuristic rules*:
- The rules reorder the operations in a query tree so that the sizes of the input relations at every is smallest.
 1) How to deal with `SELECT` in the tree:
	- push `SELECT` down the tree (execute before `JOIN`)
	- execute the most restrictive `SELECT` first. i.e. first execute equality "`=`" operation before range  "`>`"
2) How to deal with `PROJECT` in the tree:
	- push `PROJECT` down the tree (execute before `JOIN`) but before the `SELECT` (related to point number 4)
3) replace cross/cartesian product followed by `SELECT` (both should be in that order) with a `JOIN` (because cross products are very expensive, so we don't execute them)
4) If we only only to "project" certain attributes only, then we will not carry whole tables throughout the execution of the tree, instead will filter out only the useful attributes that are used for further operations (such as the primary key) using "project".
- For example, suppose we have a query in SQL,
	- then the canonical tree will be with the order of the execution of the tree being the same as the order that query was written in SQL
	- Then the above rules will be used to convert the canonical tree into an optimized tree.
# 2) based on *cost estimation*:
- This uses cost estimation of different execution strategies and chooses the execution plan (tree) that minimizes the total estimated cost.
- Steps in cost-based query optimization:
	1) Generate logically equivalent expressions using equivalence rules
	2) Annotate (label) resultant expressions to get alternative query plans
	3) Choose the cheapest plan based on estimated cost
- Regarding the equivalence rules, the query optimizer can choose any equivalent relational algebra expression to execute, depending on the statistics of the tables. So the query optimizer can select any one of the relational algebra expressions on the right hand side or the left hand side, it depends on the statistics of the tables.
### Cost Functions:
- Cost functions for `JOIN`
	- CJ1:  Nested-loop join
	- CJ2: index-based nested-loop join
	- CJ3: Sort-merge join
		- read table once + writing the result + sorting
- Cost functions for `JOIN`: 
	- `JOIN` selectivity ($j_s$): it is the ratio of the resulting file after `JOIN` to the cartesian product.
	- obtaining the `JOIN` selectivity determines which algorithm to use for `JOIN`
	- number of blocks needed to store/write the result: $$(js\ * \ |R| \ * \ |S|)/bfr_{RS} $$
	- $bfr_{RS} \text{ = blocking factor of resultant joined table}$ 

___
- Then which operations will I use to execute the operations of the tree, called "evaluation plan", it will resolve how each operation should be executed, eg. will it use sequential search, or indexes, will it use hash join or merge join, DBMS uses statistical information from the catalog to choose an execution option, can use command in Oracle to check the plan: `EXPLAIN PLAN FOR <SQL query>`

- will always make deep left trees, advantage is that it reduces the number of possible plans to be generated, 
- statistics based is cost based
___
References:
[Query Optimization, washingtonU](https://courses.cs.washington.edu/courses/cse444/12sp/exams/practice-optimizer-sol.pdf)

