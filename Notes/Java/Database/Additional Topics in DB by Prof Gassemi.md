- will see these problems in industry
- There are functional requirements and non-functional requirements to any system (software/application/etc.)
- example of non functional requirement:
	- number of requests per sec to a website i.e. the quality
## how IT will implement the database:
### 3 types of data are in databases
- **Transaction data**: the data included in a transaction provided by an employee for ex, and will contain the data that is either accepted or rejected, whereas the Master Data (system of records) will contain the transaction data ONLY when the transaction is ACCEPTED.
- **Master Data**: the actual data/system of records, does not contain the intermediate transactional data.
- **Analytical Data**: describes the enterprise performance/analyses the performance of the entity. It supports research on the Master Data/transactional data.
### 3 types of Databases:
- **systems of records**: is the Master data. Filtered Data is consolidated into the Master Data from numerous sources, also called a data hub.
- **System of insight**: is the analytical data. software/data warehouse, contains EVERYTHING like master data/operational data/transactional data. is used for Data analytics/BI platforms. An ETL can use data from here to generate Reports etc. Oracle uses ODI (oracle data integrator) to do ETL.
- **System of engagement**: data used to interact with end-user. implementation: lookup table uses stored procedures to transition from state to state

## Non-functional requirements/quality attribute examples:
- If everything goes down, the client/end-user should not be affected.
### Types of the Quality attributes:
- **High availability**: There are 2 identical databases, and a load balancer diverts the transactions to the other database incase one goes down. RAC and oracle active guard.
- **scalability**: database should scale with increasing number of users. 2 types of scaling: 
	- horizontal: add more machines/nodes and replicates the database
	- vertical: one machine increases the resources
- **Disaster Recovery**: having a standby site/secondary site, in a completely different geographical site. if a primary site fails then we will transfer to secondary site. --Switchover is done intentionally to transfer, switchback is done to revert back to the primary site.

Additional info:
- weblogic server is used in ministry for deploying java software. Configurations are done in this, and these configurations are also data, these are called meta data.
- ORM: Can be used instead of normal JDBC, maps objects to the DBMS automatically:
	- Types of ORMs for different languages:
		- for dotnet (c#) : entity framework
		- for java : JPA