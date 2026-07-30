Module 1 – SQL Fundamentals
Day 8 – SQL Subqueries

Duration: 60–90 minutes

Difficulty: ⭐⭐⭐⭐☆

🎯 Learning Objectives

By the end of today's lesson, you will be able to:

Understand what a subquery is.
Write subqueries inside the WHERE clause.
Use IN with subqueries.
Use aggregate functions inside subqueries.
Solve real-world Data Analyst questions using subqueries.
🤔 What is a Subquery?

A subquery is simply a query inside another query.

Think of it like asking SQL one question to help answer another question.

Example:

"Show employees who earn more than the company's average salary."

SQL cannot know the average salary until it calculates it first.

Sample Employees Table
EmployeeID	Name	Department	Salary
1	James	IT	45000
2	Mary	HR	39000
3	Peter	Finance	50000
4	Grace	IT	47000
5	David	HR	41000
Example 1 – Average Salary

First, calculate the average salary.

SELECT AVG(Salary)
FROM Employees;

Result:

44400

Now use that result inside another query.

SELECT Name,
       Salary
FROM Employees
WHERE Salary >
(
    SELECT AVG(Salary)
    FROM Employees
);
Result
Name	Salary
James	45000
Grace	47000
Peter	50000
How It Works

The inner query runs first.

SELECT AVG(Salary)
FROM Employees;

Result:

44400

Then SQL replaces the subquery with that value.

WHERE Salary > 44400
Example 2 – Highest Salary

Show the employee(s) earning the highest salary.

SELECT Name,
       Salary
FROM Employees
WHERE Salary =
(
    SELECT MAX(Salary)
    FROM Employees
);

Result

Name	Salary
Peter	50000
Example 3 – IN with Subqueries

Suppose we have another table.

Managers
Department
IT
Finance

Find employees who work in departments that have managers.

SELECT Name,
       Department
FROM Employees
WHERE Department IN
(
    SELECT Department
    FROM Managers
);

Result

Name	Department
James	IT
Grace	IT
Peter	Finance
Example 4 – Lowest Salary

Find the employee with the lowest salary.

SELECT Name,
       Salary
FROM Employees
WHERE Salary =
(
    SELECT MIN(Salary)
    FROM Employees
);

Result

Name	Salary
Mary	39000
Real-World Example

Imagine you're working for a bank.

Management asks:

Which customers have balances above the average account balance?

SELECT CustomerName,
       Balance
FROM Accounts
WHERE Balance >
(
    SELECT AVG(Balance)
    FROM Accounts
);

This is a common reporting task.

📝 Practice Exercises

Use the Employees table.
Question 1
Show employees whose salary is above the average salary.
SELECT Name,
       Salary
FROM Employees
WHERE Salary >
(
    SELECT AVG(Salary)
    FROM Employees
);

Question 2
Show employees who earn the highest salary.
SELECT Name,
       Salary
FROM Employees
WHERE Salary =
(
    SELECT MAX(Salary)
    FROM Employees
);

Question 3
Show employees who earn the lowest salary.
SELECT Name,
       Salary
FROM Employees
WHERE Salary =
(
    SELECT MIN(Salary)
    FROM Employees
);

Question 4
Show employees whose salary is below the average salary.
SELECT Name,
       Salary
FROM Employees
WHERE Salary <
(
    SELECT AVG(Salary)
    FROM Employees
);

Question 5
Using the Managers table, show employees who belong to departments listed in the Managers table.
SELECT Name,
       Department
FROM Employees
WHERE Department IN
(
    SELECT Department
    FROM Managers
);

⭐ Challenge 1
Show employees whose salary is greater than the average salary and display the results from the highest salary to the lowest.
SELECT Name,
       Salary
FROM Employees
WHERE Salary >
(
    SELECT AVG(Salary)
    FROM Employees
)
ORDER BY Salary DESC;

⭐⭐ Challenge 2
Management wants to know:
Which department has employees earning above the company average salary?
Display:
Employee Name
Department
Salary
(Hint: Use a subquery in the WHERE clause.)
SELECT EmployeeName,
       Department,
       Salary
FROM Employees
WHERE Salary >
(
    SELECT AVG(Salary)
    FROM Employees
);

💼 Interview Tip

A common interview question is:

"What is a subquery?"

A strong answer is:

"A subquery is a query nested inside another SQL query. It allows SQL to calculate or retrieve a value first, then use that result in the main query for filtering or comparison."

📝 GitHub Portfolio Task

Create:

SQL/
└── Day-08-Subqueries/
    ├── README.md
    ├── day8_notes.md
    ├── exercises.sql
    └── solutions.sql

Commit with:

Completed Day 8 - SQL Subqueries
🎯 Weekly Challenge

Without looking back at your previous lessons, answer these questions:

What is the difference between WHERE and HAVING?
What is the difference between INNER JOIN and LEFT JOIN?
What is a Primary Key?
What is a Foreign Key?
What is a Subquery?

If you can answer these confidently, you'll know you're retaining the concepts rather than just copying syntax.
