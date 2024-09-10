# Algunos de los ejercicios del curso de SQL Intermedio de DataCamp 
Puedes acceder al curso [aquí](https://www.datacamp.com/courses/intermediate-sql), tiene una duración de 4 horas, 14 videos y 50 ejercicios. 👩‍💻

### Descripción del curso:

SQL es ampliamente reconocido como el lenguaje más popular para convertir datos sin procesar almacenados en una base de datos en información procesable. Este curso utiliza una base de datos de películas para enseñar cómo navegar y extraer información de los datos mediante SQL.

#### ➡️ Descubra el filtrado con SQL:

Descubrirá técnicas para filtrar y comparar datos, lo que le permitirá extraer información específica para obtener información y responder preguntas sobre los datos.

#### ➡️ Conozca la agregación:

Conocerá las funciones de agregación, esenciales para resumir datos de manera eficaz y obtener información valiosa de grandes conjuntos de datos. También combinará esto con la clasificación y agrupación de datos, lo que agregará otra capa de significado a sus conocimientos y análisis.

#### ➡️ Escribir consultas limpias:

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

Combina funciones agregadas con WHERE


## 4️⃣ Ordenar y agrupar: 

En este capítulo final, aprenderá a ordenar y agrupar datos. Estas habilidades le permitirán llevar sus análisis a un nuevo nivel, ya que le ayudarán a descubrir información empresarial fundamental e identificar tendencias y resultados. Obtendrá experiencia práctica para determinar qué películas tuvieron el mejor rendimiento y cómo cambiaron las duraciones y los presupuestos de las películas con el tiempo.

