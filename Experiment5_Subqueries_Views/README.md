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
<img width="1220" height="601" alt="image" src="https://github.com/user-attachments/assets/54d0589a-0b26-4c5c-b826-267bf0ad52a1" />

```sql
SELECT *
FROM Employee
WHERE age < (
SELECT AVG(age)
FROM Employee
WHERE income > 250000
);
```

**Output:**

<img width="1283" height="548" alt="image" src="https://github.com/user-attachments/assets/d9abeae7-38bb-4f46-9c1e-d7369efffe4e" />

**Question 2**
---
<img width="1213" height="630" alt="image" src="https://github.com/user-attachments/assets/83688ea2-83cd-43f2-ad0a-66c5939a9498" />

```sql
SELECT commission
FROM salesman 
WHERE salesman_id IN (
SELECT salesman_id
FROM customer
WHERE city = 'Paris'
);
```

**Output:**

<img width="810" height="392" alt="image" src="https://github.com/user-attachments/assets/8a3ff004-00ae-49e2-b59a-6bf63a99497e" />

**Question 3**
---
<img width="1257" height="753" alt="image" src="https://github.com/user-attachments/assets/07f7ad1b-bb32-4f05-951c-6b70daebc627" />

```sql
SELECT ord_no, purch_amt, ord_date, salesman_id
FROM orders
WHERE salesman_id IN(
SELECT salesman_id
FROM salesman
WHERE commission = (
SELECT MAX(commission)
FROM salesman
)
);
```

**Output:**

<img width="1250" height="523" alt="image" src="https://github.com/user-attachments/assets/13a30200-5a10-43b2-b1ad-2ee48d086cc4" />

**Question 4**
---
<img width="1202" height="612" alt="image" src="https://github.com/user-attachments/assets/d29ccbf8-0471-4f3f-a1aa-5a66e5d90df3" />

```sql
SELECT * FROM CUSTOMERS WHERE SALARY > 4500;
```

**Output:**

<img width="1247" height="475" alt="image" src="https://github.com/user-attachments/assets/dddda9a2-1e40-4e59-a97d-cebaa7e52c5f" />

**Question 5**
---
<img width="1153" height="687" alt="image" src="https://github.com/user-attachments/assets/20f5ec15-9435-4638-bd03-c6a89d87864e" />

```sql
SELECT * 
FROM CUSTOMERS
WHERE SALARY > 1500;
```

**Output:**

<img width="1212" height="635" alt="image" src="https://github.com/user-attachments/assets/52ebe1a9-401d-4e11-ab75-058841a4ed22" />

**Question 6**
---
<img width="1137" height="498" alt="image" src="https://github.com/user-attachments/assets/e1b8c7c2-1fc0-47eb-8887-0aac36cbacfd" />

```sql
SELECT *
FROM customer
WHERE city <> (
SELECT city
FROM customer
WHERE id = (SELECT MAX(id) FROM customer)
);
```

**Output:**

<img width="1272" height="528" alt="image" src="https://github.com/user-attachments/assets/10de67d6-4163-442a-8ab1-ceec37d2f23b" />

**Question 7**
---
<img width="1247" height="727" alt="image" src="https://github.com/user-attachments/assets/0dd281f1-8882-4c2f-bb7e-4068545f8831" />

```sql
SELECT ord_no, purch_amt, ord_date, customer_id, salesman_id
FROM ORDERS
WHERE salesman_id IN (
SELECT salesman_id
FROM SALESMAN
WHERE city = 'New York'
);
```

**Output:**

<img width="1247" height="523" alt="image" src="https://github.com/user-attachments/assets/42205954-12a5-4f06-9ea3-667db7de8d76" />

**Question 8**
---
<img width="1216" height="585" alt="image" src="https://github.com/user-attachments/assets/d90fc57d-0bfc-4578-9a39-2815c6555848" />

```sql
SELECT ord_no, purch_amt, ord_date, customer_id, salesman_id
FROM Orders
WHERE salesman_id = (
SELECT salesman_id
FROM Salesman
WHERE name = 'Paul Adam'
);
```

**Output:**

<img width="1242" height="432" alt="image" src="https://github.com/user-attachments/assets/157368bd-4c36-41a5-855a-abc7878978e5" />

**Question 9**
---
<img width="1212" height="435" alt="image" src="https://github.com/user-attachments/assets/4755486e-3b7c-49f9-be01-748a51271b4b" />

```sql
SELECT grade, COUNT(*)
FROM customer
GROUP BY grade
HAVING grade > (
SELECT AVG(grade)
FROM customer
WHERE city = 'New York'
);
```

**Output:**

<img width="867" height="392" alt="image" src="https://github.com/user-attachments/assets/28e89243-6e25-4e8b-9cfd-754cab7e9319" />

**Question 10**
---
<img width="1238" height="582" alt="image" src="https://github.com/user-attachments/assets/e7b5ab36-ecd2-4f52-807a-4b815c2256a6" />

```sql
SELECT student_name, grade
FROM GRADES g1
WHERE grade = (
SELECT MAX(grade)
FROM GRADES g2
WHERE g2.subject = g1.subject
);
```

**Output:**

<img width="1228" height="473" alt="image" src="https://github.com/user-attachments/assets/54e75a6c-05d8-4cac-9619-bd1578452349" />

## RESULT
Thus, the SQL queries to implement subqueries and views have been executed successfully.
