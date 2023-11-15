>[!warning]
>The input query format **must** be as follows (taking care of where to put spaces):
> - For selection on 1 table:
>```plsql
>SELECT * FROM tableName WHERE attribute = "theAttribute"
>```
>- For selection on 2 tables (JOIN):
>```plsql
>SELECT * FROM tableName1,tableName2 WHERE tableName1.attribute = tableName2.attribute
>```
>- We will NOT put a semicolon at the end of the query (;)

>[!warning]
>We are not considering cost of PROJECT operation, so all selection on attributes will return same cost as selecting from * (wildcard operator)
	
>[!warning]
>- Did not use $C_{S2}$ cost formula because our tables are only sorted (ordering field is) on primary keys, which does not contain same values.
>

>[!warning]
>- Did not use $S5$ cost formula because our tables are sorted on (ordering field is) on primary key (no clustering index), which does not contain the same values.

# Design choices for storing metadata:
- We stored our metadata as tables in the Oracle DBMS.
- We did this because actual Database Management Systems (DBMS) also store their metadata/data in table format, so it made sense to store our metadata in table format.
- It was also easier to call and store the metadata in the data buffer of our application when the metadata was in a table format.

# Formula for finding conjunctive select:
- Then, filter using Salary and Sex on the selected records: 
$$Filter \ Cost = \text{Number of records × Filter Selectivity × SSC}$$
- Finally, calculate the total cost: 
$$Total \ Cost = \text{ISC + Filter Cost}$$
- Where $$\text{SSC = (muliply all selectivites of attributes in the query) / 2}$$
- and $$\text{Filter selectivity=(muliply all selectivites of attributes in the query)/total number of records}$$
- 