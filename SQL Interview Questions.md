# Top SQL Interview Questions

## 1. HR Phone Screen SQL Interview

<img width="720" alt="Screenshot 2024-03-26 at 15 34 20" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/77b74219-f981-44c4-bda6-e444fa658953">


- **Difference between LEFT JOIN and LEFT OUTER JOIN?**
  - NO DIFFERENCE!!!
 
- **When do the left join, what if the key is not present in the right table?**
  - 左表格所有的Row都还在，右表格other columns will be NULL

- **LEFT ANTI JOIN**
<img width="705" alt="Screenshot 2024-03-26 at 16 58 11" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/3074da31-1780-4a43-9662-912baea08168">

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
