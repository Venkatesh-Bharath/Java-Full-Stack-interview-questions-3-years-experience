## Basic SQL Questions

1. **What is SQL?**
   - SQL (Structured Query Language) is a standardized language for managing and manipulating relational databases.

2. **What are the different types of SQL statements?**
   - **DDL (Data Definition Language):** `CREATE`, `ALTER`, `DROP`
   - **DML (Data Manipulation Language):** `SELECT`, `INSERT`, `UPDATE`, `DELETE`
   - **DCL (Data Control Language):** `GRANT`, `REVOKE`
   - **TCL (Transaction Control Language):** `COMMIT`, `ROLLBACK`, `SAVEPOINT`

3. **What is a primary key?**
   - A primary key is a unique identifier for a record in a table, ensuring that no two rows can have the same primary key value.
   - Example:
     ```sql
     CREATE TABLE Employees (
         EmployeeID INT PRIMARY KEY,
         Name VARCHAR(50),
         Department VARCHAR(50)
     );
     ```

4. **What is a foreign key?**
   - A foreign key is a field (or collection of fields) in one table that uniquely identifies a row in another table. The foreign key enforces referential integrity.
   - Example:
     ```sql
     CREATE TABLE Orders (
         OrderID INT PRIMARY KEY,
         OrderDate DATE,
         CustomerID INT,
         FOREIGN KEY (CustomerID) REFERENCES Customers(CustomerID)
     );
     ```

5. **What is a unique key?**
   - A unique key ensures that all values in a column are unique.
   - Example:
     ```sql
     CREATE TABLE Employees (
         EmployeeID INT PRIMARY KEY,
         Email VARCHAR(100) UNIQUE
     );
     ```

6. **What is a candidate key?**
   - A candidate key is a column, or a set of columns, that can uniquely identify a record in a table. A table can have multiple candidate keys, one of which is chosen as the primary key.

7. **What is a composite key?**
   - A composite key is a primary key composed of multiple columns.
   - Example:
     ```sql
     CREATE TABLE Enrollment (
         StudentID INT,
         CourseID INT,
         EnrollmentDate DATE,
         PRIMARY KEY (StudentID, CourseID)
     );
     ```

8. **What is a join? Explain different types of joins.**
   - A join is a SQL operation that combines rows from two or more tables based on a related column.
   - Types of joins:
     - **Inner Join:** Returns only the rows with matching values in both tables.
     - **Left Join (Left Outer Join):** Returns all rows from the left table and matched rows from the right table.
     - **Right Join (Right Outer Join):** Returns all rows from the right table and matched rows from the left table.
     - **Full Join (Full Outer Join):** Returns all rows when there is a match in either left or right table.
   - Example:
     ```sql
     SELECT Employees.Name, Departments.DepartmentName
     FROM Employees
     INNER JOIN Departments ON Employees.DepartmentID = Departments.DepartmentID;
     ```

9. **What is a self-join?**
   - A self-join is a regular join, but the table is joined with itself.
   - Example:
     ```sql
     SELECT A.EmployeeID, A.Name, B.ManagerID
     FROM Employees A, Employees B
     WHERE A.ManagerID = B.EmployeeID;
     ```

10. **What is a cross join?**
    - A cross join returns the Cartesian product of the two tables, combining all rows of the first table with all rows of the second table.
    - Example:
      ```sql
      SELECT A.Name, B.DepartmentName
      FROM Employees A
      CROSS JOIN Departments B;
      ```

11. **What is an inner join?**
    - An inner join returns only the rows that have matching values in both tables.
    - Example:
      ```sql
      SELECT Employees.Name, Departments.DepartmentName
      FROM Employees
      INNER JOIN Departments ON Employees.DepartmentID = Departments.DepartmentID;
      ```

12. **What is an outer join?**
    - An outer join returns the matched rows and some or all the unmatched rows from one or both tables.
    - Example:
      ```sql
      SELECT Employees.Name, Departments.DepartmentName
      FROM Employees
      LEFT JOIN Departments ON Employees.DepartmentID = Departments.DepartmentID;
      ```

13. **What is a left join?**
    - A left join returns all rows from the left table and the matched rows from the right table.
    - Example:
      ```sql
      SELECT Employees.Name, Departments.DepartmentName
      FROM Employees
      LEFT JOIN Departments ON Employees.DepartmentID = Departments.DepartmentID;
      ```

