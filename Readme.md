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
## Orden de ejecución de Querys
<br>

1. FROM
2. WHERE
3. GROUP BY
4. HAVING
5. SELECT
6. ORDER BY
7. LIMIT

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