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
![Screenshot 2025-04-29 110750](https://github.com/user-attachments/assets/01d6816e-3c04-4c4b-8537-0dee1d8cf6f1)

```sql
SELECT department_id, department_name
FROM Departments
WHERE LENGTH(department_name) > (
    SELECT AVG(LENGTH(department_name)) FROM Departments
);
```

**Output:**

![Screenshot 2025-04-29 111144](https://github.com/user-attachments/assets/ce9a5d5a-1d8e-4dd2-8aee-7972f38c31e2)

**Question 2**
---
![Screenshot 2025-04-29 110758](https://github.com/user-attachments/assets/4e90ca7c-d87c-4494-a7e4-75d5cfe16e60)

```sql
SELECT name, city
FROM customer
WHERE city IN (
    SELECT city
    FROM customer
    WHERE id IN (3, 7)
);
```

**Output:**

![Screenshot 2025-04-29 111151](https://github.com/user-attachments/assets/38e2b57f-8935-4e63-83ed-9b88317a86b0)

**Question 3**
---
![Screenshot 2025-04-29 110807](https://github.com/user-attachments/assets/2b57fbf9-cf69-49f2-9eb6-a20cce47ea3a)

```sql
SELECT id, name, city, email, phone
FROM customer
WHERE city <> (
    SELECT city
    FROM customer
    WHERE id = (
        SELECT MAX(id) FROM customer
    )
);
```

**Output:**

![Screenshot 2025-04-29 111204](https://github.com/user-attachments/assets/904ee223-4c35-4424-b202-8fb4d14d84e3)

**Question 4**
---
![Screenshot 2025-04-29 110817](https://github.com/user-attachments/assets/72e87c5b-ea42-46a2-bc11-df0f82f31981)

```sql
SELECT orders.ord_no AS ord_no, 
       orders.purch_amt, 
       orders.ord_date AS ord_date, 
       orders.customer_id, 
       orders.salesman_id
FROM orders
JOIN salesman ON orders.salesman_id = salesman.salesman_id
WHERE salesman.city = 'London';
```

**Output:**

![Screenshot 2025-04-29 111214](https://github.com/user-attachments/assets/68bca1b5-0aad-41c3-ac58-dfb9dc5ef5c2)

**Question 5**
---
![Screenshot 2025-04-29 110826](https://github.com/user-attachments/assets/ea6e2198-b835-4f5e-a6fa-0c8441e06c7e)

```sql
SELECT medication_id, medication_name, dosage
FROM Medications
WHERE dosage = (
    SELECT MIN(dosage) FROM Medications
);
```

**Output:**

![Screenshot 2025-04-29 111221](https://github.com/user-attachments/assets/711e878b-3ed3-44a0-b81b-8d01eb456f18)

**Question 6**
---
![Screenshot 2025-04-29 110834](https://github.com/user-attachments/assets/eab6b48c-bdc0-45e0-9a7b-69fd18af9bb3)

```sql
SELECT ord_no, purch_amt, ord_date, customer_id, salesman_id
FROM orders
WHERE purch_amt > (
    SELECT AVG(purch_amt)
    FROM orders
    WHERE ord_date = '2012-10-10'
);
```

**Output:**

![Screenshot 2025-04-29 111230](https://github.com/user-attachments/assets/8dfcdcca-7b8a-4aec-b6bd-23fdcfeb0e22)

**Question 7**
---
![Screenshot 2025-04-29 110842](https://github.com/user-attachments/assets/8f964d4c-1a2b-47a2-b9ba-61cf742f96a8)

```sql
SELECT *
FROM CUSTOMERS
WHERE SALARY > 4500;
```

**Output:**

![Screenshot 2025-04-29 111238](https://github.com/user-attachments/assets/0712aca1-d1ac-4915-bd8b-65912726b79f)

**Question 8**
---
![Screenshot 2025-04-29 110849](https://github.com/user-attachments/assets/ff4e8bce-3cfa-4043-bb71-d4b272362d64)

```sql
SELECT student_name, grade
FROM GRADES
WHERE (subject, grade) IN (
    SELECT subject, MAX(grade)
    FROM GRADES
    GROUP BY subject
);
```

**Output:**

![Screenshot 2025-04-29 111249](https://github.com/user-attachments/assets/194ab6d4-27f7-49bc-ba9b-b1885e2d5bec)

**Question 9**
---
![Screenshot 2025-04-29 110901](https://github.com/user-attachments/assets/f04436f3-9739-4e06-a202-c8e48dd31bb0)

```sql
SELECT orders.ord_no, orders.purch_amt, orders.ord_date, orders.customer_id, orders.salesman_id
FROM orders
JOIN salesman ON orders.salesman_id = salesman.salesman_id
WHERE salesman.city = 'New York';
```

**Output:**

![Screenshot 2025-04-29 111256](https://github.com/user-attachments/assets/0a4add51-14de-40e0-a307-ae9896440e7e)

**Question 10**
---
![Screenshot 2025-04-29 110912](https://github.com/user-attachments/assets/12ae3e1d-3c30-47d4-a18b-55319022b103)

```sql
SELECT orders.ord_no, orders.purch_amt, orders.ord_date, orders.customer_id, orders.salesman_id
FROM orders
JOIN salesman ON orders.salesman_id = salesman.salesman_id
WHERE salesman.name = 'Paul Adam';
```

**Output:**

![Screenshot 2025-04-29 111305](https://github.com/user-attachments/assets/55b89a5e-7a5e-4103-b42f-4c5c41eba2c9)


## RESULT
Thus, the SQL queries to implement subqueries and views have been executed successfully.
