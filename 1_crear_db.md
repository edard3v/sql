# Acceder a PostgreSQL y Crear una Base de Datos

## Acceder desde la Consola

1. Abre una terminal.
2. Conéctate al cliente de PostgreSQL con el siguiente comando:

```sh
sudo -u postgres psql
```

## Crear una Base de Datos

Para crear una base de datos en PostgreSQL, usa el siguiente comando dentro de la consola de `psql`:

```sql
CREATE DATABASE nombre_base_datos;
```

Puedes verificar que la base de datos se creó con:

```sql
\l
```

Para conectarte a la nueva base de datos, usa:

```sql
\c nombre_base_datos
```

## Crear un Usuario y Asignarle Permisos

Si necesitas crear un usuario y asignarle permisos a la nueva base de datos, ejecuta:

```sql
CREATE USER nombre_usuario WITH PASSWORD 'tu_contraseña';
GRANT ALL PRIVILEGES ON DATABASE nombre_base_datos TO nombre_usuario;
```

## Salir de PostgreSQL

Para salir de la consola de `psql`, usa el comando:

```sh
\q
```

## Modificar nombre de db

```sh
ALTER DATABASE nombre_actual RENAME TO nuevo_nombre;
```

## Conclusión

Con estos pasos, puedes ingresar a PostgreSQL desde la terminal, crear una base de datos y asignar permisos a un usuario. ¡Listo para empezar a trabajar con SQL!
