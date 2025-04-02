# 📌 Cláusulas SQL Básicas en PostgreSQL

Principales cláusulas para consultas (`SELECT`), con ejemplos prácticos:

## 1. `WHERE` (Filtrar registros)

```sql
SELECT * FROM productos
WHERE precio > 100 AND stock <= 10;  -- Condiciones lógicas
```

## 2. `ORDER BY` (Ordenar resultados)

```sql
SELECT nombre, precio FROM productos
ORDER BY precio DESC;  -- ASC (ascendente) o DESC (descendente)
```

## 3. `GROUP BY` (Agrupar datos)

```sql
SELECT categoria, COUNT(*) as total
FROM productos
GROUP BY categoria;  -- Útil con funciones de agregación (COUNT, SUM, AVG)
```

## 4. `HAVING` (Filtrar grupos)

```sql
SELECT categoria, AVG(precio) as promedio
FROM productos
GROUP BY categoria
HAVING AVG(precio) > 50;  -- Filtra después del GROUP BY
```

## 5. `LIMIT` y `OFFSET` (Paginación)

```sql
SELECT * FROM clientes
LIMIT 10 OFFSET 20;  -- Muestra 10 registros, saltando los primeros 20
```

## 6. `JOIN` (Relacionar tablas)

```sql
SELECT p.nombre, c.nombre as categoria
FROM productos p
JOIN categorias c ON p.categoria_id = c.id;  -- INNER JOIN (solo coincidencias)
```

## 7. `DISTINCT` (Eliminar duplicados)

```sql
SELECT DISTINCT ciudad FROM clientes;  -- Valores únicos
```

## 8. `CASE` (Condicionales en consultas)

```sql
SELECT nombre,
       CASE
           WHEN precio < 50 THEN 'Económico'
           ELSE 'Premium'
       END as tipo
FROM productos;
```

## 9. `LIKE` e `ILIKE` (Búsqueda de patrones)

```sql
SELECT * FROM clientes
WHERE nombre LIKE 'A%';  -- % (cualquier texto), _ (un carácter), ILIKE (insensible a mayúsculas)
```

## 10. `COALESCE` (Valores por defecto para NULL)

```sql
SELECT nombre, COALESCE(telefono, 'No registrado') FROM clientes;
```

## ⚠️ Importante

- El orden de ejecución **no** es el mismo que el orden de escritura:  
  `FROM` → `WHERE` → `GROUP BY` → `HAVING` → `SELECT` → `ORDER BY` → `LIMIT`.

¿Necesitas profundizar en alguna? ¡Dímelo! 🎯

_(Ejemplo avanzado: Subconsultas, `WITH` (CTEs), `FILTER`, `WINDOW functions`)._
