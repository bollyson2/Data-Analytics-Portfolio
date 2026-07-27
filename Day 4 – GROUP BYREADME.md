📘 Data Analytics Learning Journal
Module 1 – SQL Fundamentals
Day 4 – GROUP BY

Today we'll answer questions like:

"How much salary is paid in each department?"

instead of

"How much salary is paid in the whole company?"

Sample Data
EmployeeID	Name	Department	Salary
1	James	IT	45000
2	Mary	HR	39000
3	Peter	Finance	50000
4	Grace	IT	47000
5	David	HR	41000
1. GROUP BY

Imagine your manager asks:

How many employees work in each department?

Instead of counting the whole company:

SELECT COUNT(*)
FROM Employees;

Use:

SELECT Department,
       COUNT(*) AS NumberOfEmployees
FROM Employees
GROUP BY Department;
Result
Department	NumberOfEmployees
Finance	1
HR	2
IT	2
2. SUM() with GROUP BY

Business question:

How much salary does each department cost?

SELECT Department,
       SUM(Salary) AS TotalSalary
FROM Employees
GROUP BY Department;
Result
Department	Total Salary (£)
Finance	50000
HR	80000
IT	92000
3. AVG() with GROUP BY

Manager asks:

What is the average salary in each department?

SELECT Department,
       AVG(Salary) AS AverageSalary
FROM Employees
GROUP BY Department;
Result
Department	Average Salary (£)
Finance	50000
HR	40000
IT	46000
4. MAX() with GROUP BY
SELECT Department,
       MAX(Salary) AS HighestSalary
FROM Employees
GROUP BY Department;

Result

Department	Highest Salary (£)
Finance	50000
HR	41000
IT	47000
5. MIN() with GROUP BY
SELECT Department,
       MIN(Salary) AS LowestSalary
FROM Employees
GROUP BY Department;
Why is GROUP BY Important?

Suppose you work for:

NHS
Tesco
Amazon
HMRC
Office for National Statistics

Managers rarely ask:

"What's the total salary?"

They usually ask:

How many employees are in each department?
Which department spends the most?
What's the average salary by team?
How many customers purchased each product?
How much revenue came from each region?

This is why GROUP BY is one of the most-used SQL clauses.

Real-World Example

Imagine a Sales table:

Product	Quantity	Revenue (£)
Milk	20	30
Milk	15	25
Bread	10	15
Bread	25	38
Rice	8	40

Question:

How much revenue did each product generate?

SELECT Product,
       SUM(Revenue) AS TotalRevenue
FROM Sales
GROUP BY Product;

Result

Product	Total Revenue (£)
Bread	53
Milk	55
Rice	40
📝 Practice Exercises

Using the Employees table, write SQL for the following:

Question 1
Count the number of employees in each department.
SELECT Department,
       COUNT(*) AS TotalEmployees
FROM Employees
GROUP BY Department;

Question 2
Calculate the total salary for each department.
SELECT Department,
       SUM(Salary) AS TotalSalary
FROM Employees
GROUP BY Department;

Question 3
Calculate the average salary for each department.
SELECT Department,
       AVG(Salary) AS AverageSalary
FROM Employees
GROUP BY Department;

Question 4
Show the highest salary in each department.
SELECT Department,
       MAX(Salary) AS HighestSalary
FROM Employees
GROUP BY Department;

Question 5
Show the lowest salary in each department.
SELECT Department,
       MIN(Salary) AS LowestSalary
FROM Employees
GROUP BY Department;

⭐ Challenge 1
Show the total salary for each department, ordered from the highest total salary to the lowest.
SELECT Department,
       SUM(Salary) AS TotalSalary
FROM Employees
GROUP BY Department
ORDER BY TotalSalary DESC;
(Hint: combine GROUP BY and ORDER BY.)

⭐⭐ Challenge 2
SELECT Department,
       AVG(Salary) AS AverageSalary
FROM Employees
GROUP BY Department
HAVING AVG(Salary) > 45000;
