# Cómo Actualizar Registros en PostgreSQL

## Sintaxis Básica

```sql
UPDATE nombre_tabla
SET columna1 = nuevo_valor1, columna2 = nuevo_valor2
WHERE condición;  -- ¡IMPORTANTE! Sin WHERE se actualizan TODOS los registros.
```

### Ejemplo

```sql
UPDATE clientes
SET email = 'nuevo_email@example.com', telefono = '+123456789'
WHERE id = 1;  -- Actualiza solo el cliente con ID 1
```

## Actualizar con Datos de Otra Tabla

```sql
UPDATE pedidos
SET total = productos.precio * pedidos.cantidad
FROM productos
WHERE pedidos.producto_id = productos.id;
```

## Usando Subconsultas

```sql
UPDATE empleados
SET salario = salario * 1.10
WHERE departamento_id IN (SELECT id FROM departamentos WHERE nombre = 'Ventas');
```

## Devolver los Registros Actualizados

```sql
UPDATE productos
SET precio = precio * 0.9  -- Aplica 10% de descuento
WHERE stock > 100
RETURNING id, nombre, precio;  -- Muestra los registros afectados
```

## Consejos Clave

1. **Siempre usa `WHERE`** a menos que quieras actualizar _toda_ la tabla.
2. Prueba con `SELECT` primero para ver qué registros serán afectados:
   ```sql
   SELECT * FROM clientes WHERE edad > 30;  -- Verifica antes de hacer:
   UPDATE clientes SET categoria = 'VIP' WHERE edad > 30;
   ```
3. Para valores incrementales: `SET cantidad = cantidad + 1`.

⚠️ **¡Cuidado!** No hay "Ctrl+Z" en SQL. Usa transacciones (`BEGIN; ... COMMIT/ROLLBACK;`) en operaciones críticas.

```sql
BEGIN;  -- Inicia transacción
UPDATE cuenta SET saldo = saldo - 100 WHERE id = 1;
UPDATE cuenta SET saldo = saldo + 100 WHERE id = 2;
COMMIT;  -- Confirma los cambios (o ROLLBACK para cancelar)
```

¿Necesitas un ejemplo más complejo o tienes un caso específico? 🛠️
