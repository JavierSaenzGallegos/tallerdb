Elaborado por Javier Saenz Gallegos
Uso de GROUP BY en SQL
El comando GROUP BY en SQL se usa para agrupar filas que tienen los mismos valores en columnas específicas y luego aplicar funciones de agregación sobre esos grupos.

Sintaxis básica

SELECT columna1, AGG_FUNC(columna2)
FROM tabla
GROUP BY columna1;
Donde AGG_FUNC puede ser una función de agregación como SUM(), COUNT(), AVG(), MIN(), MAX(), etc.

Ejemplo básico
Si tenemos una tabla Empleados con las siguientes columnas:

EmpID	Salario
1	200
1	300
2	300
Podemos usar GROUP BY para sumar los salarios por empleado:


SELECT EmpID, SUM(Salario) AS TotalSalario
FROM Empleados
GROUP BY EmpID;
Resultado:

EmpID	TotalSalario
1	500
2	300
Uso con HAVING
El HAVING se usa para filtrar resultados después de aplicar GROUP BY. Ejemplo:


SELECT departamento, COUNT(*) AS Empleados
FROM empleados
GROUP BY departamento
HAVING COUNT(*) >= 10;
Esto devolverá solo los departamentos con 10 o más empleados​.

Uso con múltiples columnas
Se pueden agrupar datos en base a más de una columna:


SELECT departamento, puesto, COUNT(*) AS Empleados
FROM empleados
GROUP BY departamento, puesto;
Esto agrupará primero por departamento y luego por puesto​.

Consideraciones
Todas las columnas en el SELECT deben estar en GROUP BY o ser usadas en una función de agregación.
HAVING filtra después de agrupar, mientras que WHERE filtra antes de agrupar.
Se puede combinar con ORDER BY para ordenar los resultados.
