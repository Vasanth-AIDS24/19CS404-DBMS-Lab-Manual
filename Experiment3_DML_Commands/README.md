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
Write a SQL statement to double the availability of the product with product_id 1. products table

product_id product_name category_id availability
```sql
update products
set availability = availability * 2
where product_id = 1;
```

**Output:**

<img width="817" height="156" alt="image" src="https://github.com/user-attachments/assets/27d3ed8e-f94f-4fe0-9d56-ff57996b69f5" />

**Question 2**
---
Write a SQL statement to Double the salary for employees in department 20 who have a job_id ending with 'MAN' Employees table


```sql
---------------
employee_id
first_name
last_name
email
phone_number
hire_date
job_id
salary
commission_pct
manager_id
department_id
```
```
update Employees 
set SALARY = SALARY * 2 
where job_id like "%MAN"
```

**Output:**

<img width="817" height="235" alt="image" src="https://github.com/user-attachments/assets/e338284e-8d3d-4b46-8aad-55ae029fb83c" />

**Question 3**
---
Write a SQL statement to Update the address to '58 Lakeview, Magnolia' where supplier ID is 5 in the suppliers table.


```sql
Suppliers Table
name               type
-----------------  ---------------
supplier_id        INT
supplier_name      VARCHAR(100)
contact_person     VARCHAR(100)
phone_number       VARCHAR(20)
email              VARCHAR(100)
address            VARCHAR(250)
```
```
update Suppliers
set address = '58 Lakeview, Magnolia'
where supplier_id=5
```
**Output:**

<img width="817" height="265" alt="image" src="https://github.com/user-attachments/assets/a76ef8e2-4ba8-4066-8a4b-baa4d23854b4" />

**Question 4**
---
Write a SQL statement to change the email column of employees table with 'Unavailable' for all employees in employees table.


```sql
Employees table
---------------
employee_id
first_name
last_name
email
phone_number
hire_date
job_id
salary
commission_pct
manager_id
department_id
```
```
update Employees 
set EMAIL = 'Unavailable'
```
**Output:**

<img width="812" height="312" alt="image" src="https://github.com/user-attachments/assets/a4ec3998-05d7-47b2-9bb9-fe29c2716ea5" />

**Question 5**
---
Decrease the reorder level by 30 percent where the product name contains 'cream' and quantity in stock is higher than reorder level in the products table.

```sql
name               type
-----------------  ---------------
product_id         INT
product_name       VARCHAR(100)
category           VARCHAR(50)
cost_price         DECIMAL(10,2)
sell_price         DECIMAL(10,2)
reorder_lvl        INT
quantity           INT
supplier_id        INT
```
```
UPDATE  PRODUCTS 
set reorder_lvl = reorder_lvl * 0.7
where product_name like '%cream%' and quantity > reorder_lvl;
```
**Output:**

<img width="817" height="332" alt="image" src="https://github.com/user-attachments/assets/a556a5c5-7d14-4535-acc6-70494b0b5a4f" />

**Question 6**
---
Write a SQL query to Delete customers from 'customer' table where 'CUST_CITY' is not 'New York' and 'OUTSTANDING_AMT' is greater than 5000.
```sql
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
|CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO     | AGENT_CODE |
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
| C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003       |
| C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008       |
| C00020    | Albert      | New York    | New York     | USA          |     3 |     5000.00 |     7000.00 |     6000.00 |       6000.00 |BBBBSBB      | A008
```
```
delete FROM Customer
where CUST_CITY <>'New York' and OUTSTANDING_AMT > 5000;
```
**Output:**

<img width="822" height="385" alt="image" src="https://github.com/user-attachments/assets/e4801c31-639d-4e51-b32e-e3054bc49c93" />

**Question 7**
---
Write a SQL query to Delete customers from 'customer' table where 'GRADE' is odd.


```sql
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
|CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO     | AGENT_CODE |
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
| C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003       |
| C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008       |
| C00020    | Albert      | New York    | New York     | USA          |     3 |     5000.00 |     7000.00 |     6000.00 |       6000.00 | BBBBSBB      | A008
```
```
delete from Customer
where grade%2=1;
```
**Output:**

<img width="817" height="287" alt="image" src="https://github.com/user-attachments/assets/8c8ace54-06ad-422f-8a9c-56aa1e4a798b" />

**Question 8**
---
Write a SQL query to Delete All Doctors with a NULL Specialization

Sample table: Doctors

attributes : doctor_id, first_name, last_name, specialization


```sql
delete from Doctors
where specialization is null;
```

**Output:**
<img width="812" height="627" alt="image" src="https://github.com/user-attachments/assets/2cf6618a-79a9-430f-a9ed-9cd17788c600" />


**Question 9**
---
Show the categoryName and description from the categories table sorted by categoryName.
```sql
name                     type
---------------       ---------------
CategoryID           INTEGER
CategoryName     VARCHAR(25)
Description          VARCHAR(255)
```
```
select CategoryName,Description from categories
order by CategoryName ASC;
```
**Output:**

<img width="813" height="331" alt="image" src="https://github.com/user-attachments/assets/c55e0a52-1727-421f-8de1-0b074d3154c9" />

**Question 10**
---
Write a SQL query to categorize value1 in the Calculations table as 'High' if it is greater than 50, otherwise 'Low'.


```sql
cid         name        type        notnull     dflt_value  pk
----------  ----------  ----------  ----------  ----------  ----------
0           id          INTEGER     0                       1
1           value1      REAL        0                       0
2           value2      REAL        0                       0
3           base        INTEGER     0                       0
4           exponent    INTEGER     0                       0
5           number      REAL        0                       0
6           decimal     REAL        0                       0
```
```
select id,value1,
    case
        when value1 > 50 then 'High'
        else 'Low'
    end as value_category
from Calculations;
```
**Output:**

<img width="778" height="247" alt="image" src="https://github.com/user-attachments/assets/36430074-e252-4a46-960c-d1b2241bb97c" />

## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
