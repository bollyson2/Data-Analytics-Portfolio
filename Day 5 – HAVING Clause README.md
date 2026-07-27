Module 1 – SQL Fundamentals
Understanding WHERE vs HAVING

This is one of the most important concepts in SQL.

Think of it like this:

WHERE

Filters individual rows before grouping.

HAVING

Filters groups after grouping.

Example 1 – WHERE

Find employees earning more than £40,000.

SELECT *
FROM Employees
WHERE Salary > 40000;

This looks at each employee individually.

Example 2 – HAVING

Find departments whose average salary is greater than £45,000.

SELECT Department,
       AVG(Salary) AS AverageSalary
FROM Employees
GROUP BY Department
HAVING AVG(Salary) > 45000;

Notice:

We are filtering departments, not employees.

Sample Data
Employee	Department	Salary
James	IT	45000
Mary	HR	39000
Peter	Finance	50000
Grace	IT	47000
David	HR	41000
Example 1
Departments with more than one employee
SELECT Department,
       COUNT(*) AS Employees
FROM Employees
GROUP BY Department
HAVING COUNT(*) > 1;
Result
Department	Employees
HR	2
IT	2

Finance is excluded because it has only one employee.

Example 2

Departments spending more than £80,000.

SELECT Department,
       SUM(Salary) AS TotalSalary
FROM Employees
GROUP BY Department
HAVING SUM(Salary) > 80000;
Result
Department	Total Salary
IT	£92,000
Example 3

Departments with an average salary above £45,000.

SELECT Department,
       AVG(Salary) AS AverageSalary
FROM Employees
GROUP BY Department
HAVING AVG(Salary) > 45000;
Result
Department	Average Salary
Finance	£50,000
IT	£46,000
WHERE and HAVING Together

You can use both in one query.

Suppose management asks:

Show departments where employees earn more than £40,000, and only include departments whose total salary exceeds £45,000.

SELECT Department,
       SUM(Salary) AS TotalSalary
FROM Employees
WHERE Salary > 40000
GROUP BY Department
HAVING SUM(Salary) > 45000;

Execution order:

FROM
WHERE
GROUP BY
HAVING
SELECT
ORDER BY
Real-World Example

Imagine you're working for Tesco.

Table: Sales

Product	Revenue
Bread	£50
Bread	£30
Milk	£40
Milk	£45
Rice	£20

Management asks:

Which products generated more than £70?

SELECT Product,
       SUM(Revenue) AS TotalRevenue
FROM Sales
GROUP BY Product
HAVING SUM(Revenue) > 70;

Result:

Product	Revenue
Bread	£80
Milk	£85
📝 Practice Exercises

Use the Employees table.

Question 1
Show departments with more than one employee.
SELECT Department,
       COUNT(*) AS TotalEmployees
FROM Employees
GROUP BY Department
HAVING COUNT(*) > 1;

Question 2
Show departments where the total salary exceeds £80,000.
SELECT Department,
       SUM(Salary) AS TotalSalary
FROM Employees
GROUP BY Department
HAVING SUM(Salary) > 80000;

Question 3
Show departments where the average salary exceeds £45,000.
SELECT Department,
       AVG(Salary) AS AverageSalary
FROM Employees
GROUP BY Department
HAVING AVG(Salary) > 45000;

Question 4
Show departments where the highest salary is above £45,000.
SELECT Department,
       MAX(Salary) AS HighestSalary
FROM Employees
GROUP BY Department
HAVING MAX(Salary) > 45000;

Question 5
Show departments where the lowest salary is below £40,000.
SELECT Department,
       MIN(Salary) AS LowestSalary
FROM Employees
GROUP BY Department
HAVING MIN(Salary) < 40000;

⭐ Challenge 1
Find departments that:
have more than one employee, and
have a total salary greater than £80,000.
SELECT Department,
       COUNT(*) AS TotalEmployees,
       SUM(Salary) AS TotalSalary
FROM Employees
GROUP BY Department
HAVING COUNT(*) > 1
   AND SUM(Salary) > 80000;
   
⭐⭐ Challenge 2
Management wants departments with:
an average salary greater than £40,000, and
display the results from the highest average salary to the lowest.
SELECT Department,
       AVG(Salary) AS AverageSalary
FROM Employees
GROUP BY Department
HAVING AVG(Salary) > 40000
ORDER BY AverageSalary DESC;
