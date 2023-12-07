# SQL Schema Creation, Data Insertion, and Function Examples

## Part 1: `employees` Table and SQL Function Examples

### Create `employees` Table and Insert Data

```sql
CREATE TABLE employees (
    id INT,
    name VARCHAR(50),
    salary DECIMAL(10, 2),
    join_date DATE
);

-- Insert sample data into employees
INSERT INTO employees (id, name, salary, join_date) VALUES
(1, 'Alice', 70000, '2019-04-23'),
(2, 'Bob', 85000, '2018-05-15'),
(3, 'Charlie', 56000, '2020-09-10'),
(4, 'David', 60000, '2017-03-08');
```

### SQL Function Examples Using `employees`

#### Counting Employees

```sql
-- Counts the total number of employees
SELECT COUNT(*) FROM employees;
```

#### Calculating Average Salary

```sql
-- Calculates the average salary of all employees
SELECT AVG(salary) FROM employees;
```

#### Finding Maximum and Minimum Salary

```sql
-- Finds the highest and lowest salary in the employees table
SELECT MAX(salary) AS HighestSalary, MIN(salary) AS LowestSalary FROM employees;
```

#### Listing Employees Who Joined After a Specific Date

```sql
-- Filters employees who joined after January 1, 2019
SELECT name, join_date FROM employees WHERE join_date > '2019-01-01';
```

#### String Concatenation and Case Conversion

```sql
-- Concatenates and converts employee names to upper case
SELECT CONCAT(UPPER(name), ' (ID: ', id, ')') AS EmployeeDetails FROM employees;
```

#### Calculating Tenure

```sql
-- Calculates how many days each employee has worked
SELECT name, DATEDIFF(NOW(), join_date) AS DaysWorked FROM employees;
```

## Part 2: Introducing `departments` Table and SQL Joins

### Create `departments` Table and Alter `employees` Table

```sql
CREATE TABLE departments (
    dept_id INT,
    dept_name VARCHAR(50),
    PRIMARY KEY (dept_id)
);

-- Insert sample data into departments
INSERT INTO departments (dept_id, dept_name) VALUES
(1, 'Human Resources'),
(2, 'Finance'),
(3, 'IT'),
(4, 'Marketing');

ALTER TABLE employees ADD COLUMN dept_id INT;
ALTER TABLE employees ADD FOREIGN KEY (dept_id) REFERENCES departments(dept_id);
```

### SQL Join Examples Using `employees` and `departments`

#### Joining Employees with Departments

```sql
-- Joins employees with their respective departments
SELECT e.name, d.dept_name FROM employees e
JOIN departments d ON e.dept_id = d.dept_id;
```

#### Average Salary by Department

```sql
-- Calculates the average salary for each department
SELECT d.dept_name, AVG(e.salary) AS AvgSalary
FROM employees e
JOIN departments d ON e.dept_id = d.dept_id
GROUP BY d.dept_name;
```

#### Counting Employees in Each Department

```sql
-- Counts the number of employees in each department
SELECT d.dept_name, COUNT(e.id) AS NumberOfEmployees
FROM departments d
LEFT JOIN employees e ON d.dept_id = e.dept_id
GROUP BY d.dept_name;
```

This document provides a detailed guide on creating and manipulating data in SQL, including basic functions and more advanced operations involving joins between tables.
```