14. **What is a right join?**
    - A right join returns all rows from the right table and the matched rows from the left table.
    - Example:
      ```sql
      SELECT Employees.Name, Departments.DepartmentName
      FROM Employees
      RIGHT JOIN Departments ON Employees.DepartmentID = Departments.DepartmentID;
      ```

15. **What is a full join?**
    - A full join returns all rows when there is a match in either left or right table.
    - Example:
      ```sql
      SELECT Employees.Name, Departments.DepartmentName
      FROM Employees
      FULL JOIN Departments ON Employees.DepartmentID = Departments.DepartmentID;
      ```

16. **What is a Cartesian join?**
    - A Cartesian join returns the Cartesian product of the sets of records from the two joined tables.
    - Example:
      ```sql
      SELECT Employees.Name, Departments.DepartmentName
      FROM Employees, Departments;
      ```

17. **What is an index? Explain its types.**
    - An index is a database object that improves the speed of data retrieval operations on a table.
    - Types of indexes:
      - **Clustered Index:** Sorts and stores the data rows in the table based on the key values. Each table can have only one clustered index.
      - **Non-Clustered Index:** Contains a pointer to the data row that contains the key value. Each table can have multiple non-clustered indexes.
    - Example:
      ```sql
      CREATE INDEX idx_employee_name ON Employees(Name);
      ```

18. **What is a view?**
    - A view is a virtual table based on the result set of a SQL query.
    - Example:
      ```sql
      CREATE VIEW EmployeeView AS
      SELECT Name, DepartmentID
      FROM Employees;
      ```

19. **What is a subquery?**
    - A subquery is a query nested inside another query.
    - Example:
      ```sql
      SELECT Name
      FROM Employees
      WHERE DepartmentID = (SELECT DepartmentID FROM Departments WHERE DepartmentName = 'Sales');
      ```

20. **What is a correlated subquery?**
    - A correlated subquery is a subquery that references columns from the outer query.
    - Example:
      ```sql
      SELECT E1.Name
      FROM Employees E1
      WHERE E1.Salary > (SELECT AVG(Salary) FROM Employees E2 WHERE E1.DepartmentID = E2.DepartmentID);
      ```

21. **What is a stored procedure?**
    - A stored procedure is a prepared SQL code that you can save and reuse.
    - Example:
      ```sql
      CREATE PROCEDURE GetEmployeeDetails
      AS
      BEGIN
          SELECT * FROM Employees;
      END;
      ```

22. **What is a trigger?**
    - A trigger is a set of SQL statements that automatically executes in response to certain events on a particular table or view.
    - Example:
      ```sql
      CREATE TRIGGER trgAfterInsert ON Employees
      FOR INSERT
      AS
      BEGIN
          PRINT 'Record inserted';
      END;
      ```

23. **What is normalization?**
    - Normalization is the process of organizing data to reduce redundancy and improve data integrity.

24. **Explain the different normal forms.**
    - **1NF (First Normal Form):** Ensures that the table has no repeating groups of columns.
    - **2NF (Second Normal Form):** Achieves 1NF and all non-key attributes are fully functional dependent on the primary key.
    - **3NF (Third Normal Form):** Achieves 2NF and all the attributes are functionally dependent only on the primary key.
    - **BCNF (Boyce-Codd Normal Form):** A stronger version of 3NF.

25. **What is denormalization?**
    - Denormalization is the process of combining normalized tables into larger tables to improve database read performance.

26. **What is a schema?**
    - A schema is a logical collection of database objects, such as tables, views, and stored procedures.

27. **What is a database?**
    - A database is an organized collection of data, generally stored and accessed electronically from a computer system.

28. **What is a table?**
    - A table is a collection of related data entries and it consists of columns and rows.

29. **What is a field?**
    - A field is a single piece of data stored in a table. It is also known as a column.

30. **What is a record?**
    - A record is a single row of data in a table. It is also known as a row.

31. **What is a constraint?**
    - A constraint is a rule enforced on data columns to ensure data integrity.

32. **Explain the different types of constraints.**
    - **Primary Key Constraint:** Uniquely identifies each row in a table.
    - **Foreign Key Constraint:** Ensures refer ential integrity between tables.
    - **Unique Constraint:** Ensures all values in a column are unique.
    - **Check Constraint:** Ensures that all values in a column satisfy a specific condition.
    - **Default Constraint:** Assigns a default value to a column when no value is specified.

