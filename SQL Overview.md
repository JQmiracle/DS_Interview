# SQL 
<img width="643" alt="Screenshot 2024-03-26 at 14 06 04" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/3085565f-e3cb-41cf-81d1-45e47972dda1">

## SQL Syntax
- **Primary Key**: Not Null; No Duplicates; Can be consisted of multiple columns
- **Row**: observation, trail, record; **Column**: feature, variable; **Cell**: entity
<img width="630" alt="Screenshot 2024-03-26 at 14 12 20" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/87b16ddf-10be-46b9-9002-f638b82d6f8a">

## Basic Syntax
<img width="424" alt="Screenshot 2024-03-26 at 14 21 32" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/0dfc6006-29f4-4aa2-8a90-7911c0c655a1">

## 1. SELECT
- CONCAT(Country, ' ', City)
- Country ||' '|| City
<img width="679" alt="Screenshot 2024-03-26 at 14 25 31" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/c4c52f08-796e-4599-8b44-5601bf273515">

<img width="644" alt="Screenshot 2024-03-26 at 14 24 46" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/88dbb3a0-76aa-49ea-88c4-70c7bc3bb5f5">

## 2. FILTER

<img width="870" alt="Screenshot 2024-03-26 at 14 33 50" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/e0238d5a-b0c2-4501-b603-4a7f933304ea">

### Where XXX
- CustomerName LIKE 'B%'
- LEFT(CustomerName, 1) = 'B'
- PostalCode LIKE '%9'
- RIGHT(PostalCode :: varchar, 1) = '9'
- CAST(PostalCode AS varchar)

## 3. AGGREGATION
<img width="1003" alt="Screenshot 2024-03-26 at 14 38 06" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/4752cd62-d8d3-4a18-b8c8-96d61bc45290">

### GROUP BY XXX
- AVG
- COUNT
- MAX
- MIN
- SUM

<img width="1162" alt="Screenshot 2024-03-26 at 14 37 42" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/50befff0-f1d5-4f6f-ba90-8b8a10c03527">

## 4. SORTING AND GROUPING
<img width="701" alt="Screenshot 2024-03-26 at 14 43 27" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/57da0307-a79a-42f1-9cc5-d7769e035a9a">

### ORDER BY
- come in the last of the order
- Default is ASC
- Careful on the ORDER BY columns data type
  - **when column has null, null will be ranked as smallest**

## 5. HAVING

<img width="915" alt="Screenshot 2024-03-26 at 15 30 51" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/e82d13e8-5e2e-4ea4-94d8-d8f49e15f118">

- HAVING after GROUP BY
- HAVING is a filter of AGG Function


## 6. Order of Execution 

<img width="787" alt="Screenshot 2024-03-26 at 15 31 26" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/cfcc366b-dd23-4df7-8f0d-97ea9404144f">

- FROM + JOIN
- WHERE
- GROUP BY
- HAVING
- SELECT (**Windows Function Happens Here**)
- ORDER BY
- LIMIT


## 7. JOIN

- LEFT JOIN 首选！！
- 为什么分很多表格？？
  - 如果都储存在一张表，Data Dimension会很大，导致data redundancy
  - 如果都储存在一张表，并且更新表格的信息， Update中用到的人力成本和数据库调度成本会很大，导致Data Integrity
 
<img width="765" alt="Screenshot 2024-03-26 at 16 44 30" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/3686c43f-474f-4480-979f-1a29b890d24c">
<img width="290" alt="Screenshot 2024-03-26 at 16 45 12" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/8f5e9201-f953-4da3-b5d1-d2b91ea04652">
<img width="958" alt="Screenshot 2024-04-08 at 15 27 12" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/b3eed7b9-53f7-4498-b6b9-143e1d68aa53">


## 8. UNION & UNION ALL

- Vertical Stack of Two Results
- Columns have to be the same type
- **UNION** 去除 duplicate （O(n) Time Complexity）
- **UNION ALL** 包含所有 （O（1）Time Complexity）--> **速度更快**
<img width="740" alt="Screenshot 2024-03-26 at 16 49 49" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/3b9c19ec-d068-4841-a574-11d633d4cadb">


## 9. Data Definition Language (Create Table, Alter Table, Delete Table)

