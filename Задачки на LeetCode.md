## Task - 175

```sql
SELECT firstName as firstname, lastName as lastname, city, state FROM 
Person
LEFT JOIN Address ON Person.personID = Address.personID;
```
![image](https://github.com/RedAYF/Parkhomenko_AD_Vorobyov/assets/119556348/b7eacefc-7735-47cb-ae2b-d154dd3efbed)

## Task - 176

```sql
SELECT MAX(salary) as SecondHighestSalary
FROM Employee
WHERE salary < (SELECT MAX(salary)FROM Employee);
```
## Case 1
![image](https://github.com/RedAYF/Parkhomenko_AD_Vorobyov/assets/119556348/7ff663bc-9445-4b0b-99fc-6e9a8062c5cf)

## Case 2
![image](https://github.com/RedAYF/Parkhomenko_AD_Vorobyov/assets/119556348/cb62f0bf-23e9-4da3-9582-ba2aeca9a80c)

## Task - 177

```sql
CREATE OR REPLACE FUNCTION NthHighestSalary(N INT) RETURNS TABLE (Salary INT) AS $$
BEGIN
  RETURN QUERY (
    -- Write your PostgreSQL query statement below.
    SELECT DISTINCT tab.salary  as "getNthHighestSalary"
    FROM (
        SELECT 
            Employee.salary, 
            DENSE_RANK() OVER(ORDER BY Employee.salary DESC) AS rank 
        FROM Employee
  ) AS tab
  WHERE tab.rank = N
  );
END;
$$ LANGUAGE plpgsql;
```
## Case 1
![image](https://github.com/RedAYF/Parkhomenko_AD_Vorobyov/assets/119556348/720872d2-a49b-4c3e-900c-5d2dae5fe471)

## Case 2
![image](https://github.com/RedAYF/Parkhomenko_AD_Vorobyov/assets/119556348/60bafc1c-3645-4920-8330-8118377d4390)

## Task - 178
```sql
-- Write your PostgreSQL query statement belo
WITH RankedScores AS (
    SELECT score,
            DENSE_RANK() OVER(ORDER BY score DESC) AS rank
            FROM Scores
)
SELECT score, rank
FROM RankedScores
ORDER BY score DESC;
```
## Case 1
![image](https://github.com/RedAYF/Parkhomenko_AD_Vorobyov/assets/119556348/948495c7-5f01-4451-a889-c42c09d3fa75)

## Task - 181
```sql
-- Write your PostgreSQL query statement below
SELECT name AS "Employee" FROM Employee e
WHERE (e.managerId IS NOT NULL) 
AND (e.salary > (SELECT salary FROM Employee WHERE Employee.id = e.managerId)) 
```
## Task - 182
```sql
SELECT email 
FROM Person
GROUP BY email
HAVING COUNT(email) > 1;
```
## Task - 183
```sql
# Write your MySQL query statement below
SELECT cust.name AS "Customers" FROM Customers cust
LEFT JOIN Orders ord ON cust.id = ord.customerId
WHERE ord.customerId IS NULL;
```
## Task - 184
```sql
SELECT d.name AS Department, e.name AS Employee, e.salary AS Salary
FROM (
    SELECT departmentId, MAX(salary) AS max_salary
    FROM Employee
    GROUP BY departmentId
) AS max_salaries
JOIN Employee e ON e.departmentId = max_salaries.departmentId AND e.salary = max_salaries.max_salary
JOIN Department d ON e.departmentId = d.id;
```
## Task - 511
```sql
SELECT player_id, MIN(event_date) AS first_login FROM Activity
GROUP BY player_id
ORDER BY player_id;
```
