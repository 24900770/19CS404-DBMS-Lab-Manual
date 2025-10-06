# Experiment 2: DDL Commands

## AIM
To study and implement DDL commands and different types of constraints.

## THEORY

### 1. CREATE
Used to create a new relation (table).

**Syntax:**
```sql
CREATE TABLE (
  field_1 data_type(size),
  field_2 data_type(size),
  ...
);
```
### 2. ALTER
Used to add, modify, drop, or rename fields in an existing relation.
(a) ADD
```sql
ALTER TABLE std ADD (Address CHAR(10));
```
(b) MODIFY
```sql
ALTER TABLE relation_name MODIFY (field_1 new_data_type(size));
```
(c) DROP
```sql
ALTER TABLE relation_name DROP COLUMN field_name;
```
(d) RENAME
```sql
ALTER TABLE relation_name RENAME COLUMN old_field_name TO new_field_name;
```
### 3. DROP TABLE
Used to permanently delete the structure and data of a table.
```sql
DROP TABLE relation_name;
```
### 4. RENAME
Used to rename an existing database object.
```sql
RENAME TABLE old_relation_name TO new_relation_name;
```
### CONSTRAINTS
Constraints are used to specify rules for the data in a table. If there is any violation between the constraint and the data action, the action is aborted by the constraint. It can be specified when the table is created (using CREATE TABLE) or after it is created (using ALTER TABLE).
### 1. NOT NULL
When a column is defined as NOT NULL, it becomes mandatory to enter a value in that column.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) NOT NULL
);
```
### 2. UNIQUE
Ensures that values in a column are unique.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) UNIQUE
);
```
### 3. CHECK
Specifies a condition that each row must satisfy.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) CHECK (logical_expression)
);
```
### 4. PRIMARY KEY
Used to uniquely identify each record in a table.
Properties:
Must contain unique values.
Cannot be null.
Should contain minimal fields.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) PRIMARY KEY
);
```
### 5. FOREIGN KEY
Used to reference the primary key of another table.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size),
  FOREIGN KEY (column_name) REFERENCES other_table(column)
);
```
### 6. DEFAULT
Used to insert a default value into a column if no value is specified.

Syntax:
```sql
CREATE TABLE Table_Name (
  col_name1 data_type,
  col_name2 data_type,
  col_name3 data_type DEFAULT 'default_value'
);
```

**Question 1**
--
Write an SQL query to add a new column email of type TEXT to the Student_details table, and ensure that this column cannot contain NULL values and make default value as 'Invalid'

For example:

Test	Result
INSERT INTO Student_details (RollNo, Name, Gender, Subject, email) 
VALUES (1, 'John Doe', 'M', 'Math', 'john@example.com');
select * from Student_details;
RollN  Name   Gen  Subject     email
-----  -----  ---  ----------  ----------------
1      John   M    Math        john@example.com

```sql
ALTER TABLE student_details
ADD COLUMN email TEXT NOT NULL DEFAULT 'Invalid';
```

**Output:**
<img width="1252" height="363" alt="Screenshot 2025-10-06 132037" src="https://github.com/user-attachments/assets/d8be2d7c-6c33-4376-88ff-4931d726644f" />



**Question 2**
---
Create a table named Employees with the following constraints:

EmployeeID should be the primary key.
FirstName and LastName should be NOT NULL.
Email should be unique.
Salary should be greater than 0.
DepartmentID should be a foreign key referencing the Departments table.

```sql
CREATE TABLE Employees (
EmployeeID INTEGER PRIMARY KEY, 
FirstName TEXT NOT NULL, 
LastName TEXT NOT NULL, 
Email TEXT UNIQUE,
Salary REAL CHECK(Salary > 0),
DepartmentID INTEGER,
FOREIGN KEY (DepartmentID) REFERENCES Departments(DepartmentID)
);
```

**Output:**
<img width="1228" height="535" alt="Screenshot 2025-10-06 132207" src="https://github.com/user-attachments/assets/ff25b905-0a8d-4c93-97eb-a1acc23a9412" />


**Question 3**

---
Write a SQL query for adding a new column named "email" with the datatype VARCHAR(100) to the  table "customer" 

Sample table: customer

 customer_id |   cust_name    |    city    | grade | salesman_id 
-------------+----------------+------------+-------+-------------
        3002 | Nick Rimando   | New York   |   100 |        5001
        3007 | Brad Davis     | New York   |   200 |        5001
        3005 | Graham Zusi    | California |   200 |        5002
 

For example:

Test	Result
pragma table_info('customer');
cid         name         type                               notnull     dflt_value  pk
----------  -----------  ---------------------------------  ----------  ----------  ----------
0           customer_id  integer primarykey auto increment  0                       0
1           cust_name    varchar2(30)                       0                       0
2           city         varchar(30)                        0                       0
3           grade        number                             0                       0
4           salesman_id  number                             0                       0
5           email        VARCHAR(100)  

```sql
ALTER TABLE customer
ADD COLUMN email VARCHAR(100);
```

**Output:**

<img width="862" height="392" alt="Screenshot 2025-10-06 132311" src="https://github.com/user-attachments/assets/d5f3cd92-a964-40f1-ae89-ccb42092d1e2" />


**Question 4**
---
Create a table named Shipments with the following constraints:
ShipmentID as INTEGER should be the primary key.
ShipmentDate as DATE.
SupplierID as INTEGER should be a foreign key referencing Suppliers(SupplierID).
OrderID as INTEGER should be a foreign key referencing Orders(OrderID).
For example:

Test	Result
INSERT INTO Shipments (ShipmentID, ShipmentDate, SupplierID, OrderID) VALUES (2, '2024-08-03', 99, 1);
Error: FOREIGN KEY constraint failed


```sql
CREATE TABLE Shipments(
ShipmentID INTEGER PRIMARY KEY,
ShipmentDate DATE,
SupplierID INTEGER,
OrderID INTEGER,
FOREIGN KEY (SupplierID) REFERENCES Suppliers(SupplierID),
FOREIGN KEY (OrderID) REFERENCES Orders(OrderID)
);
```

**Output:**

<img width="884" height="324" alt="Screenshot 2025-10-06 132351" src="https://github.com/user-attachments/assets/6655b3bc-3f34-473d-9192-eb13651f9024" />


**Question 5**
---
Insert all customers from Old_customers into Customers

Table attributes are CustomerID, Name, Address, Email

For example:

Test	Result
select * from Customers;
CustomerID  Name             Address         Email
----------  ---------------  --------------  ---------------------
301         Michael Johnson  123 Elm Street  michael.j@example.com
302         Sarah Lee        456 Oak Avenue  sarah.lee@example.com
303         David Wilson     789 Pine Road   david.w@example.com


```sql
Insert or IGNORE into
Customers (CustomerID, Name, Address, Email)
select CustomerID, Name, Address, Email from Old_customers;
```

**Output:**

<img width="845" height="362" alt="Screenshot 2025-10-06 132431" src="https://github.com/user-attachments/assets/553679e6-9b47-4cd1-82c8-7e557513f49c" />


**Question 6**
---
Create a table named Department with the following constraints:
DepartmentID as INTEGER should be the primary key.
DepartmentName as TEXT should be unique and not NULL.
Location as TEXT.
For example:

Test	Result
INSERT INTO Department (DepartmentID, DepartmentName, Location) VALUES (1, 'Human Resources', 'New York');
select * from Department;

```sql
create table Department(
DepartmentID PRIMARY KEY, DepartmentName TEXT UNIQUE NOT NULL,
Location TEXT 
);
```

**Output:**

<img width="857" height="355" alt="Screenshot 2025-10-06 132507" src="https://github.com/user-attachments/assets/16182ce4-d0b7-43aa-8d7e-7b79120a81ea" />


**Question 7**
---
Create a table named Invoices with the following constraints:

InvoiceID as INTEGER should be the primary key.
InvoiceDate as DATE.
DueDate as DATE should be greater than the InvoiceDate.
Amount as REAL should be greater than 0.
For example:

Test	Result
INSERT INTO Invoices (InvoiceID, InvoiceDate)
VALUES (1, '2024-08-08'),(1,'2024-09-08');
Error: UNIQUE constraint failed: Invoices.InvoiceID

```sql
create table Invoices(
InvoiceID PRIMARY KEY,
InvoiceDate DATE,
DueDate DATE check(DueDate > InvoiceDate),
Amount REAL check(Amount > 0)
);
```

**Output:**

<img width="853" height="355" alt="Screenshot 2025-10-06 132534" src="https://github.com/user-attachments/assets/c0a5a499-9465-461e-a4a5-6ecdc4f77be0" />


**Question 8**
---
In the Student_details table, insert a student record where some fields are NULL, another record where all fields are filled without any NULL values, and a third record where some fields are filled, and others are left as NULL.

RollNo      Name            Gender      Subject      MARKS
----------  ------------    ----------  ----------   ----------
205         Olivia Green    F
207         Liam Smith      M           Mathematics  85
208         Sophia Johnson  F           Science
For example:

Test	Result
select * from Student_details;
RollNo      Name          Gender      Subject     MARKS
----------  ------------  ----------  ----------  ----------
205         Olivia Green  F
207         Liam Smith    M           Mathematic  85
208         Sophia Johns  F           Science

```sql
insert into 
Student_details(RollNo, Name, Gender, Subject, MARKS) VALUES
(205, 'Olivia Green', 'F', '', ''),
(207, 'Liam Smith', 'M', 'Mathematic', '85'),
(208, 'Sophia Johns', 'F', 'Science', '');
```

**Output:**

<img width="866" height="374" alt="Screenshot 2025-10-06 132602" src="https://github.com/user-attachments/assets/b9de5287-b6f3-4979-a57a-a70b01373778" />


**Question 9**
---
Insert the below data into the Books table, allowing the Publisher and Year columns to take their default values.

ISBN             Title                 Author
---------------  --------------------  ---------------
978-6655443321   Big Data Analytics    Karen Adams

Note: The Publisher and Year columns will use their default values.
 
 
For example:

Test	Result
SELECT ISBN, Title, Author
FROM Books 


ISBN             Title                 Author
---------------  --------------------  ---------------
978-6655443321   Big Data Analytics    Karen Adams

```sql
Insert into
Books(ISBN, Title, Author) VALUES
('978-6655443321', 'Big Data Analytics', 'Karen Adams');
```

**Output:**

<img width="861" height="400" alt="Screenshot 2025-10-06 132622" src="https://github.com/user-attachments/assets/9fec4a12-1866-4223-9029-62e3f4252db6" />


**Question 10**
---
Create a table named Customers with the following columns:

CustomerID as INTEGER
Name as TEXT
Email as TEXT
JoinDate as DATETIME
For example:

Test	Result
pragma table_info('Customers');
cid         name        type        notnull     dflt_value  pk
----------  ----------  ----------  ----------  ----------  ----------
0           CustomerID  INTEGER     0                       0
1           Name        TEXT        0                       0
2           Email       TEXT        0                       0
3           JoinDate    DATETIME    0                       0


```sql
CREATE TABLE Customers(
CustomerID INTEGER,
Name TEXT,
Email TEXT,
JoinDate DATETIME
);
```

**Output:**

<img width="864" height="490" alt="Screenshot 2025-10-06 132650" src="https://github.com/user-attachments/assets/92a3a112-7b32-4de5-9acb-aa320536f7d9" />

## Screenshot of Module 1 SEB Completion Grades

<img width="1292" height="413" alt="image" src="https://github.com/user-attachments/assets/fd8a363d-e0b1-4ae8-8bfa-281b17d3eef9" />

## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
