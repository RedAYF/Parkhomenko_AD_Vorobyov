## Task - 570

```sql
-- Write your PostgreSQL query statement below
SELECT e1.name FROM Employee AS e1
INNER JOIN Employee AS e2 ON e1.id = e2.managerId
GROUP BY e2.managerId, e1.name
HAVING COUNT(e2.managerId) >= 5;
```
## Task - 1934

```sql
SELECT s.user_id, ROUND(AVG(CASE WHEN c.action = 'confirmed' THEN 1.00 ELSE 0.00 END),2) AS confirmation_rate
FROM Signups AS s
LEFT JOIN Confirmations AS c ON s.user_id = c.user_id
GROUP BY s.user_id;
```
## Task - 1193. Monthly Transactions I

```sql
-- Write your PostgreSQL query statement below
SELECT TO_CHAR(trans_date,'YYYY-MM') AS month, country, 
COUNT(*) AS trans_count, 
SUM (CASE STATE WHEN 'approved' THEN 1 WHEN 'declined' THEN 0 END) AS approved_count, SUM(amount) AS trans_total_amount, SUM (CASE STATE WHEN 'approved' THEN amount WHEN 'declined' THEN 0 END) AS approved_total_amount
FROM Transactions
GROUP BY month,country;
```
## Task - 1174. Immediate Food Delivery II
```sql
SELECT ROUND(AVG(CASE WHEN order_date=customer_pref_delivery_date THEN 1.0 ELSE 0 END)*100, 2) 
AS immediate_percentage
FROM DELIVERY
WHERE (customer_id, order_date) IN (
    SELECT customer_id, MIN(order_date)
    FROM Delivery
    GROUP BY customer_id
)
```
