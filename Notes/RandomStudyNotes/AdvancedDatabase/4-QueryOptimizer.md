- Relies on heuristics
- does not rely on user input, the database is responsible for the execution
- works based on the information of the catalog

- DBMS takes a query and represents it as at tree

1) scanner and parser
2) query optimized according to heuristics

- The tree is first made by listing all the tables and listing the cross products between them
- execute `SELECT` before `jOIN`
- push `PROJECT` down the tree (execute before `JOIN`)
- push `SELECT` operation down the tree (execute before `JOIN`)
- replace cartesian product with a `JOIN`
