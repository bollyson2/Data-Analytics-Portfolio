Module 1 – SQL Fundamentals
Day 13 – SQL Indexes

Duration: 60–90 minutes

Difficulty: ⭐⭐⭐⭐☆

🎯 Learning Objectives

By the end of today's lesson, you will be able to:

Understand what an SQL Index is.
Explain why indexes improve query performance.
Create an index.
Remove an index.
Understand clustered and non-clustered indexes.
Know when indexes should and should not be used.
🤔 What is an SQL Index?

An Index is a database object that helps SQL find data faster.

Think of a textbook.

Without an index, if you wanted to find "Data Analytics", you would have to read every page.

With an index, you simply look at the index page and go straight to the correct page number.

SQL indexes work in the same way.

Without an Index

Suppose you have 5 million employees.

You run:

SELECT *
FROM Employees
WHERE EmployeeID = 100045;

Without an index, SQL may have to scan every row until it finds EmployeeID 100045.

This is called a Table Scan.

With an Index

If EmployeeID has an index:

SELECT *
FROM Employees
WHERE EmployeeID = 100045;

SQL goes directly to the matching row instead of checking every record.

This is much faster.

Creating an Index
CREATE INDEX idx_EmployeeName
ON Employees(Name);

Explanation:

CREATE INDEX creates the index.
idx_EmployeeName is the name of the index.
Employees is the table.
Name is the indexed column.
Creating an Index on Multiple Columns
CREATE INDEX idx_DepartmentSalary
ON Employees(Department, Salary);

This helps queries such as:

SELECT *
FROM Employees
WHERE Department = 'IT'
AND Salary > 50000;
Removing an Index

In SQL Server:

DROP INDEX idx_EmployeeName
ON Employees;

In MySQL:

DROP INDEX idx_EmployeeName
ON Employees;
Clustered vs Non-Clustered Indexes
Clustered Index

A clustered index determines the physical order of the data in the table.

Imagine books arranged on a shelf in alphabetical order.

A table can normally have only one clustered index.

Non-Clustered Index

A non-clustered index is like the index at the back of a book.

It points to where the data is stored but does not change the order of the table.

A table can have many non-clustered indexes.

Real-World Example

Imagine a bank with 20 million customers.

A customer searches using their account number.

Without an index:

SQL scans millions of rows.

With an index:

SQL locates the customer almost instantly.

This is why banks, hospitals, retailers, and government organisations use indexes extensively.

When Should You Create an Index?

Indexes are useful for columns that are:

Frequently searched.
Used in WHERE clauses.
Used in JOIN conditions.
Used in ORDER BY.
Used in GROUP BY.

Example:

SELECT *
FROM Employees
WHERE Department = 'Finance';

Creating an index on Department could improve performance.

When Should You Avoid Indexes?

Indexes are not always beneficial.

Avoid excessive indexing on tables that:

Receive frequent INSERT operations.
Receive frequent UPDATE operations.
Receive frequent DELETE operations.

Each change to the data also requires the index to be updated, which adds overhead.

📝 Practice Exercises

Use the Employees table.
Question 1
Create an index called idx_Name on the Name column.
CREATE INDEX idx_Name
ON Employees(Name);

Question 2
Create an index called idx_Department on the Department column.
CREATE INDEX idx_Department
ON Employees(Department);

Question 3
Create a multi-column index called idx_DepartmentSalary on:
Department
Salary
CREATE INDEX idx_DepartmentSalary
ON Employees(Department, Salary);

Question 4
Drop the index idx_Name.
DROP INDEX idx_Name
ON Employees;

Question 5
Write a query that would benefit from an index on the Department column.
SELECT *
FROM Employees
WHERE Department = 'IT';

⭐ Challenge 1
Create an index called idx_HireDate on the HireDate column.
Then write a query to find all employees hired after 1 January 2023.
CREATE INDEX idx_HireDate
ON Employees(HireDate);
Then
SELECT *
FROM Employees
WHERE HireDate > '2023-01-01';

⭐⭐ Challenge 2
Suppose a company has a table with 10 million employees.
Write a short explanation (3–5 sentences) describing:
Why an index improves performance.
Which columns you would index.
Which columns you would avoid indexing and why.
An index improves performance by allowing SQL Server to locate records quickly without scanning the entire table.
I would create indexes on columns such as EmployeeID, Department, and HireDate because they are frequently used in searches and joins
I would avoid indexing columns with many duplicate values, such as salary alone in some organisations, 
or columns that are updated very frequently, as maintaining indexes can reduce write performance.

💼 Interview Question
Question:
What is the purpose of an SQL Index?
A strong answer:
"An SQL index improves the speed of data retrieval by allowing the database to locate rows more efficiently, reducing the need to scan the entire table."

📚 Quick Revision
Answer these without looking at your notes:
What is an SQL Index?
Why does an index improve performance?
Which command creates an index?
Which command removes an index?
What is the difference between a clustered and a non-clustered index?
