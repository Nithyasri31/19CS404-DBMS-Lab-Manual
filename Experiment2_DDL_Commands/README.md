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
Insert the following products into the Products table:

Name        Category     Price       Stock
----------  -----------  ----------  ----------
Smartphone  Electronics  800         150
Headphones  Accessories  200         300
```
INSERT INTO Products (Name, Category, Price, Stock) VALUES("Smartphone", "Electronics",  800,150);
INSERT INTO Products (Name, Category, Price, Stock) VALUES("Headphones", "Accessories",  200,300);
 
        
```

**Output:**

<img width="1217" height="436" alt="image" src="https://github.com/user-attachments/assets/8643c3f1-e87a-49fd-a17f-b21d935d6ffd" />


**Question 2**
---
Create a table named Shipments with the following constraints:
ShipmentID as INTEGER should be the primary key.
ShipmentDate as DATE.
SupplierID as INTEGER should be a foreign key referencing Suppliers(SupplierID).
OrderID as INTEGER should be a foreign key referencing Orders(OrderID).

```
CREATE TABLE Shipments(
ShipmentID  INTEGER  primary key,
ShipmentDate  DATE,
SupplierID INTEGER,
OrderID INTEGER,
foreign key(SupplierID) references Suppliers (SupplierID),
foreign key(OrderID) references Orders(OrderID)
);
```

**Output:**

<img width="1221" height="327" alt="image" src="https://github.com/user-attachments/assets/13412bca-4b29-477a-8425-1f2e16077498" />


**Question 3**
---
Insert all products from Discontinued_products into Products.

Table attributes are ProductID, ProductName, Price, Stock

```
INSERT INTO Products
SELECT * FROM Discontinued_products;
```

**Output:**

<img width="1234" height="377" alt="image" src="https://github.com/user-attachments/assets/061a45f1-3a45-4899-8d50-22ea62727c6c" />


**Question 4**
---
Write a SQL query to Add a new column named "discount" with the data type DECIMAL(5,2) to the "customer" table.

Sample table: customer

 customer_id |   cust_name    |    city    | grade | salesman_id 
-------------+----------------+------------+-------+-------------
        3002 | Nick Rimando   | New York   |   100 |        5001
        3007 | Brad Davis     | New York   |   200 |        5001
        3005 | Graham Zusi    | California |   200 |        5002

```
ALTER TABLE customer
add column discount DECIMAL(5,2);
```

**Output:**

<img width="1221" height="453" alt="image" src="https://github.com/user-attachments/assets/5925f6fc-b5d8-4a58-9f69-65db9798bc80" />


**Question 5**
---
Insert a record with EmployeeID 001, Name Sarah Parker, Position Manager, Department HR, and Salary 60000 into the Employee table.

```
INSERT INTO Employee (EmployeeID,Name,Position,Department,Salary)values(001,'Sarah Parker','Manager','HR',60000); 
```

**Output:**

<img width="1226" height="330" alt="image" src="https://github.com/user-attachments/assets/765a95d4-0376-4579-aa65-2c3dbc2e637c" />


**Question 6**
---
Create a table named Orders with the following columns:

OrderID as INTEGER
OrderDate as TEXT
CustomerID as INTEGER

```
CREATE TABLE Orders(
OrderID INTEGER,
OrderDate TEXT,
CustomerID INTEGER 
);
```

**Output:**

<img width="1238" height="473" alt="image" src="https://github.com/user-attachments/assets/f182b89b-dd30-4199-be33-f1f22b1ff6e8" />


**Question 7**
---
Create a table named Invoices with the following constraints:

InvoiceID as INTEGER should be the primary key.
InvoiceDate as DATE.
DueDate as DATE should be greater than the InvoiceDate.
Amount as REAL should be greater than 0.

```
CREATE TABLE Invoices(
InvoiceID INTEGER primary key,
InvoiceDate DATE,
DueDate DATE CHECK(DueDate>InvoiceDate),
Amount REAL check(Amount>0)
);
```

**Output:**

<img width="1225" height="379" alt="image" src="https://github.com/user-attachments/assets/0dd945ed-dba5-40e8-a759-7cc622133c7e" />


**Question 8**
---
Create a table named Invoices with the following constraints:
InvoiceID as INTEGER should be the primary key.
InvoiceDate as DATE.
Amount as REAL should be greater than 0.
DueDate as DATE should be greater than the InvoiceDate.
OrderID as INTEGER should be a foreign key referencing Orders(OrderID).

```
CREATE TABLE Invoices(
InvoiceID INTEGER primary key,
InvoiceDate DATE,
Amount REAL check(Amount>0),
DueDate DATE check(DueDate>InvoiceDate),
OrderID INTEGER,
foreign key(OrderID) references Orders(OrderID)
);
```

**Output:**

<img width="1235" height="368" alt="image" src="https://github.com/user-attachments/assets/739b8a1e-3257-4d4d-9579-7e7a063b6ffe" />


**Question 9**
---
Write a SQL query for adding a new column named "email" with the datatype VARCHAR(100) to the  table "customer" 

Sample table: customer

 customer_id |   cust_name    |    city    | grade | salesman_id 
-------------+----------------+------------+-------+-------------
        3002 | Nick Rimando   | New York   |   100 |        5001
        3007 | Brad Davis     | New York   |   200 |        5001
        3005 | Graham Zusi    | California |   200 |        5002

```
ALTER table customer 
add column email VARCHAR(100);
```

**Output:**

<img width="1249" height="456" alt="image" src="https://github.com/user-attachments/assets/8437dc71-ac79-4763-96dc-63130fb66769" />


**Question 10**
---
Create a table named Bonuses with the following constraints:
BonusID as INTEGER should be the primary key.
EmployeeID as INTEGER should be a foreign key referencing Employees(EmployeeID).
BonusAmount as REAL should be greater than 0.
BonusDate as DATE.
Reason as TEXT should not be NULL.

```
CREATE TABLE Bonuses(
BonusID INTEGER primary key,
EmployeeID INTEGER,
-- foreign key(EmployeeID) references Employees(EmployeeID).
BonusAmount REAL check(BonusAmount>0),
BonusDate DATE,
Reason TEXT NOT NULL, 
foreign key(EmployeeID) references Employees(EmployeeID) 
);
```

**Output:**

<img width="1224" height="364" alt="image" src="https://github.com/user-attachments/assets/89c13361-5847-45ed-9b7e-1696868f2ad1" />

![WhatsApp Image 2025-11-22 at 22 48 40_691dcabf](https://github.com/user-attachments/assets/80ab71bd-3520-43d1-ac33-eaf5f72e4870)


## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