- Drop Table: **最危险，直接放到垃圾箱** completely removes everything associated with the table - data and structure.
- Delete Table：先读取Table信息，only deletes the data within the table but leaves the table structure and its definitions (like column names, data types, etc.) in the database.
- Truncate Table：不读取Table信息，delete all rows from a table, but it does not remove the table itself from the database. It is similar to the DELETE FROM command without a WHERE clause but is often more efficient.

<img width="724" alt="Screenshot 2024-04-01 at 13 22 39" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/7f2ddf00-1eec-43ac-808f-2e9f29fec3b8">


## 10. Subquery and Temp Table (*****)
<img width="602" alt="Screenshot 2024-04-01 at 13 34 02" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/50bfbb30-0d2d-4baf-a275-c85419908b35">


```SQL

SELECT ProductID
FROM Table
ORDER BY Price desc
LIMIT 1 OFFSET 3

```

## 11. Case When
- Don't Forget **'end'** during the interview
- Case When Can be used within **agg**

<img width="623" alt="Screenshot 2024-04-01 at 13 35 44" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/0423136b-2d8b-4e06-abbd-4aa94933619f">



```SQL

WITH Temp AS (
SELECT *, CASE WHEN Price >= 100 THEN 'high_end'
            WHEN Price Between 20 AND 100 THEN 'middle_end'
            ELSE 'low_end' END AS category
FROM Table
)

SELECT category, COUNT(1) as num_product
FROM Temp
GROUP BY category

```

## 12. Windows Function

<img width="711" alt="Screenshot 2024-04-01 at 13 53 17" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/571b8196-e1c3-4bc1-947c-700b7a56e387">

<img width="627" alt="Screenshot 2024-04-01 at 13 54 29" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/9012c853-8678-44fc-b285-f1b811cd7031">
<img width="456" alt="Screenshot 2024-04-01 at 13 59 07" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/f5fa7c6a-af48-461f-a703-8690f93db8ba">

```SQL

WITH Temp AS (
SELECT *, dense_rank() over (order by price desc) as rnk
FROM Table
)

SELECT productID
FROM Temp
WHERE rnk = 4

```
<img width="464" alt="Screenshot 2024-04-01 at 13 59 16" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/89de36c9-df5d-42d1-8afc-549a83a40580">

```SQL

WITH Temp AS (
SELECT *, dense_rank() over (partition by categoryID order by price desc) as rnk
FROM Table
)

SELECT categroyID, productID
FROM Temp
WHERE rnk = 4

```

## 13. More on NULL value in SQL

<img width="902" alt="Screenshot 2024-04-08 at 15 13 37" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/bab30475-8fcd-4181-be19-771c7611cf15">

<img width="1072" alt="Screenshot 2024-04-08 at 15 12 52" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/1d0926b6-e3fd-4442-8711-d62bc6ececf9">
<img width="968" alt="Screenshot 2024-04-08 at 15 13 20" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/e8a7410e-9263-4202-bfca-c4b4065436a0">


## 14. Date Functions
```SQL
SELECT DATE_ADD("2017-06-15", INTERVAL 10 DAY);

# DATE_ADD("2017-06-15", INTERVAL 10 DAY)
# 2017-06-25


SELECT DATE_SUB("2017-06-15", INTERVAL 10 DAY);

# DATE_SUB("2017-06-15", INTERVAL 10 DAY)
# 2017-06-05


SELECT DATEDIFF("2017-06-25", "2017-06-15");
# DATEDIFF("2017-06-25", "2017-06-15")
# 10


SELECT CURDATE();
# The CURDATE() function returns the current date.
# Note: The date is returned as "YYYY-MM-DD" (string) or as YYYYMMDD (numeric).
# Note: This function equals the CURRENT_DATE() function.


The NOW();
# returns the current date and time.
# Note: The date and time is returned as "YYYY-MM-DD HH:MM:SS" (string) or as YYYYMMDDHHMMSS.uuuuuu (numeric).


SELECT DATE("2017-06-15 09:34:21");
# DATE("2017-06-15 09:34:21")
# 2017-06-15


CAST(date_col as DATE);


SELECT MONTH("2017-06-15 09:34:21");
# MONTH("2017-06-15 09:34:21")
# 6


SELECT YEAR("2017-06-15 09:34:21");
YEAR("2017-06-15 09:34:21")
2017

```