33. **What is a default constraint?**
    - A default constraint assigns a default value to a column when no value is specified during record insertion.
    - Example:
      ```sql
      CREATE TABLE Employees (
          EmployeeID INT,
          Name VARCHAR(50),
          Salary DECIMAL(10, 2) DEFAULT 50000
      );
      ```

34. **What is a check constraint?**
    - A check constraint ensures that all values in a column satisfy a specific condition.
    - Example:
      ```sql
      CREATE TABLE Employees (
          EmployeeID INT,
          Name VARCHAR(50),
          Age INT,
          CHECK (Age >= 18)
      );
      ```

35. **What is a unique constraint?**
    - A unique constraint ensures that all values in a column are unique.
    - Example:
      ```sql
      CREATE TABLE Employees (
          EmployeeID INT,
          Email VARCHAR(100) UNIQUE
      );
      ```

36. **What is a primary key constraint?**
    - A primary key constraint uniquely identifies each row in a table.
    - Example:
      ```sql
      CREATE TABLE Employees (
          EmployeeID INT PRIMARY KEY,
          Name VARCHAR(50)
      );
      ```

37. **What is a foreign key constraint?**
    - A foreign key constraint ensures referential integrity between tables.
    - Example:
      ```sql
      CREATE TABLE Orders (
          OrderID INT PRIMARY KEY,
          OrderDate DATE,
          CustomerID INT,
          FOREIGN KEY (CustomerID) REFERENCES Customers(CustomerID)
      );
      ```

38. **What is an auto-increment?**
    - An auto-increment is a feature that automatically generates a unique number when a new record is inserted into a table.
    - Example:
      ```sql
      CREATE TABLE Employees (
          EmployeeID INT AUTO_INCREMENT PRIMARY KEY,
          Name VARCHAR(50)
      );
      ```

39. **What is the difference between SQL and MySQL?**
    - **SQL:** A standard language for accessing and manipulating databases.
    - **MySQL:** An open-source relational database management system that uses SQL.

40. **What is a transaction? Explain its properties.**
    - A transaction is a sequence of one or more SQL operations treated as a single unit. It has the following properties (ACID):
      - **Atomicity:** Ensures all operations within a transaction are completed successfully. If not, the transaction is aborted.
      - **Consistency:** Ensures the database is in a consistent state before and after the transaction.
      - **Isolation:** Ensures that transactions are securely and independently processed.
      - **Durability:** Ensures that the results of a completed transaction are permanently stored in the database.

## Intermediate SQL Questions

41. **What is the ACID property in a database?**
    - **Atomicity, Consistency, Isolation, Durability** are the properties that ensure reliable processing of database transactions.

42. **What is a deadlock in SQL?**
    - A deadlock occurs when two or more transactions hold locks on resources and each is waiting for the other to release the lock, preventing them from proceeding.

43. **What is a clustered index?**
    - A clustered index sorts and stores the data rows in the table based on the key values. Each table can have only one clustered index.
    - Example:
      ```sql
      CREATE CLUSTERED INDEX idx_employee_id ON Employees(EmployeeID);
      ```

44. **What is a non-clustered index?**
    - A non-clustered index contains a pointer to the data row that contains the key value. Each table can have multiple non-clustered indexes.
    - Example:
      ```sql
      CREATE INDEX idx_employee_name ON Employees(Name);
      ```

45. **What is the difference between DELETE and TRUNCATE commands?**
    - **DELETE:** Removes rows one at a time and logs each deletion. It can have a WHERE clause.
    - **TRUNCATE:** Removes all rows from a table without logging individual row deletions. It cannot have a WHERE clause.

46. **What is the difference between DROP and TRUNCATE commands?**
    - **DROP:** Deletes the table structure and its data permanently.
    - **TRUNCATE:** Deletes all rows from a table but preserves the table structure.

47. **What is the difference between WHERE and HAVING clauses?**
    - **WHERE:** Filters rows before the grouping is applied.
    - **HAVING:** Filters groups after the grouping is applied.

48. **What is a wildcard in SQL?**
    - A wildcard is a character used to substitute one or more characters in a string.
    - Example:
      ```sql
      SELECT * FROM Employees WHERE Name LIKE 'A%';
      ```

49. **What is the LIKE operator?**
    - The LIKE operator is used in a WHERE clause to search for a specified pattern in a column.
    - Example:
      ```sql
      SELECT * FROM Employees WHERE Name LIKE 'A%';
      ```

