📘 Data Analytics Learning Journal
Module 1 – SQL Fundamentals
Day 4 – GROUP BY

Duration: 60–90 minutes

Difficulty: ⭐⭐⭐☆☆ (Intermediate)

🎯 Learning Objectives

By the end of today's lesson, you will be able to:

Understand what GROUP BY does.
Group records by categories.
Use COUNT(), SUM(), AVG(), MIN(), and MAX() with GROUP BY.
Create reports similar to those used in business.
📖 Quick Recap

So far you've learned:

✅ SELECT

✅ FROM

✅ WHERE

✅ ORDER BY

✅ AND / OR

✅ COUNT()

✅ SUM()

✅ AVG()

✅ MIN()

✅ MAX()

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

Question 2

Calculate the total salary for each department.

Question 3

Calculate the average salary for each department.

Question 4

Show the highest salary in each department.

Question 5

Show the lowest salary in each department.

⭐ Challenge 1

Show the total salary for each department, ordered from the highest total salary to the lowest.

(Hint: combine GROUP BY and ORDER BY.)

📘 Day 4 Assessment – GROUP BY
Question 1

Task: Count the number of employees in each department.

Your answer:

SELECT Department,
       COUNT(*) AS TotalEmployees
FROM Employees
GROUP BY Department;

✅ Excellent!

This is exactly how a Data Analyst would write it.

Score: 10/10

Question 2

Task: Calculate the total salary for each department.

Your answer:

SELECT Department,
       SUM(Salary) AS TotalSalary
FROM Employees
GROUP BY Department;

✅ Perfect

Score: 10/10

Question 3

Task: Calculate the average salary for each department.

Your answer:

SELECT Department,
       AVG(Salary) AS AverageSalary
FROM Employees
GROUP BY Department;

✅ Correct

Score: 10/10

Question 4

Task: Show the highest salary in each department.

Your answer:

SELECT Department,
       MAX(Salary) AS HighestSalary
FROM Employees
GROUP BY Department;

✅ Perfect

Score: 10/10

Question 5

Task: Show the lowest salary in each department.

Your answer:
SELECT Department,
       MIN(Salary) AS LowestSalary
FROM Employees
GROUP BY Department;

⭐ Challenge 1

Your answer:

SELECT Department,
       SUM(Salary) AS TotalSalary
FROM Employees
GROUP BY Department
ORDER BY TotalSalary DESC;

✅ Excellent!

This is exactly how professionals write reports.

Result:

Department	Total Salary
IT	£92,000
HR	£80,000
Finance	£50,000

Score: 10/10

⭐⭐ Challenge 2

Your answer:

SELECT Department,
       AVG(Salary) AS AverageSalary
FROM Employees
GROUP BY Department
WHERE Salary > £45000
Good Attempt 👍
corret
SELECT Department,
       AVG(Salary) AS AverageSalary
FROM Employees
GROUP BY Department
HAVING AVG(Salary) > 45000;

Result

Department	Average Salary
Finance	£50,000
IT	£46,000

Notice that HR is excluded because its average salary is £40,000.

Score: 7/10

This is still a good attempt because you were trying to apply new concepts before learning HAVING.

📊 Overall Score
Question	Score
Q1	10/10
Q2	10/10
Q3	10/10
Q4	10/10
Q5	9/10
Challenge 1	10/10
Challenge 2	7/10
Final Score: 66/70 (94%)
⭐ Grade: A

⭐⭐ Challenge 2

Show departments where the average salary is greater than £45,000.

Don't worry if you're not sure how to do this yet—give it your best attempt. We'll cover the proper solution when we learn HAVING in the next lesson.
