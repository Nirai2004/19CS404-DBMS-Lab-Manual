# Experiment 6: Joins

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
![Screenshot 2025-04-29 234116](https://github.com/user-attachments/assets/43d1cf87-4dbc-47d5-bffa-ec4405e91212)

```sql
SELECT c.*
FROM customer c
LEFT JOIN salesman s ON c.salesman_id = s.salesman_id
WHERE s.name = 'Mc Lyon';
```

**Output:**

![Screenshot 2025-04-29 234318](https://github.com/user-attachments/assets/73435ac1-524c-4605-adb3-ad06ec9770f1)

**Question 2**
---
![Screenshot 2025-04-29 234133](https://github.com/user-attachments/assets/6f061504-5519-4f0b-9229-d0c7fdd3cddb)

```sql
SELECT s.name AS Salesman, c.cust_name, s.city
FROM salesman s
JOIN customer c ON s.city = c.city;
```

**Output:**

![Screenshot 2025-04-29 234328](https://github.com/user-attachments/assets/59de80b9-e65f-4713-abbc-e844c2b24cd1)

**Question 3**
---
![Screenshot 2025-04-29 234144](https://github.com/user-attachments/assets/c3d079e2-2fba-452b-b353-002448af3e4b)

```sql
SELECT 
    c.cust_name AS "Customer Name",
    c.city AS city,
    s.name AS Salesman,
    s.commission
FROM customer c
JOIN salesman s ON c.salesman_id = s.salesman_id
WHERE s.commission > 0.12;
```

**Output:**

![Screenshot 2025-04-29 234338](https://github.com/user-attachments/assets/630be828-282a-4578-8f2f-d871d2f7873f)

**Question 4**
---
![Screenshot 2025-04-29 234154](https://github.com/user-attachments/assets/431bd016-9e12-4ec6-8e10-30d5ff5a2619)

```sql
SELECT s.name
FROM salesman s
LEFT JOIN customer c ON s.salesman_id = c.salesman_id
WHERE c.city = 'London';
```

**Output:**

![Screenshot 2025-04-29 234348](https://github.com/user-attachments/assets/ba268e1c-a98e-4e90-82b8-3eede6de0399)

**Question 5**
---
![Screenshot 2025-04-29 234207](https://github.com/user-attachments/assets/f34b476e-61ae-4442-ac32-3a0b0b5a6412)

```sql
SELECT t.*
FROM test_results t
INNER JOIN patients p ON t.patient_id = p.patient_id
WHERE p.first_name = 'Alice';
```

**Output:**

![Screenshot 2025-04-29 234358](https://github.com/user-attachments/assets/82b1aa93-4091-4109-b765-ffbb3bb3dcdf)

**Question 6**
---
![Screenshot 2025-04-29 234219](https://github.com/user-attachments/assets/775b01cd-fa7c-417a-b8b1-2c49a601a005)

```sql
SELECT 
    o.ord_no,
    o.purch_amt,
    c.cust_name,
    c.city
FROM orders o
JOIN customer c ON o.customer_id = c.customer_id
WHERE o.purch_amt BETWEEN 500 AND 2000;
```

**Output:**

![Screenshot 2025-04-29 234408](https://github.com/user-attachments/assets/d6f957f7-b29e-49e4-a7cd-c2be565045fe)

**Question 7**
---
![Screenshot 2025-04-29 234228](https://github.com/user-attachments/assets/79a1cbdc-1222-424b-9881-1d05a118aea9)

```sql
SELECT p.*
FROM patients p
INNER JOIN appointments a ON p.patient_id = a.patient_id
WHERE a.appointment_date BETWEEN '2024-02-01' AND '2024-02-28';
```

**Output:**

![Screenshot 2025-04-29 234420](https://github.com/user-attachments/assets/436351a5-3a28-48e7-8d29-a7fb691e8849)

**Question 8**
---
![Screenshot 2025-04-29 234238](https://github.com/user-attachments/assets/05a2e12e-e466-43e3-bd49-e64b1ebd4b9a)

```sql
SELECT p.*
FROM patients p
INNER JOIN test_results t ON p.patient_id = t.patient_id
WHERE t.test_date BETWEEN '2024-03-01' AND '2024-03-31';
```

**Output:**

![Screenshot 2025-04-29 234434](https://github.com/user-attachments/assets/fa6ac3ab-6831-4912-84a0-446cf6c7203c)

**Question 9**
---
![Screenshot 2025-04-29 234252](https://github.com/user-attachments/assets/5d7f2756-de4f-45ba-a061-03cb1e4e64cd)

```sql
SELECT 
    c.cust_name AS "Customer Name",
    c.city AS "city",
    s.name AS "Salesman",
    s.city AS "city",
    s.commission
FROM customer c
JOIN salesman s ON c.salesman_id = s.salesman_id
WHERE c.city <> s.city
  AND s.commission > 0.12;
```

**Output:**

![Screenshot 2025-04-29 234443](https://github.com/user-attachments/assets/c8020bc3-d3b5-4646-8627-c8643156a778)

**Question 10**
---
![Screenshot 2025-04-29 234304](https://github.com/user-attachments/assets/4f228bb4-fefe-4313-a584-310923964690)

```sql
SELECT 
    c.cust_name AS "Customer Name",
    c.city AS "city",
    s.name AS "Salesman",
    s.commission
FROM customer c
JOIN salesman s ON c.salesman_id = s.salesman_id;
```

**Output:**

![Screenshot 2025-04-29 234455](https://github.com/user-attachments/assets/94b71f71-1f0f-427f-a7f5-b6258d12f8f4)


## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
