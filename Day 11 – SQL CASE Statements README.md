Module 1 – SQL Fundamentals
Day 11 – SQL CASE Statements

Duration: 60–90 minutes

Difficulty: ⭐⭐⭐⭐☆

🎯 Learning Objectives

By the end of today's lesson, you will be able to:

Understand the CASE statement.
Categorise data using business rules.
Create custom labels in SQL.
Use CASE with SELECT.
Use CASE with ORDER BY.
Solve real-world business reporting problems.
🤔 What is a CASE Statement?

A CASE statement works like IF...ELSE in Excel.

It checks conditions and returns different values depending on whether the conditions are true or false.

Think of it like this:

If Salary is greater than £50,000 → "High Salary"

Otherwise → "Standard Salary"

Sample Employees Table
EmployeeID	Name	Department	Salary
1	James	IT	45000
2	Mary	HR	39000
3	Peter	Finance	52000
4	Grace	IT	47000
5	David	HR	61000
Basic CASE Syntax
SELECT
    Name,
    Salary,
    CASE
        WHEN Salary >= 50000 THEN 'High Salary'
        ELSE 'Standard Salary'
    END AS SalaryCategory
FROM Employees;
Result
Name	Salary	SalaryCategory
James	45000	Standard Salary
Mary	39000	Standard Salary
Peter	52000	High Salary
Grace	47000	Standard Salary
David	61000	High Salary
Example 2 – Multiple Conditions
SELECT
    Name,
    Salary,
    CASE
        WHEN Salary >= 60000 THEN 'Excellent'
        WHEN Salary >= 50000 THEN 'Good'
        WHEN Salary >= 40000 THEN 'Average'
        ELSE 'Low'
    END AS SalaryBand
FROM Employees;
Result
Salary	SalaryBand
61000	Excellent
52000	Good
47000	Average
39000	Low
Example 3 – Department Categories
SELECT
    Name,
    Department,
    CASE
        WHEN Department = 'IT' THEN 'Technology'
        WHEN Department = 'HR' THEN 'People Operations'
        ELSE 'Business'
    END AS DepartmentGroup
FROM Employees;
Example 4 – Using CASE in ORDER BY

Suppose management wants IT staff listed first.

SELECT
    Name,
    Department
FROM Employees
ORDER BY
CASE
    WHEN Department='IT' THEN 1
    WHEN Department='Finance' THEN 2
    ELSE 3
END;
Real-World Example

Imagine you're analysing bank customers.

Management asks:

Categorise customers based on account balance.

SELECT
    CustomerName,
    Balance,
    CASE
        WHEN Balance >= 100000 THEN 'Premium'
        WHEN Balance >= 25000 THEN 'Gold'
        ELSE 'Standard'
    END AS CustomerType
FROM Customers;

This type of logic is commonly used in dashboards and customer segmentation.

📝 Practice Exercises
Use the Employees table.
Question 1
Display:
Name
Salary
Create a new column called SalaryCategory:
Salary 50,000 or more → High
Otherwise → Normal
SELECT
    Name,
    Salary,
    CASE
        WHEN Salary >= 50000 THEN 'High'
        ELSE 'Normal'
    END AS SalaryCategory
FROM Employees;

Question 2
Display:
Name
Salary
Create a column called SalaryBand:
60,000 or more → Excellent
50,000–59,999 → Good
40,000–49,999 → Average
Below 40,000 → Low
SELECT
    Name,
    Salary,
    CASE
        WHEN Salary >= 60000 THEN 'Excellent'
        WHEN Salary >= 50000 THEN 'Good'
        WHEN Salary >= 40000 THEN 'Average'
        ELSE 'Low'
    END AS SalaryBand
FROM Employees;

Question 3
Display:
Name
Department
Create a column called DepartmentGroup:
IT → Technology
HR → Human Resources
Everything else → Other
SELECT
    Name,
    Department,
    CASE
        WHEN Department = 'IT' THEN 'Technology'
        WHEN Department = 'HR' THEN 'Human Resources'
        ELSE 'Other'
    END AS DepartmentGroup
FROM Employees;

Question 4
Display:
Name
Salary
Create a column showing:
"Eligible for Bonus" if salary is 45,000 or more
"Not Eligible" otherwise
SELECT
    Name,
    Salary,
    CASE
        WHEN Salary >=45000 THEN 'Eligible for Bonus'
        ELSE 'Not Eligible'
    END AS BonusStatus
FROM Employees;

Question 5
Display:
Name
Department
Sort the results so that:
Finance appears first.
IT appears second.
HR appears last.
(Hint: Use CASE inside ORDER BY.)
SELECT
    Name,
    Department
FROM Employees
ORDER BY
CASE
WHEN Department='Finance' THEN 1
WHEN Department='IT' THEN 2
ELSE 3
END;

⭐ Challenge 1
Management wants to identify employee grades.
Display:
Name
Salary
Grade
Rules:
60,000+ → Grade A
50,000–59,999 → Grade B
40,000–49,999 → Grade C
Below 40,000 → Grade D
SELECT
    Name,
    Salary,
    CASE
        WHEN Salary >=60000 THEN 'Grade A'
        WHEN Salary >=50000 THEN 'Grade B'
        WHEN Salary >=40000 THEN 'Grade C'
        ELSE 'Grade D'
    END AS Grade
FROM Employees;

⭐⭐ Challenge 2
Create a complete employee report showing:
Name
Department
Salary
Salary Band
Department Group
Bonus Eligibility
Sort the report by:
Salary (highest first)
Name (A–Z)
SELECT
    Name,
    Department,
    Salary,

    CASE
        WHEN Salary >=60000 THEN 'Excellent'
        WHEN Salary >=50000 THEN 'Good'
        WHEN Salary >=40000 THEN 'Average'
        ELSE 'Low'
    END AS SalaryBand,

    CASE
        WHEN Department='IT' THEN 'Technology'
        WHEN Department='HR' THEN 'Human Resources'
        ELSE 'Other'
    END AS DepartmentGroup,

    CASE
        WHEN Salary >=45000 THEN 'Eligible for Bonus'
        ELSE 'Not Eligible'
    END AS BonusEligibility

FROM Employees

ORDER BY Salary DESC,
         Name ASC;

💼 Interview Tip
Question:
Why would you use a CASE statement?
A strong answer:
"A CASE statement allows you to apply business rules to data, create categories, classify records, and produce meaningful reports without changing the underlying data."

📚 Quick Revision
Answer these without looking at your notes:
What does a CASE statement do?
What is the purpose of WHEN?
What is the purpose of ELSE?
Why do we use END?
Can CASE be used in ORDER BY?
