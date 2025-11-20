# Experiment 5: Subqueries and Views
# NAME: THIRIVIKARAMAN
# REG NO: 212224060286
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
---
From the following tables, write a SQL query to find all the orders issued by the salesman 'Paul Adam'. Return ord_no, purch_amt, ord_date, customer_id and salesman_id.
```
salesman table

name             type
---------------  ---------------
salesman_id      numeric(5)
name                 varchar(30)
city                    varchar(15)
commission       decimal(5,2)

orders table

name             type
---------------  --------
order_no         int
purch_amt        real
order_date       text
customer_id      int
salesman_id      int
```
```sql
SELECT ord_no, purch_amt, ord_date, customer_id, salesman_id
FROM orders
WHERE salesman_id = (
    SELECT salesman_id
    FROM salesman
    WHERE name = 'Paul Adam'
);
```

**Output:**

<img width="1214" height="426" alt="image" src="https://github.com/user-attachments/assets/e6d86873-044d-44ba-aa83-dc664f649635" />

**Question 2**
---
Write a SQL query that retrieve all the columns from the table "Grades", where the grade is equal to the maximum grade achieved in each subject.
Sample table: GRADES (attributes: student_id, student_name, subject, grade)

```sql
SELECT student_id, student_name, subject, grade
FROM Grades g
WHERE grade = (
    SELECT MAX(grade)
    FROM Grades
    WHERE subject = g.subject
);

```

**Output:**

<img width="1213" height="478" alt="image" src="https://github.com/user-attachments/assets/10020402-72c2-4620-bf09-eabb010c695b" />


**Question 3**
---
Write a query to display all the customers whose ID is the difference between the salesperson ID of Mc Lyon and 2001.
```sql
SELECT customer_id, cust_name, city, grade, salesman_id
FROM customer
WHERE customer_id = (
    SELECT salesman_id - 2001
    FROM salesman
    WHERE name = 'Mc Lyon'
);

```

**Output:**

<img width="1215" height="347" alt="image" src="https://github.com/user-attachments/assets/125e22d9-543a-4cac-ba35-2965f190edb4" />


**Question 4**
---
Write a SQL query that retrieves the names of students and their corresponding grades, where the grade is equal to the minimum grade achieved in each subject.

Sample table: GRADES (attributes: student_id, student_name, subject, grade)

```sql
SELECT student_name, grade
FROM Grades g
WHERE grade = (
    SELECT MIN(grade)
    FROM Grades
    WHERE subject = g.subject
);

```

**Output:**

<img width="1074" height="456" alt="image" src="https://github.com/user-attachments/assets/3e6f0ec5-25d4-488b-8c2f-7bcc7a4fb113" />


**Question 5**
---
From the following tables, write a SQL query to find those salespeople who earned the maximum commission. Return ord_no, purch_amt, ord_date, and salesman_id.

```sql
SELECT o.ord_no, o.purch_amt, o.ord_date, o.salesman_id
FROM orders o
JOIN salesman s ON o.salesman_id = s.salesman_id
WHERE s.commission = (
    SELECT MAX(commission)
    FROM salesman
);

```

**Output:**

<img width="774" height="329" alt="image" src="https://github.com/user-attachments/assets/429a0954-ac11-4a93-984e-a9515455d15b" />


**Question 6**
---
From the following tables write a SQL query to find salespeople who had more than one customer. Return salesman_id and name.
```
salesman table

name                 type
---------------   ---------------
salesman_id       numeric(5)
name                  varchar(30)
city                     varchar(15)
commission       decimal(5,2)

customer table

name              type
-----------       ----------
customer_id   int
cust_name     text
city                text
grade            int
salesman_id  int
```
```sql
SELECT s.salesman_id, s.name
FROM salesman s
JOIN (
    SELECT salesman_id
    FROM customer
    GROUP BY salesman_id
    HAVING COUNT(*) > 1
) c ON s.salesman_id = c.salesman_id;

```

**Output:**

<img width="865" height="511" alt="image" src="https://github.com/user-attachments/assets/96ac023c-158e-4e17-be36-07d97e8fcb56" />


**Question 7**
---
Write a SQL query to List departments with names longer than the average length
Departments Table (attributes: department_id, department_name)

```sql
SELECT department_id, department_name
FROM Departments
WHERE LENGTH(department_name) > (
    SELECT AVG(LENGTH(department_name))
    FROM Departments
);

```

**Output:**

<img width="823" height="427" alt="image" src="https://github.com/user-attachments/assets/bcc9f2b4-7a57-4d32-aab4-da87cf416afc" />


**Question 8**
---
From the following tables, write a SQL query to find all orders generated by the salespeople who may work for customers whose id is 3007. Return ord_no, purch_amt, ord_date, customer_id, salesman_id.

```sql
SELECT ord_no, purch_amt, ord_date, customer_id, salesman_id
FROM orders
WHERE salesman_id = (
    SELECT salesman_id
    FROM orders
    WHERE customer_id = 3007
);

```

**Output:**

<img width="1216" height="476" alt="image" src="https://github.com/user-attachments/assets/51add59b-9b6f-43c8-9afe-324e0846a6e4" />


**Question 9**
---
Write a SQL query to Retrieve the medications with dosages equal to the lowest dosage
Table Name: Medications (attributes: medication_id, medication_name, dosage)

```sql
SELECT *
FROM Medications
WHERE dosage = (
    SELECT MIN(dosage)
    FROM Medications
);

```

**Output:**

<img width="895" height="315" alt="image" src="https://github.com/user-attachments/assets/f38dda81-ac38-41a9-9533-5b12ab792e59" />


**Question 10**
---
Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose AGE is LESS than $30

```sql
SELECT *
FROM CUSTOMERS
WHERE AGE < 30;
```

**Output:**

<img width="1217" height="644" alt="image" src="https://github.com/user-attachments/assets/75030149-7513-4fe7-90eb-6b4f712b789d" />


## RESULT
Thus, the SQL queries to implement subqueries and views have been executed successfully.
