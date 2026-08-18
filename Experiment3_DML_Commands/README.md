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
<img width="1168" height="290" alt="image" src="https://github.com/user-attachments/assets/a00283da-5274-4481-b565-e76938929344" />

```sql
SELECT * FROM customer WHERE cust_name LIKE '%n';
```

**Output:**

<img width="1282" height="381" alt="image" src="https://github.com/user-attachments/assets/73ecd5a9-6de8-4c58-8bb0-ba08f82d2e61" />

**Question 2**
---
<img width="1237" height="448" alt="image" src="https://github.com/user-attachments/assets/30fe27df-8995-4e8f-9e75-9d6cf9259084" />

```sql
UPDATE products
SET sell_price = sell_price * 1.15
WHERE quantity < 50 And supplier_id = 10;
```

**Output:**

<img width="1323" height="486" alt="image" src="https://github.com/user-attachments/assets/761f3bbf-e6f3-4b86-8f4c-64c2ccf01a71" />

**Question 3**
---
<img width="1212" height="550" alt="image" src="https://github.com/user-attachments/assets/3b625eca-48ab-46e7-98e3-7b1c1fdede32" />

```sql
SELECT NAME, CITY
FROM salesman
WHERE CITY IN ('London', 'Rome');
```

**Output:**

<img width="1133" height="366" alt="image" src="https://github.com/user-attachments/assets/80a38093-5b4b-48e9-a1d1-a9877d25c5f5" />

**Question 4**
---
<img width="1313" height="445" alt="image" src="https://github.com/user-attachments/assets/c7619988-c1d5-4199-b69c-127b7f41039e" />

```sql
DELETE FROM Customer
WHERE CUST_COUNTRY NOT IN ('UK', 'USA', 'Canada')
AND GRADE >= 3;
```

**Output:**

<img width="1298" height="426" alt="image" src="https://github.com/user-attachments/assets/669dc651-4454-4970-9032-628b999a09eb" />

**Question 5**
---
<img width="1336" height="392" alt="image" src="https://github.com/user-attachments/assets/508855b9-20fa-4971-893c-daf667e1acc5" />

```sql
DELETE FROM Customer
WHERE CUST_COUNTRY = 'UK'
AND WORKING_AREA = 'London'
AND GRADE < 3;
```

**Output:**

<img width="1313" height="450" alt="image" src="https://github.com/user-attachments/assets/75144d3c-50be-448d-97e8-2bea4f684c63" />

**Question 6**
---
<img width="1251" height="188" alt="image" src="https://github.com/user-attachments/assets/4f8f27b9-b370-445c-98f7-20a185278a84" />

```sql
UPDATE products
SET availability = availability * 2
WHERE product_id = 1;
```

**Output:**

<img width="1293" height="267" alt="image" src="https://github.com/user-attachments/assets/06577af4-f54d-4c46-b6c2-05f08781fc25" />

**Question 7**
---
<img width="1212" height="543" alt="image" src="https://github.com/user-attachments/assets/f51fffd0-ef27-4700-beb4-eb04aebaca37" />

```sql
UPDATE employees
SET hire_date = '2024-01-24'
WHERE department_id = 50;
```

**Output:**

<img width="1318" height="313" alt="image" src="https://github.com/user-attachments/assets/9f0e4f34-d3ac-4868-b413-c810cb0533bf" />

**Question 8**
---
<img width="1316" height="527" alt="image" src="https://github.com/user-attachments/assets/8ab1a529-e051-4495-839f-bbd36a4d21b3" />

```sql
SELECT customer_id, cust_name, city, grade, salesman_id
FROM customer
WHERE customer_id IN (3007, 3008, 3009);
```

**Output:**

<img width="1301" height="390" alt="image" src="https://github.com/user-attachments/assets/fd127fff-ccaa-4291-a3e5-6d9e207b461c" />

**Question 9**
---
<img width="1332" height="570" alt="image" src="https://github.com/user-attachments/assets/b538a3d3-5717-43c4-91ef-c3e839324c15" />

```sql
SELECT
ename,
hiredate, 
CASE strftime('%w', hiredate)
WHEN '0' THEN 'Sunday'
WHEN '1' THEN 'Monday'
WHEN '2' THEN 'Tuesday'
WHEN '3' THEN 'Wednesday'
WHEN '4' THEN 'Thursday'
WHEN '5' THEN 'Friday'
WHEN '6' THEN 'Saturday'
END AS day_of_week
FROM emp;
```

**Output:**

<img width="1185" height="373" alt="image" src="https://github.com/user-attachments/assets/1da702ae-67f6-45e3-85e2-c63524f42597" />

**Question 10**
---
<img width="1326" height="537" alt="image" src="https://github.com/user-attachments/assets/b65343bb-1ee3-4adb-aa33-f1b7646fd854" />

```sql
DELETE FROM customer
WHERE GRADE >= 2;
```

**Output:**

<img width="1257" height="521" alt="image" src="https://github.com/user-attachments/assets/0ffda9b2-9c2c-4173-b2b0-b22a828af709" />

## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
