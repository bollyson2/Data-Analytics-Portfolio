ORDER BY

Suppose your Employees table contains:

EmployeeID	Name	Department	Salary
1	James	IT	45000
2	Mary	HR	39000
3	Peter	Finance	50000
4	Grace	IT	47000
5	David	HR	41000

If you write:

SELECT *
FROM Employees
ORDER BY Salary;

SQL automatically sorts from the smallest salary to the largest.

Result:

Mary → 39000

David → 41000

James → 45000

Grace → 47000

Peter → 50000

3. ASC (Ascending)

ASC means smallest to largest or A to Z.

These two queries are exactly the same:

SELECT *
FROM Employees
ORDER BY Salary;

and

SELECT *
FROM Employees
ORDER BY Salary ASC;

Because ASC is SQL's default.

4. DESC (Descending)

Suppose your manager asks:

Show me the employees earning the highest salaries first.

Now use:

SELECT *
FROM Employees
ORDER BY Salary DESC;

Result:

Peter → 50000

Grace → 47000

James → 45000

David → 41000

Mary → 39000

Think:

DESC = Biggest → Smallest

5. Sorting Names

Sort alphabetically:

SELECT *
FROM Employees
ORDER BY Name ASC;

Result:

David

Grace

James

Mary

Peter

Reverse alphabetical order:

SELECT *
FROM Employees
ORDER BY Name DESC;

Result:

Peter

Mary

James

Grace

David

6. Using AND

Suppose you only want employees:

in the IT department
earning more than £46,000

Write:

SELECT *
FROM Employees
WHERE Department = 'IT'
AND Salary > 46000;

Result:

Grace

James is excluded because his salary is £45,000.

7. Using OR

Suppose you want employees who work in:

HR
OR Finance
SELECT *
FROM Employees
WHERE Department = 'HR'
OR Department = 'Finance';

Result:

Mary

David

Peter

8. Real-World Example

Imagine you're working for an NHS hospital.

Table: Patients

Patient	Age	Gender	Ward
John	68	Male	Cardiology
Sarah	45	Female	Oncology
David	72	Male	Cardiology
Lucy	38	Female	Maternity

Patients over 65:

SELECT *
FROM Patients
WHERE Age > 65;

Patients in Cardiology:

SELECT *
FROM Patients
WHERE Ward = 'Cardiology';

Cardiology patients over 65:

SELECT *
FROM Patients
WHERE Ward = 'Cardiology'
AND Age > 65;
💻 Practice Exercise

Using the Employees table above, write SQL queries for the following:

Question 1
Show all employees sorted by Salary from highest to lowest.
SELECT *
FROM Employees
ORDER BY Salary DESC;

Question 2
Show all employees sorted by Name alphabetically.
SELECT *
FROM Employees
ORDER BY Name ASC;
or SELECT *
FROM Employees
ORDER BY Name;

Question 3
Show employees in the HR department whose salary is greater than 40,000.
SELECT *
FROM Employees
WHERE Department = ‘HR’
AND Salary > 40000;

Question 4
Show employees who work in Finance OR IT.
SELECT *
FROM Employees
WHERE Department = ‘Finance’
OR Department = ‘IT’;

Question 5 (Challenge)
Show only the Name and Salary of employees in the IT department, ordered by salary from highest to lowest.
SELECT Name, Salary
FROM Employees
WHERE Department = ‘IT’
ORDER BY Salary DESC;
