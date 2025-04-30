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
--![Screenshot 2025-04-29 105516](https://github.com/user-attachments/assets/b1eb6dab-d469-44c9-9600-a15d51af16f9)


```sql
SELECT Diagnosis, COUNT(*) AS DiagnosisCount
FROM MedicalRecords
GROUP BY Diagnosis
ORDER BY DiagnosisCount DESC
LIMIT 1;
```

**Output:**

![Screenshot 2025-04-29 105942](https://github.com/user-attachments/assets/c4da70d8-8634-4579-ba8d-cf871d735ec2)

**Question 2**
---
![Screenshot 2025-04-29 105525](https://github.com/user-attachments/assets/ca1bf3d1-e68f-4409-8bf7-246e508b4a37)

```sql
SELECT 
  CASE 
    WHEN age < 20 THEN 'Under 20'
    WHEN age BETWEEN 20 AND 30 THEN '20-30'
    WHEN age BETWEEN 31 AND 40 THEN '31-40'
    WHEN age BETWEEN 41 AND 50 THEN '41-50'
    ELSE 'Above 50'
  END AS AgeGroup,
  COUNT(*) AS TotalPatients
FROM (
  SELECT 
    PatientID,
    CAST((julianday('now') - julianday(DateOfBirth)) / 365.25 AS INTEGER) AS age
  FROM Patients
)
GROUP BY AgeGroup
ORDER BY AgeGroup;
```

**Output:**

![Screenshot 2025-04-29 105951](https://github.com/user-attachments/assets/6900a31b-f0e4-4468-9d78-ab63d9e910f9)

**Question 3**
---
![Screenshot 2025-04-29 105534](https://github.com/user-attachments/assets/a4a1c34e-d98a-4925-81bd-656615fd453c)

```sql
SELECT Gender, COUNT(*) AS TotalPatients
FROM Patients
GROUP BY Gender;
```

**Output:**

![Screenshot 2025-04-29 105958](https://github.com/user-attachments/assets/6fbeddba-9a43-46f1-9566-1850ecabe9f6)

**Question 4**
---
![Screenshot 2025-04-29 105543](https://github.com/user-attachments/assets/9a571831-397f-4b84-a505-cfb3c5bf2394)

```sql
SELECT COUNT(*) AS COUNT
FROM (
  SELECT DISTINCT age
  FROM employee
);
```

**Output:**

![Screenshot 2025-04-29 110006](https://github.com/user-attachments/assets/7502d9d0-cf97-4bf2-92f1-96b0396d9194)

**Question 5**
---
![Screenshot 2025-04-29 105553](https://github.com/user-attachments/assets/ed3511f2-bbe2-46ff-8a1c-d9e40ab73dff)

```sql
SELECT name AS fruit_name, inventory AS lowest_quantity
FROM fruits
ORDER BY inventory ASC
LIMIT 1;
```

**Output:**

![Screenshot 2025-04-29 110016](https://github.com/user-attachments/assets/5b632e6f-eaf9-4fa0-af86-2028276a9959)

**Question 6**
---
![Screenshot 2025-04-29 105602](https://github.com/user-attachments/assets/c805447f-52aa-4e0b-86a4-5f453c3af904)

```sql
SELECT COUNT(*) AS employees_in_california
FROM employee
WHERE city = 'California';

```

**Output:**

![Screenshot 2025-04-29 110024](https://github.com/user-attachments/assets/51221a74-3bfd-4fe8-ad66-748debc73e89)

**Question 7**
---
![Screenshot 2025-04-29 105612](https://github.com/user-attachments/assets/db2e8b93-31da-4fea-81ee-ce9a969bc004)

```sql
SELECT AVG(income) AS avg_income
FROM employee
WHERE name LIKE 'A%';
```

**Output:**

![Screenshot 2025-04-29 110032](https://github.com/user-attachments/assets/24fa5445-7b41-4269-b899-7be7074628ec)

**Question 8**
---
![Screenshot 2025-04-29 105621](https://github.com/user-attachments/assets/6ddcc4ca-fb91-4467-8b53-4ec919cc1a55)

```sql
SELECT address, AVG(salary)
FROM customer1
GROUP BY address
HAVING AVG(salary) < 15000;
```

**Output:**

![Screenshot 2025-04-29 110039](https://github.com/user-attachments/assets/291fda91-2a72-4eb0-ae56-2366b5a4b358)

**Question 9**
---
![Screenshot 2025-04-29 105630](https://github.com/user-attachments/assets/95391a74-99f2-4d3d-ad93-c9d7abf726b6)

```sql
SELECT address, SUM(salary)
FROM customer1
GROUP BY address
HAVING SUM(salary) > 2000;
```

**Output:**

![Screenshot 2025-04-29 110046](https://github.com/user-attachments/assets/4e139121-3bb2-423a-93f0-8c9c4b8edafc)

**Question 10**
---
![Screenshot 2025-04-29 105640](https://github.com/user-attachments/assets/d874ac78-7ed1-4126-8701-530846d1ce03)

```sql
SELECT jdate, SUM(workhour)
FROM employee1
GROUP BY jdate
HAVING SUM(workhour) > 40;
```

**Output:**

![Screenshot 2025-04-29 110053](https://github.com/user-attachments/assets/a46f8ea5-3d2b-4ada-be9e-f9f2ca307727)


## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
