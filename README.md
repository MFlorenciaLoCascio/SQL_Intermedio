# SQL-Intermedio---Ejercicios-Curso-DataCamp

## 1-Selección de Datos

### Consultar una Base de Datos

#### Practica con COUNT ()
COUNT(*) indica cuántos registros hay en una tabla. Sin embargo, si deseas contar el número de valores que no faltan en un campo en particular, puedes llamar a COUNT() solo en ese campo.

-- Cuenta el número de registros en la tabla de personas
```
SELECT COUNT (*) AS count_records
FROM people;
```

-- Cuenta el número de fechas de nacimiento en la tabla «people»
```
SELECT COUNT(birthdate) AS count_birthdate
FROM people;
```

-- Cuenta los registros de los idiomas y países representados en la tabla «films»
```
SELECT COUNT(language) AS count_languages, COUNT(country) AS count_countries
FROM films;
```

#### SELECT DISTINCT
A menudo, los resultados de las consultas incluyen muchos valores duplicados. Puedes usar la palabra clave DISTINCT para seleccionar los valores únicos de un campo.

-- Devuelve los países únicos de la tabla «films»
```
SELECT DISTINCT(country)
FROM films;
```

-- Cuenta los distintos países de la tabla «films»
```
SELECT COUNT(DISTINCT country) AS count_distinct_countries
FROM films;
```

## 2- Filtrar Registros

Uso de WHERE con números
Filtrar con WHERE te permite analizar mejor tus datos. 

-- Selecciona film ids e imdb_score con una puntuacion imdb superior a 7.
```
SELECT film_id, imdb_score
FROM reviews
WHERE imdb_score > 7.0;
```

Uso de WHERE con texto
WHERE también puede filtrar valores «string».

-- Cuenta las peliculas en espanol
```
SELECT COUNT (Language) AS count_spanish
FROM films
WHERE Language = 'Spanish';
```

Los siguientes ejercicios combinan AND y OR con la cláusula WHERE . EI uso conjunto de estos operadores fortalece tus consultas y análisis de datos.

Usando AND

-- Selecciona title y release_year para todas las peliculas estrenadas antes del 2000
```
SELECT title, release_year
FROM films
WHERE Language = 'German' AND release_year < 2000;
```

Usando OR

-- Encuentra el título y el año de las películas de 1990 o 1999
```
SELECT title, release_year
FROM films
WHERE release_year = 1990 OR release_year = 1999;
```

Uso de BETWEEN

-- Selecciona el titulo y release_year para peliculas estrenadas entre 1990 y 2000
```
SELECT title, release_year
FROM films
WHERE release_year BETWEEN 1990 and 2000;
```

LIKE y NOT LIKE
Los operadores LIKE y NOT LIKE se pueden utilizar para encontrar registros que coincidan o no con un patrón especificado, respectivamente. Se pueden acoplar con los comodines % y _ . El %
coincidirá con cero o muchos caracteres, y _ coincidirá con un solo carácter.

-- Selecciona los nombres que comienzan con B
```
SELECT name
FROM people
WHERE name LIKE 'B%'
```

WHERE IN
Consultar varias condiciones utilizando el operador IN y un conjunto de paréntesis. Es una valiosa pieza de código que nos ayuda a mantener nuestras consultas limpias y concisas.

-- Encuentra el <title> y <release_year> para todas las peliculas de mas de dos horas de duracion estrenadas en 1990 y 2000
```
SELECT title, release_year
FROM films
WHERE release_year IN (1990, 2000)
AND duration > 120;
```

Combinación de filtrado y selección
Hasta ahora, el vocabulario en SQL de este curso incluye COUNT() , DISTINT , LIMIT , WHERE, OR, AND BETWEEN , LIKE, NOT LIKE e IN . En este ejercicio, tratarás de usar algunos de estos conjuntamente.

```
--Cuenta los titulos unicos
SELECT COUNT (DISTINCT title) AS nineties_english_films_for_teens
FROM films
-- Filtra a release_years entre 1990 y 1999
WHERE release_year BETWEEN 1990 AND 1999
-- Filtro a películas en ingles
AND Language = 'English'
Reducirlo a las certificaciones G, PG y PG-13
AND certification IN ('G', 'PG', 'PG-13');
```

Practica con NULLs

-- Lista todos los titulos de peliculas a las que les faltan presupuestos
```
SELECT title AS no_budget_info
FROM films
WHERE budget IS NULL;
```

## 3- Funciones Agregadas

-- Consulta la suma de las duraciones de las películas
```
SELECT SUM(duration) AS total_duration
FROM films;
```

Combina funciones agregadas con WHERE
V
