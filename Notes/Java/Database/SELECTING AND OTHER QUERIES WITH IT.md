# SQL
- Has three types of accents in its language that are used to do the following: 
	- DDL: select, create, alter, delete
		- This affects the table itself i.e. attributes/columns
	- DML: insert, update, delete
		- This affects the rows of the table i.e. tuples/records
	- DCL: revoke, grant

## Language Queries:
- can use > or < for DATE datatype
- <> is not equals
```SQL
SELECT ename,job,mgr,sal
FROM emp
-- here % is the wildcard and can only use it with LIKE keyword and _ represents a single character which could have any value, will use LIKE for strings, = for int
WHERE mgr LIKE '_M%';
WHERE mgr IN (7902,7566,7788);
--is the same as:
WHERE mgr=7902 OR mgr=7566 OR mgr=7788;
----------------------------------------
WHERE mgr IS NULL;
--to query the field that is null or NOT NULL, then we will use IS
ORDER BY sal ASC, SAL DESC; 
--will show sorted data, DESC for descending and will first sort sal and then sal will be sorted inside the sal rows

```
## SQL Functions:

- GROUP BY will collect same data names and group them, this is helpful when we have to find aggregates for different roles in a field.
   to put condition on the GROUP, will use keyword HAVING e.g.
```SQL
SELECT deptno, sal
FROM emp
GROUP BY deptno
HAVING deptno<>30;
```
- If we want to do some query with a field, and some of fields values are NULL, then we can just replace the NULL values by No Value Function, this will replace the NULL values e.g.
```SQL
NVL(TO_CHAR(COMM), 'No Commission'), NVL(SAL, 0) -- will replace NULLs with given value so we can do any operations with it-----But the 2nd arg should be of same type as field, thats why made the first example 'TO_CHAR'
```

- Can use 'Aliases' by using "AS" keyword e.g. 
```SQL
ENAME AS NameOFEmployee
```
 
#### VARCHAR2 functions
```SQL
SELECT 
UPPER(ENAME), -- converts to uppercase
LOWER(ENAME), -- converts to lowercase
LENGTH(ENAME), -- gives length, also works with NUMBER
SUBSTR(ENAME), -- gives the substring specified by 
INSTR(ENAME, 'A'), -- gives the string location
ROUND(45.45, 0), -- 1st argument: number to be rounded, 2nd argument: decimal places to be rounded upto, can also use TRUNC to just cut without rounding  
-- can use FROM DUAL, if just want to test any function and you dont have specific table
FROM EMP;
```

#### DATE functions
```SQL
SELECT
HIREDATE, HIREDATE + 1, HIREDATE -1, -- will give date value adding a day
SYSDATE - HIREDATE, -- date - date will give number of days 
MONTHS_BETWEEN(SYSDATE, HIREDATE), -- will give number of months between the arguments (SYSDATE gives todays date) (will do ROUND so that it does not give too much decimal places)
ADD_MONTHS(HIREDATE, 6),
TO_CHAR(HIREDATE, ''), -- this will convert the format of the date to your choice e.g. 'mm dd yy', 'yyyy month DAY' etc.
TO_DATE() -- 1st arg will have string of the date, and 2nd arg will have the date format

FROM EMP;
```

#### Multiple-Row functions
- can use MIN, MAX, SUM, COUNT, AVG

### Joins
1) equi-join/inner join: when doing a JOIN based on the primary key and foreign key being the same. example:
```SQL
SELECT emp.ename, dept.dname -- calling the attribute like speedups processing
FROM emp, dept
WHERE dept.deptno = emp.deptno -- this is the equi-join condition
----------------can also do this-----------------------------
SELECT ename, dname
FROM emp NATURAL JOIN dept;
----------------can also do this-----------------------------
SELECT ename, dname
FROM emp JOIN dept ON (emp.deptno = dept.deptno);
```

2) non equi-join: when doing a JOIN not based on the primary key and foreign key. example:
```SQL
SELECT sal, grade
FROM emp, salgrade
WHERE emp.sal BETWEEN sal.losal AND sal.hisal;
```

3) self joins: Will need to use 'Aliases' to do self join, will make two aliases from the same table perform the join. example:
```SQL
SELECT e.ename AS employee, m.ename AS manager
FROM emp e, emp m
WHERE e.mgr = m.empno;
```

4) outer join: When we do inner join, will only show values that are related by the primary key, so outer join select rows from the fields of tables that have null values and are not connected by a primary key. example: "show me the departments that do not have an employee, as well as the all of the other ones ":
```SQL
SELECT emp.ename, dept.dname
FROM emp RIGHT OUTER JOIN dept ON (emp.deptno = dept.deptno);
-----------------is the same as-----------------------
HOW TO WRITE (+) NOTATION????
```

>note: SUBQUERIES are like nested functions where an inner function returns a value to an outer function who in turn, uses that value to process info