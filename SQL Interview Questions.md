# Top SQL Interview Questions

## 1. HR Phone Screen SQL Interview

<img width="720" alt="Screenshot 2024-03-26 at 15 34 20" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/77b74219-f981-44c4-bda6-e444fa658953">

### 1. **Difference between LEFT JOIN and LEFT OUTER JOIN?**
  - NO DIFFERENCE!!!
 
### 2. **When do the left join, what if the key is not present in the right table?**
  - 左表格所有的Row都还在，右表格other columns will be NULL

### 3. **LEFT ANTI JOIN**
<img width="705" alt="Screenshot 2024-03-26 at 16 58 11" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/3074da31-1780-4a43-9662-912baea08168">

### 4. What function can fill null value?
- **CASE WHEN col1 IS NULL THEN '1'**
- **ISNULL/IFNULL(col1, 0)**
- **COALESCE(Col1, 0)**
- **COALESCE(Col1, Col2, 0)**
  - if Col1 is null, it replaces null with Col2
  - if Col1 and Col2 are null, it replaces null with 0
<img width="594" alt="Screenshot 2024-04-08 at 14 35 09" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/8096ac02-c928-482f-8e73-9bb342cacc28">

### 5. **Between ... And...**
  - 闭区间
 
 
### 6. **Find the name of employees that begin with 'z' or 'Z'**
  - name LIKE 'z%' OR name LIKE 'Z%'
  - LOWER(name) LIKE 'z%'
 
### 7. **What is the difference between NULL and 0?**
  - **NULL is used in SQL to represent a missing, unknown, or inapplicable value in a database**. It is a marker or placeholder used to indicate that the data value does not exist in the database. Importantly, NULL signifies the absence of any data type and is not equivalent to zero, an empty string, or any other value. Operations involving NULL values usually result in NULL, underlining the concept that an operation involving an unknown value yields an unknown result.
  - **Comparisons**: In SQL, comparing any value (including zero) with NULL using standard comparison operators (e.g., =, <, >) will result in NULL, which is interpreted as false in the context of a where clause. This necessitates the use of the **IS NULL or IS NOT NULL** operators to **properly handle NULL values in conditions.**
  - **Arithmetic operations**: Arithmetic operations involving NULL (e.g.,**NULL + 10) result in NULL**, while operations with zero follow standard arithmetic rules (e.g., 0 + 10 results in 10).
  - **Aggregate functions**: Most aggregate functions (like **SUM, AVG) ignore NULL values but treat zero as a legitimate value**. For example, the **average of {NULL, 5, 10} is 7.5, not including the NULL in the calculation**, whereas the average of {0, 5, 10} includes zero, resulting in an average of 5.

### 8. What is the primary key?
  - Not Null
  - No Duplicates
  - Combo Primary Key


### 9. On vs. Where Condition?
<img width="909" alt="Screenshot 2024-04-08 at 15 00 36" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/64336eef-6cfb-4d8a-a893-64f76a09d134">
- 第二个方式更快：在表格join之前，把ORDER表格做了**Partition**分割，Table Size变小，执行速度更快


### 10. UNION VS. UNION ALL
- Vertical Stack of Two Results
- Columns have to be the same type
- UNION 去除 duplicate （O(n) Time Complexity）
- UNION ALL 包含所有 （O（1）Time Complexity）--> 速度更快

### 11. UNION VS. JOIN
- UNION:Vertical Stack of Two Results
- JOIN: Horizontal Stack of Two Results


## 2. Quiz
<img width="877" alt="Screenshot 2024-03-26 at 15 36 36" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/8e97d86a-1866-4314-89f2-8c44d0ca2a40">

```SQL
## Primary Key is item_no
SELECT vendor, vendor_name, COUNT(distinct item_no) as num_of_offers, AVG(bottle_price) as avg_price
FROM Table
GROUP BY vendor, vendor_name
ORDER BY num_of_offers desc


```

<img width="542" alt="Screenshot 2024-04-02 at 08 53 25" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/c6d45495-e49a-4f4a-99bb-60d3a0340d46">

### Orders
<img width="1316" alt="Screenshot 2024-04-02 at 09 18 22" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/80516bf0-4527-4a17-b2ce-b2c106c1603c">

### OrderDetails
<img width="1376" alt="Screenshot 2024-04-02 at 09 18 32" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/52fea4c7-ac1f-4b48-9825-c4cd0da68697">

```SQL

SELECT o.EmployeeID, COUNT(o.OrderID) as total_orders, SUM(od.Quantity) as total_quantity
FROM Orders o 
LEFT JOIN OrderDetails od
ON o.OrderID = od.OrderID
GROUP BY o.EmployeeID


```

### Employees
<img width="1025" alt="Screenshot 2024-04-02 at 09 18 38" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/56bd5cc1-bacf-4aa2-a313-9b06220dbc69">

