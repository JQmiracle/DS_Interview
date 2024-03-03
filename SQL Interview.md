# SQL Interview

## 1. Top N Problems

- **Top N Records**
  - Query the 5th largest value in the table t.
  - Assume the values are unique, and there are more than 5 values in the table.

```SQL
-- Select values from table t and sort values in descending order.
-- Sort the numbers, use OFFSET , and LIMIT to return the 5th row.
SELECT value
FROM t
ORDER BY value DESC 
LIMIT 1
OFFSET 4;
```

- **Top N Per Category**

![Screenshot 2024-03-02 at 16.30.23](/Users/moonqj/Library/Application Support/typora-user-images/Screenshot 2024-03-02 at 16.30.23.png)

![Screenshot 2024-03-02 at 16.30.53](/Users/moonqj/Library/Application Support/typora-user-images/Screenshot 2024-03-02 at 16.30.53.png)

```sql

WITH avg_ratings AS ( 
SELECT
name, city,
AVG(rating * 1.0) AS avg_rating 
FROM rating
GROUP BY name, city
),

rating_rank AS ( 
SELECT
name, city, avg_rating,
DENSE_RANK() OVER(PARTITION BY city ORDER BY avg_rating DESC) as rk 
FROM avg_ratings
)

SELECT
name, city, avg_rating
FROM rating_rank 
WHERE rk <= 5;


```



## 2. **Ratios**

### Example: Subscription Rate

### ![Screenshot 2024-03-02 at 16.51.34](/Users/moonqj/Library/Application Support/typora-user-images/Screenshot 2024-03-02 at 16.51.34.png)

```sql
SELECT
COUNT(user_id) * 1.0 / (SELECT COUNT(user_id) FROM subscription) AS ratio
FROM subscription 
WHERE premium = 'TRUE';



SELECT
SUM(CASE WHEN premium = 'TRUE' THEN 1 ELSE 0 END) * 1.0 / COUNT(user_id) AS ratio
FROM subscription;

-- AVG (Case When...Then...Else... End as) -- Best
SELECT
AVG(CASE WHEN premium = 'TRUE' THEN 1.0 ELSE 0.0 END)
AS ratio
FROM subscription;
```

### Example: Immediate Order ([1174. Immediate Food Delivery II](https://leetcode.com/problems/immediate-food-delivery-ii/))

```sql
WITH ordered_delivery
AS (SELECT
*,
ROW_NUMBER() OVER (PARTITION BY customer_id ORDER BY order_date) AS order_rk
FROM delivery)

SELECT 
AVG(CASE
WHEN order_date = pref_delivery_date THEN 1.0
ELSE 0.0 END
) AS immediate_percentage
FROM ordered_delivery
WHERE order_rk = 1 # first order
```



## 3. SQL Categories

Of course, the best way to make sure that you have these 3 categories down is to practice. This post has a list of practice SQL problems to help you do just that. They are broken down into the three categories discussed in the video.

### Computing Ratios

- [LeetCode 1174 Immediate Food Delivery II](https://leetcode.com/problems/immediate-food-delivery-ii/)
- [LeetCode 1322 Ads Performance](https://leetcode.com/problems/ads-performance)
- [LeetCode 1211 Queries Quality and Percentage](https://leetcode.com/problems/queries-quality-and-percentage)

### Data Categorization![Screenshot 2024-03-02 at 17.14.03](/Users/moonqj/Library/Application Support/typora-user-images/Screenshot 2024-03-02 at 17.14.03.png)

- [LeetCode 1393. Capital Gain Loss](https://leetcode.com/problems/capital-gainloss)
- [LeetCode 1907. Count Salary Categories](https://leetcode.com/problems/count-salary-categories)
- [LeetCode 1468. Calculate Salaries](https://leetcode.com/problems/calculate-salaries)
- [LeetCode 1212. Team Scores in Football Tournament](https://leetcode.com/problems/team-scores-in-football-tournament)

### Cumulative Sums![Screenshot 2024-03-02 at 17.21.17](/Users/moonqj/Library/Application Support/typora-user-images/Screenshot 2024-03-02 at 17.21.17.png)

- [LeetCode 1097. Game Play Analysis V](https://leetcode.com/problems/game-play-analysis-v) (Hard)
- [LeetCode 1454. Active Users](https://leetcode.com/problems/active-users)
- [LeetCode 579. Find cumulative salary of an employee](https://leetcode.com/problems/find-cumulative-salary-of-an-employee) (Hard)

For even more practice, the following problems will help you practice the self join which you can use to solve cumulative sum problems.

### Self Join

- [LeetCode 1270 All People Report to the Given Manager](https://leetcode.com/problems/all-people-report-to-the-given-manager)
- [LeetCode 1811 Find Interview Candidates](https://leetcode.com/problems/find-interview-candidates)
- [LeetCode 1285 Find the Start and End Number of Continuous Ranges](https://leetcode.com/problems/find-the-start-and-end-number-of-continuous-ranges)







## 4. Windows Function

### **Aggregate Function: Sum, Avg, Count, Min, Max**

![Screenshot 2024-03-03 at 15.06.36](/Users/moonqj/Library/Application Support/typora-user-images/Screenshot 2024-03-03 at 15.06.36.png)



![Screenshot 2024-03-03 at 15.20.50](/Users/moonqj/Library/Application Support/typora-user-images/Screenshot 2024-03-03 at 15.20.50.png)



### **Ranking Functions**: Row_Number, Rank, Dense_Rank

![Screenshot 2024-03-03 at 15.07.54](/Users/moonqj/Library/Application Support/typora-user-images/Screenshot 2024-03-03 at 15.07.54.png)



![Screenshot 2024-03-03 at 15.21.24](/Users/moonqj/Library/Application Support/typora-user-images/Screenshot 2024-03-03 at 15.21.24.png)





### **Analytic Functions:** LAG and LEAD

![Screenshot 2024-03-03 at 15.09.06](/Users/moonqj/Library/Application Support/typora-user-images/Screenshot 2024-03-03 at 15.09.06.png)



![Screenshot 2024-03-03 at 15.10.25](/Users/moonqj/Library/Application Support/typora-user-images/Screenshot 2024-03-03 at 15.10.25.png)







![Screenshot 2024-03-03 at 14.59.56](/Users/moonqj/Library/Application Support/typora-user-images/Screenshot 2024-03-03 at 14.59.56.png)



![Screenshot 2024-03-03 at 15.00.16](/Users/moonqj/Library/Application Support/typora-user-images/Screenshot 2024-03-03 at 15.00.16.png)



![Screenshot 2024-03-03 at 15.00.33](/Users/moonqj/Library/Application Support/typora-user-images/Screenshot 2024-03-03 at 15.00.33.png)



![Screenshot 2024-03-03 at 15.01.48](/Users/moonqj/Library/Application Support/typora-user-images/Screenshot 2024-03-03 at 15.01.48.png)



![Screenshot 2024-03-03 at 15.01.10](/Users/moonqj/Library/Application Support/typora-user-images/Screenshot 2024-03-03 at 15.01.10.png)

![Screenshot 2024-03-03 at 15.04.09](/Users/moonqj/Library/Application Support/typora-user-images/Screenshot 2024-03-03 at 15.04.09.png)

![Screenshot 2024-03-03 at 15.04.44](/Users/moonqj/Library/Application Support/typora-user-images/Screenshot 2024-03-03 at 15.04.44.png)

![Screenshot 2024-03-03 at 15.05.27](/Users/moonqj/Library/Application Support/typora-user-images/Screenshot 2024-03-03 at 15.05.27.png)