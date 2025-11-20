# Experiment 4: Aggregate Functions, Group By and Having Clause

## NAME : THIRIVIKARAMAN P
## REG.NO.: 212224060286

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
How many appointments are scheduled for each patient?

```sql
select PatientID, COUNT(*) AS TotalAppointments
from Appointments group by PatientID;
```

**Output:**

<img width="726" height="700" alt="image" src="https://github.com/user-attachments/assets/6373b781-b18d-45ca-bdf9-e1628b6a7db5" />

**Question 2**
---
What is the most common diagnosis among patients?

```sql
select Diagnosis, COUNT(*) AS DiagnosisCount
from MedicalRecords
group by Diagnosis
order by DiagnosisCount DESC LIMIT 1;
```

**Output:**

<img width="853" height="378" alt="image" src="https://github.com/user-attachments/assets/c881f62b-3f36-4c1d-82d0-78500a182883" />

**Question 3**
---
Write a SQL query to find the total amount of fruits with a unit type of 'LB'.

```sql
select SUM(inventory) AS total 
from Fruits
where unit = 'LB';
```

**Output:**

<img width="597" height="377" alt="image" src="https://github.com/user-attachments/assets/7f8e3414-a4ec-4c5e-bc09-cd0795ebc3c3" />

**Question 4**
---
Write a SQL query to calculate the average purchase amount of all orders. Return average purchase amount.

```sql
select AVG(purch_amt) as 'AVERAGE'
from orders;
```

**Output:**

<img width="470" height="382" alt="image" src="https://github.com/user-attachments/assets/bd4182d8-5e53-4ccc-8264-3fedf252e433" />

**Question 5**
---
Write a SQL query to find the total number of unique cities in the customer table?

```sql
select COUNT(DISTINCT city) AS
unique_cities
from customer;
```

**Output:**

<img width="471" height="392" alt="image" src="https://github.com/user-attachments/assets/33a7e04b-642b-406d-baf4-dbf633dd00e8" />

**Question 6**
---
Write a SQL query to find the customer with longest name?

```sql
select name,LENGTH(name) as length
from customer order by length DESC limit 1
```

**Output:**

<img width="786" height="388" alt="image" src="https://github.com/user-attachments/assets/e7ef47e4-2ce3-4925-8128-6a8c996c3d7b" />

**Question 7**
---
Write the SQL query that accomplishes the grouping of data by joining date (jdate), calculates the total work hours for each date, and excludes dates where the total work hour sum is not greater than 40.

```sql
select jdate, SUM(workhour) 
from employee1
group by jdate
having SUM(workhour) > 40;
```

**Output:**

<img width="687" height="464" alt="image" src="https://github.com/user-attachments/assets/46927559-43ca-4c6e-9f52-b99a2843fbfa" />

**Question 8**
---
Write the SQL query that achieves the grouping of data by city, calculates the total income for each city, and includes only those cities where the total income sum is greater than 200,000.

```sql
select city, SUM(income ) AS Income
from employee
group by city
having SUM(income) > 200000;
```

**Output:**

<img width="654" height="598" alt="image" src="https://github.com/user-attachments/assets/dcdb32ac-5f72-460e-b314-d23bd3c8d771" />

**Question 9**
---
Write the SQL query that achieves the grouping of data by occupation, calculates the total work hours for each occupation, and excludes occupations where the total work hour sum is not greater than 20.

```sql
select occupation, SUM(workhour)
from employee1
group by occupation
having SUM(workhour) > 20;
```

**Output:**

<img width="705" height="531" alt="image" src="https://github.com/user-attachments/assets/3dc2037d-451e-445d-b4ed-bdc964362eab" />

**Question 10**
---
What is the count of male and female patients?

```sql
SELECT Gender , COUNT(*) as TotalPatients from Patients
Group by Gender;
```

**Output:**

<img width="916" height="524" alt="image" src="https://github.com/user-attachments/assets/bdcad170-c99f-44e3-9537-72ee823bd0a5" />


## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
