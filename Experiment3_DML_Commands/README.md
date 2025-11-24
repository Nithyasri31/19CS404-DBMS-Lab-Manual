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
Write a SQL statement to Change the category to 'Household' where product name contains 'Detergent' in the products table.

Products Table 

name          type       
----------    ---------- 
product_id     INT PRIMARY KEY        
product_name   VARCHAR(10) 
category       VARCHAR(50) 
cost_price     DECIMAL(10) 
sell_price     DECIMAL(10) 
reorder_lvl    INT        
quantity       INT        
supplier_id    INT      

```
update products
set category='Household'
where product_name like '%Detergent%';
```

**Output:**

<img width="1213" height="589" alt="image" src="https://github.com/user-attachments/assets/21886e3b-b9a5-48bc-8fbc-653c28a48f1f" />


**Question 2**
---
Write a SQL statement to update the product_name as 'Grapefruit' whose product_id is 4 in the products table.

products table

---------------
product_id
product_name
category_id
availability

```
update products
set product_name="Grapefruit"
where product_id=4;
```

**Output:**

<img width="1223" height="327" alt="image" src="https://github.com/user-attachments/assets/1b548c22-efed-48e6-aa54-47374f2b7566" />

**Question 3**
---
Change the supplier name to upper case where contact person contains ' Singh' in suppliers table.

name               type
-----------------  ---------------
supplier_id        INT
supplier_name      VARCHAR(100)
contact_person     VARCHAR(100)
phone_number       VARCHAR(20)
email              VARCHAR(100)
address            VARCHAR(250)

```
update SUPPLIERS
set supplier_name=UPPER(supplier_name)
where contact_person like '%SINGH%';
```

**Output:**

<img width="1224" height="447" alt="image" src="https://github.com/user-attachments/assets/0b271e62-4ba4-4d96-b6d9-01bc728b4955" />


**Question 4**
---
Write a SQL statement to Update the hire_date of employees in department 50 to 2024-01-24.

Employees table

---------------
employee_id
first_name
last_name
email
phone_number
hire_date
job_id
salary
commission_pct
manager_id
department_id

```
update Employees
set hire_date="2024-01-24";
```

**Output:**

<img width="1238" height="376" alt="image" src="https://github.com/user-attachments/assets/4c9a7fd9-9510-4bd8-94b7-25e4f81cf1f3" />


**Question 5**
---
Write a SQL statement to Update the per_unit_price to 25 and total_price accordingly in purchases table where purchase_date is '2022-08-15' and product_id is 12.

```
update purchases
set per_unit_price=25,
total_price=quantity*25
where product_id=12 and purchase_date='2022-08-15';
```

**Output:**

<img width="1240" height="612" alt="image" src="https://github.com/user-attachments/assets/0b417510-50b2-4a36-8502-c25fb0090e82" />


**Question 6**
---
Write a SQL query to Delete a Specific Surgery which was made on 28th Feb 2024.

Sample table: Surgeries

attributes: surgery_id, patient_id, surgeon_id, surgery_date

```
delete from Surgeries
where surgery_date='2024-02-28';
```

**Output:**

<img width="1230" height="470" alt="image" src="https://github.com/user-attachments/assets/f9aade89-130b-4c2c-85d3-e2db5242942b" />


**Question 7**
---
Write a SQL query to remove rows from the table 'customer' with the following condition -

1. 'cust_city' should begin with the letter 'L',

```
delete from Customer
where cust_city like "L%";
```

**Output:**

<img width="1218" height="949" alt="image" src="https://github.com/user-attachments/assets/b02cdd59-a5ec-48da-b38e-9d7b010ca856" />


**Question 8**
---
Write a SQL query to delete a doctor from Doctors table whose Specialization is 'Pediatrics' and First name is 'Michael'.

```
delete from Doctors
where specialization="Pediatrics" and first_name="Michael";
```

**Output:**

<img width="1227" height="469" alt="image" src="https://github.com/user-attachments/assets/07447f57-b7f6-4862-ac0b-8d63e8366be4" />


**Question 9**
---
Write a SQL query to remove rows from the table 'customer' with the following condition -

1. 'cust_country' must be 'India',

2. 'cus_city' must not be 'Chennai',

```
delete from Customer
where cust_country="India" and cust_city!="Chennai";
```

**Output:**

<img width="1232" height="942" alt="image" src="https://github.com/user-attachments/assets/9a1dde37-9bb7-4e04-a591-5583f59ebdd8" />


**Question 10**
---
Write a SQL query to Delete customers from 'customer' table where 'GRADE' is odd.

```
delete from Customer
where grade%2!=0;
```

**Output:**

<img width="1233" height="501" alt="image" src="https://github.com/user-attachments/assets/05ec7685-4afa-4d2e-98db-2d5213568644" />

![WhatsApp Image 2025-11-22 at 22 48 40_3ce24fb1](https://github.com/user-attachments/assets/a3b4c1b6-89ac-4f9e-82a2-3a16d9689289)

## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