50. **What is the IN operator?**
    - The IN operator allows you to specify multiple values in a WHERE clause.
    - Example:
      ```sql
      SELECT * FROM Employees WHERE DepartmentID IN (1, 2, 3);
      ```

51. **What is the BETWEEN operator?**
    - The BETWEEN operator selects values within a given range.
    - Example:
      ```sql
      SELECT * FROM Employees WHERE Age BETWEEN 30 AND 40;
      ```

52. **What is a CASE statement?**
    - The CASE statement is a way to implement conditional logic in SQL.
    - Example:
      ```sql
      SELECT Name,
      CASE
          WHEN Age < 18 THEN 'Minor'
          WHEN Age BETWEEN 18 AND 65 THEN 'Adult'
          ELSE 'Senior'
      END AS AgeGroup
      FROM Employees;
      ```

53. **What is a COALESCE function?**
    - The COALESCE function returns the first non-null value in a list of arguments.
    - Example:
      ```sql
      SELECT COALESCE(NULL, NULL, 'SQL', 'Server');
      ```

54. **What is a NULL value?**
    - A NULL value represents a missing or unknown value in a column.

55. **What is a UNION operator?**
    - The UNION operator combines the result sets of two or more SELECT statements and removes duplicate rows.
    - Example:
      ```sql
      SELECT Name FROM Employees
      UNION
      SELECT Name FROM Managers;
      ```

56. **What is the difference between UNION and UNION ALL?**
    - **UNION:** Removes duplicate rows.
    - **UNION ALL:** Includes duplicate rows.

57. **What is the difference between CHAR and VARCHAR data types?**
    - **CHAR:** Fixed-length character data.
    - **VARCHAR:** Variable-length character data.

58. **What is the difference between VARCHAR and NVARCHAR data types?**
    - **VARCHAR:** Stores non-Unicode characters.
    - **NVARCHAR:** Stores Unicode characters.

59. **What is a CTE (Common Table Expression)?**
    - A CTE is a temporary result set that can be referenced within a SELECT, INSERT, UPDATE, or DELETE statement.
    - Example:
      ```sql
      WITH EmployeeCTE AS (
          SELECT EmployeeID, Name, DepartmentID
          FROM Employees
      )
      SELECT * FROM EmployeeCTE;
      ```

60. **What is the difference between a temporary table and a table variable?**
    - **Temporary Table:** Created with `CREATE TABLE #tempTable` and stored in tempdb.
    - **Table Variable:** Declared with `DECLARE @tableVariable TABLE` and stored in memory.

61. **What is a cursor?**
    - A cursor is a database object used to retrieve, manipulate, and navigate through a result set row by row.
    - Example:
      ```sql
      DECLARE @EmployeeID INT
      DECLARE EmployeeCursor CURSOR FOR
      SELECT EmployeeID FROM Employees

      OPEN EmployeeCursor
      FETCH NEXT FROM EmployeeCursor INTO @EmployeeID
      WHILE @@FETCH_STATUS = 0
      BEGIN
          PRINT @EmployeeID
          FETCH NEXT FROM EmployeeCursor INTO @EmployeeID
      END
      CLOSE EmployeeCursor
      DEALLOCATE EmployeeCursor
      ```

62. **What is a trigger? Explain different types of triggers.**
    - A trigger is a set of SQL statements that automatically executes in response to certain events on a particular table or view.
    - Types:
      - **DML Triggers:** `AFTER` and `INSTEAD OF`
      - **DDL Triggers:** Fire in response to DDL events like `CREATE`, `ALTER`, `DROP`
      - **Logon Triggers:** Fire in response to LOGON events

63. **What is a stored function?**
    - A stored function is a set of SQL statements that perform a task and return a value.
    - Example:
      ```sql
      CREATE FUNCTION GetEmployeeName (@EmployeeID INT)
      RETURNS VARCHAR(50)
      AS
      BEGIN
          DECLARE @Name VARCHAR(50)
          SELECT @Name = Name FROM Employees WHERE EmployeeID = @EmployeeID
          RETURN @Name
      END;
      ```

64. **How do you optimize a query?**
    - Techniques include:
      - Using indexes
      - Avoiding unnecessary columns in SELECT
      - Using joins instead of subqueries
      - Avoiding functions in WHERE

 clauses

