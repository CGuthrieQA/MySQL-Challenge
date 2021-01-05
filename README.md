# SQL Challenges

## Sakila Challenge SQL

### 1)

```SQL
SELECT first_name, last_name
FROM actor;
```

### 2)

```SQL
SELECT last_name
FROM actor
WHERE first_name='John';
```

### 3)

```SQL
SELECT first_name, last_name
FROM actor
WHERE last_name='Neeson';
```

### 4)

```SQL
SELECT first_name, last_name
FROM actor
WHERE actor_id % 10 = 0;
```

### 5)

```SQL
SELECT description
FROM film
WHERE film_id=100;
```

### 6)

```SQL
SELECT title
FROM film
WHERE rating='R';
```

### 7)

```SQL
SELECT title
FROM film
WHERE rating!='R';
```

### 8)

```SQL
SELECT title, length
FROM film
ORDER BY length ASC
LIMIT 10;
```

### 9) ????? maybe do TOP 1 and GROUP BY length??

```SQL
SELECT title, length
FROM film
ORDER BY length DESC;
```

### 10) 

```SQL
SELECT title
FROM film
WHERE special_features='Deleted Scenes';
```

### 11) why do we use HAVING here???

```SQL
SELECT DISTINCT last_name
FROM actor
HAVING last_name IS NOT NULL
ORDER BY last_name DESC;
```

### 12)

```SQL
SELECT last_name, COUNT(last_name)
FROM actor
GROUP BY last_name
HAVING COUNT(last_name) > 1
ORDER BY COUNT(last_name) DESC;
```

### 13)

```SQL
SELECT film_actor.actor_id, actor_info.first_name, actor_info.last_name, COUNT(film_actor.actor_id) AS films
FROM film_actor
JOIN actor_info ON film_actor.actor_id=actor_info.actor_id
GROUP BY film_actor.actor_id
ORDER BY COUNT(film_actor.actor_id) DESC
LIMIT 1;
```

### 14)

```SQL
SELECT release_year
FROM film 
WHERE title = 'Academy Dinosaur';
```

### 15)

```SQL
SELECT AVG(length)
FROM film;
```

### 16)

```SQL
SELECT category.name, AVG(film.length)
FROM category
JOIN film_category ON film_category.category_id=category.category_id
JOIN film ON film.film_id=film_category.film_id
GROUP BY category.category_id
ORDER BY AVG(film.length) DESC;
```

### 17)

```SQL
SELECT film.title
FROM film_text 
JOIN film ON film.film_id=film_text.film_id
WHERE film_text.description LIKE '%robot%';
```

### 18)

```SQL
SELECT COUNT(release_year) AS 2010_films
FROM film
WHERE release_year=2010;
```

### 19)

```SQL
SELECT film.title
FROM category
JOIN film_category ON film_category.category_id=category.category_id
JOIN film ON film_category.film_id=film.film_id
WHERE category.name='Horror';
```

### 20)

```SQL
SELECT first_name, last_name
FROM staff
WHERE staff_id=2;
```

### 21)

```SQL
SELECT film.title
FROM film
JOIN film_actor ON film_actor.film_id=film.film_id
JOIN actor ON actor.actor_id=film_actor.actor_id
WHERE actor.first_name='FRED' AND actor.last_name='Costner';
```

### 22)

```SQL
SELECT DISTINCT COUNT(country) AS distinct_countries
FROM country;
```

### 23)

```SQL
SELECT name
FROM language
ORDER BY name DESC;
```

### 24)

```SQL
SELECT first_name, last_name
FROM actor
WHERE last_name LIKE '%son'
ORDER BY first_name ASC;
```

### 25)

```SQL
SELECT category.name
FROM category
JOIN film_category ON film_category.category_id=category.category_id
GROUP BY category.category_id
ORDER BY COUNT(film_category.category_id) DESC
LIMIT 1;
```

## World Challenge SQL

### 1)

```SQL
SELECT COUNT(CountryCode) 
FROM city 
WHERE CountryCode = 'USA';
```

### 2)

```SQL
SELECT Population, LifeExpectancy 
FROM country 
WHERE Name = 'Argentina';
```

### 3)

```SQL
SELECT LifeExpectancy 
FROM country 
WHERE LifeExpectancy IS NOT NULL 
ORDER BY LifeExpectancy DESC 
LIMIT 1;
```

### 4)

```SQL
SELECT country.Name, city.Name 
FROM country 
JOIN city ON country.Capital=city.id 
WHERE country.Name='Spain';
```

### 5)

```SQL
SELECT countrylanguage.Language 
FROM countrylanguage 
JOIN country ON country.Code=countrylanguage.CountryCode 
WHERE country.Region='Southeast Asia';
```

### 6)

```SQL
SELECT Name 
FROM city 
WHERE Name 
LIKE 'F%' 
LIMIT 25;
```

### 7)

```SQL
SELECT COUNT(CountryCode) 
FROM city 
JOIN country ON country.Code=city.CountryCode 
WHERE country.Name='China';
```

### 8)

```SQL
SELECT Name, Population 
FROM country 
WHERE Population IS NOT NULL 
ORDER BY Population ASC 
LIMIT 1;
```

### 9)

```SQL
SELECT COUNT(Name) 
FROM country;
```

### 10)

```SQL
SELECT Name, SurfaceArea 
From country 
ORDER BY SurfaceArea DESC 
LIMIT 10;
```

### 11)

```SQL
SELECT city.Name 
FROM city 
JOIN country ON city.CountryCode=country.Code 
WHERE country.Name='Japan' 
ORDER BY city.Population DESC 
LIMIT 5;
```

### 12) - there is also a REPLACE method that I will not use here

```SQL
UPDATE country 
SET HeadOfState='Elizabeth II' 
WHERE HeadOfState='Elisabeth II';

SELECT Name, Code 
FROM country 
WHERE HeadOfState='Elizabeth II';
```

### 13)

```SQL
SELECT Name, SurfaceArea, Population, Population / SurfaceArea  
FROM country 
ORDER BY Population / SurfaceArea ASC, SurfaceArea DESC 
LIMIT 10;
```

### 14)

```SQL
SELECT DISTINCT Language 
FROM countrylanguage;
```

### 15) 

```SQL
SELECT Name, GNP 
FROM country 
ORDER BY GNP DESC 
LIMIT 10;
```

### 16)

```SQL
SELECT country.Name, COUNT(countrylanguage.CountryCode) 
FROM country 
JOIN countrylanguage ON countrylanguage.CountryCode=country.Code 
GROUP BY country.Name
ORDER BY COUNT(countrylanguage.CountryCode) DESC 
LIMIT 10;
```

### 17)

```SQL
SELECT country.Name
FROM country
JOIN countrylanguage ON countrylanguage.CountryCode=country.Code
WHERE countrylanguage.Language='German' 
AND countrylanguage.Percentage >= 50.00;
```

### 18)

```SQL
SELECT Name, LifeExpectancy 
FROM country 
WHERE LifeExpectancy IS NOT NULL 
AND LifeExpectancy > 0
ORDER BY LifeExpectancy ASC 
LIMIT 1;
```

### 19)

```SQL
SELECT GovernmentForm, COUNT(GovernmentForm)
FROM country
GROUP BY GovernmentForm
ORDER BY COUNT(GovernmentForm) DESC
LIMIT 3;
```

### 20)

```SQL
SELECT COUNT(IndepYear)
FROM country
WHERE IndepYear IS NOT NULL;
```