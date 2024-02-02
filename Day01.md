## Task - 1
```sql
SELECT pizzeria_id,pizza_name FROM menu 
UNION 
SELECT id,name FROM person
ORDER BY pizzeria_id, pizza_name
```
![image](https://github.com/nikeyzdereva/oad_vorobyov/assets/112609367/8e4dc904-1583-4ef1-b822-9a16e9784e7b)

## Task - 2
```sql
SELECT DISTINCT person.name, menu.pizza_name
FROM person
JOIN menu ON person.id = menu.pizzeria_id
ORDER BY person.name, menu.pizza_name;
```
![image](https://github.com/nikeyzdereva/oad_vorobyov/assets/112609367/604f8c9b-f5d8-4d45-947c-1fb3ab9bacdb)


## Task - 3
```sql
SELECT po.order_date, po.person_id
FROM person_order po
JOIN person_visits pv ON po.person_id = pv.person_id AND po.order_date = pv.visit_date
ORDER BY po.order_date ASC, po.person_id DESC;
```

![image](https://github.com/nikeyzdereva/oad_vorobyov/assets/112609367/567ea0b3-3eb3-4a7a-a962-7be0fc3fafdf)


## Task - 4
```sql
SELECT person_id
FROM person_order
WHERE order_date = '2022-01-07'
EXCEPT
SELECT person_id
FROM person_visits
WHERE visit_date = '2022-01-07';
```


![image](https://github.com/nikeyzdereva/oad_vorobyov/assets/112609367/89452439-1a53-4879-919e-2cdaf326e266)

## Task - 05

```sql
SELECT * FROM person, pizzeria
ORDER BY person.id, pizzeria.id;
```
![image](https://github.com/nikeyzdereva/oad_vorobyov/assets/112609367/35069106-c8ea-47fc-bc84-008d14cbc76a)


## Task - 06

```sql
SELECT action_date, p.name FROM
(
 SELECT order_date AS action_date, person_id FROM person_order
 INTERSECT ALL
 SELECT visit_date,person_id FROM person_visits
) AS tab
JOIN person p ON tab.person_id = p.id
```
![image](https://github.com/nikeyzdereva/oad_vorobyov/assets/112609367/0a3d9faf-4a90-41d9-9ee0-725965ab1bf4)

## Task - 07

```sql
SELECT po.order_date, CONCAT(p.name, ' (возраст:', p.age, ')') AS personal_info
FROM person_order po
JOIN person p ON po.person_id = po.person_id
ORDER BY po.order_date, p.name, p.age;
```
![image](https://github.com/nikeyzdereva/oad_vorobyov/assets/112609367/1c385a68-811d-4158-bb2d-7084020d73a5)



## Task - 08

```sql
SELECT po.order_date, CONCAT(p.name, ' (возраст:', p.age, ')') AS personal_info
FROM person_order po
NATURAL JOIN person p
ORDER BY po.order_date, p.name, p.age;
```

![image](https://github.com/nikeyzdereva/oad_vorobyov/assets/112609367/1cd8742c-2360-4aa9-afc8-4cf3a674e08d)


## Task - 09

```sql
SELECT name
FROM pizzeria
WHERE id NOT IN (
    SELECT DISTINCT pizzeria_id
    FROM person_visits
);
```

![image](https://github.com/nikeyzdereva/oad_vorobyov/assets/112609367/ec04afe9-ca01-47a4-9271-67ec81f203f2)



```sql
SELECT name
FROM pizzeria p
WHERE NOT EXISTS (
    SELECT 1
    FROM person_visits v
    WHERE v.pizzeria_id = p.id
);
```

![image](https://github.com/nikeyzdereva/oad_vorobyov/assets/112609367/3a688f2c-c3c4-47d5-b159-acc04f579674)


## Task - 10

```sql
SELECT
    person.name AS person_name,
    menu.pizza_name AS pizza_name,
    pizzeria.name AS pizzeria_name
FROM
    person_order
JOIN
    person ON person_order.person_id = person.id
JOIN
    menu ON person_order.id = menu.id
JOIN
    pizzeria ON person_order.id = pizzeria.id
ORDER BY
    person_name ASC, pizza_name ASC, pizzeria_name ASC;
```


![image](https://github.com/nikeyzdereva/oad_vorobyov/assets/112609367/8a3422f3-7747-4547-9bc1-589008fb22f7)
