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
![Screenshot 2025-04-29 120800](https://github.com/user-attachments/assets/58f41ad1-a713-4ad3-b299-fdd849cb2cca)

```sql
UPDATE products
SET reorder_lvl = 40
WHERE category = 'Grocery';
```

**Output:**

![Screenshot 2025-04-29 121349](https://github.com/user-attachments/assets/32a2b973-d275-416d-9479-00db10e6c80f)

**Question 2**
---
![Screenshot 2025-04-29 120827](https://github.com/user-attachments/assets/4252aa30-2b65-4929-843d-0762a3415249)

```sql
UPDATE employees
SET hire_date = '2024-01-24'
WHERE department_id = 50;
```

**Output:**

![Screenshot 2025-04-29 121401](https://github.com/user-attachments/assets/e97fbcc4-153d-433d-b4c0-efb9b09b0084)

**Question 3**
---
![Screenshot 2025-04-29 120836](https://github.com/user-attachments/assets/dfc4f6c3-1278-493c-b631-6a6062c32f65)

```sql
UPDATE sales
SET total_sell_price = quantity * sell_price
WHERE product_id = 10;
```

**Output:**

![Screenshot 2025-04-29 121411](https://github.com/user-attachments/assets/0c8949a7-ce77-48db-b53a-e861756e3042)

**Question 4**
---
![Screenshot 2025-04-29 120845](https://github.com/user-attachments/assets/93855f75-bebc-4c02-aa72-d989c8b3b60c)

```sql
UPDATE employees
SET salary = salary + 500,
    email = 'updated'
WHERE job_id = 'SA_REP' AND commission_pct > 0.15;
```

**Output:**

![Screenshot 2025-04-29 121429](https://github.com/user-attachments/assets/8fbad5ae-92a7-4b71-bd58-53d2556a25ea)

**Question 5**
---
![Screenshot 2025-04-29 120854](https://github.com/user-attachments/assets/05731636-1e53-4790-a40b-c8e2b94f6c30)

```sql
UPDATE products
SET reorder_lvl = 20
WHERE category = 'Snacks' AND quantity < 10;
```

**Output:**

![Screenshot 2025-04-29 121439](https://github.com/user-attachments/assets/4588273f-3e46-4b1c-bf7e-ac07ab57a58a)

**Question 6**
---
![Screenshot 2025-04-29 120902](https://github.com/user-attachments/assets/9e5d3d03-1723-4708-9652-7cd24590dd13)

```sql
DELETE FROM Doctors
WHERE doctor_id = 1;
```

**Output:**

![Screenshot 2025-04-29 121451](https://github.com/user-attachments/assets/3309667a-6133-4963-92b0-9d164444a417)

**Question 7**
---
![Screenshot 2025-04-29 120911](https://github.com/user-attachments/assets/047b30de-229e-45b0-87e7-6788d1518d20)

```sql
DELETE FROM Doctors
WHERE last_name = 'Brown'
  AND specialization IN ('Pediatrics', 'Cardiology');
```

**Output:**

![Screenshot 2025-04-29 121513](https://github.com/user-attachments/assets/20758650-30e0-415c-8a68-6986ef820d76)

**Question 8**
---
![Screenshot 2025-04-29 120922](https://github.com/user-attachments/assets/e3e65701-9bca-4774-8471-9293d5d5729c)

```sql
DELETE FROM customer
WHERE WORKING_AREA = 'New York';
```

**Output:**

![Screenshot 2025-04-29 121527](https://github.com/user-attachments/assets/526f67db-bf67-4933-af89-ac462325c356)

**Question 9**
---
![Screenshot 2025-04-29 120932](https://github.com/user-attachments/assets/28ef27bc-9ca2-49dc-85ef-208020bc6ab9)

```sql
DELETE FROM Surgeries
WHERE surgery_date = '2024-02-28';
```

**Output:**

![Screenshot 2025-04-29 121536](https://github.com/user-attachments/assets/1693498f-eba9-4f08-ae84-c32384b004aa)

**Question 10**
---
![Screenshot 2025-04-29 120943](https://github.com/user-attachments/assets/a409b2a9-7fe9-419d-820a-808bbfc55b87)

```sql
SELECT *
FROM EmployeeInfo
WHERE EmpFname NOT IN ('Sanjay', 'Sonia');
```

**Output:**

![Screenshot 2025-04-29 121550](https://github.com/user-attachments/assets/5de6eaf6-0df0-4b94-9040-5db9cafd4593)

## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
