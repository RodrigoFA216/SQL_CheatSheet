# SQL Cheatsheet 

[![Maintenance](https://img.shields.io/badge/Maintained%3F-yes-green.svg)](https://GitHub.com/Naereen/StrapDown.js/graphs/commit-activity)
![Maintainer](https://img.shields.io/badge/RodrigoFA216-theMaintainer-blue)
[![GitHub license](https://img.shields.io/github/license/Naereen/StrapDown.js.svg)](https://github.com/Naereen/StrapDown.js/blob/master/LICENSE)
<br>

## Enfocado a
![Javascript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)
![TypeScript](https://img.shields.io/badge/TypeScript-007ACC?style=for-the-badge&logo=typescript&logoColor=white)
![NodeJS](https://img.shields.io/badge/Node.js-43853D?style=for-the-badge&logo=node.js&logoColor=white)
<br>

## Aplicable a

![MariaDB](https://img.shields.io/badge/MariaDB-003545?style=for-the-badge&logo=mariadb&logoColor=white)
![MSQLS](https://img.shields.io/badge/Microsoft%20SQL%20Server-CC2927?style=for-the-badge&logo=microsoft%20sql%20server&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-005C84?style=for-the-badge&logo=mysql&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-316192?style=for-the-badge&logo=postgresql&logoColor=white)
![SQLLite](https://img.shields.io/badge/SQLite-07405E?style=for-the-badge&logo=sqlite&logoColor=white)
***
## Comandos/Querys/Clausulas

### Comandos básicos

|Comando|Acción|
|---|---|
| SELECT        | Selecciona datos de una DB |
| FROM          | Especifica la tabla de la que van a ser traidos los datos |
| WHERE         | Filtra los datos y trae solo los que queden con una condición específica |
| AS            | Renombra una columna o tabla como un alias |
| JOIN          | Combina filas de dos tablas diferentes |
| AND           | Combina condiciones del comando. Ambas se tienen que cumplir |
| OR            | Combina condiciones del comando. Una de las dos tienen que coincidir |
| LIMIT         | Limita las filas regresadas. FETCH y TOP son alternativas |
| IN            | Especifica multiples valores para usar WHERE |
| CASE          | Regresaun valor que coincida con una condición específica |
| IS NULL       | Regresa las filas donde haya un valor NULL |
| LIKE          | Busca patrones en las columnas que coincidan en la especificación |
| COMMIT        | Escribe una transacción en la DB |
| ROLLBACK      | Regresa una transacción en la DB |

### Comandos Para ordenar

|Comando|Acción|
|---|---|
| GROUP BY      | Agrupa los datos según operaciones lógicas |
| ORDER BY      | Establece un orden para el resultado (Usa DESC para invertir el orden) |
| HAVING        | Similar a WHERE pero filtra por grupos |
| COUNT         | Cuenta los numeros de filas |
| SUM           | Regresa la suma de columnas |
| AVG           | Regresa el promedio de una columna |
| MIN           | Regresa el valor minimo de una columna |
| MAX           | Regresa el valor máximo de una columna |

### Comandos Para tablas

|Comando|Acción|
|---|---|
| ALTER TABLE   | Añade o remueve columnas de la tabla |
| UPDATE        | Actualiza los datos de la tabla |
| CREATE        | Crea TABLE, DATABASE, INDEX o VIEW |
| DELETE        | Elimina Filas de la tabla |
| INSERT        | Añade una fila a la tabla |
| DROP          | Elimina una TABLE, DATABASE o un INDEX |

### Comandos para unir resultados

|Comando|Acción|Ejemplo|
|---|---|---|
| INNER JOIN | Fusiona la union de los conjuntos | a INNER JOIN b |
| LEFT JOIN | Fusiona el izquierdo con la union del izquiero y derecho | a LEFT JOIN b |
| RIGHT JOIN | Fusiona el derecho con la union del izquierdo y el derecho | a RIGHT JOIN b |
| FULL OUTER JOIN | Fusiona ambas, la derecha la izquierda y la union de ambas | a FULL OUTER JOIN b  |
***
# Orden de ejecución de Querys
<br>

1. FROM
2. WHERE
3. GROUP BY
4. HAVING
5. SELECT
6. ORDER BY
7. LIMIT
***
## Baby steps

Para saber que base de datos estamos usando o cuales son las bases de datos dispponibles dentro de nuestra conexión actual usamos el siguiente comando:

    show databases;

Lo que nos devolverá en el conjunto de resultados un listado de las bases de datos disponibles. Para esta sección usaremos la base de datos Sakila que viene instalada por defecto en la  mayoría de GDB (si no está instalada la puedes descargar desde https://dev.mysql.com/doc/index-other.html). 

Después de eso necesitaremos que el GDB nos muestre las tablas que contiene la base de datos Sakila, Para ello usaremos el siguiente comando:

    show tables from sakila;

El resultado se verá así:

    actor
    actor_info
    address
    category
    city
    country
    customer
    customer_list
    film
    film_actor
    film_category
    film_list
    film_text
    inventory
    language
    nicer_but_slower_film_list
    payment
    rental
    sales_by_film_category
    sales_by_store
    staff
    staff_list
    store

Una vez sabiendo que tablas contiene la base de datos Sakila podemos empezar a definir algunas cosas sobre el SELECT.

### SELECT

La instrucción SELECT se utiliza para consultar la información de una tabla.

Los datos devueltos se muestran en una tabla, denominada conjunto de resultados.

Sintaxis:

    SELECT column_1, column_2, … FROM tabla_name;

Aquí, columna1, columna2, ... son los nombres de campo de la tabla de la que desea seleccionar datos.

Si desea seleccionar todos los campos disponibles en la tabla, utilice la siguiente sintaxis:

    SELECT * FROM tabla_name;

Por ejemplo, seleccionemos todos los datos de la tabla *actor* dentro de sakila.

    SELECT * FROM actor;

el resultado es muy grande y contiene información de las columnas actor_id, first_name, last_name, last_update.

Ahora seleccionaré solamente las columnas first_name y last_name de la tabla actor:

    SELECT first_name, last_name FROM actor;

El resultado es igual de largo sin embargo solo contiene las dos columnas que elegimos.

### Alias

A la instrucción select se le puede añadir el keyword *as* para especificar que eso que vamos a traer tendrá un alias o un apodo para su futura manipulación.

Seleccionaré la columna first_name como nombre y last_name como apellido:

    SELECT first_name AS nombre, last_name AS apellido FROM actor;

Otra opción es:

    SELECT first_name AS "nombre", last_name AS "apellido" FROM actor;

(Recordemos que como buena práctica de programación debemos conservar el tipo de escritura de las instancias, si estas se encuentran en camelCase se debe continuar con ello, sin embargo si se encuentra en camelCase no se debe cambiar a snake_Case)

### SELECT DISTINCT 

SELECT DISTINCT es una declaración que se usa para devolver solo valores distintos (diferentes).

Dentro de una tabla, una columna suele contener muchos valores duplicados; y, a veces, solo desea enumerar los diferentes valores (distintos).

Sintaxis:

    SELECT DISTINCT column_1, column_2 FROM table_name;

Para estos ejercicios usaremos la tabla  y consultaremos postal_code:

    SELECT distinct postal_code FROM address;

### Ejercicios SELECT

1. Ejercicio:  Muestra film_id y title de la tabla film
    ~~~
    SELECT film_id, title FROM film;

2. Ejercicio:  Asigna un Alías a title y escribe 'Titulo de la pelicula' y a description y escribe 'Descripción de la pelicula' de la tabla film
    ~~~
    SELECT title as "Titulo de la pelicula", description as "Descripcion de la pelicula" FROM film;

3. Ejercicio: Muestra los campos distintos de postal_code
    ~~~
    SELECT distinct postal_code FROM address;

4. Ejercicio:  Consulta la inicial de la columna country de la tabla country (selecciona solo el primer caracter de la columna de izquierda a derecha con LEFT)
    ~~~
    SELECT LEFT(country,1) FROM country;

5. Ejercicio:  Consulta la tabla country y muestra en mayusculas la columna country
    ~~~
    SELECT UPPER(country) FROM country;

6. Ejercicio:  Consulta la tabla country y muestra cuantos caracteres tienen los campos de la columna country
    ~~~
    SELECT LENGTH(country) FROM country;

* Ejercicio adicional de nivel alto: consulta la tabla country, obten las dos iniciales de la columna country como "capital" la columna country con mayusculas, y el largo de la palabra como "length"

    ~~~
    SELECT LEFT(country, 2) AS "capital", UPPER(country) AS "country", LENGTH(country) AS "length" FROM country;

7. Ejercicio:  Concatena country_id y country de la tabla country (junta ambas columnas y las muestra una seguida de la otra)
    ~~~
    SELECT CONCAT(COUNTRY_ID, country) FROM country;

8. Ejercicio:  Multiplica amount por el 19.84 que es el precio actual del dolar de la tabla payment
    ~~~
    SELECT amount, (amount*19.84) FROM payment;

9. Ejercicio:  Redondea a 0 decimales la columna amount de la tabla payment
    ~~~
    SELECT amount, ROUND(amount,0) FROM payment;

10. Ejercicio: Muestra el valor de PI
    ~~~
    SELECT PI();
<br><br>

***
## Where

WHERE se utiliza para filtrar registros y extraer solo aquellos registros que cumplen una condición específica. Sintaxis:

    SELECT column_1, column_2, … FROM tabla_name WHERE condition

Cuando utilizamos WHERE la búsqueda la podemos realizar con un filtro de tipo carácter o de tipo numérico. Los tipo carácter debemos colocarlos entre comillas y los numéricos no.

Además podemos combinar el filtro where con otros operadores como IN, BETWEEN o LIKE cuya finalidad es realizar búsquedas de patrones. Sin embargo también se pueden usar comparadores lógicos como AND, OR, NOT, XOR y comparadores matemáticos como >, <, <=, >= etc.

Ejemplo: Encontrar el query para que de la tabla film solo muestre la columna title y rental_rate de las películas que su rental_rate sea mayor o igual a 4

    SELECT title, rental_rate FROM film WHERE rental_rate >= 4;

Funciona igual para carácteres o texto.

    SELECT * FROM actor WHERE first_name = "ED";

Para usar más de una condicion podemos usar IN 

    SELECT * FROM country WHERE country IN ("Chile", "France");

Para especificar un rango de cosas a comparar podemos usar BETWEEN 

    SELECT * FROM rental WHERE rental_date BETWEEN '2005-05-01' ADN '2005-06-01';

Para declarar valores específicos en una columna se usa LIKE

    SELECT * FROM actor WHERE first_name LIKE 'j%';

- LIKE 'a%' Valores que empiezen con a.
- LIKE '%a' Valores que terminen con a.
- LIKE '%or%' Valores que contengan or en cualquier posicion.
- LIKE '_r%' Valores que contengan r en la segunda posición.
- LIKE 'a_%' Valores que empiezen con a y tenga al menos dos carácteres de longitud.
- LIKE 'a__%' Valores que empiezen con a y tenga al menos tres carácteres de longitud.
- LIKE 'a%o' Valores que empiezen con a y terminen con o.

### AND OR Y NOT

WHERE se puede combinar con los operadores AND, OR NOT. Los operadores AND y OR se utilizan para filtrar registros en función de más de una condición.

El operador AND muestra un registro si todas las condiciones separadas por AND son VERDADERAS.

    SELECT column_1, column_2, … FROM tabla_name WHERE condition_1 AND condition_2 AND condition_3,…

El operador OR muestra un registro si alguna de las condiciones separadas por OR es VERDADERA.

    SELECT column_1, column_2, … FROM tabla_name WHERE condition_1 OR condition_2 OR condition_3,…

El operador NOT muestra un registro si la(s) condición(es) NO ES VERDADERA.

    SELECT column_1, column_2, … FROM tabla_name WHERE NOT condition

Ejercicios:
- Muestra los actores cuyo nombre empiece con J y su apellido con C.

    SELECT * FROM actor WHERE first_name LIKE 'J%' AND last_name LIKE 'C%';

- Muestra los actores que su nombre empiece con Z o su apellido con P
    ~~~
    SELECT * FROM actor WHERE first_name LIKE 'Z%' OR last_name LIKE 'P%';

- Muestra los registros de country pero que no aparezca Brazil
    ~~~
    SELECT * FROM country WHERE NOT country = 'Brazil';


## ORDER BY

ORDER BY se utiliza para clasificar el conjunto de resultados en orden ascendente o descendente sin embargo ordena los registros en orden ascendente de forma predeterminada. Para ordenar los registros en orden descendente, se debe colocar DESC

    SELECT column_1, column_2, … FROM tabla_name
    ORDER BY column_1, column_2, … ASC | DESC



<br><br>



# Ejemplos
## Lenguaje de definición de datos

### CREATE

~~~
    CREATE DATABASE MiBaseDeDatos;

    CREATE TABLE MiTabla(
        id int,
        name varchar(10)
    );

    CREATE INDEX NombreDelIndex ON NombreDeTabla(Columna);
~~~

### ALTER

~~~
    ALTER TABLE MiTabla DROP COLUMN col5;

    ALTER TABLE MiTabla ADD col5 int;
~~~

### DROP

~~~
    DROP DATABASE MiBaseDeDatos;
    DROP TABLE MiTabla;
~~~

## Lenguaje de manipulación de datos
### UPDATE
~~~
    UPDATE MiTabla SET col1=56 WHERE col2='algo';
~~~

### INSERT
~~~
    INSERT INTO MyTable (col1, col2) VALUES ('valor1','valor2');
~~~

### DELETE
~~~
    DELETE FROM MiTabla WHERE col1='algo';
~~~

### SELECT
~~~
    SELECT col1, col2 DROM MiTabla;
~~~

# Ejemplos Específicos

>Selecciona todas las filas donde el valor de la columna sea mayor a 5
~~~
SELECT * FROM tabla WHERE col>5;
~~~

>Selecciona las primeras diez filas de dos columnas
~~~
SELECT col1, col2 FROM tabla LIMIT 10;
~~~

>Selecciona todas las filas con multiples filtros
~~~
SELECT * FROM tabla WHERE col1>5 OR col2<2;
~~~

>Selecciona todas las filas de col1 y col2 ordenado por col1
~~~
SELECT col1, col2 FROM tabla ORDER BY 1;
~~~

>Regresa el conteo de filas en una tabla
~~~
SELECT COUNT(*) FROM tabla;
~~~

>Regresa la suma de la columna 1
~~~
SELECT SUM(col1) FROM tabla;
~~~

>Regresa el valor máximo de la columna 1
~~~
SELECT MAX(col1) FROM table;
~~~

>Compute el promedio de las estadísticas agrupadas por la columna 2
~~~
AELECT AVG(col1) FROM tabla GROUP BY col2;
~~~

>Combine los datos de dos tablas usando left join
~~~
SELECT * FROM tabla1 AS t1 LEFT JOIN tabla2 AS t2 ON t2.col1=t1.col1;
~~~

>Agregando filtros al resultado
~~~
SELECT col1, COUNT(*) AS total FROM tabla GROUP BY col1 HAVING COUNT(*) > 10;
~~~

>implementación de CASE en los querys
~~~
SELECT col1,
CASE
    WHEN col1 >10 THEN 'more than 10'
    WHEN col1 <10 THEN 'less than 10'
    ELSE '10'
END AS NewColumnName
FROM table;
~~~