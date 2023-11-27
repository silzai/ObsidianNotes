- chap-30
# Types of Database Security Mechanisms:
1) Discretionary: 
2) Mandatory:
	- classify users/data into various security classes
3) Role-based: 
	- enforces policies and privileges based on organizational roles
# Control Measures:
## 1) Access control: 
- create accounts and passwords
- to preserve database integrity
- Has a login session which is stored in log: we can add more columns to the system log, which are user id and machine id
- can do database audit to scan the log file to see what was done by each user. 
- access control handles "all sensitive" and "all data is not sensitive" easily

### Discretionary access control (DAC) based on granting and revoking privileges
- Account level
- Relation (table) level:
	- we need to associate privileges with each table
- We have a "access matrix": 
	- rows are users 
	- columns are data objects 
	- a cell has type of privilege OR we can say??? 30.2
	-  
## 2) inference control:
- information about individuals should not be accessed even when summaries are generated 
- called inference because information can be inferred with this info
## 3) Flow control:
- Prevent flow of privileges to unauthorized users
## 3) data encryption:
- data should be encrypted

>integrity: improper use of the data
# The DBA:
- Central authority for administering database systems
- can do hidden operations on the database, that normal users cannot do
- Access control:
	- can create accounts
- privilege granting

# asd
- We need security to ensure "privacy"