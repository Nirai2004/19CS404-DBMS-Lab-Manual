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
---
Create a table named Events with the following columns:
EventID as INTEGER
EventName as TEXT
EventDate as DATE

```sql
-- CREATE TABLE Events (
EventID  INTEGER,
EventName TEXT,
EventDate  DATE)
```

**Output:**

![Screenshot 2025-04-29 084624](https://github.com/user-attachments/assets/6da534c3-984f-439f-9f01-e72af1e1585a)

**Question 2**
---
Create a table named Products with the following constraints:
ProductID as INTEGER should be the primary key.
ProductName as TEXT should be unique and not NULL.
Price as REAL should be greater than 0.
StockQuantity as INTEGER should be non-negative.

```sql
CREATE TABLE Products (
ProductID  INTEGER  primary key,
ProductName  TEXT  unique not NULL,
Price  REAL CHECK(Price > 0),
StockQuantity  INTEGER CHECK(StockQuantity > 0)
)
```

**Output:**
![Screenshot 2025-04-29 084846](https://github.com/user-attachments/assets/6f4b5f43-e8b6-4c41-b707-961d4582ebff)



**Question 3**
---
Create a new table named contacts with the following specifications:
contact_id as INTEGER and primary key.
first_name as TEXT and not NULL.
last_name as TEXT and not NULL.
email as TEXT.
phone as TEXT and not NULL with a check constraint to ensure the length of phone is at least 10 characters.

```sql
CREATE TABLE contacts(
contact_id  INTEGER  primary key,
first_name  TEXT  not NULL,
last_name TEXT not NULL,
email  TEXT,
phone TEXT CHECK(length (phone) = 10))
```

**Output:**

![Screenshot 2025-04-29 084846](https://github.com/user-attachments/assets/35d1bb87-aa67-4d1d-aeb9-f39dee2d6f05)


**Question 4**
---
Write a SQL query for adding a new column named "email" with the datatype VARCHAR(100) to the  table "customer" 


```sql
alter table customer add email VARCHAR(100)
```

**Output:**

![Screenshot 2025-04-29 090447](https://github.com/user-attachments/assets/d020139a-e5c1-419c-b4d4-f1bbca877961)



**Question 5**
---
-- Write a SQL query to modify the Student_details table by adding a new column Email of type VARCHAR(50) and updating the column MARKS to have a default value of 0.

```sql
alter table Student_details add Email VARCHAR (50);
alter table Student_details add MARKS default 0;

```

**Output:**

![Screenshot 2025-04-29 090550](https://github.com/user-attachments/assets/7ac84df1-c5d1-4893-988f-ebb24a0759a0)

**Question 6**
---
-- Create a table named Invoices with the following constraints:
InvoiceID as INTEGER should be the primary key.
InvoiceDate as DATE.
Amount as REAL should be greater than 0.
DueDate as DATE should be greater than the InvoiceDate.
OrderID as INTEGER should be a foreign key referencing Orders(OrderID).

```sql
 create table Invoices(
InvoiceID  INTEGER primary key,
InvoiceDate  DATE,
Amount  REAL CHECK(Amount >0),
DueDate  DATE CHECK(DueDate> InvoiceDate),
OrderID  INTEGER ,
foreign key(OrderID) REFERENCES Orders(OrderID)
)
```

**Output:**

![Screenshot 2025-04-29 090854](https://github.com/user-attachments/assets/7bf2d61e-6868-4590-ad6e-e21d1394e34e)


**Question 7**
---
Create a table named ProjectAssignments with the following constraints:
AssignmentID as INTEGER should be the primary key.
EmployeeID as INTEGER should be a foreign key referencing Employees(EmployeeID).
ProjectID as INTEGER should be a foreign key referencing Projects(ProjectID).
AssignmentDate as DATE should be NOT NULL.

```sql
create table ProjectAssignments(
AssignmentID  INTEGER  primary key,
EmployeeID INTEGER,
ProjectID INTEGER ,
AssignmentDate  DATE  NOT NULL,
FOREIGN KEY (EmployeeID) REFERENCES Employees(EmployeeID),
FOREIGN KEY (ProjectID) REFERENCES Projects(ProjectID)
)
```

**Output:**

![Screenshot 2025-04-29 090919](https://github.com/user-attachments/assets/7b1bd890-3250-4a98-b1fd-9e5e0fce466e)


**Question 8**
---
-- Insert all products from Discontinued_products into Products.

Table attributes are ProductID, ProductName, Price, Stock

```sql
INSERT INTO Products(ProductID, ProductName, Price, Stock)
SELECT ProductID, ProductName, Price, Stock
FROM Discontinued_products
```

**Output:**

![Screenshot 2025-04-29 091258](https://github.com/user-attachments/assets/09d8a97b-84c7-4dc7-8fce-af0f4e230cc4)


**Question 9**
---
Insert a customer with CustomerID 301, Name Michael Jordan, Address 123 Maple St, City Chicago, and ZipCode 60616 into the Customers table.

```sql
INSERT INTO Customers (CustomerID ,Name,Address, City, ZipCode) VALUES (301 ,"Michael Jordan" ,"123 Maple St" , "Chicago" ,   60616)```
```
**Output:**

![Screenshot 2025-04-29 091313](https://github.com/user-attachments/assets/893d22df-1966-4b8c-aecd-16e1e42877a6)


**Question 10**
---
In the Employee table, insert a record where some fields are NULL, another record where all fields are filled without any NULL values, and a third record where some fields are filled, and others are left as NULL.

```sql
INSERT INTO Employee (EmployeeID,Name,Position,Department,Salary) VALUES (5 ,"George Clark","Consultant" ,NULL,NULL),(7,"Noah Davis","Manager","HR",60000),(8,"Ava Miller","Consultant","IT",NULL);
```

**Output:**

![Screenshot 2025-04-29 091326](https://github.com/user-attachments/assets/b880734d-29e0-4348-9b22-8b72edcd728d)



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
