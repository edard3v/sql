# Operadores SQL en PostgreSQL: BETWEEN, AND, OR y más

## 1. `BETWEEN`

El operador `BETWEEN` se usa para filtrar valores dentro de un rango inclusivo.

### **Sintaxis:**

```sql
SELECT * FROM tabla WHERE columna BETWEEN valor1 AND valor2;
```

### **Ejemplo:**

```sql
SELECT * FROM productos WHERE precio BETWEEN 100 AND 500;
```

Este ejemplo selecciona productos con un precio entre 100 y 500 (incluyendo ambos extremos).

## 2. `AND`

El operador `AND` se usa para combinar múltiples condiciones en una consulta, y devuelve resultados solo si todas las condiciones son verdaderas.

### **Sintaxis:**

```sql
SELECT * FROM tabla WHERE condicion1 AND condicion2;
```

### **Ejemplo:**

```sql
SELECT * FROM empleados WHERE edad > 25 AND salario > 3000;
```

Este ejemplo selecciona empleados que tengan más de 25 años **y** un salario superior a 3000.

## 3. `OR`

El operador `OR` permite combinar múltiples condiciones y devuelve resultados si al menos una de las condiciones es verdadera.

### **Sintaxis:**

```sql
SELECT * FROM tabla WHERE condicion1 OR condicion2;
```

### **Ejemplo:**

```sql
SELECT * FROM clientes WHERE ciudad = 'Madrid' OR ciudad = 'Barcelona';
```

Este ejemplo selecciona clientes que vivan en Madrid **o** en Barcelona.

## 4. `NOT`

El operador `NOT` invierte el resultado de una condición.

### **Ejemplo:**

```sql
SELECT * FROM clientes WHERE NOT ciudad = 'Madrid';
```

Este ejemplo selecciona todos los clientes que **no** viven en Madrid.

## 5. `IN`

El operador `IN` comprueba si un valor pertenece a una lista de valores.

### **Ejemplo:**

```sql
SELECT * FROM empleados WHERE departamento IN ('Ventas', 'Marketing');
```

Este ejemplo selecciona empleados cuyo departamento sea "Ventas" o "Marketing".

## 6. `NOT IN`

Es la negación de `IN`, selecciona los valores que **no** están en la lista.

### **Ejemplo:**

```sql
SELECT * FROM empleados WHERE departamento NOT IN ('Ventas', 'Marketing');
```

Selecciona empleados que **no** pertenecen a "Ventas" ni "Marketing".

## 7. `EXISTS`

Verifica si una subconsulta devuelve resultados.

### **Ejemplo:**

```sql
SELECT * FROM clientes WHERE EXISTS (SELECT 1 FROM pedidos WHERE pedidos.cliente_id = clientes.id);
```

Este ejemplo selecciona clientes que tienen al menos un pedido registrado.

## 8. `NOT EXISTS`

Es la negación de `EXISTS`, devuelve `TRUE` si la subconsulta **no** devuelve resultados.

### **Ejemplo:**

```sql
SELECT * FROM clientes WHERE NOT EXISTS (SELECT 1 FROM pedidos WHERE pedidos.cliente_id = clientes.id);
```

Este ejemplo selecciona clientes **sin** pedidos registrados.

## 9. `ANY`

Compara un valor con cualquiera de los valores devueltos por una subconsulta.

### **Ejemplo:**

```sql
SELECT * FROM empleados WHERE salario > ANY (SELECT salario FROM empleados WHERE departamento = 'IT');
```

Selecciona empleados cuyo salario sea mayor que **cualquier** salario en el departamento de IT.

## 10. `ALL`

Similar a `ANY`, pero la condición debe cumplirse para **todos** los valores de la subconsulta.

### **Ejemplo:**

```sql
SELECT * FROM empleados WHERE salario > ALL (SELECT salario FROM empleados WHERE departamento = 'IT');
```

Selecciona empleados cuyo salario sea mayor que **todos** los salarios en el departamento de IT.

---

Estos operadores son fundamentales para hacer consultas más precisas y efectivas en PostgreSQL.
