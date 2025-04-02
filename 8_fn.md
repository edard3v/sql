# Funciones más comunes en el `SELECT` (PostgreSQL)

## 1. Funciones de Agregación

- `COUNT(*)` → Cuenta el número de filas.

  ```sql
  SELECT COUNT(*) FROM empleados;
  ```

- `SUM(columna)` → Suma los valores de una columna numérica.

  ```sql
  SELECT SUM(sueldo) FROM empleados;
  ```

- `AVG(columna)` → Calcula el promedio.

  ```sql
  SELECT AVG(edad) FROM clientes;
  ```

- `MIN(columna)` / `MAX(columna)` → Mínimo y máximo.

  ```sql
  SELECT MIN(precio), MAX(precio) FROM productos;
  ```

## 2. Funciones de Texto

- `UPPER(texto)` / `LOWER(texto)` → Convierte a mayúsculas/minúsculas.

  ```sql
  SELECT UPPER(nombre) FROM clientes;
  ```

- `CONCAT(str1, str2)` → Concatena cadenas.

  ```sql
  SELECT CONCAT(nombre, ' ', apellido) FROM usuarios;
  ```

- `SUBSTRING(texto FROM inicio FOR longitud)` → Extrae parte de un texto.

  ```sql
  SELECT SUBSTRING(nombre FROM 1 FOR 3) FROM empleados;
  ```

- `LENGTH(texto)` → Longitud del texto.

  ```sql
  SELECT LENGTH(direccion) FROM clientes;
  ```

## 3. Funciones de Fecha y Hora

- `CURRENT_DATE` / `CURRENT_TIMESTAMP` → Fecha y hora actual.

  ```sql
  SELECT CURRENT_DATE;
  ```

- `EXTRACT(field FROM fecha)` → Extrae año, mes, día, etc.

  ```sql
  SELECT EXTRACT(YEAR FROM fecha_nacimiento) FROM personas;
  ```

- `DATE_TRUNC('precision', fecha)` → Trunca a precisión (ej: 'month', 'year').

  ```sql
  SELECT DATE_TRUNC('month', fecha_pedido) FROM pedidos;
  ```

## 4. Funciones Condicionales

- `COALESCE(val1, val2, ...)` → Retorna el primer valor no nulo.

  ```sql
  SELECT COALESCE(telefono, 'Sin teléfono') FROM clientes;
  ```

- `CASE WHEN ... THEN ... ELSE ... END` → Condicionales personalizados.

  ```sql
  SELECT nombre, CASE WHEN edad >= 18 THEN 'Mayor' ELSE 'Menor' END FROM personas;
  ```

## 5. Funciones Matemáticas

- `ROUND(numero, decimales)` → Redondea un número.

  ```sql
  SELECT ROUND(precio, 2) FROM productos;
  ```

- `ABS(numero)` → Valor absoluto.

  ```sql
  SELECT ABS(descuento) FROM ventas;
  ```

- `RANDOM()` → Número aleatorio entre 0 y 1.

  ```sql
  SELECT RANDOM();
  ```

## 6. Funciones de Conversión

- `CAST(valor AS tipo)` → Convierte tipos de datos.

  ```sql
  SELECT CAST('2023-01-01' AS DATE);
  ```

- `TO_CHAR(fecha/número, formato)` → Formatea fechas/números.

  ```sql
  SELECT TO_CHAR(fecha_pedido, 'DD/MM/YYYY') FROM pedidos;
  ```

---

### 📌 Notas:

- PostgreSQL tiene muchas más funciones (JSON, GIS, etc.).
- Usa `\df` en `psql` para listar funciones disponibles.
- Documentación oficial: [https://www.postgresql.org/docs/](https://www.postgresql.org/docs/).
