### UANL
### FCFM, MCD

## Bases de datos relacionales

#### Funciones de agregación en un Sistema Gestor de BDD (SQL Server):

En este ejercicio se usará SQL Server para trabajar sobre ciertas relaciones de la base de datos de la ENIGH 2020 (el archivo llamado "enighdb" que esta en el repositorio se puede descargar), con el fin de obtener algunas funciones de agregación:

##### 1) Conteos de frecuencias/medias:
 <code>
 --conteo de frecuencias de tipo_vivienda
SELECT COUNT(*) FROM vivienda GROUP BY tipo_vivienda

--media por cada tamaño de localidad
SELECT AVG(renta) FROM vivienda GROUP BY tam_loc
 </code>

En este ejercicio, la cláusula *GROUP BY* es primordial debido a que para obtener frecuencias se tienen que agrupar los datos por cierta categoría, y esta cláusula lo permite.


##### 2) Mínimos y máximos:

$
/*tipo_vivienda=5: donde la vivienda no esta construida para habitar
material_pisos=1: viviendas donde el material de sus pisos es tierra*/

SELECT MAX(num_cuarto) FROM vivienda WHERE tipo_vivienda=5
SELECT MIN(renta) FROM vivienda WHERE material_pisos=1

$

En este ejercicio se uso el comando *WHERE* para filtrar la tabla en base a cierta condición de cierta columna. (Dan 10 y 100, respectivamente).


##### 3) Cuantiles

- Con función preestablecida (basado en *https://popsql.com/learn-sql/sql-server/how-to-calculate-percentiles-in-sql-server*)

$
-- mediana clave_ing=="P001" (salarios de trabajo principal)

SELECT 
  percentile_cont(0) WITHIN GROUP(ORDER BY ing_trim) over () as minimum,
  percentile_cont(0.25) WITHIN GROUP(ORDER BY ing_trim) over () as firstquantile,
  percentile_cont(0.50) WITHIN GROUP(ORDER BY ing_trim) over () as median,
  percentile_cont(0.75) WITHIN GROUP(ORDER BY ing_trim) over () as thirdquantile,
  percentile_cont(1) WITHIN GROUP(ORDER BY ing_trim) over () as maximum
FROM ingreso --WHERE clave_ing='P002'
$

Usando la función preestablecida *percentile_cont* de SQL Server facilita mucho el trabajo, únicamente te limitas a colocar el número de cuantil que deseas (no sin no colocar sus respectivas adecuaciones de agrupacion y ordenamiento).

- De forma manual:

$
DECLARE @nonulls INT
SET @nonulls =  ( SELECT COUNT(ing_trim) FROM ingreso WHERE ing_trim IS NOT NULL)/2
SELECT @nonulls  --197456 variable temporal que cuenta los no nulls  

--SELECT ing_trim FROM ingreso ORDER BY ing_trim ASC 
SELECT ing_trim
FROM (
    SELECT
        ROW_NUMBER() OVER(ORDER BY ing_trim ASC) AS rownumber,
        ing_trim
    FROM ingreso) AS num
WHERE rownumber = @nonulls
$

Esta manera, más elaborada, permite repasar un poco más las funciones de SQL Server. Primero creamos una varable tipo *int* que servirá para contar los registros no nulos (debido a que esta columna en cuestión cuenta con valores nulos, y para obtener la mediana se excluyen estos valores). El resultado de este conteo dividido entre 2 (para obtener la ubicación del valor medio de la distribución de registros de la columna) es *197,456*, y después de eso en síntesis se ordena la columna ingreso trimestral de manera ascendente, y se obtiene el valor que se ubica en la posición igual a la variable *nonulls* y con ello se obtiene la mediana.  Ambos resultados dan como valor *$3,239.99*

##### 4) Moda

$
--Moda del Número de computadoras en los hogares

SELECT TOP 1 num_compu FROM hogar GROUP BY num_compu ORDER BY COUNT(*) DESC 
$

Con esta cláusula lo que se esta haciendo es escoger la primera fila de una tabla ordenada de manera descendente de las frecuencias de los valores únicos de la variable "número de computadoras". En otras palabras, la moda del número de computadoras por hogar en la base de datos (spoiler: es 0).

