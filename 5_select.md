# 📋 Guía Rápida de `SELECT` en PostgreSQL

## Sintaxis Básica

```sql
SELECT columnas FROM tabla [WHERE condición] [ORDER BY] [LIMIT];
```

## Selección de Columnas

```sql
-- Todas las columnas
SELECT * FROM productos;

-- Columnas específicas
SELECT nombre, precio FROM productos;

-- Expresiones y alias
SELECT nombre, precio * 1.21 AS precio_con_iva FROM productos;
```

## Filtrado con WHERE

```sql
-- Operadores básicos
SELECT * FROM productos WHERE precio > 100;

-- Múltiples condiciones
SELECT * FROM productos
WHERE precio BETWEEN 50 AND 100
AND stock > 0;

-- Fechas
SELECT * FROM pedidos
WHERE fecha BETWEEN '2024-01-01' AND '2024-12-31';
```

## Ordenamiento (ORDER BY)

```sql
-- Ascendente (default)
SELECT * FROM productos ORDER BY nombre;

-- Descendente
SELECT * FROM productos ORDER BY precio DESC;

-- Múltiples criterios
SELECT * FROM empleados
ORDER BY departamento ASC, salario DESC;
```

## Limitar Resultados (LIMIT/OFFSET)

```sql
-- Primeros 10 registros
SELECT * FROM clientes LIMIT 10;

-- Paginación (registros 11-20)
SELECT * FROM clientes LIMIT 10 OFFSET 10;
```

## Funciones Comunes

```sql
-- Agregación
SELECT COUNT(*) FROM productos;
SELECT AVG(precio) FROM productos WHERE categoria = 'Electrónicos';

-- Texto
SELECT UPPER(nombre) FROM clientes;
SELECT CONCAT(nombre, ' ', apellido) AS nombre_completo FROM empleados;

-- Fechas
SELECT nombre, EXTRACT(YEAR FROM fecha_nacimiento) AS año_nacimiento
FROM clientes;
```

## Consultas Avanzadas

```sql
-- Subconsultas
SELECT nombre FROM productos
WHERE precio > (SELECT AVG(precio) FROM productos);

-- WITH (CTEs)
WITH productos_caros AS (
  SELECT * FROM productos WHERE precio > 1000
)
SELECT * FROM productos_caros WHERE stock > 5;
```

## Consejos Prácticos

1. Usa `EXPLAIN ANALYZE` para optimizar consultas lentas
2. Evita `SELECT *` en tablas grandes (especifica solo las columnas necesarias)
3. Para pruebas, siempre agrega `LIMIT` a consultas sobre datos desconocidos

¿Necesitas algún ejemplo específico o explicación más detallada? 😊
