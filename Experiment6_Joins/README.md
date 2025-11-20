# Experiment 6: Joins
# NAME: THIRIVIKARAMAN P
# REG NO: 212224060286
## AIM
To study and implement different types of joins.

## THEORY

SQL Joins are used to combine records from two or more tables based on a related column.

### 1. INNER JOIN
Returns records with matching values in both tables.

**Syntax:**
```sql
SELECT columns
FROM table1
INNER JOIN table2
ON table1.column = table2.column;
```

### 2. LEFT JOIN
Returns all records from the left table, and matched records from the right.

**Syntax:**

```sql
SELECT columns
FROM table1
LEFT JOIN table2
ON table1.column = table2.column;
```
### 3. RIGHT JOIN
Returns all records from the right table, and matched records from the left.

**Syntax:**

```sql
SELECT columns
FROM table1
RIGHT JOIN table2
ON table1.column = table2.column;
```
### 4. FULL OUTER JOIN
Returns all records when there is a match in either left or right table.

**Syntax:**

```sql
SELECT columns
FROM table1
FULL OUTER JOIN table2
ON table1.column = table2.column;
```

**Question 1**
--
Write the SQL query that achieves the selection of all columns from the "patients" table (aliased as "p"), with an inner join on the "patient_id" column and conditions filtering for test results with the test names 'Blood Test' or 'Blood Pressure' and results not containing the substring 'Normal'.

PATIENTS TABLE:

ATTRIBUTES - patient_id, first_name, last_name, date_of_birth, admission_date, discharge_date, doctor_id

TEST_RESULT TABLES:

ATTRIBUTES - result_id, patient_id, test_name, result, test_date

```sql
SELECT
    p.*
FROM
    patients p
INNER JOIN
    test_results tr ON p.patient_id = tr.patient_id
WHERE
    tr.test_name IN ('Blood Test', 'Blood Pressure')
    AND tr.result NOT LIKE '%Normal%';
```

**Output:**

<img width="839" height="439" alt="image" src="https://github.com/user-attachments/assets/2ddf7d5e-dbf8-4024-82ca-ed82ae984abc" />


**Question 2**
---
Write the SQL query that achieves the selection of all columns from the "patients" table (aliased as "p"), with an inner join on the "patient_id" column and a condition filtering for test results with a test date between '2024-03-01' and '2024-03-31'.

PATIENTS TABLE:

ATTRIBUTES - patient_id, first_name, last_name, date_of_birth, admission_date, discharge_date, doctor_id
TEST_RESULT TABLES:

ATTRIBUTES - result_id, patient_id, test_name, result, test_date

```sql
SELECT
    p.*
FROM
    patients p
INNER JOIN
    test_results tr ON p.patient_id = tr.patient_id
WHERE
    tr.test_date BETWEEN '2024-03-01' AND '2024-03-31';
```

**Output:**

<img width="841" height="438" alt="image" src="https://github.com/user-attachments/assets/236883e4-4c94-4427-a3ba-e16c94443fac" />


**Question 3**
---
Write the SQL query that achieves the selection of all columns from the "customer" table (aliased as "c"), with a left join on the "salesman_id" column and a condition filtering for salesman with the name 'Mc Lyon'.

Customer Table: (customer_id, cust_name, city, grade, salesman_id)

Salesman Table: (salesman_id, name, city, commission)

```sql
SELECT c.*
FROM customer c
LEFT JOIN salesman s ON c.salesman_id = s.salesman_id
WHERE s.name = 'Mc Lyon';

```

**Output:**

<img width="843" height="441" alt="image" src="https://github.com/user-attachments/assets/15b51a59-7459-4667-a3bd-2ea8c0fabfe0" />


**Question 4**
---
Write an SQL query that retrieves all columns from the 'customer' table (using the alias 'c'), performs a LEFT JOIN with the 'orders' table on the 'customer_id' column, and includes only those orders with an order date after '2012-08-17'.

'customer' Table: (customer_id, cust_name, city, grade, salesman_id)

'orders' Table: (ord_no, purch_amt, ord_date, customer_id, salesman_id)

