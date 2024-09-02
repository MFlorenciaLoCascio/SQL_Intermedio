# SQL-Intermedio---Ejercicios-Curso-DataCamp

## 1-Selección de Datos

### Consultar una Base de Datos

#### Practica con COUNT ()
COUNT(*) indica cuántos registros hay en una tabla. Sin embargo, si deseas contar el número de valores que no faltan en un campo en particular, puedes llamar a COUNT() solo en ese campo.

```
-- Cuenta el número de registros en la tabla de personas
SELECT COUNT (*) AS count_records
FROM people;
```

```
-- Cuenta el número de fechas de nacimiento en la tabla «people»
SELECT COUNT(birthdate) AS count_birthdate
FROM people;
```

```
-- Cuenta los registros de los idiomas y países representados en la tabla «films»
SELECT COUNT(language) AS count_languages, COUNT(country) AS count_countries
FROM films;
```

#### SELECT DISTINCT
A menudo, los resultados de las consultas incluyen muchos valores duplicados. Puedes usar la palabra clave DISTINCT para seleccionar los valores únicos de un campo.

```
-- Devuelve los países únicos de la tabla «films»
SELECT *
FROM films;
```

```
SELECT DISTINCT(country)
FROM films;
```

```
-- Cuenta los distintos países de la tabla «films»
SELECT COUNT(DISTINCT country) AS count_distinct_countries
FROM films;
```