65. **What is a query execution plan?**
    - A query execution plan is a detailed breakdown of how SQL Server will execute a query. It helps in understanding and optimizing the performance of queries.
    - Example:
      ```sql
      EXPLAIN SELECT * FROM Employees;
      ```

66. **What are the different isolation levels in SQL Server?**
    - **Read Uncommitted:** Allows dirty reads
    - **Read Committed:** Default level, prevents dirty reads
    - **Repeatable Read:** Prevents dirty and non-repeatable reads
    - **Serializable:** Highest level, prevents dirty, non-repeatable reads, and phantom reads
    - **Snapshot:** Provides a versioned view of the data

67. **What is SQL injection?**
    - SQL injection is a code injection technique that exploits a vulnerability in an application’s software by inserting malicious SQL code into a query.

68. **How can you prevent SQL injection?**
    - Using parameterized queries
    - Using stored procedures
    - Validating and sanitizing user inputs
    - Using ORM frameworks

69. **What are the different types of backup in SQL Server?**
    - **Full Backup:** Backs up the entire database
    - **Differential Backup:** Backs up data that has changed since the last full backup
    - **Transaction Log Backup:** Backs up the transaction log
    - **File/Filegroup Backup:** Backs up individual files or filegroups

70. **What is a user-defined function?**
    - A user-defined function is a function provided by the user to perform a specific task and return a value.
    - Example:
      ```sql
      CREATE FUNCTION GetTotalSalary (@DepartmentID INT)
      RETURNS DECIMAL(10, 2)
      AS
      BEGIN
          DECLARE @Total DECIMAL(10, 2)
          SELECT @Total = SUM(Salary) FROM Employees WHERE DepartmentID = @DepartmentID
          RETURN @Total
      END;
      ```

71. **What is the difference between a scalar function and a table-valued function?**
    - **Scalar Function:** Returns a single value.
    - **Table-Valued Function:** Returns a table.

72. **How do you handle errors in SQL?**
    - Using `TRY...CATCH` blocks
    - Example:
      ```sql
      BEGIN TRY
          -- SQL statements
      END TRY
      BEGIN CATCH
          -- Error handling
      END CATCH;
      ```

73. **What is the difference between RAISERROR and THROW in SQL Server?**
    - **RAISERROR:** Generates an error message and sets the `@@ERROR` variable.
    - **THROW:** Re-raises the error message generated by `RAISERROR` or `TRY...CATCH`.

74. **What is the purpose of the SET NOCOUNT ON statement?**
    - The `SET NOCOUNT ON` statement prevents SQL Server from sending messages that indicate the number of rows affected by a query, which can improve performance.

## Advanced SQL Questions

75. **What is replication in SQL Server?**
    - Replication is the process of copying and distributing data and database objects from one database to another and synchronizing between databases to maintain consistency.

76. **What is log shipping?**
    - Log shipping is the process of automating the backup of database and transaction log files on a primary server and then restoring them onto a standby server.

77. **What is database mirroring?**
    - Database mirroring is a solution for increasing database availability by duplicating the database to a standby server.

78. **What is Always On Availability Groups?**
    - Always On Availability Groups is a high-availability and disaster-recovery solution that provides an enterprise-level alternative to database mirroring.

79. **What is a partitioned table?**
    - A partitioned table is a table that is divided into smaller, more manageable pieces, yet accessed as a single table.

80. **What are the advantages and disadvantages of partitioned tables?**
    - **Advantages:** Improved performance, easier maintenance, and better manageability.
    - **Disadvantages:** Complexity in design and potential performance issues if not properly implemented.

81. **How do you implement partitioning in SQL Server?**
    - By creating partition functions and partition schemes, and then associating tables or indexes with these schemes.
    - Example:
      ```sql
      CREATE PARTITION FUNCTION myRangePF1 (int)
      AS RANGE LEFT FOR VALUES (1, 100, 1000);
      CREATE PARTITION SCHEME myRangePS1
      AS PARTITION myRangePF1
      TO (fg1, fg2, fg3, fg4);
      CREATE TABLE PartitionedTable (
          col1 int,
          col2 char(20)
      ) ON myRangePS1 (col1);
      ```

82. **What is a materialized view?**
    - A materialized view is a database object that contains the results of a query and is periodically refreshed to maintain consistency with its base tables.