```sql
SELECT c.*
FROM customer c
LEFT JOIN orders o ON c.customer_id = o.customer_id
WHERE o.ord_date > '2012-08-17';

```

**Output:**

<img width="840" height="811" alt="image" src="https://github.com/user-attachments/assets/bb657122-fc4b-426c-9f93-697f8cde9e08" />


**Question 5**
---
 From the following tables write a SQL query to find salespeople who received commissions of more than 12 percent from the company. Return Customer Name, customer city, Salesman, commission.  

Sample table: customer
```sql
SELECT c.cust_name AS "Customer Name",
       c.city AS "city",
       s.name AS "Salesman",
       s.commission AS "commission"
FROM customer c
JOIN salesman s ON c.salesman_id = s.salesman_id
WHERE s.commission > 0.12;

```

**Output:**

<img width="836" height="831" alt="image" src="https://github.com/user-attachments/assets/875c3aaf-5c15-49df-83b5-74122abd5f0e" />


**Question 6**
---
write a SQL query to find the salesperson and customer who reside in the same city. Return Salesman, cust_name and city.

```sql
SELECT
    s.name AS Salesman,
    c.cust_name,
    s.city
FROM
    salesman s
INNER JOIN
    customer c ON s.city = c.city;
```


**Output:**

<img width="845" height="740" alt="image" src="https://github.com/user-attachments/assets/0c5e2dbc-0594-4355-b2d8-135eb01a3a9f" />


**Question 7**
---
From the following tables write a SQL query to find those customers with a grade less than 300. Return cust_name, customer city, grade, Salesman, salesmancity. The result should be ordered by ascending customer_id. 

```sql
SELECT c.cust_name,
       c.city,
       c.grade,
       s.name AS Salesman,
       s.city AS city
FROM customer c
JOIN salesman s ON c.salesman_id = s.salesman_id
WHERE c.grade < 300
ORDER BY c.customer_id ASC;

```

**Output:**

<img width="840" height="714" alt="image" src="https://github.com/user-attachments/assets/3740a547-dc2c-4b33-8f1a-bcdd43583ca9" />


**Question 8**
---
From the following tables write a SQL query to find the salesperson(s) and the customer(s) he represents. Return Customer Name, city, Salesman, commission.

```sql
SELECT c.cust_name AS "Customer Name",
       c.city,
       s.name AS "Salesman",
       s.commission
FROM customer c
JOIN salesman s ON c.salesman_id = s.salesman_id;

```

**Output:**

<img width="831" height="778" alt="image" src="https://github.com/user-attachments/assets/796924a2-33a6-4b0b-b34c-6441ad685f8d" />


**Question 9**
---
Write a SQL statement to join the tables salesman, customer and orders so that the same column of each table appears once and only the relational rows are returned.

```sql
SELECT o.ord_no,
       o.purch_amt,
       o.ord_date,
       c.cust_name,
       c.city AS customer_city,
       c.grade,
       s.name AS salesman_name,
       s.city AS salesman_city,
       s.commission
FROM orders o
JOIN customer c ON o.customer_id = c.customer_id
JOIN salesman s ON o.salesman_id = s.salesman_id;

```

**Output:**

<img width="844" height="823" alt="image" src="https://github.com/user-attachments/assets/f91c54d6-5a1f-4a18-aa85-af355303ccab" />


**Question 10**
---
Write the SQL query that achieves the selection of the first name from the "patients" table (aliased as "patient_name") and the first name from the "doctors" table (aliased as "doctor_name"), with an inner join on the "doctor_id" column and a condition filtering for patients with a date of birth after '1990-01-01'.

```sql
SELECT p.first_name AS patient_name,
       d.first_name AS doctor_name
FROM patients p
INNER JOIN doctors d ON p.doctor_id = d.doctor_id
WHERE p.date_of_birth > '1990-01-01';

```

**Output:**

<img width="848" height="420" alt="image" src="https://github.com/user-attachments/assets/458c600f-723d-45a1-be7c-1893afaa04a4" />


## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
