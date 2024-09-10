# Algunos de los ejercicios del curso de SQL Intermedio de DataCamp 

Puedes acceder al curso [aquí](https://www.datacamp.com/courses/intermediate-sql), tiene una duración de 4 horas, 14 videos y 50 ejercicios. 👩‍💻

Certificado [aquí](https://www.datacamp.com/completed/statement-of-accomplishment/course/107f68827dfadbcbcef6569c0f7e263eff874cab)

## Descripción del curso:

SQL es ampliamente reconocido como el lenguaje más popular para convertir datos sin procesar almacenados en una base de datos en información procesable. Este curso utiliza una base de datos de películas para enseñar cómo navegar y extraer información de los datos mediante SQL.

### ✔️ Descubra el filtrado con SQL:

Descubrirá técnicas para filtrar y comparar datos, lo que le permitirá extraer información específica para obtener información y responder preguntas sobre los datos.

### ✔️ Conozca la agregación:

Conocerá las funciones de agregación, esenciales para resumir datos de manera eficaz y obtener información valiosa de grandes conjuntos de datos. También combinará esto con la clasificación y agrupación de datos, lo que agregará otra capa de significado a sus conocimientos y análisis.

### ✔️ Escribir consultas limpias:

Por último, se le mostrarán algunos consejos y prácticas recomendadas para presentar sus datos y consultas de forma ordenada. A lo largo del curso, tendrá consultas prácticas para consolidar su comprensión de los conceptos. Al final del curso, tendrá todo lo que necesita saber para analizar datos utilizando su propio código SQL hoy mismo.

## 1️⃣ Selección de Datos: 

Aprenderá a consultar una base de datos de películas y a seleccionar los datos necesarios para responder preguntas sobre las películas y los actores. También comprenderá cómo se ejecuta y se formatea el código SQL.

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

## 2️⃣ Filtrar Registros:

Aprenda a filtrar datos numéricos y textuales con SQL. El filtrado es un uso importante de este lenguaje. Aprenderá a utilizar nuevas palabras clave y operadores para acotar su consulta y obtener resultados que cumplan con los criterios deseados, además de comprender mejor los valores NULL y cómo manejarlos.

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

## 3️⃣ Funciones Agregadas:

SQL le permite ampliar y reducir la información para comprender mejor un conjunto de datos completo, sus subconjuntos y sus registros individuales. Aprenderá a resumir datos mediante funciones agregadas y a realizar cálculos aritméticos básicos dentro de las consultas para obtener información sobre lo que hace que una película sea exitosa.

-- Consulta la suma de las duraciones de las películas
```
SELECT SUM(duration) AS total_duration
FROM films;
```

Combinar funciones agregadas con WHERE: Esta combinación es útil cuando solo quieres resumir un subconjunto de los datos.

-- Calcula la suma de los brutos del ano 2000 o posteriores
```
SELECT SUM(gross) AS total_gross
FROM films
WHERE release_year >= 2000;
```

ROUND()

-- Redondea el número promedio de facebook_likes a un decimal
```
SELECT ROUND (AVG(facebook_Likes), 1) AS avg_facebook_likes
FROM reviews;
```

ROUND() con un parametro negativo

-- Calcula el presupuesto medio redondeado a los miles
```
SELECT ROUND (AVG (budget), -3) AS avg_budget_thousands
FROM films;
```

Aliasing con funciones: El alias puede ser un salvavidas, especialmente cuando empezamos a hacer consultas SQL más complejas con múltiples criterios. Los alias te ayudan a mantener tu código limpio y legible.

- Calcula title, duration_hours y redondea a 2 decimales de la tabla films
```
SELECT title, ROUND(duration / 60.0,2) AS duration_hours
FROM films;
```

## 4️⃣ Ordenar y agrupar: 

En este capítulo final, aprenderá a ordenar y agrupar datos. Estas habilidades le permitirán llevar sus análisis a un nuevo nivel, ya que le ayudarán a descubrir información empresarial fundamental e identificar tendencias y resultados. Obtendrá experiencia práctica para determinar qué películas tuvieron el mejor rendimiento y cómo cambiaron las duraciones y los presupuestos de las películas con el tiempo.

Ordenar campos individuales con ORDER BY

-- Selecciona el nombre de las personas y ordena alfabéticamente
```
SELECT name
FROM people
ORDER BY name;
```

Ordenar varios campos: ORDER BY tambien se puede usar para ordenar en varios campos. Ordenara por el primer campo especificado, uego ordenara por el siguiente, y asi sucesivamente. Como ejemplo, puedes ordenar los datos de las personas por edad y mantener los nombres en orden alfabetico.

-- Selecciona el ano de lanzamiento, La duracion y el titulo ordenados por ano de lanzamiento y duración
```
SELECT release_year, duration, title
FROM films
ORDER BY release_year ASC, duration ASC;
```

GROUP BY campos individuales: GROUP BY es una palabra clave de SQL que te permite agrupar y resumir resultados con el uso adicional de funciones agregadas. Por ejemplo, las peliculas se pueden agrupar por certificación e idioma antes de contar los titulos de las peliculas en cada grupo. Esto te permite ver cuantas peliculas tenian una certificacion y una agrupacion de idiomas en particular.

-- Encuentra el release_year y film_count de cada año
```
SELECT release_year, COUNT(*) AS film_count
FROM films
GROUP BY release_year;
```

GROUP BY con varios campos: GROUP BY se vuelve mas poderoso cuando se usa en varios campos o se combina con ORDER BY y LIMIT.
Tal vez estes interesado en conocer los cambios presupuestarios a lo largo de los aflos en paises individuales. Utilizaras la agrupacion en este ejercicio para ver el presupuesto máximo para cada pais en cada afo en el que hay datos disponibles.

-- Busca el release_year, country y max_budget, Luego agrupa y ordena por release_year y country
```
SELECT release_year, country, MAX(budget) AS max_budget
FROM films
GROUP BY release_year, country
ORDER BY release_year, country;
```

Filtrar con HAVING
Su palabra clave final es HAVING . Funciona de manera similar a WHERE en que es una clausula de filtrado, con la diferencia de que HAVING filtra datos agrupados.
El filtrado de datos agrupados puede ser especialmente útil cuando se trabaja con un gran conjunto de datos. Cuando trabajes con miles o incluso millones de filas, HAVING te permitirá filtrar solo el grupo de datos que desees, como peliculas de más de dos horas de duración.
```
-- Selecciona el pais y el recuento distinto de certificacion como certification_count
SELECT country, COUNT(DISTINCT certification) AS certification_count
FROM films
-- Group by country
GROUP BY country
-- Filtra los resultados a paises con mas de 10 certificaciones diferentes
HAVING COUNT(DISTINCT certification)>10;
```

HAVING y ORDER BY: El filtrado y la clasificación van de la mano y te brindan una mayor interpretabilidad al ordenar nuestros resultados.

-- Selecciona el country y el presupuesto medio como average_budget , redondeado a dos decimales, de filns. Agrupar los resultados por country. Filtra los resultados a paises con un presupuesto promedio de mas de mil millones ( 1000000000 ). Ordenar por orden descendente del average_budget.

```
SELECT country, ROUND(AVG(budget), 2) AS average_budget
FROM films
GROUP BY country
HAVING AVG(budget) > 1000000000
ORDER BY average_budget DESC;
```
