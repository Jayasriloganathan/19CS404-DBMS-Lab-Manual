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
<img width="1033" height="251" alt="image" src="https://github.com/user-attachments/assets/b9ca91cb-342d-4999-afab-d533287db0fd" />


```
select Address ,count(*) as TotalPatients from Patients group by Address;
```

**Output:**

<img width="757" height="427" alt="image" src="https://github.com/user-attachments/assets/c06a09d4-008e-422e-abe9-c3c5702cbf14" />


**Question 2**
<img width="1007" height="225" alt="image" src="https://github.com/user-attachments/assets/7d3f7804-f3b0-4dc0-8c8c-0bb9e2a087d5" />

```
select PatientID, count(*)  as TotalMedications from Prescriptions group by PatientID;
```

**Output:**

<img width="712" height="762" alt="image" src="https://github.com/user-attachments/assets/a44d8889-8db3-4043-9096-b28bc1985899" />


**Question 3**
```
What is the average duration of insurance coverage for patients covered by each insurance company?

Sample table:Insurance Table

name               type
-----------------  ----------
InsuranceID        INTEGER
PatientID          INTEGER
InsuranceCompany   TEXT
PolicyNumber       TEXT
PolicyHolder       TEXT
StartDate          DATE
EndDate            DATE
```

```
select InsuranceCompany,avg(EndDate-StartDate) as AvgCoverageDurationDays from Insurance group by InsuranceCompany;
```

**Output:**

<img width="897" height="672" alt="image" src="https://github.com/user-attachments/assets/4457d0f6-c4f1-467d-b4da-f035ec3a7b53" />


**Question 4**
```
Write a SQL query to find the total number of unique cities in the customer table?

Table: customer

name        type
----------  ----------
id          INTEGER
name        TEXT
city        TEXT
email       TEXT
phone       INTEGER
```

```
select count(distinct city) as unique_cities from customer;
```

**Output:**
<img width="480" height="297" alt="image" src="https://github.com/user-attachments/assets/e0516096-8c05-46bd-8645-75cf27b2e3eb" />



**Question 5**
<img width="946" height="282" alt="image" src="https://github.com/user-attachments/assets/8cf22fee-8d29-429e-82cd-dc4b79096c2a" />


```
select count(*) as COUNT from customer where city!='Noida';
```

**Output:**

<img width="380" height="307" alt="image" src="https://github.com/user-attachments/assets/b2f4f2a5-b44d-4ea0-b2ed-c78860fafb75" />


**Question 6**
```
Write a SQL query to Calculate the average income of the employees with names starting with 'A': 

Table: employee

name        type
----------  ----------
id          INTEGER
name        TEXT
age         INTEGER
city        TEXT
income      INTEGER
```

```
select avg(income) as avg_income from employee where name like 'A%';
```

**Output:**

<img width="407" height="312" alt="image" src="https://github.com/user-attachments/assets/f8d21420-da06-479c-b743-9a2c5420da32" />


**Question 7**
```
Write a SQL query to find  how many employees work in California?

Table: employee

name        type
----------  ----------
id          INTEGER
name        TEXT
age         INTEGER
city        TEXT
income      INTEGER
 
```

```
select count(*) as employees_in_california from employee where city='California';
```

**Output:**

<img width="640" height="317" alt="image" src="https://github.com/user-attachments/assets/846c1e15-e175-44d6-b838-58487f7c59bc" />


**Question 8**
<img width="1162" height="260" alt="image" src="https://github.com/user-attachments/assets/0e004ec6-0b50-4056-8d19-07130f9e4283" />


```
select (age/5)*5 as age_group, min(salary) as "MIN(salary)" from customer1 group by (age/5)*5 having min(salary)<2000;
```

**Output:**

<img width="613" height="321" alt="image" src="https://github.com/user-attachments/assets/8e364c17-ace9-48fd-ba8a-cfcf185e36b7" />


**Question 9**
<img width="1188" height="275" alt="image" src="https://github.com/user-attachments/assets/8f26e234-52fb-4750-b725-15138fbf5582" />


```
select category_id, sum(price) as Total_Cost from products group by category_id having Total_Cost>50;
```

**Output:**

<img width="600" height="341" alt="image" src="https://github.com/user-attachments/assets/1739ea89-ea14-4df6-8c8e-4b0d4e04b93d" />


**Question 10**

<img width="1221" height="261" alt="image" src="https://github.com/user-attachments/assets/b8f8c632-6488-49fe-8bea-dd2fb754e38a" />


```
select jdate,max(workhour) as "MAX(workhour)" from employee1 group by jdate having max(workhour)>12;
```

**Output:**

<img width="652" height="377" alt="image" src="https://github.com/user-attachments/assets/5faca0d6-13d7-4bd6-b0ef-cfb7243019bc" />



## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
