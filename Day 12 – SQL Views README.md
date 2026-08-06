Module 1 – SQL Fundamentals
Day 12 – SQL Views

Duration: 60–90 minutes

Difficulty: ⭐⭐⭐⭐☆

🎯 Learning Objectives

By the end of today's lesson, you will be able to:

Understand what a SQL View is.
Create a View.
Query data from a View.
Update a View (where allowed).
Understand why Views are used in business.
Explain Views in a SQL interview.
🤔 What is a SQL View?

A View is a virtual table.

It does not store data itself. Instead, it stores a SQL query. Every time you query the view, SQL runs that stored query and returns the latest data from the underlying tables.

Think of it like a saved report.

For example:

Instead of writing this query every day:

SELECT Name,
       Department,
       Salary
FROM Employees
WHERE Salary > 50000;

You can save it as a view and simply query the view.

Sample Employees Table
EmployeeID	Name	Department	Salary
1	James	IT	45000
2	Mary	HR	39000
3	Peter	Finance	52000
4	Grace	IT	47000
5	David	HR	61000
1. Create a View
CREATE VIEW HighSalaryEmployees AS
SELECT
    Name,
    Department,
    Salary
FROM Employees
WHERE Salary >=50000;

The view is now stored in the database.

2. Query the View

Instead of writing the full query again:

SELECT *
FROM HighSalaryEmployees;

Result

Name	Department	Salary
Peter	Finance	52000
David	HR	61000
3. View Specific Columns
SELECT Name,
       Salary
FROM HighSalaryEmployees;
4. Create a View Using CASE
CREATE VIEW EmployeeGrades AS

SELECT
    Name,
    Salary,

    CASE
        WHEN Salary >=60000 THEN 'A'
        WHEN Salary >=50000 THEN 'B'
        WHEN Salary >=40000 THEN 'C'
        ELSE 'D'
    END AS Grade

FROM Employees;

Now simply run:

SELECT *
FROM EmployeeGrades;
5. Replace or Alter a View

Some databases (e.g., MySQL) support:

CREATE OR REPLACE VIEW HighSalaryEmployees AS

SELECT
    Name,
    Salary
FROM Employees
WHERE Salary >=45000;

In SQL Server, you would use:

ALTER VIEW HighSalaryEmployees AS
SELECT Name,
       Salary
FROM Employees
WHERE Salary >=45000;
6. Delete a View
DROP VIEW HighSalaryEmployees;

This removes the view, not the underlying table.

💼 Why Businesses Use Views

Imagine you work in HR.

The Employees table contains:

Salary
National Insurance Number
Home Address
Bank Details
Emergency Contact

Managers should only see:

Name
Department
Job Title

A view allows you to expose only those columns, improving security and privacy.

Real-World Example

A finance team runs this query every morning:

SELECT
    CustomerName,
    Balance
FROM Customers
WHERE Balance >100000;

Instead of rewriting it daily, they create:

CREATE VIEW PremiumCustomers AS
SELECT
    CustomerName,
    Balance
FROM Customers
WHERE Balance >100000;

Then they simply use:

SELECT *
FROM PremiumCustomers;

📝 Practice Exercises
Use the Employees table.
Question 1
Create a view called ITEmployees that displays:
Name
Department
Salary
Only for employees in the IT department.
CREATE VIEW ITEmployees AS
SELECT
    Name,
    Department,
    Salary
FROM Employees
WHERE Department = 'IT';

Question 2
Display all records from the ITEmployees view.


Question 3
Create a view called HighEarners showing employees earning £50,000 or more.
Display:
Name
Salary
CREATE VIEW HighEarners AS
SELECT
    Name,
    Salary
FROM Employees
WHERE Salary >=50000;

Question 4
Display only:
Name
Salary
from the HighEarners view.
SELECT
    Name,
    Salary
FROM HighEarners;

Question 5
Delete the HighEarners view.
DROP VIEW HighEarners;

⭐ Challenge 1
Create a view called EmployeeSummary that displays:
Name
Department
Salary
Create another column called SalaryBand using:
60,000+ → Excellent
50,000–59,999 → Good
40,000–49,999 → Average
Below 40,000 → Low
SELECT
    Name,
    Department,
    Salary,
    CASE
       WHEN Salary >= 60000 THEN 'Excellent' WHEN Salary >= 50000 THEN 'Good' WHEN Salary >= 40000 THEN 'Average' ELSE 'Low' END AS SalaryBand FROM Employees;

⭐⭐ Challenge 2
SELECT *
FROM BonusEligible;
Display:
Name
Department
Salary
BonusStatus
Rules:
Salary >=45000 → Eligible
Otherwise → Not Eligible
CREATE VIEW BonusEligible AS

SELECT
    Name,
    Department,
    Salary,

CASE
WHEN Salary >=45000 THEN 'Eligible for Bonus'
ELSE 'Not Eligible'
END AS BonusStatus

FROM Employees;


Then display all records from the view.

💼 Interview Question

Question:

What is the difference between a table and a view?

A strong answer:

A table stores data physically in the database.
A view does not store data. It stores a SQL query that retrieves data from one or more tables.
📚 Quick Revision

Answer these questions without looking at your notes:

What is a SQL View?
Does a view store data?
Which command creates a view?
Which command removes a view?
Why do businesses use views?
