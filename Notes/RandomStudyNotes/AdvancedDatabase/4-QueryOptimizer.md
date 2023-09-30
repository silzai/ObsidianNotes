- Chap-19
# There are 2 techniques for query optimization:
1) based on heuristic rules
2) based on cost estimation
## 1) based on ***heuristic rules***:
- for ordering the operations in a query execution strategy, the rules typically reorder the operations in a query tree.
 - How to deal with `SELECT` in the tree:
	- push `SELECT` down the tree (execute before `JOIN`)
	- execute the most restrictive `SELECT` first. i.e. first execute equality "`=`" operation before range  "`>`"
- How to deal with `PROJECT` in the tree:
	- push `PROJECT` down the tree (execute before `JOIN`) but before the `SELECT`
- replace cartesian product and `SELECT` with a `JOIN`
## 2) based on ***cost estimation***:
- This uses cost estimation of different execution strategies and chooses the execution plan (tree) that minimizes the total estimated cost.
- Regarding the equivalence rules, the query optimizer can choose any equivalent relational algebra expression to execute, depending on the statistics of the tables. So the query optimizer can select any one of the relational algebra expressions on the right hand side or the left hand side, it depends on the statistics of the tables.
### Cost Functions:
- Cost functions for `JOIN`
	- CJ1:  
	- CJ3: read table once + writing the result + sorting
- Cost functions for `JOIN`: 
	- `JOIN` selectivity: it is the ratio of the resulting file after `JOIN` to the cartesian product.
	- obtaining the `JOIN` selectivity determines which algorithm to use for `JOIN`
	- number of blocks needed to store/write the result: $$(js\ * \ |R| \ * \ |S|)/bfr_{RS} $$

___
- Then which operations will I use to execute the operations of the tree, called "evaluation plan", it will resolve how each operation should be executed, eg. will it use sequential search, or indexes, will it use hash join or merge join, DBMS uses statistical information from the catalog to choose an execution option, can use command in Oracle to check the plan: `EXPLAIN PLAN FOR <SQL query>`

midterm chapters: 16, 17, 18, 19

