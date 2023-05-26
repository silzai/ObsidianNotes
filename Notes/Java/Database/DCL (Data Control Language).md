- Can grant or revoke privileges
- To create a user for any purpose, will do:
```PLSQL
CREATE USER user1 IDENTIFIED BY userPass
```
#### To GRANT:
```PLSQL
GRANT SELECT, INSERT -- or can write any privilege name instead of SELECT
ON object_name
TO user_name;
-- TO GIVE ACCESS TO EVERYONE:
GRANT SELECT ON tableName TO PUBLIC;
-- TO ALLOW USERS TO GIVE ACCESS TO OTHERS, WILL WRITE "WITH GRANT OPTION" AT THE END OF GRANT STATEMENT.
GRANT SELECT ON table1 TO userF WITH GRANT OPTION; 
-- to GRANT privilage to CREATE a table, will write:
GRANT CREATE TABLE TO user_name
-- to grant privilege to create table in the the admins account too, will write "ANY" before TABLE:
GRANT CREATE ANY TABLE to user_name;
```
#### To REVOKE
```PLSQL
REVOKE 
SELECT ON table_name
FROM user_name;
```
- then the person who was granted the rights will access the tables by adding the granter username and dot as follow:
```PLSQL
SELECT * FROM granterUserName.emp_table;
```
#### ROLE
-  To grant/revoke privileges very quickly to multiple users, we can use roles.
```PLSQL
-- first we will create the role
CREATE ROLE ROLE1;
-- now give permissions to that role
GRANT CREATE SESSION, CREATE TABLE, CREATE VIEW TO ROLE1;
-- now we can give that role to any user
GRANT ROLE1 TO user1;
-- can DROP roles also, while can also add CREATE TRIGGER to roles
```