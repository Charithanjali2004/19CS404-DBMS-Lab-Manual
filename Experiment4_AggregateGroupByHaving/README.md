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
<img width="1073" height="421" alt="image" src="https://github.com/user-attachments/assets/ccf2d217-cafb-4326-9079-f116392303e7" />


```sql
SELECT MAX(age) - MIN(age) AS age_difference
FROM employee;
```

**Output:**

<img width="1045" height="363" alt="image" src="https://github.com/user-attachments/assets/1d2da448-0dc2-4944-a13b-8fc5226310b4" />

**Question 2**
---
<img width="1155" height="455" alt="image" src="https://github.com/user-attachments/assets/99c9ca1e-b02e-40f4-a06a-93c1e1f67233" />

```sql
SELECT MAX(price) - MIN(price) AS price_diff
FROM fruits;
```

**Output:**

<img width="1045" height="367" alt="image" src="https://github.com/user-attachments/assets/da811fa3-a589-46ff-8b33-95139abc7e06" />

**Question 3**
---
<img width="1183" height="432" alt="image" src="https://github.com/user-attachments/assets/db1becbb-b385-4968-9e31-43355c303e02" />

```sql
SELECT name, max(income)
FROM employee
WHERE city = 'California';
```

**Output:**

<img width="1135" height="363" alt="image" src="https://github.com/user-attachments/assets/2041863a-846f-4106-8479-a140a4196059" />

**Question 4**
---
<img width="1143" height="561" alt="image" src="https://github.com/user-attachments/assets/563e7102-8118-4cd8-a059-4add50965764" />

```sql
SELECT 
STRFTIME('%H', AppointmentDateTime) AS HourOfDay,
COUNT(AppointmentID) AS TotalAppointments
FROM
Appointments
GROUP BY
HourOfDay
ORDER BY
HourOfDay;
```

**Output:**

<img width="1291" height="555" alt="image" src="https://github.com/user-attachments/assets/81f722a5-4ad2-4778-b2e3-8ab53cd44638" />

**Question 5**
---
<img width="1222" height="602" alt="image" src="https://github.com/user-attachments/assets/9ecde6d4-5cb5-467c-98b3-c5a1358d98d9" />

```sql
SELECT 
InsuranceCompany,
COUNT(*) AS TotalExpiredPatients
FROM Insurance
WHERE SUBSTR(validityPeriod, -10) < DATE('now')
GROUP BY InsuranceCompany
ORDER BY InsuranceCompany;
```

**Output:**

<img width="1212" height="765" alt="image" src="https://github.com/user-attachments/assets/64a77a81-0761-4ae2-8c43-054d772318ca" />

**Question 6**
---
<img width="1197" height="598" alt="image" src="https://github.com/user-attachments/assets/fc93a758-de77-4190-a453-5f746d353a98" />

```sql
SELECT 
DoctorID,
COUNT(*) AS TotalPrescriptions
FROM
Prescriptions
GROUP BY
DoctorID;
```

**Output:**

<img width="1183" height="765" alt="image" src="https://github.com/user-attachments/assets/6bf94346-025e-4d6e-a807-4e63a08f60ce" />

**Question 7**
---
<img width="1245" height="511" alt="image" src="https://github.com/user-attachments/assets/57e00210-303c-4939-8250-52d61bdb4920" />

```sql
SELECT category_id, SUM(price * category_id) AS Revenue
FROM products
GROUP BY category_id
HAVING SUM(price * category_id) > 25;
```

**Output:**

<img width="1225" height="472" alt="image" src="https://github.com/user-attachments/assets/2abf1415-2b1a-4ddb-81f7-d6f629697098" />

**Question 8**
---
<img width="1255" height="477" alt="image" src="https://github.com/user-attachments/assets/85eaf75a-a97e-4793-a55e-5dd01169b6c2" />

```sql
SELECT category_id, count(product_name)
FROM products
GROUP BY category_id
HAVING MIN(category_id) <3;
```

**Output:**

<img width="1296" height="406" alt="image" src="https://github.com/user-attachments/assets/37b5fb15-7952-4254-8d62-7483fe0df3e5" />

**Question 9**
---
<img width="1242" height="476" alt="image" src="https://github.com/user-attachments/assets/092219aa-5a49-4f95-b983-442f5824dab5" />

```sql
SELECT address, SUM(salary)
FROM customer1
GROUP BY address
HAVING SUM(salary) > 2000;
```

**Output:**

<img width="1257" height="515" alt="image" src="https://github.com/user-attachments/assets/8e224fd4-96b8-46c0-be6d-35a84aa22ee4" />

**Question 10**
---
<img width="1213" height="525" alt="image" src="https://github.com/user-attachments/assets/25c5d409-7bda-4299-8356-683d4d0d1d15" />

```sql
SELECT address, AVG(salary)
FROM customer1
GROUP BY address
HAVING AVG(salary) < 15000;
```

**Output:**

<img width="1251" height="627" alt="image" src="https://github.com/user-attachments/assets/d8af7863-0435-4c68-babb-5e926c0d71cd" />

## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
