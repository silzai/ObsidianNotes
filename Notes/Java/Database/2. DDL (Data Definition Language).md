### DDL (Data Definition Language): (week 5)
1) Create
2) Alter
3) Drop
4) Truncate
- Will also do Views
- And sequence

### 1) Create:
```SQL
CREATE TABLE emp1; -- Creating table where emp1 is the object name of the table
(
ID NUMBER(10),
NAME VARCHAR(20),
);

DESC emp1; -- will show the properties of the table
```
- To insert values into the table:
```SQL
INSERT INTO emp1 (ID,NAME)
	SELECT empno, ename 
	FROM emp 
	WHERE deptno IN (10,20); -- Basically copy pasting data from previous table namely emp into emp1
```
- To create a table based on a previously created table (copy the table):
```SQL
CREATE TABLE emp2
AS
	SELECT * FROM emp;

------and to create a table that does not have data but same structure:
CREATE TABLE emp3
AS
	SELECT * FROM emp;
	WHERE 4=6; -- basically pass a wrong condition so that data values do not get copied.
------Creating a table from another table using its values
CREATE TABLE MANAGER (ID, NAME, SALARY, JOB)
AS
	SELECT empno, ename, sal, job,
	FROM emp
	WHERE job LIKE 'MANAGER';
```
### 2) Alter, will make changes on the columns of table:
```SQL
ALTER TABLE TAXT
ADD (SALARY NUMBER(6)); -- ADD will put a column on the table, while insert is used for inserting rows/records with data.

------------To change column name-------------

ALTER TABLE TAXT
RENAME COLUMN tax TO saltax; -- RENAME will change name of column

------------change data type of column---------    

ALTER TABLE TAXT
MODIFY (salary NUMBER(10));
```
### 3) Drop:
```SQL
ALTER TABLE TAXT
DROP COLUMN salary;

--for 2 columns
DROP (salary, saltax);
--for dropping whole table
DROP TABLE tablename
```
### 4) Truncate:
 ¯\_(ツ)_/¯

### View:
```SQL
CREATE VIEW VU_SIMPLE
AS
SELECT * FROM emp
WHERE job LIKE 'SALESMAN';

SELECT * FROM VU_SIMPLE;
```
### Sequence:
```SQL
CREATE SEQUENCE seq_id
INCREMENT BY 10
START WITH 10
MINVALUE 1
MAXVALUE 100;

--------Using this object as key

INSERT INTO person(ID, NAME)
VALUES (seq_id.NEXTVAL, 'AHMED');
```

### Constraints (week 6)
1) NOT NULL
2) UNIQUE
3) PRIMARY KEY
4) FOREIGN KEY
5) CHECK

- can add contraint when creating table, also can use 'alter' to add constraints, example:
```SQL
CREATE TABLE DEPT1 -- CONSTRAINTs when creating table
(
	-- PRIMARY KEY constraint makes the column automatically UNIQUE and NOT NULL
	DEPTNO NUMBER(3) PRIMARY KEY,
	DNAME VARCHAR(20) UNIQUE,
	LOC VARCHAR(20) NOT NULL
	-- To add a constraint with constraint name
	CONSTRAINT DEPT1_DEPTNO_PK PRIMARY KEY(DEPTNO), --DEPT1_DEPTNO_PK is name
);

CREATE TABLE EMP1
(
	EMPNO NUMBER(5),
	DEPTNO NUMBER(3),
	GENDER CHAR(1),
	CONSTRAINT EMP1_GENDER_CK CHECK (GENDER='M' OR GENDER='F'),
	-- To add foreign key, will use same statement, while also adding extra keyword: REFERENCE, and that will be the location of the exact column of the primary key in the other table that will be a foreign key.
	CONTRAINT EMP1_DEPTNO_FK FOREIGN KEY(DEPTNO) REFERENCE DEPT1(DEPTNO)
)
```

- adding constraint by altering it. Case study: if emp1_ename has constraint of only 10 characters, but user attemps to input a larger value, then we can alter the constraint by adding 20 characters:
```SQL
ALTER TABLE EMP1
MODIFY (ENAME VARCHAR(20));
```

- Cascade Delete:
Case Study: if want to delete some dept tuples, then the emp tuples that are linked by foreign key to those dept tuples should be deleted automatically.
```SQL
-- add the line below at the end of the table with foreign key to delete the tuples when the other table tuples are deleted, so in above example, will add this statement at the end of creating TABLE EMP1
ON DELETE CASCADE
```

- To create a composite key (primary key with 2 or more columns):
```SQL
CREATE TABLE CUSTOMER
(
	NAME VARCHAR(2),
	PHONE NUMBER(15),
	AREACODE VARCHAR(10)
	-- creating composite key
	CONSTRAINT CUSTOMER_NAME_PHONE_PK PRIMARY KEY(NAME, PHONE)
	-- can do CHECK for OR multiple values
	CONSTRAINT CUSTOMER_AREACODE_CK CHECK (AREACODE IN ('+974','00974'))
);
```

#### Additional thing:
- Oracle data dictionary: will tell us information about the tables.
```SQL
SELECT TABLE_NAME, TABLESPACE_NAME, STATUS FROM USER_TABLES;
SELECT TBALESPACE_NAME, STATUS, BLOCK_SIZE FROM USER_TABLESPACES;
```
