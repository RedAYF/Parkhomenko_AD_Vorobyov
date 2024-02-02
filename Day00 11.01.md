## Task - 2

```sql
SELECT (name,age)
FROM person WHERE address = 'Novosibirsk';
```
![image](https://github.com/nikeyzdereva/oad_vorobyov/assets/112609367/bca836c9-bcb4-4220-93f7-1c2ef3a73990)


## Task - 3

```sql
SELECT name, age, gender
FROM person WHERE gender= 'female' AND address= 'Kazan'
ORDER BY name DESC
```

![Task3](https://github.com/RedAYF/Parkhomenko_AD_Vorobyov/assets/119556348/bd530c27-ce41-4555-9238-06ee6c8cc404)


## Task - 4

```sql
SELECT name,rating FROM pizzeria
WHERE rating BETWEEN 3.5 AND 5
ORDER BY rating DESC
```
![image](https://github.com/RedAYF/Parkhomenko_AD_Vorobyov/assets/119556348/5c6b1cd8-1d64-4929-9ff5-2b2306f2270d)



## Task - 5

```sql
SELECT DISTINCT person_id FROM person_visits
WHERE pizzeria_id = 2 OR visit_date BETWEEN '2022-01-01' AND '2022-01-04'
ORDER BY person_id DESC
```
![image](https://github.com/RedAYF/Parkhomenko_AD_Vorobyov/assets/119556348/c2c3cbd1-26fc-460d-afc3-11f2b9c15687)



## Task - 6

```sql
SELECT name FROM person
WHERE id IN (
 SELECT person_id FROM person_order WHERE menu_id = 3
)
```

![image](https://github.com/RedAYF/Parkhomenko_AD_Vorobyov/assets/119556348/4216ce13-3305-4cc4-b14d-fecfddbb5519)





## Task - 7

```sql
SELECT EXISTS (SELECT 1 FROM person WHERE name = 'Anna')

```

![image](https://github.com/RedAYF/Parkhomenko_AD_Vorobyov/assets/119556348/17351737-9033-41af-9bc0-f5c3ab36d12d)


