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
How many medical records are there for each patient?

Sample table:MedicalRecords Table

```
select PatientID,count(RecordID) as TotalRecords from MedicalRecords
group by PatientID;
```

**Output:**

<img width="755" height="749" alt="image" src="https://github.com/user-attachments/assets/2d3ba139-a3e8-4580-8021-51dc75025cf4" />


**Question 2**
---
How many appointments are scheduled for each patient?

Sample table: Appointments Table

name                  type
--------------------  ----------
AppointmentID         INTEGER
PatientID             INTEGER
DoctorID              INTEGER
AppointmentDateTime   DATETIME
Purpose               TEXT
Status                TEXT

```
select PatientID,count(AppointmentID) as TotalAppointments from Appointments
group by PatientID;
```

**Output:**

<img width="856" height="723" alt="image" src="https://github.com/user-attachments/assets/25b5a739-112f-4116-9e36-2e2f99b714e3" />

**Question 3**
---
How many patients have insurance coverage valid in each year?

Sample table:Insurance Table

name               type
-----------------  ----------
InsuranceID        INTEGER
PatientID          INTEGER
InsuranceCompany   TEXT
PolicyNumber       TEXT
PolicyHolder       TEXT
ValidityPeriod     TEXT

```
select strftime("%Y",ValidityPeriod)as ValidityYear, count(PatientID) as TotalPatients from Insurance
group by strftime("%Y", ValidityPeriod);
```

**Output:**

<img width="696" height="472" alt="image" src="https://github.com/user-attachments/assets/829e6555-e077-4e79-a5b4-d9e970c85e94" />


**Question 4**
---
Write a SQL query to find the average length of email addresses (in characters):

Table: customer

name        type
----------  ----------
id          INTEGER
name        TEXT
city        TEXT
email       TEXT
phone       INTEGER

```
select avg(length(email))as avg_email_length from customer;
```

**Output:**


<img width="577" height="418" alt="image" src="https://github.com/user-attachments/assets/0a773fe8-e904-4e9d-99c6-412fd6ca25be" />

**Question 5**
---
Write a SQL query to find the number of employees whose age is greater than 32.

```
select count(id)as COUNT from employee
where age>32;
```

**Output:**

<img width="432" height="410" alt="image" src="https://github.com/user-attachments/assets/0b754c82-9dbd-4e53-ac5c-fcec1a7c5ed4" />


**Question 6**
---
Write a SQL query to find the youngest employee in the company?

```
select name as Employee_Name,min(Age) as Age from employee;
```

**Output:**

<img width="655" height="410" alt="image" src="https://github.com/user-attachments/assets/19b1074a-9d9d-4fcc-aea2-cc83e75ef7f9" />

**Question 7**
---
Write a SQL query to find the total income of employees aged 40 or above.

```
select sum(income) as total_income from employee
where age>=40;
```

**Output:**

<img width="513" height="408" alt="image" src="https://github.com/user-attachments/assets/d51e885f-bcae-4cd8-8908-5f91a19f49d4" />


**Question 8**
---
Write the SQL query that achieves the selection of category and calculates the sum of the product of price and category ID as Revenue for each category from the "products" table, and includes only those products where the total revenue is greater than 25.

```
select category_id,sum(price*category_id) as Revenue from products
group by category_id having Revenue>25;
```

**Output:**

<img width="645" height="519" alt="image" src="https://github.com/user-attachments/assets/70e09921-184d-4d63-8b51-9263b88f46b6" />


**Question 9**
---
Write the SQL query that accomplishes the grouping of data by addresses, calculates the sum of salaries for each address, and excludes addresses where the total salary sum is not greater than 2000.

```
select address, SUM(salary) from customer1
group by address having SUM(salary)>2000;
```

**Output:**

<img width="702" height="549" alt="image" src="https://github.com/user-attachments/assets/01bb9cdc-7260-4d72-9b34-6ebbceb240c1" />


**Question 10**
---
Write the SQL query that accomplishes the grouping of data by joining date (jdate), calculates the average work hours for each date, and excludes dates where the average work hour is not less than 10.

```
select jdate,AVG(workhour) from employee1 
group by jdate having avg(workhour)<10;
```

**Output:**

<img width="627" height="428" alt="image" src="https://github.com/user-attachments/assets/bc32e67f-29b7-4e53-a67f-361288a3df91" />



## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
