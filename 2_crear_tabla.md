# Creación de Tablas en PostgreSQL

## Sintaxis Básica

La sintaxis para crear una tabla en PostgreSQL es la siguiente:

```sql
CREATE TABLE nombre_tabla (
    nombre_columna1 tipo_dato restricciones,
    nombre_columna2 tipo_dato restricciones,
    ...
    PRIMARY KEY (columna_principal)
);
```

## Ejemplo de Creación de Tabla

Supongamos que queremos crear una tabla llamada `usuarios` con las siguientes columnas:

- `id`: identificador único (clave primaria, autoincremental)
- `nombre`: nombre del usuario (cadena de texto)
- `email`: correo electrónico (cadena de texto, único)
- `edad`: edad del usuario (entero, opcional)
- `fecha_registro`: fecha de registro (fecha por defecto al momento de inserción)

El comando SQL para crear esta tabla sería:

```sql
CREATE TABLE usuarios (
    id SERIAL PRIMARY KEY,
    nombre VARCHAR(100) NOT NULL,
    email VARCHAR(255) UNIQUE NOT NULL,
    edad INTEGER,
    fecha_registro TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

## Explicación de la Sentencia

- `id SERIAL PRIMARY KEY`: Crea una columna autoincremental y la establece como clave primaria.
- `nombre VARCHAR(100) NOT NULL`: Define una columna de texto de hasta 100 caracteres y obliga a que no sea nula.
- `email VARCHAR(255) UNIQUE NOT NULL`: Define una columna de texto única y no nula.
- `edad INTEGER`: Define una columna entera opcional.
- `fecha_registro TIMESTAMP DEFAULT CURRENT_TIMESTAMP`: Guarda la fecha y hora de registro por defecto.

## Verificar la Creación de la Tabla

Puedes listar las tablas creadas en PostgreSQL con:

```sql
\dt
```

Para ver la estructura de la tabla:

```sql
\d usuarios
```

## Conclusión

Crear una tabla en PostgreSQL es un proceso simple usando `CREATE TABLE`. Puedes definir tipos de datos, restricciones y valores por defecto para garantizar la integridad de los datos.
