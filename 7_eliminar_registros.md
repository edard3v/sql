# 🗑️ Eliminar Registros en PostgreSQL

## Sintaxis Básica de DELETE

```sql
DELETE FROM nombre_tabla
WHERE condición;
```

### Ejemplo Simple

```sql
-- Eliminar un registro específico
DELETE FROM clientes
WHERE id = 123;
```

## Eliminación con Condiciones

```sql
-- Eliminar registros que cumplen cierta condición
DELETE FROM pedidos
WHERE fecha < '2023-01-01' AND estado = 'cancelado';

-- Usando subconsultas
DELETE FROM productos
WHERE categoria_id IN (
  SELECT id FROM categorias
  WHERE nombre = 'Obsoletos'
);
```

## Eliminar Todos los Registros

```sql
-- ¡PELIGRO! Elimina TODOS los registros de la tabla
DELETE FROM temporal_logs;

-- Alternativa más rápida para tablas grandes
TRUNCATE TABLE temporal_logs;
```

## Eliminación con JOIN

```sql
-- Eliminar usando relación con otra tabla
DELETE FROM detalle_pedidos
USING pedidos
WHERE detalle_pedidos.pedido_id = pedidos.id
AND pedidos.estado = 'cancelado';
```

## Devolver Registros Eliminados

```sql
DELETE FROM empleados
WHERE departamento = 'Ventas'
RETURNING *;  -- Muestra los registros eliminados
```

## Buenas Prácticas

1. **SIEMPRE** usa WHERE a menos que realmente quieras vaciar la tabla
2. Haz primero un SELECT con las mismas condiciones para ver qué se eliminará:
   ```sql
   SELECT * FROM clientes WHERE ultima_compra < '2020-01-01';
   -- Luego:
   DELETE FROM clientes WHERE ultima_compra < '2020-01-01';
   ```
3. Para operaciones críticas, usa transacciones:
   ```sql
   BEGIN;
   DELETE FROM log_errores WHERE fecha < CURRENT_DATE - INTERVAL '6 months';
   ROLLBACK;  -- o COMMIT si estás seguro
   ```

## TRUNCATE vs DELETE

| Característica      | TRUNCATE   | DELETE    |
| ------------------- | ---------- | --------- |
| Velocidad           | Más rápido | Más lento |
| Clausula WHERE      | No permite | Permite   |
| Reinicia secuencias | Sí         | No        |
| Dispara triggers    | No         | Sí        |

```sql
-- TRUNCATE es ideal para tablas temporales o de reinicio
TRUNCATE TABLE sesiones_temporales RESTART IDENTITY;
```