83. **What is the difference between a view and a materialized view?**
    - **View:** A virtual table that is based on the result of a SELECT query.
    - **Materialized View:** Stores the result of a query physically and periodically refreshes to reflect changes in the base tables.

84. **What is the difference between OLTP and OLAP?**
    - **OLTP (Online Transaction Processing):** Handles day-to-day transaction data.
    - **OLAP (Online Analytical Processing):** Handles complex queries and analysis on historical data.

85. **What are the differences between SQL Server and Oracle?**
    - **SQL Server:** Developed by Microsoft, uses T-SQL.
    - **Oracle:** Developed by Oracle Corporation, uses PL/SQL.
    - **SQL Server:** Integrated with Windows.
    - **Oracle:** Cross-platform support.

86. **How do you handle concurrency in SQL Server?**
    - By using isolation levels, locks, and transactions to manage concurrent access to data.

87. **What is the difference between pessimistic and optimistic concurrency control?**
    - **Pessimistic Concurrency Control:** Locks resources to prevent conflicts.
    - **Optimistic Concurrency Control:** Assumes that conflicts are rare and checks for conflicts before committing a transaction.

88. **What is a heap table?**
    - A heap table is a table without a clustered index.

89. **What is a B-tree index?**
    - A B-tree index is a balanced tree index used to maintain sorted data and allow searches, insertions, deletions, and sequential access.

90. **What is a bitmap index?**
    - A bitmap index uses bitmaps and is efficient for queries that filter on low-cardinality columns.

91. **How do you use window functions in SQL?**
    - Window functions perform calculations across a set of table rows related to the current row.
    - Example:
      ```sql
      SELECT Name, Salary,
      RANK() OVER (ORDER BY Salary DESC) AS Rank
      FROM Employees;
      ```

92. **Explain the ROW_NUMBER, RANK, DENSE_RANK, and NTILE functions.**
    - **ROW_NUMBER:** Assigns a unique number to each row.
    - **RANK:** Assigns a rank to each row, with gaps for duplicate values.
    - **DENSE_RANK:** Assigns a rank to each row without gaps.
    - **NTILE:** Distributes rows into a specified number of groups.

93. **What is a recursive query?**
    - A recursive query is a query that refers to itself.
    - Example:
      ```sql
      WITH EmployeeHierarchy AS (
          SELECT EmployeeID, ManagerID
          FROM Employees
          WHERE ManagerID IS NULL
          UNION ALL
          SELECT e.EmployeeID, e.ManagerID
          FROM Employees e
          INNER JOIN EmployeeHierarchy eh ON e.ManagerID = eh.EmployeeID
      )
      SELECT * FROM EmployeeHierarchy;
      ```

94. **What is the difference between CROSS APPLY and OUTER APPLY?**
    - **CROSS APPLY:** Similar to INNER JOIN, returns only matching rows.
    - **OUTER APPLY:** Similar to LEFT JOIN, returns all rows from the left table and matching rows from the right table.

95. **How do you implement paging in SQL Server?**
    - Using the `OFFSET` and `FETCH` clauses.
    - Example:
      ```sql
      SELECT * FROM Employees
      ORDER BY EmployeeID
      OFFSET 10 ROWS FETCH NEXT 10 ROWS ONLY;
      ```

96. **What is dynamic SQL?**
    - Dynamic SQL is SQL code that is generated and executed at runtime.
    - Example:
      ```sql
      DECLARE @sql NVARCHAR(MAX)
      SET @sql = 'SELECT * FROM Employees WHERE EmployeeID = @EmployeeID'
      EXEC sp_executesql @sql, N'@EmployeeID INT', @EmployeeID = 1;
      ```

97. **What are the risks of using dynamic SQL?**
    - SQL injection vulnerabilities
    - Complexity in debugging and maintenance
    - Performance overhead

98. **What is the FOR XML PATH in SQL Server?**
    - The `FOR XML PATH` clause converts the result of a query into XML format.
    - Example:
      ```sql
      SELECT EmployeeID, Name
      FROM Employees
      FOR XML PATH('Employee');
      ```

99. **What is JSON support in SQL Server?**
    - SQL Server supports JSON functions to parse, read, and write JSON data.
    - Example:
      ```sql
      SELECT Name, Age
      FROM Employees
      FOR JSON AUTO;
      ```

100. **How do you migrate a database from one server to another?**
    - Using backup and restore
    - Using detach and attach
    - Using SQL Server Integration Services (SSIS)
    - Using database replication

---
