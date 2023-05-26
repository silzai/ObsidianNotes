- Can be used to write script like programming language like variable declarations, loops etc.

- Structure of PL/SQL script:
```PLSQL
declare
	(declare your variables)
begin
	SQL statement (write your pl/sql statements)
	(IMPORTANT: for SELECT statement, we must use INTO, or it will not work)
exception
	Exception
```

- Example:
```PLSQL
SET SERVEROUTPUT ON; -- This line will make oracle run this program, need to do only once
DECLARE
	V1_ENAME VARCHAR(10);
	V2_JOB EMP.JOB%TYPE; -- declare this variable based on existing field in tables; meaning the same datatype as the attribute described in the declaration
BEGIN
	SELECT ENAME,JOB
	INTO V1_ENAME, V2_JOB
	FROM EMP
	WHERE ENAME LIKE 'JAMES';
	DBMS_OUTPUT.PUT_LINE('ENAME = ' || V1_ENAME); -- this statements prints line; 
												  -- || means concatenate
EXCEPTION
	WHEN NO_DATA_FOUND
	THEN 
		DBMS_OUTPUT.PUT_LINE('NO RECORD FOUND');
END;
```

### RowType (declare a tuple all at once):
- If want to declare one row in one go from a table instead of individual variables for attributes. rowType will be a tuple of values of one record, and can call an individual attribute/column from the rowType:
```PLSQL
DECLARE
	DEPT_REC DEPT%ROWTYPE; -- declare a rowType of table dept
BEGIN
	SELECT * -- select all columns
	INTO DEPT_REC 
	FROM DEPT
	WHERE DNAME LIKE 'SALES';
	DBMS_OUTPUT.PUT_LINE('DNAME =' || DEPT_REC.DNAME); -- will access the tuple for taking dname
EXCEPTION
	WHEN NO_DATA_FOUND
	THEN 
		DBMS_OUTPUT.PUT_LINE('NO RECORD FOUND');
END;
```

### DML:
- DML using PL/SQL, e.g. updating emp salary:
```PLSQL
DECLARE
	V_INC CONSTANT NUMBER(10) := 1000;
BEGIN
	UPDATE EMP
	SET SAL = SAL + V_INC;
	WHERE ename LIKE 'BLAKE';
END;
```

### Conditional:
```PLSQL
DECLARE 
	EMP_TOT NUMBER(5) := 0;
BEGIN
	SELECT COUNT(*)
	INTO EMP_TOT
	FROM EMP
	WHERE SAL<5000
	IF EMP_TOT = 0
	THEN
		DBMS_OUTPUT.PUT_LINE('NO EMPLOYEES FOUND');
	ELSE
		DBMS_OUTPUT.PUT_LINE('FOUND :' || EMP_TOT);
	END IF;
END;
```

### Cursor (To select multiple rows):
- To select multiple rows, because declaring normal variable just stores one tuple/data/row.
- Now, with cursor, will not use variables, but will use a cursor.
- Will perform operation on each row using a LOOP:
```PLSQL
DECLARE
	CURSOR CUR IS
	SELECT ENAME, DNAME
	FROM EMP NATURAL JOIN DEPT;
BEGIN
	FOR I iN CUR
	LOOP
		DBMS_OUTPUT.PUT_LINE(I.ENAME || ' ' || I.DNAME);
	END LOOP;
END;
```

# Procedures, funtions and triggers (Lab08)

- We can make *stored* procedures and functions, this will make each procedure/function in different files.
- difference bw procedures and funtions:
	- procedures: We can call it like a function and can pass values to update any attribute, there is no return value
	- funtions: there is return value

- creating procedure will store the procedure into the dbms:
```PLSQL
CREATE OR REPLACE PROCEDURE dept_sal(deptid NUMBER, sal_raise NUMBER)
IS
BEGIN
	UPDATE emp
	SET sal = sal + (sal*sal_raise)
	WHERE deptno = deptid;
END;
```
- to call it:
```PLSQL
EXEC dept_sal(10, 0.05);
```

- creating function will store the funtion into the dbms:
```PLSQL
CREATE OR REPLACE FUNCTION count_emp(deptid NUMBER)
RETURN NUMBER IS total NUMBER(5) := 0; -- declaring variables
BEGIN
	SELECT COUNT(*)
	INTO total
	FROM emp
	WHERE deptno = deptid;
RETURN total; -- actually returning
END;
```
- to call it:
```PLSQL
DECLARE
T NUMBER(5);
BEGIN
	T := count_emp(10);
	DBMS_OUTPUT.PUT_LINE('NUMBER OF EMPLOYEES IS:' || T);
	------OR CAN ALSO DO WITHOUT DECLARING VARIABLE-------
	DBMS_OUTPUT.PUT_LINE('NUMBER OF EMPLOYEES IS:' || count_emp);
END:
```

#### Triggers:
- When doing DML, we have triggers, they will run automatically BEFORE or AFTER any DML operation that we can specify:
	  - 2 types:
		  - statement triggers: will run on background (default)
		  - row triggers: will run for all DML operations that are executed.

- creating triggers:
```PLSQL
CREATE OR REPLACE TRIGGER check_hire_date
AFTER/BEFORE INSERT (OR UPDATE OR DELETE) ON emp; -- This will specifiy for which table to run the trigger and which DML operation for, can only create one trigger per table
FOR EACH ROW
BEGIN
	iF SYSDATE - :NEW.hiredate > 30 -- :NEW will contain the value after the trigger firing, and :OLD will contain value before the trigger fires.
	THEN
		RAISE_APPLICATION_ERROR(-20001, 'MORE THAN 30 DAYS APART') -- will stop execution of program
	END IF;
END;
```
- To disable or delete trigger:
```PLSQL
ALTER TRIGGER check_hire_date DISABLE;
DROP TRIGGER check_hire_date;
```

Questionable note: we will not add 'declare' block for function/procedure, but can add for triggers.