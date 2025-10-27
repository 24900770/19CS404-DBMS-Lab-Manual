# Experiment 4: Aggregate Functions, Group By and Having Clause

## AIM
To study and implement aggregate functions, GROUP BY, and HAVING clause with suitable examples.

## THEORY

### Aggregate Functions
These perform calculations on a set of values and return a single value.

- **MIN()** – Smallest value  
- **MAX()** – Largest value  
- **COUNT()** – Number of rows  
- **SUM()** – Total of values  
- **AVG()** – Average of values

**Syntax:**
```sql
SELECT AGG_FUNC(column_name) FROM table_name WHERE condition;
```
### GROUP BY
Groups records with the same values in specified columns.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name;
```
### HAVING
Filters the grouped records based on aggregate conditions.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name
HAVING condition;
```

**Question 1**
--How many medical records does each doctor have?

Sample table:MedicalRecords Table



For example:

Result
DoctorID    TotalRecords
----------  ------------
3           4
5           1
6           1
7           1
8           3

```sql
SELECT DoctorID, COUNT(*) as TotalRecords 
FROM MedicalRecords
Group By DoctorID;
```

**Output:**
<img width="663" height="658" alt="Screenshot 2025-10-27 133645" src="https://github.com/user-attachments/assets/e15ce187-8936-48e8-900d-5105ffa0e048" />



**Question 2**
---
What is the count of male and female patients?

Sample table: Patients Table



For example:

Result
Gender      TotalPatients
----------  -------------
Female      5
Male        5


```sql
select Gender, COUNT(*) as TotalPatients 
From Patients
Group by Gender;

```

**Output:**
<img width="703" height="429" alt="Screenshot 2025-10-27 133653" src="https://github.com/user-attachments/assets/4894715c-d78c-4191-a312-1ac8b96fb0e1" />



**Question 3**
---
Write a SQL query to find how many employees have an income greater than 50K?

Table: employee

name        type
----------  ----------
id          INTEGER
name        TEXT
age         INTEGER
city        TEXT
income      INTEGER

For example:

Result
employees_count
---------------
8


```sql
select COUNT(*) AS employees_count
from employee
where income > 50000;
```

**Output:**
<img width="607" height="384" alt="Screenshot 2025-10-27 133658" src="https://github.com/user-attachments/assets/6f4ca358-537d-4d71-ac12-cefe1956ee68" />



**Question 4**
---
Write a SQL query to find the shortest email address in the customer table?

Table: customer

name        type
----------  ----------
id          INTEGER
name        TEXT   
city        TEXT
email       TEXT
phone       INTEGER
For example:

Result
name        email           min_email_length
----------  --------------  ----------------
Ravi Kumar  ravi@gmail.com  14

```sql
select name, email, LENGTH(email) as min_email_length
FROM customer
WHERE LENGTH(email) = (
SELECT MIN(LENGTH(email)) FROM customer
)
LIMIT 1;
```

**Output:**

<img width="1066" height="331" alt="Screenshot 2025-10-27 133713" src="https://github.com/user-attachments/assets/11b2ab6d-efed-4798-99f6-a3e3380a49b2" />


**Question 5**
---
Write a SQL query to find the customer with longest name?

Table: customer

name        type
----------  ----------
id          INTEGER
name        TEXT
city        TEXT
email       TEXT
phone       INTEGER
For example:

Result
name          length
------------  ----------
Preeti Patel  12

```sql
SELECT name, LENGTH(name) as length
FROM customer
WHERE LENGTH(name) = (SELECT MAX(LENGTH(name)) FROM customer)
LIMIT 1;
```

**Output:**

<img width="728" height="318" alt="Screenshot 2025-10-27 133719" src="https://github.com/user-attachments/assets/0f02a688-dbd4-4137-aac9-5c5cd8762450" />



**Question 6**
---
Write a SQL query to find the total income of employees aged 40 or above.

Table: employee

name        type
----------  ----------
id          INTEGER
name        TEXT
age         INTEGER
city        TEXT
income      INTEGER
For example:

Result
total_income
------------
1800000


```sql
SELECT SUM(income) as total_income
from employee
where age>=40;
```

**Output:**
<img width="496" height="321" alt="Screenshot 2025-10-27 133726" src="https://github.com/user-attachments/assets/e07c4386-d701-4d5d-9570-9ac22f78474c" />



**Question 7**
---
Write the SQL query that accomplishes the selection of average price for each category from the "products" table and includes only those products where the average price falls between 10 and 15.

Sample table: products



For example:

Result
category_id  AVG(Price)
-----------  ----------
1            12.375


```sql
select category_id, AVG(Price)
from products
group by category_id
Having AVG(price) BETWEEN 10 and 15;
```

**Output:**
<img width="696" height="343" alt="Screenshot 2025-10-27 133732" src="https://github.com/user-attachments/assets/9b3e0dca-6351-442b-835a-08b45f232884" />



**Question 8**
---
Write the SQL query that accomplishes the grouping of data by joining date (jdate), calculates the minimum work hours for each date, and excludes dates where the minimum work hour is not less than 10.

Sample table: employee1



For example:

Result
jdate       MIN(workhour)
----------  -------------
2002.0      9
2004.0      9
2006.0      9

```sql
select jdate, MIN(workhour) 
from employee1
group by jdate HAVING
MIN(workhour) < 10;
```

**Output:**

<img width="692" height="431" alt="Screenshot 2025-10-27 133737" src="https://github.com/user-attachments/assets/34f3078a-5aed-4103-b1f7-976e4208c601" />


**Question 9**
---
Write an SQL query that groups the customer data into 5-year age intervals, calculates the minimum salary for each group, and excludes groups where the minimum salary is not less than 2000.

Table: customer1



For example:

Result
age_group   MIN(salary)
----------  -----------
25          1500

```sql
select (age/5) * 5 as age_group, MIN(salary)
from customer1
GROUP BY (age/5) * 5
HAVING MIN(salary) < 2000;

```

**Output:**

<img width="671" height="350" alt="Screenshot 2025-10-27 133743" src="https://github.com/user-attachments/assets/d70d2c85-0ba6-4690-b03e-4235096128ea" />



## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