```SQL

SELECT o.EmployeeID, CONCAT(e.LastName, ' ', e.FirstName) AS name, COUNT(o.OrderID) as total_orders, SUM(od.Quantity) as total_quantity
FROM Orders o 
LEFT JOIN OrderDetails od
ON o.OrderID = od.OrderID
LEFT JOIN Employees e
ON o.EmployeesID = e.Employees
GROUP BY o.EmployeeID, name


```

```SQL

SELECT o.EmployeeID, CONCAT(e.LastName, ' ', e.FirstName) AS name, COUNT(o.OrderID) as total_orders, SUM(od.Quantity) as total_quantity
FROM Orders o 
LEFT JOIN OrderDetails od
ON o.OrderID = od.OrderID
LEFT JOIN Employees e
ON o.EmployeesID = e.Employees
GROUP BY o.EmployeeID, name
ORDER BY total_orders DESC
LIMIT 10

```


## 3. Practice Questions
<img width="1044" alt="Screenshot 2024-04-08 at 15 29 29" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/6c1eecb9-edd7-4318-a01b-8711dcb90f4f">


```SQL
WITH temp AS(
SELECT
  CONCAT(YEAR(transaction_date), MONTH(transaction_date) AS year_month ,
  from_user_id,
  COUNT(transaction_id) as num_email_sent
FROM email_transaction
GROUP BY 1, 2
)
SELECT
  num_email_sent,
  COUNT(DISTINCT from_user_id) AS num_from_user_id
FROM temp
GROUP BY num_email_sent
ORDER BY num_email_sent desc
LIMIT 1

```

```SQL
## What is the distribution of likes everyday?
## 两次GROUP BY
## GROUP BY user_id, timestamp -> COUNT(Likes) -> total_num_likes
## GROUP BY total_num_likes, timestamp -> COUNT(user_id) -> total_num_users
```
<img width="339" alt="Screenshot 2024-04-08 at 16 01 47" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/cca8f681-11e5-4182-8942-df3b95f31271">


<img width="1003" alt="Screenshot 2024-04-08 at 16 05 30" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/1a947770-9366-4c89-b3f3-ea3f3184c2d0">


```SQL

SELECT
  s.sender_IP_city, COUNT(s.transaction_id) as number_of_emails, SUM(spam) as number_of_spams, AVG(spam * 1.0) as spam_rate
FROM email_transaction e
LEFT JOIN spam s
ON e.transaction_id = s.transaction_id
WHERE e.transaction_date > '2018-01-01'
GROUP BY s.sender_IP_city


```

<img width="1280" alt="Screenshot 2024-04-18 at 12 16 58" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/fd138d20-6077-4af9-a996-7758dba5d910">


```SQL
## Solution 1 (Windows Functions):
SELECT
  CAST(CONCAT(SUBSTRING(year_month,1,4), '-', SUBSTRING(year_month,5,2), '-', '01') AS DATE) AS year_month_2,
  num_spam,
  sum(num_spam) over(group by year_month) AS cum_num_spam
FROM result_table r
WHERE r.LEFT(year_mouth,4) >= 2018 AND r.state = 'CA'
```

```SQL
## Solution 2 (Self Join):
WITH t1 AS (
  SELECT
    CAST (CONCAT (SUBSTRING(year_month, 1,4), '-', SUBSTRING(year_month, 5 ‚2),'-01') as DATE) AS year _month_2,
    num_spam
  FROM result_table
)
SELECT
  a.year_month_2,
  a.num_spam,
  SUM(b.num_spam) AS cum_num_spam
FROM t1 a
LEFT JOIN t1 b
ON a.year_month_2 >= b.year_month_2
GROUP BY 1, 2
ORDER BY 1
```
<img width="285" alt="Screenshot 2024-04-18 at 13 01 25" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/ad4b3618-6e9a-4ae9-8a27-2a751bd82496">




<img width="897" alt="Screenshot 2024-04-18 at 13 11 48" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/1be9b9a6-5932-4f09-bb51-3b7c534aaf14">

### 做题习惯：大表格 LEFT JOIN 小表格
```SQL

WITH temp AS (
  SELECT
    s.sender_IP_city,
    e.from_user_id,
    COUNT(1) as num_email_sent,
  FROM email_transaction e
  LEFT JOIN spam s 
  ON e.transaction_id = s.transaction_id
  LEFT JOIN city_to_state c
  ON s.sender_IP_city = c.city
  WHERE c.state = 'CA'
  GROUP BY 1, 2
),
temp2 AS (
  SELECT *, ROW_NUMBER() OVER (PARTITION BY sender_IP_city ORDER BY num_email_sent DESC) as rr
  FROM temp
)
SELECT *
FROM temp2
WHERE rr <= 3

```


