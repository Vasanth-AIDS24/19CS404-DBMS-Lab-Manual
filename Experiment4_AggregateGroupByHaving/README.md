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
--
What is the average dosage prescribed for each medication?

Sample tablePrescriptions Table
```sql
Medication     AvgDosage
-------------  ----------
Ciprofloxacin  500.0
Doxorubicin    60.0
Ibuprofen      400.0
Levothyroxine  50.0
Lisinopril     10.0
MMR            0.5
Pending        0.0
Prenatal vita  1.0
Sertraline     50.0
Topiramate     25.0
```
```
SELECT
  Medication,
  AVG(Dosage) AS AvgDosage
FROM
  Prescriptions
GROUP BY
  Medication;
```

**Output:**
<img width="695" height="742" alt="image" src="https://github.com/user-attachments/assets/e15a6f86-13ee-4ae6-9b3e-e4bc6b44a3c1" />


**Question 2**
---
How many patients are there in each city?


```sql
Address     TotalPatients
----------  -------------
Berlin      3
Chicago     4
Mexico      3
```
```
select Address,count(*)
as TotalPatients
from Patients
group by Address
```
**Output:**

<img width="658" height="392" alt="image" src="https://github.com/user-attachments/assets/16f732f5-da46-40b3-ba15-262734e0fdb1" />

**Question 3**
---
Write a SQL Query to find how many medications are prescribed for each patient?


```sql

PatientID   AvgMedications
----------  --------------
4           5
6           1
7           1
8           3
```
```
SELECT PatientID,COUNT(*) AS 
AvgMedications
FROM MedicalRecords
GROUP BY PatientID;
```
**Output:**

<img width="677" height="612" alt="image" src="https://github.com/user-attachments/assets/73d165e3-12ec-4852-ad77-58aca5fd61af" />

**Question 4**
---
Write a SQL query to find the maximum purchase amount.

Sample table: orders
```sql
-- Paste your SQL code below for Question 4
```

**Output:**

![Output4](output.png)

**Question 5**
---
Write a SQL query to find the total income of employees aged 40 or above.

```sql

name        type
----------  ----------
id          INTEGER
name        TEXT
age         INTEGER
city        TEXT
income      INTEGER```
```
```
SELECT
  SUM(income) AS total_income
FROM
  employee
WHERE
  age >= 40;
```
**Output:**

<img width="437" height="311" alt="image" src="https://github.com/user-attachments/assets/40272f30-d039-43c7-9934-dc85f1aff4c2" />

**Question 6**
---
Write a SQL query to find the number of employees whose age is greater than 32.


Table: employee
```sql
SELECT
  COUNT(*) AS COUNT
FROM
  employee
WHERE
  age > 32;
```

**Output:**
<img width="435" height="316" alt="image" src="https://github.com/user-attachments/assets/3e321c5c-eabd-463d-a804-dfa9912a619d" />


**Question 7**
---
Write a SQL query to find the average length of names for people living in Chennai?



```sql
name        type
----------  ----------
id          INTEGER
name        TEXT   
city        TEXT
email       TEXT
phone       INTEGER
```
```
SELECT
  AVG(LENGTH(name)) AS avg_name_length
FROM
  customer
WHERE
  city = 'Chennai';
```
**Output:**

<img width="438" height="295" alt="image" src="https://github.com/user-attachments/assets/8c98e110-818e-4e04-bd43-f9556fa20096" />

**Question 8**
---
Write the SQL query that accomplishes the grouping of data by joining date (jdate), calculates the maximum work hours for each date, and excludes dates where the maximum work hour is not greater than 12.

Sample table: employee1


```sql
jdate       MAX(workhour)
----------  -------------
2004.0      15
2006.0      15
```
```
SELECT
  jdate,
  MAX(workhour) AS "MAX(workhour)"
FROM
  employee1
GROUP BY
  jdate
HAVING
  MAX(workhour) > 12;
```
**Output:**

<img width="670" height="377" alt="image" src="https://github.com/user-attachments/assets/5d5c79bd-a447-469c-aa95-9ebc59993ba4" />

**Question 9**
---
Write the SQL query that achieves the grouping of data by occupation, calculates the total work hours for each occupation, and excludes occupations where the total work hour sum is not greater than 20.

Sample table: employee1
```sql
occupation  SUM(workhour)
----------  -------------
Business    30
Doctor      30
Engineer    24
Teacher     27
```
```
SELECT
  occupation,
  SUM(workhour) AS "SUM(workhour)"
FROM
  employee1
GROUP BY
  occupation
HAVING
  SUM(workhour) > 20;
```
**Output:**

<img width="616" height="437" alt="image" src="https://github.com/user-attachments/assets/0449b4b8-ebe2-4424-aed2-a0c7900ecdba" />

**Question 10**
---
Write the SQL query that achieves the grouping of data by occupation, calculates the average work hours for each occupation, and includes only those occupations where the average work hour falls between 10 and 12.

Sample table: employee1
```sql
Result
occupation  AVG(workhour)
----------  -------------
Business    10.0
Engineer    12.0
```
```
SELECT
  occupation,
  AVG(workhour) AS "AVG(workhour)"
FROM
  employee1
GROUP BY
  occupation
HAVING
  AVG(workhour) BETWEEN 10 AND 12;
```
**Output:**
<img width="753" height="387" alt="image" src="https://github.com/user-attachments/assets/bb5d79fc-5246-4eb3-9084-e55bfe69d02e" />



## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
