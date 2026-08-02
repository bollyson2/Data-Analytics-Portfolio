Module 1 – SQL Fundamentals
Day 10 – SQL Date Functions

Duration: 60–90 minutes

Difficulty: ⭐⭐⭐⭐☆

🎯 Learning Objectives

By the end of today's lesson, you will be able to:

Retrieve the current date and time.
Extract the year, month, and day from a date.
Calculate the difference between two dates.
Add or subtract days, months, or years from a date.
Filter records using dates.
Answer common interview questions on SQL date functions.
🤔 Why Date Functions Matter

Almost every business stores data with dates:

Customer registrations
Employee hire dates
Sales transactions
Orders
Payments
Deliveries
Support tickets

As a Data Analyst, you'll frequently answer questions like:

How many employees joined this year?
Which orders were placed last month?
How many days has an invoice been overdue?
What were total sales in July?
Sample Employees Table
EmployeeID	Name	HireDate
1	James	2023-05-15
2	Mary	2022-09-10
3	Peter	2024-01-08
4	Grace	2021-12-20
1. Get Today's Date
MySQL / PostgreSQL
SELECT CURRENT_DATE;
SQL Server
SELECT GETDATE();

Example output:

2026-08-02
2. Extract the Year
SELECT Name,
       YEAR(HireDate) AS HireYear
FROM Employees;

Result:

Name	HireYear
James	2023
Mary	2022
3. Extract the Month
SELECT Name,
       MONTH(HireDate) AS HireMonth
FROM Employees;

Result:

Name	HireMonth
James	5
Mary	9
4. Extract the Day
SELECT Name,
       DAY(HireDate) AS HireDay
FROM Employees;

Result:

Name	HireDay
James	15
Mary	10
5. Calculate the Difference Between Dates
SQL Server
SELECT Name,
       DATEDIFF(YEAR, HireDate, GETDATE()) AS YearsWorked
FROM Employees;

This calculates approximately how many years each employee has worked.

6. Add Days to a Date
SQL Server
SELECT DATEADD(DAY, 30, HireDate)
FROM Employees;

This adds 30 days to each hire date.

7. Employees Hired After 2023
SELECT Name,
       HireDate
FROM Employees
WHERE HireDate > '2023-01-01';

Result:

Name	HireDate
Peter	2024-01-08
8. Employees Hired in 2022
SELECT Name,
       HireDate
FROM Employees
WHERE YEAR(HireDate) = 2022;
Real-World Example

Imagine you work for an online retailer.

Management asks:

"Show all orders placed during 2025."

SELECT OrderID,
       CustomerName,
       OrderDate
FROM Orders
WHERE YEAR(OrderDate) = 2025;

Another request:

"How many days ago was each order placed?"

SELECT OrderID,
       DATEDIFF(DAY, OrderDate, GETDATE()) AS DaysAgo
FROM Orders;

📝 Practice Exercises
Use the Employees table.

Question 1
Display:
Employee Name
Hire Date
Hire Year
SELECT Name,
       HireDate,
       YEAR(HireDate) AS HireYear
FROM Employees;

Question 2
Display:
Employee Name
Hire Month
SELECT Name,
       MONTH(HireDate) AS HireMonth
FROM Employees;

Question 3
Display:
Employee Name
Hire Day
SELECT Name,
       DAY(HireDate) AS HireDay
FROM Employees;

Question 4
Show employees hired after 1 January 2023.
SELECT Name,
       HireDate
FROM Employees
WHERE HireDate > '2023-01-01';

Question 5
Show employees hired in 2022.
SELECT Name,
       HireDate
FROM Employees
WHERE YEAR(HireDate) = 2022;

⭐ Challenge 1
Display:
Employee Name
Hire Date
Number of years worked
Use DATEDIFF() (SQL Server) or the equivalent function in your SQL database.
SELECT Name,
       HireDate,
       DATEDIFF(YEAR, HireDate, GETDATE()) AS YearsWorked
FROM Employees;

⭐⭐ Challenge 2
Management wants a report showing:
Employee Name
Hire Date
Hire Year
Hire Month
Hire Day
Sort the report by Hire Date (oldest first).
SELECT Name,
       HireDate,
       YEAR(HireDate) AS HireYear,
       MONTH(HireDate) AS HireMonth,
       DAY(HireDate) AS HireDay
FROM Employees
ORDER BY HireDate ASC;

💼 Interview Tip

A common SQL interview question is:

"What is the difference between CURRENT_DATE and GETDATE()?"

A good answer:

CURRENT_DATE returns only the current date and is commonly used in MySQL and PostgreSQL.
GETDATE() returns both the current date and current time in SQL Server.
