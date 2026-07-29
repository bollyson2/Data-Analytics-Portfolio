Module 1 – SQL Fundamentals
Day 7 – SQL Aliases & Multi-Table Queries

🎯 Learning Objectives

By the end of today, you will be able to:

Use table aliases (E, D, S) to simplify queries.
Use column aliases with AS.
Write cleaner SQL.
Join three or more tables.
Read and understand SQL written by experienced analysts.
Why Do We Use Aliases?

Imagine writing this:

SELECT Employees.Name,
       Departments.DepartmentName
FROM Employees
INNER JOIN Departments
ON Employees.DepartmentID = Departments.DepartmentID;

It works, but it's long.

Instead, professionals write:

SELECT E.Name,
       D.DepartmentName
FROM Employees AS E
INNER JOIN Departments AS D
ON E.DepartmentID = D.DepartmentID;

The query is much shorter and easier to read.

Table Aliases

Suppose we have:

Employees
EmployeeID	Name	DepartmentID
1	James	101
2	Mary	102
Departments
DepartmentID	DepartmentName
101	IT
102	HR

Using aliases:

SELECT E.Name,
       D.DepartmentName
FROM Employees AS E
INNER JOIN Departments AS D
ON E.DepartmentID = D.DepartmentID;

Where:

E = Employees
D = Departments
Column Aliases

You can also rename columns in your output.

Instead of:

SELECT SUM(Salary)
FROM Employees;

write:

SELECT SUM(Salary) AS TotalSalary
FROM Employees;

Result:

TotalSalary
£182,000

This makes reports easier to understand.

Using Multiple Aliases

Suppose you also have a Salaries table.

EmployeeID	Bonus
1	2000
2	1500

Now join three tables:

SELECT E.Name,
       D.DepartmentName,
       S.Bonus
FROM Employees AS E
INNER JOIN Departments AS D
ON E.DepartmentID = D.DepartmentID
INNER JOIN Salaries AS S
ON E.EmployeeID = S.EmployeeID;

Result:

Name	Department	Bonus
James	IT	2000
Mary	HR	1500
Why Employers Prefer Aliases

Imagine a query with six tables.

Without aliases:

Employees.DepartmentID
Departments.DepartmentName
EmployeeSalary.EmployeeID
EmployeeBenefits.EmployeeID
Payroll.EmployeeID

It quickly becomes difficult to read.

With aliases:

E.DepartmentID
D.DepartmentName
S.Bonus
B.Allowance
P.PayDate

Much cleaner.

Real-World Example

Imagine you work for a retail company.

Customers
CustomerID	CustomerName
1	John
2	Sarah
Orders
OrderID	CustomerID	ProductID
101	1	5
102	2	7
Products
ProductID	ProductName
5	Laptop
7	Printer

A professional query:

SELECT C.CustomerName,
       P.ProductName
FROM Customers AS C
INNER JOIN Orders AS O
ON C.CustomerID = O.CustomerID
INNER JOIN Products AS P
ON O.ProductID = P.ProductID;

Result:

Customer	Product
John	Laptop
Sarah	Printer
📝 Practice Exercises

Use the Employees, Departments, and Salaries tables.

Question 1
Rewrite this query using aliases:
SELECT Employees.Name,
       Departments.DepartmentName
FROM Employees
INNER JOIN Departments
ON Employees.DepartmentID = Departments.DepartmentID;

SELECT E.Name,
       D.DepartmentName
FROM Employees AS E
INNER JOIN Departments AS D
ON E.DepartmentID = D.DepartmentID;

Question 2
Display:
Employee Name
Department Name
Bonus
using aliases.
SELECT E.Name,
       D.DepartmentName,
       S.Bonus
FROM Employees AS E
INNER JOIN Departments AS D
ON E.DepartmentID = D.DepartmentID
INNER JOIN Salaries AS S
ON E.EmployeeID = S.EmployeeID;

Question 3
Calculate the total salary for each department and rename the total as DepartmentTotal.
SELECT D.DepartmentName,
       SUM(E.Salary) AS DepartmentTotal
FROM Employees AS E
INNER JOIN Departments AS D
ON E.DepartmentID = D.DepartmentID
GROUP BY D.DepartmentName;

Question 4
Display:
Employee Name
Salary
Department Name
using aliases.
SELECT E.Name,
       E.Salary,
       D.DepartmentName
FROM Employees AS E
INNER JOIN Departments AS D
ON E.DepartmentID = D.DepartmentID;

Question 5
Show employees whose salary is greater than 45000, using aliases.
SELECT E.Name,
       E.Salary,
       D.DepartmentName
FROM Employees AS E
INNER JOIN Departments AS D
ON E.DepartmentID = D.DepartmentID
WHERE E.Salary > 45000;

⭐ Challenge 1
Display:
Employee Name
Department Name
Salary
Bonus
Sort the results by Salary from highest to lowest.
SELECT E.Name,
       D.DepartmentName,
       E.Salary,
       S.Bonus
FROM Employees AS E
INNER JOIN Departments AS D
ON E.DepartmentID = D.DepartmentID
INNER JOIN Salaries AS S
ON E.EmployeeID = S.EmployeeID
ORDER BY E.Salary DESC;

⭐⭐ Challenge 2
Management wants a report showing:
Department Name
Number of Employees
Total Salary
Average Salary
Display the departments from the highest total salary to the lowest.
SELECT D.DepartmentName,
       COUNT(*) AS TotalEmployees,
       SUM(E.Salary) AS TotalSalary,
       AVG(E.Salary) AS AverageSalary
FROM Employees AS E
INNER JOIN Departments AS D
ON E.DepartmentID = D.DepartmentID
GROUP BY D.DepartmentName
ORDER BY TotalSalary DESC;
