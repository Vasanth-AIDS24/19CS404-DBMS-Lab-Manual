# Experiment 5: Subqueries and Views

## AIM
To study and implement subqueries and views.

## THEORY

### Subqueries
A subquery is a query inside another SQL query and is embedded in:
- WHERE clause
- HAVING clause
- FROM clause

**Types:**
- **Single-row subquery**:
  Sub queries can also return more than one value. Such results should be made use along with the operators in and any.
- **Multiple-row subquery**:
  Here more than one subquery is used. These multiple sub queries are combined by means of ‘and’ & ‘or’ keywords.
- **Correlated subquery**:
  A subquery is evaluated once for the entire parent statement whereas a correlated Sub query is evaluated once per row processed by the parent statement.

**Example:**
```sql
SELECT * FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees);
```
### Views
A view is a virtual table based on the result of an SQL SELECT query.
**Create View:**
```sql
CREATE VIEW view_name AS
SELECT column1, column2 FROM table_name WHERE condition;
```
**Drop View:**
```sql
DROP VIEW view_name;
```

**Question 1**
--
Write a SQL query that retrieve all the columns from the table "Grades", where the grade is equal to the maximum grade achieved in each subject. Sample table: GRADES (attributes: student_id, student_name, subject, grade)
```sql
SELECT *
FROM GRADES g
WHERE grade = (
    SELECT MAX(grade)
    FROM GRADES
    WHERE subject = g.subject
);

```

**Output:**

<img width="813" height="237" alt="image" src="https://github.com/user-attachments/assets/9803024f-905c-43b9-923f-eb9d4b881f51" />

**Question 2**
---
Write a SQL query to Identify customers whose city is different from the city of the customer with the highest ID

SAMPLE TABLE: customer
```sql
name             type
---------------  ---------------
id               INTEGER
name             TEXT
city             TEXT
email            TEXT
phone            INTEGER
```
```
SELECT *
FROM customer
WHERE city <> (
    SELECT city
    FROM customer
    WHERE id = (SELECT MAX(id) FROM customer)
);
```
**Output:**

<img width="811" height="267" alt="image" src="https://github.com/user-attachments/assets/5bd207f7-b47b-4dab-b1f0-954debdfb4c7" />

**Question 3**
---
Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose salary is LESS than $2500.

Sample table: CUSTOMERS
```sql
ID          NAME        AGE         ADDRESS     SALARY
----------  ----------  ----------  ----------  ----------

1          Ramesh     32              Ahmedabad     2000
2          Khilan        25              Delhi                 1500
3          Kaushik      23              Kota                  2000
4          Chaitali       25             Mumbai            6500
5          Hardik        27              Bhopal              8500
6          Komal         22              Hyderabad       4500

7           Muffy          24              Indore            10000
```
```
SELECT *
FROM CUSTOMERS
WHERE SALARY < 2500;

```
**Output:**

<img width="810" height="284" alt="image" src="https://github.com/user-attachments/assets/21de604e-1209-4049-b702-d2be68a54da5" />

**Question 4**
---
From the following tables write a SQL query to count the number of customers with grades above the average in New York City. Return grade and count.

customer table
```sql
name         type
-----------  ----------
customer_id  int
cust_name    text
city         text
grade        int
salesman_id  int
```
```
SELECT grade, COUNT(*)
FROM customer
WHERE  grade > (SELECT AVG(grade) FROM customer WHERE city = 'New York')
GROUP BY grade;

```

**Output:**

<img width="610" height="321" alt="image" src="https://github.com/user-attachments/assets/20c54110-857c-406d-aa46-f7a53d35a126" />

**Question 5**
---
Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose Address as Delhi

Sample table: CUSTOMERS
```sql
ID          NAME        AGE         ADDRESS     SALARY
----------  ----------  ----------  ----------  ----------

1          Ramesh     32              Ahmedabad     2000
2          Khilan        25              Delhi                 1500
3          Kaushik      23              Kota                  2000
4          Chaitali       25             Mumbai            6500
5          Hardik        27              Bhopal              8500
6          Komal         22              Hyderabad       4500

7           Muffy          24              Indore            10000
```
```
SELECT *
FROM CUSTOMERS
WHERE ADDRESS = 'Delhi';
```
**Output:**

