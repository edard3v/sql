# Cómo Insertar Datos en una Tabla (PostgreSQL)

## Sintaxis Básica

```sql
INSERT INTO nombre_tabla (columna1, columna2, ...)
VALUES (valor1, valor2, ...);
```

### Ejemplo

```sql
INSERT INTO clientes (id, nombre, email)
VALUES (1, 'Juan Pérez', 'juan@example.com');
```

## Insertar Múltiples Filas

```sql
INSERT INTO clientes (id, nombre, email)
VALUES
    (2, 'Ana Gómez', 'ana@example.com'),
    (3, 'Carlos Ruiz', 'carlos@example.com');
```

## Insertar desde otra tabla

```sql
INSERT INTO clientes_activos (id, nombre)
SELECT id, nombre FROM clientes
WHERE estado = 'activo';
```

## Valores por Defecto

Si la tabla tiene columnas con valores por defecto (como `serial` o `DEFAULT`):

```sql
INSERT INTO productos (nombre, precio)
VALUES ('Laptop', 999.99);  -- La columna "id" se auto-genera.
```

## Consejos

- Usa `RETURNING *` para ver los datos insertados:
  ```sql
  INSERT INTO clientes (nombre) VALUES ('Luisa') RETURNING *;
  ```
- Evita errores de tipos: los valores deben coincidir con el tipo de la columna.

📌 _¿Necesitas algo más específico? ¡Pregunta!_
