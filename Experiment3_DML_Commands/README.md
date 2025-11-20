# Experiment 3: DML Commands

## NAME : THIRIVIKARAMAN P
## Reg.No. : 212224060286

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
Write a SQL statement to Update the grade of all customers in Chennai city as  5. 

```sql
update customer 
set grade=5
where city='Chennai';
```

**Output:**

<img width="1251" height="428" alt="image" src="https://github.com/user-attachments/assets/b22e6287-c2df-480b-b884-1dc29e0bdd59" />

**Question 2**
---
Write a SQL statement to Update the per_unit_price to 25 and total_price accordingly in purchases table where purchase_date is '2022-08-15' and product_id is 12.

```sql
update purchases
set per_unit_price=25, total_price=25*quantity
where purchase_date='2022-08-15' and product_id=12;
```

**Output:**

<img width="1262" height="453" alt="image" src="https://github.com/user-attachments/assets/aa4755f6-54e6-4e26-9f0b-76819f06c639" />

**Question 3**
---
Write a SQL query to Delete customers from 'customer' table where 'GRADE' is not equal to 3.

```sql
delete from customer
where GRADE not in(3);
```

**Output:**

<img width="857" height="621" alt="image" src="https://github.com/user-attachments/assets/d889d6a9-e2ef-4e84-9733-9cb01e470ec3" />

**Question 4**
---
Write a SQL query to Delete a Specific Surgery which was made on 28th Feb 2024.

```sql
delete from surgeries
where surgery_date = '2024-02-28';
```

**Output:**

<img width="1204" height="400" alt="image" src="https://github.com/user-attachments/assets/22cce069-b599-4941-850f-d289530992bd" />

**Question 5**
---
Write a SQL query to Delete All Doctors with a NULL Specialization

```sql
delete from doctors
where specialization is null;
```

**Output:**

<img width="1052" height="866" alt="image" src="https://github.com/user-attachments/assets/be531f28-9fd3-40e6-b2eb-22d8903e73ce" />

**Question 6**
---
Write a SQL query to Delete customers from 'customer' table where 'GRADE' is greater than or equal to 2.

```sql
delete from Customer
where Grade >=2;
```

**Output:**

<img width="571" height="508" alt="image" src="https://github.com/user-attachments/assets/26604053-4f23-4980-bf4c-532b9f3ede36" />

**Question 7**
---
Write a SQL query to label rows in the Calculations table as 'Even' if value1 is even, otherwise 'Odd'.

```sql
select id,value1,
    CASE
        WHEN CAST(value1 AS
        INTEGER) % 2=0 THEN 'Even'
        ELSE 'Odd'
    END AS parity
FROM calculations;
```

**Output:**

<img width="642" height="444" alt="image" src="https://github.com/user-attachments/assets/40401596-b58f-4d53-8340-30d650612fd0" />

**Question 8**
---
Write a SQL query to find the details of those salespeople who live in cities other than Paris and Rome. Return salesman_id, name, city, commission.

```sql
select salesman_id,name,city,commission from salesman
where city NOT IN ('Paris','Rome');
```

**Output:**

<img width="843" height="372" alt="image" src="https://github.com/user-attachments/assets/6adf44ce-767e-41c2-ad0a-6a0829bb1a12" />

**Question 9**
---
write a SQL query to find customers who are either from the city 'New York' or who do not have a grade greater than 100. Return customer_id, cust_name, city, grade, and salesman_id.

```sql
select customer_id,cust_name,city ,grade,salesman_id from customer
where city='New York' OR grade<=100;
```

**Output:**

<img width="1043" height="383" alt="image" src="https://github.com/user-attachments/assets/92303469-9d44-4839-afad-f9450d47a5e3" />

**Question 10**
---
Write a SQL query to calculate the discounted price for products whose original price is between $50 and $150. Return product_id, original_price, discount_percentage, and discounted_price.

```sql
select product_id,original_price,discount_percentage,
(original_price - (original_price * discount_percentage)) AS discounted_price
from products
where original_price BETWEEN 50 AND 150;
```

**Output:**

<img width="1090" height="269" alt="image" src="https://github.com/user-attachments/assets/9d2af8cc-f3ed-4004-b16e-b5a6f1fecf56" />

## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
