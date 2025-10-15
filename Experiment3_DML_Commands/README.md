# Experiment 3: DML Commands

## AIM
To study and implement DML (Data Manipulation Language) commands.

## THEORY

### 1. INSERT INTO
Used to add records into a relation.
These are three type of INSERT INTO queries which are as
A)Inserting a single record
**Syntax (Single Row):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES (value_1, value_2, ...);
```
**Syntax (Multiple Rows):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES
(value_1, value_2, ...),
(value_3, value_4, ...);
```
**Syntax (Insert from another table):**
```sql
INSERT INTO table_name SELECT * FROM other_table WHERE condition;
```
### 2. UPDATE
Used to modify records in a relation.
Syntax:
```sql
UPDATE table_name SET column1 = value1, column2 = value2 WHERE condition;
```
### 3. DELETE
Used to delete records from a relation.
**Syntax (All rows):**
```sql
DELETE FROM table_name;
```
**Syntax (Specific condition):**
```sql
DELETE FROM table_name WHERE condition;
```
### 4. SELECT
Used to retrieve records from a table.
**Syntax:**
```sql
SELECT column1, column2 FROM table_name WHERE condition;
```
**Question 1**
--
Write a SQL statement to Update the per_unit_price to 25 and total_price accordingly in purchases table where purchase_date is '2022-08-15' and product_id is 12.



```sql
update purchases
set per_unit_price = 25, 
total_price = quantity*25
where purchase_date = '2022-08-15'
and product_id = 12;
```

**Output:**
<img width="1180" height="530" alt="Screenshot 2025-10-15 102703" src="https://github.com/user-attachments/assets/66651fc8-2a79-4215-89f5-e12d0f464aec" />



**Question 2**
---
Update the reorder level to 40 pieces for all products belonging to the 'Grocery' category in the products table.




```sql
update products
set reorder_lvl = 40
where category = 'Grocery';
```

**Output:**

<img width="1188" height="401" alt="Screenshot 2025-10-15 102713" src="https://github.com/user-attachments/assets/c090f713-acc8-47ae-8369-ecaab53a5d89" />


**Question 3**
---
Write a SQL statement to change the first_name column of employees table with 'John' for those employees whose department_id is 80 and gets a commission_pct below 0.35.



```sqlupdate employees
set first_name = 'John'
where department_id = 80 and commission_pct < 0.35;
```

**Output:**
<img width="1190" height="541" alt="Screenshot 2025-10-15 102726" src="https://github.com/user-attachments/assets/5a0e53b0-6930-4362-9750-b0702ece8be2" />



**Question 4**
---
Write a SQL statement to Change the supplier name to 'A1 Suppliers' where the supplier ID is 8 in the suppliers table.

Table info

suppliers(supplier_id,supplier_name,contact_person,phone_number,email,address)




```sql
UPDATE suppliers
set supplier_name = 'A1 Suppliers'
WHERE supplier_id = 8;
```

**Output:**

<img width="1185" height="409" alt="Screenshot 2025-10-15 102736" src="https://github.com/user-attachments/assets/177a0554-e2d9-4d6b-b1eb-7ebd32c619e4" />


**Question 5**
---
Write a SQL query to Delete All Doctors with a NULL Specialization


```sql
delete from doctors
where specialization IS NULL;
```

**Output:**

<img width="1183" height="953" alt="Screenshot 2025-10-15 102749" src="https://github.com/user-attachments/assets/358e799a-24c7-485a-9bbb-49045e1bdbc6" />


**Question 6**
---
Write a SQL query to Delete customers with following conditions

'CUST_COUNTRY' is not in a list of specified countries ('UK', 'USA', 'Canada')
'GRADE' is greater than or equal to 3


```sql
delete from Customer
where CUST_COUNTRY NOT IN ('UK', 'USA', 'Canada') AND GRADE >= 3;
```

**Output:**

<img width="1206" height="431" alt="Screenshot 2025-10-15 102804" src="https://github.com/user-attachments/assets/86a53594-8aee-4348-8f0e-d29c63cf9382" />


**Question 7**
---
Write a SQL query to Delete customers from 'customer' table where 'OPENING_AMT' is between 4000 and 6000.


```sql
delete from customer
where "OPENING_AMT" BETWEEN 4000 AND 6000;
```

**Output:**

<img width="1184" height="600" alt="Screenshot 2025-10-15 102817" src="https://github.com/user-attachments/assets/13971112-bfac-4d54-8eb2-b2b0e0ab4e1b" />


**Question 8**
---
Write a SQL query to remove rows from the table 'customer' with the following condition -

1. 'cust_country' must be 'India',

2. 'cus_city' must not be 'Chennai',





```sql
DELETE FROM customer
where cust_country = 'India' and cust_city != 'Chennai';
```

**Output:**

<img width="1180" height="876" alt="Screenshot 2025-10-15 102829" src="https://github.com/user-attachments/assets/7153b87a-55ef-437b-969a-acc75e598e4a" />


**Question 9**
---
Write a SQL query to Delete customers from 'customer' table where 'CUST_COUNTRY' is neither 'India' nor 'USA'.



```sql
delete FROM customer 
where CUST_COUNTRY NOT IN ('India', 'USA');
```

**Output:**

<img width="1190" height="544" alt="Screenshot 2025-10-15 102842" src="https://github.com/user-attachments/assets/83f4d36a-9e2b-4c92-9b00-69d82b354159" />


**Question 10**
---
Write a SQL statement to Display the order number, orderdate and the purchase amount of
orders table which will be delivered by the salesman with ID 5001.



```sql
SELECT order_no, order_date, purch_amt from orders where salesman_id = 5001;
```

**Output:**

<img width="852" height="381" alt="Screenshot 2025-10-15 102849" src="https://github.com/user-attachments/assets/f0d6f6af-011a-4aad-956c-d850f7aa216d" />


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
