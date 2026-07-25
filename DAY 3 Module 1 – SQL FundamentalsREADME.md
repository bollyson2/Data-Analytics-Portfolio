– Aggregate Functions

Duration: 60–90 minutes

Difficulty: ⭐⭐☆☆☆ (Beginner–Intermediate)

🎯 Learning Objectives

By the end of today's lesson, you will be able to:

Use COUNT() to count records.
Use SUM() to add values.
Use AVG() to calculate averages.
Use MIN() and MAX() to find the smallest and largest values.
Answer real business questions using SQL.
📖 Recap

So far you've mastered:

✅ SELECT
✅ FROM
✅ WHERE
✅ ORDER BY
✅ ASC
✅ DESC
✅ AND
✅ OR

Now we're learning how to summarise data, which is a core part of data analysis.

Our Sample Table

We'll continue using this Employees table:

EmployeeID	Name	Department	Salary
1	James	IT	45000
2	Mary	HR	39000
3	Peter	Finance	50000
4	Grace	IT	47000
5	David	HR	41000
1. COUNT()
Business Question

How many employees work in the company?

SELECT COUNT(*)
FROM Employees;

Result

COUNT
5
Count only IT employees
SELECT COUNT(*)
FROM Employees
WHERE Department = 'IT';

Result

COUNT
2
2. SUM()
Business Question

How much do we spend on salaries?

SELECT SUM(Salary)
FROM Employees;

Let's calculate:

45000

39000

50000

47000

41000

Total:

£222,000

3. AVG()
Business Question

What is the average salary?

SELECT AVG(Salary)
FROM Employees;

Calculation:

£222,000 ÷ 5

= £44,400

4. MIN()
Business Question

Who earns the lowest salary?

SELECT MIN(Salary)
FROM Employees;

Result:

39000

(Mary)

5. MAX()
Business Question

Who earns the highest salary?

SELECT MAX(Salary)
FROM Employees;

Result:

50000

(Peter)

Real-World Example (Retail)

Imagine you work as a Data Analyst for a supermarket.

Table: Sales

SaleID	Product	Quantity	Revenue (£)
1	Milk	20	30
2	Bread	15	22
3	Rice	10	50
4	Eggs	30	60
Total Revenue
SELECT SUM(Revenue)
FROM Sales;
Average Revenue per Sale
SELECT AVG(Revenue)
FROM Sales;
Highest Revenue
SELECT MAX(Revenue)
FROM Sales;

These are exactly the kinds of queries used to build dashboards and reports.

📝 Practice Exercise

Use the Employees table to answer the following.

Question 1

How many employees are there?

Question 2

What is the total salary paid?

Question 3

What is the average salary?

Question 4

What is the highest salary?

Question 5

What is the lowest salary?

Question 6

How many employees work in the HR department?

Question 7

What is the total salary paid to employees in the IT department?
