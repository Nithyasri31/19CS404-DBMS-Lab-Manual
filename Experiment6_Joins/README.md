
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
Write the SQL query that achieves the selection of the first name from the "patients" table (aliased as "patient_name") and the specialization from the "doctors" table (aliased as "Doctor_specialization"), with an inner join on the "doctor_id" column and a condition filtering for patients admitted between '2024-01-01' and '2024-01-31'.

```
select p.first_name as"patient_name" ,d.specialization as "Doctor_speciali" from patients p
inner join doctors d on d.doctor_id=p.doctor_id
where p.admission_date between '2024-01-01' and '2024-01-31';
```

**Output:**

<img width="780" height="489" alt="image" src="https://github.com/user-attachments/assets/8f77685d-0257-43d4-9ceb-2745d21a0f37" />


**Question 2**
---
 From the following tables write a SQL query to find the salesperson(s) and the customer(s) he represents. Return Customer Name, city, Salesman, commission.

```
select c.cust_name as"Customer Name",c.city,s.name as "Salesman",s.commission from customer c
join salesman s on s.salesman_id=c.salesman_id;
```

**Output:**

<img width="1290" height="950" alt="image" src="https://github.com/user-attachments/assets/161d6d32-4c57-4902-90a6-412e28dbbab1" />


**Question 3**
---
Write the SQL query that achieves the selection of all columns from the "patients" table (aliased as "p"), with an inner join on the "patient_id" column and conditions filtering for test results with the test name 'X-Ray' and a result of 'Normal'.

```
select p.patient_id,p.first_name,p.last_name,p.date_of_birth,p.admission_date,p.discharge_date,p.doctor_id from patients p
inner join test_results t on t.patient_id=p.patient_id
where t.test_name="X-Ray" and t.result="Normal";
```

**Output:**

<img width="1265" height="489" alt="image" src="https://github.com/user-attachments/assets/0db04098-676c-41b0-8336-458d0b78b2be" />


**Question 4**
---
Write the SQL query that accomplishes the selection of the first name from the "patients" table (aliased as "patient_name") and the first name from the "doctors" table (aliased as "doctor_name"), with an inner join on the "doctor_id" column and a condition filtering for patients with a non-null discharge date.

```
select p.first_name as"patient_name",d.first_name as "doctor_name" from patients p
inner join doctors d on p.doctor_id=d.doctor_id
where p.discharge_date is not null;
```

**Output:**

<img width="837" height="509" alt="image" src="https://github.com/user-attachments/assets/c88ee9a4-a426-4b6e-8138-0f0a64e403bc" />


**Question 5**
---
From the following tables write a SQL query to find those orders where the order amount exists between 500 and 2000. Return ord_no, purch_amt, cust_name, city.

```
select o.ord_no,o.purch_amt,c.cust_name, c.city from customer c
join orders o on o.customer_id=c.customer_id
where purch_amt between 500 and 2000;
```

**Output:**

<img width="1289" height="563" alt="image" src="https://github.com/user-attachments/assets/48beae5d-68a4-4992-aec4-c0e60576e9fd" />


**Question 6**
---
SQL statement to generate a report with customer name, city, order number, order date, order amount, salesperson name, and commission to determine if any of the existing customers have not placed orders or if they have placed orders through their salesman or by themselves.

```
SELECT a.cust_name, a.city, b.ord_no,
       b.ord_date, b.purch_amt AS "Order Amount", 
       c.name, c.commission 
-- Specifying the tables to retrieve data from ('customer' as 'a', 'orders' as 'b', and 'salesman' as 'c')
FROM customer a 
-- Performing a left outer join based on the customer_id, including unmatched rows from 'customer'
LEFT OUTER JOIN orders b 
ON a.customer_id = b.customer_id 
-- Performing another left outer join with the result of the previous join and the 'salesman' table based on salesman_id
LEFT OUTER JOIN salesman c 
ON c.salesman_id = b.salesman_id;
```

**Output:**

<img width="1277" height="791" alt="image" src="https://github.com/user-attachments/assets/54e9c5a0-ac3c-4608-bcbc-f5bcfee2c991" />


**Question 7**
---
From the following tables write a SQL query to find those customers with a grade less than 300. Return cust_name, customer city, grade, Salesman, salesmancity. The result should be ordered by ascending customer_id. 

```
select c.cust_name,c.city,c.grade,s.name as"Salesman",s.city from customer c
JOIN salesman s ON c.salesman_id = s.salesman_id
WHERE c.grade < 300
ORDER BY c.customer_id ASC
```

**Output:**

<img width="1293" height="855" alt="image" src="https://github.com/user-attachments/assets/24f56881-a82d-4e0c-b430-21c995ac1134" />


**Question 8**
---
Write an SQL query that retrieves all columns from the 'customer' table (using the alias 'c'), performs a LEFT JOIN with the 'orders' table on the 'customer_id' column, and includes only those orders with an order date after '2012-08-17'.

```
SELECT c.*
FROM customer c
LEFT JOIN orders o ON c.customer_id = o.customer_id
where  o.ord_date > '2012-08-17';

```

**Output:**

<img width="1286" height="934" alt="image" src="https://github.com/user-attachments/assets/63b8c1a9-5674-4447-bb86-25efc6b52bb9" />


**Question 9**
---
Write a SQL statement to make a report with customer name, city, order number, order date, and order amount in ascending order according to the order date to determine whether any of the existing customers have placed an order or not.

```
SELECT 
  c.cust_name,
  c.city,
  o.ord_no,
  o.ord_date,
  o.purch_amt AS "Order Amount"
FROM customer c
left JOIN orders o ON c.customer_id = o.customer_id
ORDER BY o.ord_date ASC;

```

**Output:**

<img width="1274" height="794" alt="image" src="https://github.com/user-attachments/assets/8ebc77b3-c332-49c1-bcab-857bbc65ec46" />


**Question 10**
---
Write the SQL query that achieves the selection of all columns from the "customer" table (aliased as "c"), with a left join on the "salesman_id" column and a condition filtering for salesman with the name 'Mc Lyon'.

Customer Table: (customer_id, cust_name, city, grade, salesman_id)

Salesman Table: (salesman_id, name, city, commission)

```
SELECT c.*
FROM customer c
LEFT JOIN salesman s ON c.salesman_id = s.salesman_id
WHERE s.name = 'Mc Lyon';

```

**Output:**
  <img width="1277" height="496" alt="image" src="https://github.com/user-attachments/assets/a974e8b5-9f69-46c5-93c7-66d379457f3f" />
  
  ![WhatsApp Image 2025-11-22 at 22 48 41_03955bc6](https://github.com/user-attachments/assets/bc37beca-35e9-4be0-b752-584c09fc76ac)




## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
