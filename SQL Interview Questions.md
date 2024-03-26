# Top SQL Interview Questions

## 1. HR Phone Screen SQL Interview

<img width="720" alt="Screenshot 2024-03-26 at 15 34 20" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/77b74219-f981-44c4-bda6-e444fa658953">

## 2. Quiz
<img width="877" alt="Screenshot 2024-03-26 at 15 36 36" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/8e97d86a-1866-4314-89f2-8c44d0ca2a40">

```SQL
## Primary Key is item_no
SELECT vendor, vendor_name, COUNT(distinct item_no) as num_of_offers, AVG(bottle_price) as avg_price
FROM Table
GROUP BY vendor, vendor_name
ORDER BY num_of_offers desc

```
