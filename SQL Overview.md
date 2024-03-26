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
