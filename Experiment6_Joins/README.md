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
<img width="849" height="815" alt="image" src="https://github.com/user-attachments/assets/d2d52d1c-db2a-40b3-bad3-10c06f871ee2" />


```sql
select p.first_name
from PATIENTS as p
inner join surgeries as a on p.patient_id=a.patient_id
where a.surgery_date='2024-01-15';
```

**Output:**

<img width="901" height="492" alt="image" src="https://github.com/user-attachments/assets/6d522e9d-5863-4c2f-8890-b322496eae3f" />


**Question 2**
---
<img width="866" height="797" alt="image" src="https://github.com/user-attachments/assets/a0944b25-a578-4922-b369-bacda798d9f5" />


```sql
SELECT n.nurse_id, d.department_name
FROM nurses AS n
INNER JOIN departments AS d ON n.department_id = d.department_id
WHERE n.first_name = 'David' AND n.last_name = 'Moore';
```

**Output:**

<img width="890" height="495" alt="image" src="https://github.com/user-attachments/assets/22cedb5c-8f13-4459-89ef-af40182d6e58" />


**Question 3**
---
<img width="885" height="864" alt="image" src="https://github.com/user-attachments/assets/ea20b316-c134-4b52-8d3a-8eb89b4a3197" />


```sql
SELECT
    p.first_name AS patient_name,
    d.specialization AS Doctor_specialization
FROM
    patients AS p
INNER JOIN
    doctors AS d ON p.doctor_id = d.doctor_id
WHERE
    p.admission_date BETWEEN '2024-01-01' AND '2024-01-31';
```

**Output:**

<img width="908" height="503" alt="image" src="https://github.com/user-attachments/assets/7e89763c-da62-4160-adb2-b4d1aeb4da1a" />


**Question 4**
---
<img width="881" height="922" alt="image" src="https://github.com/user-attachments/assets/9edbcc33-ef4b-4b2f-a22c-4298d8c99f63" />


```sql
SELECT c.cust_name, c.city, c.grade, s.name AS Salesman, s.city AS city
FROM customer c
JOIN salesman s ON c.salesman_id = s.salesman_id
WHERE c.grade < 300
ORDER BY c.customer_id ASC;
```

**Output:**

<img width="864" height="786" alt="image" src="https://github.com/user-attachments/assets/6e12a8de-ca7c-4b08-abb4-9923dc679e32" />


**Question 5**
---
<img width="849" height="800" alt="image" src="https://github.com/user-attachments/assets/c91561e8-748c-4ed1-8a81-a1086a462a36" />


```sql
SELECT c.cust_name, c.city, o.ord_no, o.ord_date, o.purch_amt
FROM customer c
LEFT JOIN orders o
ON c.customer_id = o.customer_id
WHERE c.city = 'London';
```

**Output:**

<img width="899" height="579" alt="image" src="https://github.com/user-attachments/assets/eab2b296-babf-489d-a0e9-79d6b4a9a1f9" />


**Question 6**
---
<img width="879" height="871" alt="image" src="https://github.com/user-attachments/assets/4f2f2a1d-7f40-4c37-acfc-65689e7fbdbb" />


```sql
SELECT patient_name.first_name as patient_name, t.test_name
FROM patients AS patient_name
INNER JOIN test_results AS t
ON patient_name.patient_id = t.patient_id;
```

**Output:**

<img width="828" height="682" alt="image" src="https://github.com/user-attachments/assets/fd617ff2-c608-4faa-879f-710c567c6caa" />


**Question 7**
---
<img width="885" height="889" alt="image" src="https://github.com/user-attachments/assets/8f4373a9-32da-42cf-93ac-e0576b0d1089" />


```sql
SELECT
  a.ord_no,
  a.purch_amt,
  a.ord_date,
  b.cust_name,
  b.city AS customer_city,
  b.grade,
  c.name AS salesman_name,
  c.city AS salesman_city,
  c.commission
FROM orders a
JOIN customer b
  ON a.customer_id = b.customer_id
JOIN salesman c
  ON a.salesman_id = c.salesman_id;
```

**Output:**

<img width="857" height="830" alt="image" src="https://github.com/user-attachments/assets/62d0ac93-6cfd-4c79-b3e9-d0095519c62b" />


**Question 8**
---
<img width="889" height="872" alt="Screenshot 2025-11-04 205007" src="https://github.com/user-attachments/assets/6e532c8d-6849-4356-ae00-434dc6eb46f3" />


```sql
SELECT c.cust_name, o.ord_no, o.ord_date, o.purch_amt
FROM customer c
LEFT JOIN orders o
ON c.customer_id = o.customer_id;
```

**Output:**

<img width="881" height="935" alt="image" src="https://github.com/user-attachments/assets/27355ac3-7ea1-44fb-b458-cee3bbe28b2b" />


**Question 9**
---
<img width="884" height="956" alt="image" src="https://github.com/user-attachments/assets/67a63cd0-36e2-4ab3-a299-348308dad182" />


```sql
SELECT
    salesman.name as Salesman,
    customer.cust_name,
    salesman.city
FROM
    salesman
JOIN
    customer ON salesman.city = customer.city;
```

**Output:**

<img width="898" height="785" alt="image" src="https://github.com/user-attachments/assets/1b3d577b-2a87-42b9-b277-4d60aa59f17e" />


**Question 10**
---
<img width="884" height="945" alt="image" src="https://github.com/user-attachments/assets/abd2ba5e-9dd9-42e7-b353-3238462e138d" />


```sql
SELECT 
    c.cust_name AS "cust_name",
    c.city AS "city",
    c.grade AS "grade",
    s.name AS "Salesman",
    s.city AS "city"
FROM 
    customer c
JOIN 
    salesman s
ON 
    c.salesman_id = s.salesman_id
ORDER BY 
    c.customer_id ASC;

```

**Output:**
<img width="915" height="943" alt="image" src="https://github.com/user-attachments/assets/95aa851c-c64d-4af5-8c90-d2bdb122e403" />



## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
