### DML: (week 4)
1) Insert
2) Update
3) Delete
Database transactions:
- Commit (save to disk)
- RollBack (undo)
- SavePoint
```SQL
COMMIT; -- to save, cannot rollBack after commits
ROLLBACK; -- to go back
SAVEPOINT t1; -- create a savepoint that you can rollBack to
SAVEPOINT t2;
ROLLBACK TO SAVEPOINT t1; -- will rollBack to savepoint t1
```

### 1) Insert:
```SQL
INSERT INTO dept(deptno, dname, loc)
VALUES(50, 'DEVELOPMENT', 'DOHA'); -- if no argument is put, then it will be null value, but can also specify null by writing: NULL
--but this insertion is not saved yet, so we have to save it using
```

### 2) Update:
```SQL
UPDATE emp
SET deptno = 20
WHERE empno = 7782;
```

### 3) Delete:
```SQL
DELETE FROM dept
WHERE dname LIKE 'SALES';
```

DataBase Transactions:
¯\_(ツ)_/¯