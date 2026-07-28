Module 1 – SQL Fundamentals
Day 6 – SQL JOINs (The Heart of SQL)

Duration: 90 minutes

Difficulty: ⭐⭐⭐⭐☆ (Intermediate)

🎯 Learning Objectives

By the end of today's lesson, you will be able to:

Understand why SQL JOINs are needed.
Use INNER JOIN.
Use LEFT JOIN.
Understand RIGHT JOIN and FULL OUTER JOIN.
Join multiple tables together.
Write SQL queries similar to those used in real Data Analyst jobs.
Why Do We Need JOINs?

In real companies, information is rarely stored in one table.

Imagine you work for the NHS.

Employees Table
EmployeeID	Name	DepartmentID
1	James	101
2	Mary	102
3	Grace	101
4	Peter	103

Notice there is no department name.

Departments Table
DepartmentID	DepartmentName
101	IT
102	HR
103	Finance

How do we know James works in IT?

We join the two tables.

1. INNER JOIN

An INNER JOIN returns only records that match in both tables.

SELECT Employees.Name,
       Departments.DepartmentName
FROM Employees
INNER JOIN Departments
ON Employees.DepartmentID = Departments.DepartmentID;
Result
Name	Department
James	IT
Mary	HR
Grace	IT
Peter	Finance

This is the most commonly used JOIN.

Understanding the ON Clause

The ON clause tells SQL how the tables are related.

ON Employees.DepartmentID = Departments.DepartmentID

This means:

Match rows where the DepartmentID is the same in both tables.

Think of it as connecting two puzzle pieces using a common key.

2. LEFT JOIN

Suppose a new employee has not yet been assigned to a department.

Employees
EmployeeID	Name	DepartmentID
1	James	101
2	Mary	102
3	Grace	101
4	Peter	103
5	David	NULL

Using:

SELECT Employees.Name,
       Departments.DepartmentName
FROM Employees
LEFT JOIN Departments
ON Employees.DepartmentID = Departments.DepartmentID;

Result

Name	Department
James	IT
Mary	HR
Grace	IT
Peter	Finance
David	NULL

A LEFT JOIN keeps all rows from the left table, even when there is no match.

3. RIGHT JOIN

A RIGHT JOIN keeps all rows from the right table.

Example:

Suppose there is a department called Marketing that currently has no employees.

A RIGHT JOIN will still show Marketing.

SELECT Employees.Name,
       Departments.DepartmentName
FROM Employees
RIGHT JOIN Departments
ON Employees.DepartmentID = Departments.DepartmentID;

Note: Some databases, such as SQLite, do not support RIGHT JOIN. In those systems, you can usually rewrite the query using a LEFT JOIN by swapping the table order.

4. FULL OUTER JOIN

A FULL OUTER JOIN returns:

all rows from the first table
all rows from the second table
matching rows combined where possible

Some databases support this directly; others require a combination of queries.

Real-World Example

Imagine you work for Tesco.

Customers
CustomerID	CustomerName
1	John
2	Sarah
3	David
Orders
OrderID	CustomerID	Amount
100	1	£120
101	1	£80
102	2	£45

Using an INNER JOIN:

SELECT Customers.CustomerName,
       Orders.Amount
FROM Customers
INNER JOIN Orders
ON Customers.CustomerID = Orders.CustomerID;

Result

Customer	Amount
John	£120
John	£80
Sarah	£45

David does not appear because he has no orders.

Using a LEFT JOIN:

SELECT Customers.CustomerName,
       Orders.Amount
FROM Customers
LEFT JOIN Orders
ON Customers.CustomerID = Orders.CustomerID;

Result

Customer	Amount
John	£120
John	£80
Sarah	£45
David	NULL
JOIN Terminology
Term	Meaning
Primary Key	Unique identifier in a table (e.g. EmployeeID)
Foreign Key	A column that references another table (e.g. DepartmentID in Employees)
INNER JOIN	Only matching records
LEFT JOIN	All rows from the left table plus matches
RIGHT JOIN	All rows from the right table plus matches
FULL OUTER JOIN	All rows from both tables
📝 Practice Exercises

Using the Employees and Departments tables above, write SQL for the following.

Question 1
Show each employee's Name and DepartmentName using an INNER JOIN.
SELECT Employees.Name,
       Departments.DepartmentName
FROM Employees
INNER JOIN Departments
ON Employees.DepartmentID = Departments.DepartmentID;

Question 2
Show all employees and their departments using a LEFT JOIN.
SELECT Employees.Name,
       Departments.DepartmentName
FROM Employees
LEFT JOIN Departments
ON Employees.DepartmentID = Departments.DepartmentID;

Question 3
Show all departments, including those with no employees, using a RIGHT JOIN.
SELECT Employees.Name,
       Departments.DepartmentName
FROM Employees
RIGHT JOIN Departments
ON Employees.DepartmentID = Departments.DepartmentID;

Question 4
Show the employee Name and DepartmentID from the Employees table, and the DepartmentName from the Departments table.
SELECT Employees.Name,
       Employees.DepartmentID,
       Departments.DepartmentName
FROM Employees
INNER JOIN Departments
ON Employees.DepartmentID = Departments.DepartmentID;

⭐ Challenge 1
Imagine a third table:
Salaries
EmployeeID	Bonus
1	2000
2	1500
3	1800
4	2500
Write a query that displays:
Employee Name
Department Name
Bonus
(Hint: You'll need to join three tables.)
SELECT Employees.Name,
       Departments.DepartmentName,
       Salaries.Bonus
FROM Employees
INNER JOIN Departments
ON Employees.DepartmentID = Departments.DepartmentID
INNER JOIN Salaries
ON Employees.EmployeeID = Salaries.EmployeeID;

This joins:
Employees → Departments (using DepartmentID)
Employees → Salaries (using EmployeeID

⭐⭐ Challenge 2
Using the Employees and Departments tables, show only employees who belong to the IT department.
SELECT Employees.Name,
       Departments.DepartmentName
FROM Employees
LEFT JOIN Departments
ON Employees.DepartmentID = Departments.DepartmentID
WHERE Departments.DepartmentName = 'IT';

💼 Interview Tip

A very common interview question is:

"What's the difference between an INNER JOIN and a LEFT JOIN?"

A good answer is:

"An INNER JOIN returns only rows that have matching values in both tables. A LEFT JOIN returns all rows from the left table, and matching rows from the right table. If there is no match, the right table's columns return NULL."
