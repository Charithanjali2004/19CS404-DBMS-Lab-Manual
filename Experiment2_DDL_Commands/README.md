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
<img width="962" height="317" alt="image" src="https://github.com/user-attachments/assets/f2a6e685-e53f-4d15-82bc-371008d643cb" />

```sql
CREATE TABLE Departments(
DepartmentID INTEGER,
DepartmentName TEXT
);
```

**Output:**

<img width="1308" height="352" alt="image" src="https://github.com/user-attachments/assets/66d29347-5396-4482-b59f-8d1201361339" />

**Question 2**
---
<img width="1058" height="352" alt="image" src="https://github.com/user-attachments/assets/463461d8-0d65-4be5-9122-8b63230d2568" />

```sql
ALTER TABLE Student_details ADD COLUMN Date_of_birth Date;
```

**Output:**

<img width="1320" height="350" alt="image" src="https://github.com/user-attachments/assets/55ab1613-d856-4356-b375-3ab5e644885c" />

**Question 3**
---
<img width="932" height="306" alt="image" src="https://github.com/user-attachments/assets/37450041-66e2-4b57-8652-73c5c84cda3c" />

```sql
INSERT INTO Employee (EmployeeID, Name, Position, Department, Salary)
VALUES
(2, 'John Smith', 'Developer', 'IT', 75000),
(3, 'Anna Bell', 'Designer', 'Marketing', 68000);
```

**Output:**

<img width="1302" height="342" alt="image" src="https://github.com/user-attachments/assets/ef1138b1-2ba1-472d-b11b-4440b2189a8a" />

**Question 4**
---
<img width="1228" height="378" alt="image" src="https://github.com/user-attachments/assets/1af5633a-9c87-4968-8ace-f8dd20a19b83" />

```sql
CREATE TABLE products(
product_id INTEGER PRIMARY KEY,
product_name TEXT NOT NULL,
list_price DECIMAL(10,2) NOT NULL,
discount DECIMAL (10,2) DEFAULT 0 NOT NULL,
CHECK(list_price >= discount AND discount>=0 AND list_price>=0)
);
```

**Output:**

<img width="1297" height="292" alt="image" src="https://github.com/user-attachments/assets/02262bf7-50c0-44fc-b032-d81ca221f5d5" />

**Question 5**
---
<img width="1143" height="447" alt="image" src="https://github.com/user-attachments/assets/7bbfdd4e-efe0-4f60-b575-b8e5f7605c8b" />

```sql
ALTER TABLE customer ADD email VARCHAR(100);
```

**Output:**

<img width="1307" height="356" alt="image" src="https://github.com/user-attachments/assets/3ec86393-935a-48a6-af3e-3402f1cab92f" />

**Question 6**
---
<img width="1307" height="293" alt="image" src="https://github.com/user-attachments/assets/db5a34d4-ade6-4870-9a21-4bd00e45b8b7" />

```sql
CREATE TABLE contacts(
contact_id INTEGER PRIMARY KEY,
first_name TEXT NOT NULL,
last_name TEXT NOT NULL,
email TEXT,
phone TEXT NOT NULL CHECK(length(phone)>=10)
);
```

**Output:**

<img width="1357" height="295" alt="image" src="https://github.com/user-attachments/assets/6e827751-b48c-4b05-8937-94bd4bc1e9a7" />

**Question 7**
---
<img width="636" height="241" alt="image" src="https://github.com/user-attachments/assets/c9fe3b6b-cdb2-420b-926b-01160287f5c9" />

```sql
INSERT INTO Employee (EmployeeID, Name, Department, Salary)
SELECT EmployeeID, Name, Department, Salary
FROM Former_employees;
```

**Output:**

<img width="1362" height="288" alt="image" src="https://github.com/user-attachments/assets/cd96327e-000d-4402-9459-37e380b65068" />

**Question 8**
---
<img width="1250" height="277" alt="image" src="https://github.com/user-attachments/assets/25d7e080-9aab-4cf9-87c5-18cf3811867b" />

```sql
CREATE TABLE Shipments(
ShipmentID INTEGER PRIMARY KEY,
ShipmentDate INTEGER DATE,
SupplierID INTEGER,
OrderID INTEGER,
FOREIGN KEY(SupplierID) REFERENCES SupplierS(SupplierID),
FOREIGN KEY(OrderID) REFERENCES Orders(OrderID)
);
```

**Output:**

<img width="1320" height="276" alt="image" src="https://github.com/user-attachments/assets/5c1a9a1c-f3b1-4706-acec-24bcdd710a33" />

**Question 9**
---
<img width="1168" height="332" alt="image" src="https://github.com/user-attachments/assets/5fb8b9bf-11ee-4208-b981-97052046a83a" />

```sql
CREATE TABLE  Locations (
LocationID INTEGER,
LocationName TEXT,
Address TEXT
);
```

**Output:**

<img width="1290" height="387" alt="image" src="https://github.com/user-attachments/assets/334ae8ec-345b-4731-aa45-951a7db225b5" />

**Question 10**
---
<img width="1253" height="410" alt="image" src="https://github.com/user-attachments/assets/60234234-adc3-4b41-b5fd-5c0efac170fd" />

```sql
INSERT INTO Student_details (RollNo, Name, Gender, Subject, Marks)
SELECT RollNo, Name, Gender, Subject, Marks
FROM Archived_students;
```

**Output:**

<img width="1328" height="295" alt="image" src="https://github.com/user-attachments/assets/14e7e49e-a1e3-4912-84c6-20f6d322f101" />

## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