<img width="814" height="204" alt="image" src="https://github.com/user-attachments/assets/670fc2f2-8698-4d85-9c16-b3bf4c9fbb1f" />

**Question 6**
---
From the following tables write a SQL query to find the order values greater than the average order value of 10th October 2012. Return ord_no, purch_amt, ord_date, customer_id, salesman_id.

Note: date should be yyyy-mm-dd format

ORDERS TABLE
```sql
name            type
----------     ----------
ord_no          int
purch_amt    real
ord_date       text
customer_id  int
salesman_id  int
```
```
SELECT ord_no, purch_amt, ord_date, customer_id, salesman_id
FROM ORDERS
WHERE purch_amt > (
    SELECT AVG(purch_amt)
    FROM ORDERS
    WHERE ord_date = '2012-10-10'
);
```
**Output:**

<img width="814" height="282" alt="image" src="https://github.com/user-attachments/assets/27111a2c-6964-4888-9a10-c349db166105" />

**Question 7**
---
From the following tables write a SQL query to find all orders generated by New York-based salespeople. Return ord_no, purch_amt, ord_date, customer_id, salesman_id.

salesman table
```sql
name             type
---------------  ---------------
salesman_id      numeric(5)
name                 varchar(30)
city                    varchar(15)
commission       decimal(5,2)
```
```
orders table

name             type
---------------  --------
order_no         int
purch_amt        real
order_date       text
customer_id      int
salesman_id      int
```
```
SELECT o.ord_no, o.purch_amt, o.ord_date, o.customer_id, o.salesman_id
FROM orders o
JOIN salesman s ON o.salesman_id = s.salesman_id
WHERE s.city = 'New York';

```
**Output:**

<img width="819" height="289" alt="image" src="https://github.com/user-attachments/assets/5986ccd9-069a-401d-839f-b25349a76ab7" />

**Question 8**
---
From the following tables, write a SQL query to find those salespeople who earned the maximum commission. Return ord_no, purch_amt, ord_date, and salesman_id.

salesman table
```sql
name             type
---------------  ---------------
salesman_id      numeric(5)
name                 varchar(30)
city                    varchar(15)
commission       decimal(5,2)
```
```
name             type
---------------  --------
order_no         int
purch_amt        real
order_date       text
customer_id      int
salesman_id      int
```
```
SELECT o.ord_no, o.purch_amt, o.ord_date, o.salesman_id
FROM orders o
JOIN salesman s ON o.salesman_id = s.salesman_id
WHERE s.commission = (
    SELECT MAX(commission)
    FROM salesman
);
```

**Output:**
<img width="810" height="349" alt="image" src="https://github.com/user-attachments/assets/2a2e530c-5422-4f36-8e03-98bbca6b1f97" />


**Question 9**
---
From the following tables, write a SQL query to find all the orders generated in New York city. Return ord_no, purch_amt, ord_date, customer_id and salesman_id.

SALESMAN TABLE
```sql
name               type
-----------        ----------
salesman_id  numeric(5)
name             varchar(30)
city                 varchar(15)
commission   decimal(5,2)
```
```
orders table

name            type
----------      ----------
ord_no          int
purch_amt    real
ord_date       text
customer_id  int
salesman_id  int
```
```
SELECT o.ord_no, o.purch_amt, o.ord_date, o.customer_id, o.salesman_id
FROM orders o
JOIN salesman s ON o.salesman_id = s.salesman_id
WHERE s.city = 'New York';
```
**Output:**

<img width="814" height="309" alt="image" src="https://github.com/user-attachments/assets/4cafbdaf-88dd-41a7-b63e-f239d4d1df47" />

**Question 10**
---
Write a SQL query that retrieves the all the columns from the Table Grades, where the grade is equal to the minimum grade achieved in each subject.

Sample table: GRADES (attributes: student_id, student_name, subject, grade)
```sql
SELECT student_id, student_name, subject, grade
FROM Grades g
WHERE grade = (
    SELECT MIN(grade)
    FROM Grades
    WHERE subject = g.subject
);
```

**Output:**

<img width="816" height="246" alt="image" src="https://github.com/user-attachments/assets/ce16ac28-d095-4489-89d0-661a7483ee5d" />


## RESULT
Thus, the SQL queries to implement subqueries and views have been executed successfully.
