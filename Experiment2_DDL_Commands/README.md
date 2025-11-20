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
-- Insert all students from Archived_students table into the Student_details table.

```sql
INSERT INTO Student_details(RollNo,Name,Gender,Subject,Marks)
SELECT RollNo,Name,Gender,Subject,MARKS
FROM Archived_students;
```

<img width="1117" height="304" alt="image" src="https://github.com/user-attachments/assets/36b0475c-6b3f-468f-9750-2e4e5dfdf27e" />



**Question 2**
---
-- Create a table named Invoices with the following constraints.

```sql
CREATE TABLE Invoices(
        InvoiceID INTEGER PRIMARY KEY,
        InvoiceDate DATE,
        DueDate DATE, 
        Amount REAL,
        CHECK (DueDate>InvoiceDate),
        CHECK (Amount>0)
);
```

**Output:**

<img width="1168" height="290" alt="image" src="https://github.com/user-attachments/assets/bb799e61-8bea-4126-baca-fc606bacf0db" />


**Question 3**
---
--  create a table named jobs including columns job_id, job_title, min_salary and max_salary, and make sure that, the default value for job_title is blank and min_salary is 8000 and max_salary is NULL will be entered automatically at the time of insertion if no value assigned for the specified columns.

```sql
CREATE TABLE jobs(
    job_id INT PRIMARY KEY,
    job_title VARCHAR(255) DEFAULT ' ',
    min_salary INT DEFAULT 8000,
    max_salary INT DEFAULT NULL
);
```

**Output:**
<img width="1174" height="342" alt="image" src="https://github.com/user-attachments/assets/c5cde6f3-b31b-4bb0-b2e7-23c56fc8563d" />


**Question 4**
---
-- Create a table named ProjectAssignments with the following constraints

```sql
CREATE TABLE ProjectAssignments(
    AssignmentID INTEGER PRIMARY KEY,
    EmployeeID INTEGER,
    ProjectID INTEGER,
    AssignmentDate DATE NOT NULL,
    FOREIGN KEY (EmployeeID) REFERENCES Employees(EmployeeID),
    FOREIGN KEY (ProjectID) REFERENCES Projects(ProjectID)
);
```

**Output:**
<img width="1150" height="294" alt="image" src="https://github.com/user-attachments/assets/50f63f4d-ca43-4ad6-abf7-8c16aef21083" />


**Question 5**
---
-- Insert a customer with CustomerID 301, Name Michael Jordan, Address 123 Maple St, City Chicago, and ZipCode 60616 into the Customers table.

```sql
INSERT INTO Customers(CustomerID,Name,Address,City,ZipCode) 
VALUES (301,'Michael Jordan','123 Maple St','Chicago','60616');
```

**Output:**

<img width="1140" height="246" alt="image" src="https://github.com/user-attachments/assets/20b7d4a6-cddf-4093-989f-8b404d83074b" />


**Question 6**
---
-- Create a table named Products with the following columns

```sql
CREATE TABLE Products(
    ProductID INTEGER,
    ProductName TEXT,
    Price REAL,
    Stock INTEGER
);
```

**Output:**
<img width="1149" height="317" alt="image" src="https://github.com/user-attachments/assets/448c0dd2-2cbd-4316-a22c-378262d418cd" />


**Question 7**
---
-- Insert the following products into the Products table


```sql
INSERT INTO Products(Name,Category,Price,Stock) VALUES('Smartphone','Electronics',800,150);
INSERT INTO Products(Name,Category,Price,Stock) VALUES('Headphones','Accessories',200,300);
```

**Output:**
<img width="1154" height="370" alt="image" src="https://github.com/user-attachments/assets/426e791d-7210-4dac-b0bc-071bbdc4c5ea" />


**Question 8**
---
-- Insert all customers from Old_customers into Customers. Table attributes are CustomerID, Name, Address, Email


```sql
INSERT INTO Customers(CustomerID,Name,Address,Email)
SELECT CustomerID,Name,Address,Email
FROM old_customers;
```

**Output:**
<img width="1157" height="289" alt="image" src="https://github.com/user-attachments/assets/92ce54f8-39e5-4780-b220-4698c1fc3258" />

**Question 9**
---
-- Write an SQL query to add two new columns, designation and net_salary, to the table Companies. The designation column should have a data type of varchar(50), and the net_salary column should have a data type of number.

```sql
ALTER TABLE Companies
ADD COLUMN designation varchar(50);
ALTER TABLE Companies
ADD COLUMN net_salary number;
```

**Output:**

<img width="1165" height="418" alt="image" src="https://github.com/user-attachments/assets/013d2e4a-e504-4569-9660-2e3817bc273b" />


**Question 10**
---
-- Write a SQL query to add a new column MobileNumber of type NUMBER and a new column Address of type VARCHAR(100) to the Student_details table.

```sql
ALTER TABLE Student_details
ADD COLUMN MobileNumber NUMBER;
ALTER TABLE Student_details
ADD COLUMN Address VARCHAR(100);
```

**Output:**

<img width="1155" height="407" alt="image" src="https://github.com/user-attachments/assets/72a3ff56-6e46-4eae-81d1-b04d39eb63ac" />



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
