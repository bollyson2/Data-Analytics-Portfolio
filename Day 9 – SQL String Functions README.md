Module 1 – SQL Fundamentals
Day 9 – SQL String Functions

Duration: 60–90 minutes

Difficulty: ⭐⭐⭐☆☆

🎯 Learning Objectives

By the end of today's lesson, you will be able to:

Convert text to uppercase and lowercase.
Remove unwanted spaces.
Join text together.
Extract part of a string.
Replace text.
Count the number of characters.
Clean messy data before analysis.

These are common tasks when preparing data for dashboards, reports, or analysis.

🧹 Why String Functions Matter

Imagine you receive this customer data:

CustomerName
john smith
JOHN SMITH
John Smith
john smith
John Smith

These all refer to the same person, but they are formatted differently.

SQL string functions help clean and standardise data.

1. UPPER()

Converts text to uppercase.

SELECT UPPER(Name)
FROM Employees;
Result
UPPER(Name)
JAMES
MARY
PETER
2. LOWER()

Converts text to lowercase.

SELECT LOWER(Name)
FROM Employees;

Result

LOWER(Name)
james
mary
peter
3. LENGTH()

Counts the number of characters.

SELECT Name,
       LENGTH(Name) AS NameLength
FROM Employees;

Example:

Name	NameLength
James	5
Christopher	11

Note: In SQL Server, the equivalent function is LEN(Name) instead of LENGTH(Name).

4. TRIM()

Removes spaces before and after text.

Example:

"  James  "

becomes

"James"

SQL:

SELECT TRIM(Name)
FROM Employees;
5. CONCAT()

Joins text together.

Suppose you have:

FirstName	LastName
James	Brown
SELECT CONCAT(FirstName, ' ', LastName) AS FullName
FROM Employees;

Result:

FullName
James Brown
6. SUBSTRING()

Extracts part of a string.

SELECT SUBSTRING(Name,1,3)
FROM Employees;

Result:

Name
Jam
Mar
Pet

Meaning:

Start at character 1
Return 3 characters
7. REPLACE()

Replace one piece of text with another.

SELECT REPLACE(Department,'HR','Human Resources')
FROM Employees;

Result:

Department
Human Resources
IT
Finance
Real-World Example

Imagine you're cleaning customer names before creating a Power BI dashboard.

SELECT
    UPPER(TRIM(CustomerName)) AS CleanCustomerName
FROM Customers;

This removes extra spaces and converts names to uppercase, making duplicates easier to identify.

📝 Practice Exercises
Use the Employees table.

Question 1
Display employee names in uppercase.
SELECT UPPER(Name)
FROM Employees;

Question 2
Display employee names in lowercase.
SELECT LOWER(Name)
FROM Employees;

Question 3
Display employee names together with the number of characters in each name.
SELECT Name,
       LENGTH(Name) AS NameLength
FROM Employees;

Question 4
Display employee names after removing extra spaces.
SELECT Name,
       TRIM(Name) AS EmployeeName
FROM Employees;

Question 5
Assume Employees has FirstName and LastName columns.
Display the employee's full name using CONCAT().
SELECT CONCAT(FirstName, ' ', LastName) AS FullName
FROM Employees;

⭐ Challenge 1
Display:
Employee Name
First 3 letters of the name
Name length
(Hint: Use SUBSTRING() and LENGTH() or LEN().)
SELECT Name,
       SUBSTRING(Name,1,3) AS FirstThreeLetters,
       LENGTH(Name) AS NameLength
FROM Employees;

⭐⭐ Challenge 2
The Department column contains HR.
Replace HR with Human Resources in the query output without changing the data stored in the table.
SELECT Department,
       REPLACE(Department,'HR','Human Resources') AS UpdatedDepartment
FROM Employees;

💼 Interview Tip

Question:

Why are SQL string functions important?

A good answer:

"SQL string functions help clean, standardise, and transform text data. They are useful for preparing data for analysis, reporting, dashboards, and improving data quality."
