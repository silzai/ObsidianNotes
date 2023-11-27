>[!note] Data Warehouse
>- A new type of DBMS which keeps no transactional data, but only historical information (as opposed to regular DBMS which support everyday transactions)
>- In case the commercial entity wants to do analytical operation to support time-series and/or trend analysis on different aspects of the company/entity

>[!warning]
>For simple queries, can just use Views, but not a good reason because:
>- breadth and width of generating view is limited
>- will put pressure on the regular daily operations
>- 

>[!note]
>Data warehouses are read only, so no need to worry about integrity etc.

>[!success]
>A data warehouse is subject-oriented, integrated (cleaned up and combined from multiple sources), and is used to support management decisions

> [!info]
> canned queries: queries that are already prepared,

- from a data warehouse, we want to summarize a particular query, OLAP will scan huge amount of data for the purpose of getting summaries.
- data mining: is a functionality that we can apply on a data warehouse. Data mining is related to extracting knowledge and meaningful patterns from the data warehouse as opposed to machine learning, that learn from the data, and enhance themselves

- ETL: 
	- extract data from different sources
	- Transform into suitable
	- load the data into the data warehouse

- Data warehouses 
	- contain data of many years
	- it may be stored on multiple DBs
	- Data warehouse is a big store
	- we still need to refresh the data warehouse to add more data to the data warehouse and do the ETL
	- and purge the data warehouse to delete unneeded objects.
	- has cubes: multidimensional cube of the data (unlimited dimensions)
	- unlimited dimensions:
		- an object cube can have multiple dimension, for example, suppose we have a cube "milk", it has multiple dimensions such as 
		- and these dimension have levels of hierarchy called aggregation levels
	- data warehouse is fixed for some time, big data changes a lot, and has multiple data types, and normal relational databases are not suitable to store big data
		- ODS operational data store where random data is stored ==???== data is dumped and is similar to in a data lake and is used by big data

# Operations of Data Warehouse
- as opposed to normal aggregate operations in views, data warehouse has the additional operations: 
- rollup (drill up): data is summarized by generalizing (climbing up) the levels of hierarchy of data 
- drill down: complement of rollup
- slice and dice: projection operations are performed on the dimensions
- pivot: rotation of dimensions where we shift the focus on another particular dimension ==???==

- getting query from data warehouse, we are doing JOIN between star schema and indexes
- 