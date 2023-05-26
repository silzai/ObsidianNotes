- Java Database Connectivity (JDBC) is just a term used to refer to any application that uses the java.sql API, it will be used to make a Java GUI application with database connectivity.

- Classes that will be used for the JDBC app, and are included in Java.sql package:
	- DriverManager
	- Connection
	- Statement
	- ResultSet

### Connecting to the database
-  need JDBC Driver of the database that we are connecting to, in this case Oracle Driver, so will need to download that from Oracle website, and import it to the IDE and every project that will use JDBC.

- To connect to the database:
1) Make a connection to the database using DriverManager class.
2) Will need a URL, username and password to connect to the database, so will make a class that will contain fields "URL", "username" and "password". Class name will be "Declaration".
3) import DriverManager and connect like this:
```java
Declaration declaration = new Declaration();
// at the end, will also need to close the connection: connection.close();
Connection connection = DriverManager.getConnection(declaration.url, declaration.username, declaration.password);
```

5) Now can create a "statement"/Query using Statement class:
```java
Statement statement = connection.createStatement();
String sql = "SELECT empno, ename, sal FROM emp";
// Once statement is executed, it returns a ResultSet, so will store in it:
// for DML, will use statement.executeUpdate(sql); NOTE: this will also return number of rows affected
ResultSet resultSet = statement.executeQuery(sql);
```

6) Now resultSet will store the result like an input stream, so we will access each tuple in table with "next" or "get" in this case:
```java
while (resultSet.next()) {
	int no = resultSet.getInt(1);
	String name = resultSet.GetString(2);
	Double Salary = resultSet.getDouble(3);
	System.out.println(no + " " + name + " " + salary);
}
```