# Curso de PostgreSQL

Instruido por: Oswaldo Rodríguez González

## 1. CONFIGURAR POSTGRESQL 
-------------- 


## 3. Instalación y configuración de la Base de Datos


1. [Descargar Postgresql](https://www.postgresql.org/)
2. Ingresamos la contraseña del usuario administrador. De manera predeterminada, Postgres crea un usuario super administrador llamado postgres que tiene todos los permisos y acceso a toda la base de datos, tanto para consultarla como para modificarla. En éste paso indicamos la clave de ese usuario super administrador.
3. Debes ingresar una clave muy segura y guardarla porque la vas a necesitar después. Luego hacemos clic en siguiente.
4. Ingresar por el SQL shell Pgadmin
5. Crear DB
   ```sql
   create database transporte_publico;
   ```
6.  Cambiar de base de datos
    - \c transporte_publico


### Instalacion en linux
- https://www.youtube.com/watch?v=40uGNsi7ysc
- https://www.tecmint.com/install-postgresql-and-pgadmin-in-ubuntu/

- [Instalacion con docker](https://platzi.com/tutoriales/2059-practico-sql/8833-pgadmin-y-postgres-con-docker-sin-instalacion-de-programas-ni-dependencias/)




## 4. Interacción con Postgres desde la Consola


```sh
# ENTRAR A LA CONSOLA DE POSTGRES
psql -U postgres -W

# VER LOS COMANDOS \ DE POSTGRES
\?

# LISTAR TODAS LAS BASES DE DATOS
\l

#VER LAS TABLAS DE UNA BASE DE DATOS
\dt
 
#CAMBIAR A OTRA BD
\c nombre_BD
 
# DESCRIBIR UNA TABLA
\d nombre_tabla

# VER TODOS LOS COMANDOS SQL
\h

# VER COMO SE EJECTUA UN COMANDO SQL
\h nombre_de_la_funcion

# CANCELAR TODO LO QUE HAY EN PANTALLA
Ctrl + C

# VER LA VERSION DE POSTGRES INSTALADA, IMPORTANTE PONER EL ';'
SELECT version();

# VOLVER A EJECUTAR LA FUNCION REALIZADA ANTERIORMENTE
\g

#INICIALIZAR EL CONTADOR DE TIEMPO PARA QUE LA CONSOLA TE DIGA EN CADA EJECUCION ¿CUANTO DEMORO EN EJECUTAR ESA FUNCION?
\timing

# LIMPIAR PANTALLA DE LA CONSOLA PSQL
Ctrl + L
```

- [ACCEDER A LA CONSOLA DE POSTGRES](https://tecnologiaenvivo.com/acceder-a-la-consola-de-postgres/)


## 5. PgAdmin: Interacción con Postgres desde la Interfaz Gráfica

Servers -> add
Tablespaces-> espacio en memoria fisico para guardar la bd, se puede conf. para que un disco quede en c y otro en d
login/groups

- [Descargar pgAdmin](https://www.pgadmin.org/)


OPCIONES DEL PANEL IZQUIERDO
  - Cast: traduccion de tipos de datos explicito
  - Catalog: subdirectorio de tabas
  - Trigger: ejecutar funciones en base a algo que sucede en la bd
  - Extensions: instalar modulos desarrollados por terceros
  - Foreign data wrappers: acceso a BD remoto
  - Languages: Tipos de datos diferentes
  - Schemas: Informacion propia de la tabla, public es el predeterminado


### Introduction to PostgreSQL PL/pgSQL

- [Introduction to PostgreSQL PL/pgSQL](https://www.postgresqltutorial.com/introduction-to-postgresql-stored-procedures/)





## 6. Archivos de Configuración


Ver los usuarios
\du
\du+


Ruta ejemplo: C:\Program Files\PostgreSQL\12\data
Mi resumen:

Los archivos de configuración son tres principales:

  - postgreql.conf
  - pg.hba.conf
  - pg_ident.conf
La ruta de los mismos depende del sistema Operarivo, para saber que que ruta estan, basta con hacer una Query

```sql
SHOW config_file;
```

> NOTA: siempre es bueno hacer una copia original de los archivos antes de modificarlos por si movemos algo que no.


- https://platzi.com/clases/linux/
- https://platzi.com/blog/administracion-usuarios-servidores-linux/
- https://code.visualstudio.com/



## 7. Comandos más utilizados en PostgreSQL

```sql
SELECT version();
```
### Comando de ayuda

| Item     | Value |
| ------   | -----:|
| Con el cual podemos ver la lista de todos los comandos disponibles en consola, comandos que empiezan con backslash ( \ )   | `\?`  |
| Con este comando veremos la información de todas las consultas SQL disponibles en consola.    | `\h`  |
 
 
### Comandos de navegación y consulta de información

| Item                                                          | Value |
| ---------                                                     | -----:|
| Saltar entre bases de datos                                   | `\c`  |
| Listar base de datos disponibles                              | `\l`  |
| Listar las tablas de la base de datos                         | `\dt` |
| <nombre_tabla> Describir una tabla                            | `\d`  |
| Listar los esquemas de la base de datos actual                | `\dn` |
| Listar las funciones disponibles de la base de datos actual   | `\df` |
| Listar las vistas de la base de datos actual                  | `\dv` |
| Listar los usuarios y sus roles de la base de datos actual    | `\du` |

### Comandos de inspección y ejecución

|  Item   | Value |
|  ---------   | -----:|
|Volver a ejecutar el comando ejecutando justo antes                                                        |`\g`   |
|Ver el historial de comandos ejecutados                                                                    |`\s`   |
|<nombre_archivo> Si se quiere guardar la lista de comandos ejecutados en un archivo de texto plano         |`\s`   |
|<nombre_archivo> Ejecutar los comandos desde un archivo                                                    |`\i`   |
|Permite abrir un editor de texto plano, escribir comandos y ejecutar en lote. \e abre el editor de texto, escribir allí todos los comandos, luego guardar los cambios y cerrar, al cerrar se ejecutarán todos los comandos guardados.                   |`\e`   |
|Equivalente al comando anterior pero permite editar también funciones en PostgreSQL                        |`\ef`  |

### Comandos para debug y optimización

| Item                                                          | Value   |
| ---------                                                     | -----:  |
| Activar / Desactivar el contador de tiempo por consulta       |`\timing`|

### Comandos para cerrar la consola

| Item                    | Value |
| ---------               | -----:|
| Cerrar la consola       |`\q`   |


```sql
CREATE DATABASE base; -- crea base
CREATE TABLE tabla (columnas); crea tabla
INSERT INTO tabla(columna) VALUES('dato');
SELECT * FROM tabla;
UPDATE tabla SET cammpo = dato WHERE condicion;
DELETE FROM tabla WHERE condicion;
```


## 9. Tipos de datos


### Tipos de datos

- Principales:
- Numéricos(Numeros enteros, Numeros Decimales, Seriales)
- Monetarios(cantidad de moneda)
- Texto(almacenar cadenas y texto, existen tres VARCHAR, CHAR, TEXT)
- Binario(1 Y 0)
- Fecha/Hora(Para almacenar Fechas y/o Horas, DATE TYPE, TIME TYPE, TIMESTAMP, INTERVAL)
- Boolean(Verdadero o Falso)

### Especiales propios de postgres
- Geométricos: Permiten calcular distancias y áreas usando dos valores X y Y.
- Direcciones de Red: Cálculos de máscara de red
- Texto tipo bit: Cálculos en otros sistemas, ejm(hexadecimal, binario)
- XML, JSON
- Arreglos: Vectores y Matrices

### Lecturas recomendadas

- [PostgreSQL data types, tipos de datos más utilizados](https://todopostgresql.com/postgresql-data-types-los-tipos-de-datos-mas-utilizados/)
- [Chapter 8. Data Types](https://www.postgresql.org/docs/11/datatype.html)
- [Tipos de datos Postgres](https://www.ibiblio.org/pub/linux/docs/LuCaS/Tutoriales/NOTAS-CURSO-BBDD/notas-curso-BD/node134.html)


## 10. Diseñando nuestra base de datos: estructura de las tablas

1. cuales son los objetos tangibles del sistema

 - pasajero
 - Estacion
 - Tren


llaves primarias: valores unicos que no se repiten
PK y FK notaciones para llaves primarias y foraneas

Es Buena práctica como se ve en otros cursos es muy buena práctica tener los nombres de las tablas (sustantivos) en inglés y en plural.

Usar todos los nombres en singular o plural

Pensar en los elementos q existen
Cuando la relacion es una accion, crear tabla de relacion

Estandar entidad relacion


- https://platzi.com/clases/bd/
- https://platzi.com/clases/sql-mysql/
- https://platzi.com/clases/mongodb/




## 11. Jerarquía de Bases de Datos


Toda jerarquía de base de datos se basa en los siguientes elementos:

Servidor de base de datos: Computador que tiene un motor de base de datos instalado y en ejecución.

Motor de base de datos: Software que provee un conjunto de servicios encargados de administrar una base de datos.

Base de datos: Grupo de datos que pertenecen a un mismo contexto.

Esquemas de base de datos en PostgreSQL: Grupo de objetos de base de datos que guarda relación entre sí (tablas, funciones, relaciones, secuencias).

Tablas de base de datos: Estructura que organiza los datos en filas y columnas formando una matriz.

PostgreSQL es un motor de base de datos.

La estructura de la base de datos diseñada para el reto corresponde a los siguientes
elementos:




## 2. GESTION DE LA INFORMACION EN BASES DE DATOS
-------------- 

## 12. Creación de Tablas

ACCIONES:
- CREATE - Inicializar la estructura de la tabla, sin ningun tipo de 

- ALTER - Cuando ya esta creada la tabla e incluso con datos, permite agregar PK, indices, columnas, incluso roles como propietarios de la tabla 
	
- DROP - Borrar tabla con toda la info



```sql
CREATE TABLE public.estacion
(
    id integer NOT NULL DEFAULT nextval('estacion_id_seq'::regclass),
    nombre character varying COLLATE pg_catalog."default",
    direccion character varying COLLATE pg_catalog."default",
    CONSTRAINT estacion_pkey PRIMARY KEY (id)
)


ALTER TABLE public.estacion
    OWNER to postgres;



CREATE TABLE public.pasajero
(
    id integer NOT NULL DEFAULT nextval('pasajero_id_seq'::regclass),
    nombre character varying(100) COLLATE pg_catalog."default",
    direccion_residencia character varying COLLATE pg_catalog."default",
    fecha_nacimiento date,
    CONSTRAINT pasajero_pkey PRIMARY KEY (id)
)


ALTER TABLE public.pasajero
    OWNER to postgres;



CREATE TABLE public." trayecto"
(
    id integer NOT NULL DEFAULT nextval('" trayecto_id_seq"'::regclass),
    id_tren integer NOT NULL,
    id_estacion integer NOT NULL,
    CONSTRAINT trayecto_pkey PRIMARY KEY (id)
)


ALTER TABLE public." trayecto"
    OWNER to postgres;



CREATE TABLE public.tren
(
    id integer NOT NULL DEFAULT nextval('tren_id_seq'::regclass),
    modelo character varying COLLATE pg_catalog."default",
    capacidad integer,
    CONSTRAINT tren_pkey PRIMARY KEY (id)
)

ALTER TABLE public.tren
    OWNER to postgres;



CREATE TABLE public.viaje
(
    id serial,
    id_pasajero integer NOT NULL,
    id_trayecto integer NOT NULL,
    inicio date,
    fin date,
    CONSTRAINT viaje_pkey PRIMARY KEY (id)
);

ALTER TABLE public.viaje
    OWNER to postgres;

```

### Notas:

Es de buena costumbre poner el nombre de las tabla en ingles y en plural y el nombre de las columnas en ingles, porque en ingles porque así en caso de que tu proyecto sea presentado para alguien de otro país no sera nada difícil de comprenderlo, esto te lo enseñan o te lo recomienda a mas detalle en el curso de Curso de SQL y MySQL

### Lecturas recomendadas

- [Migrar de MySQL a PostgreSQL](https://www.digitalocean.com/community/tutorials/how-to-migrate-mysql-database-to-postgres-using-pgloader)



## 13. Particiones

Ej:. mucha info en una tabla, si hacemos una consuta se hace recorrido de toda la info para encontrar lo que bucamos

LA TABLA TIENE UN ESPACIO EN MEMORIA
Dos factores:

- Separacion fisica de datos: es pobsible guardar varias partes de la tabla en diferentes espacios de disco

- conserva la misma estructura logica: funciona haciendo el mismo select

Internamente: con el mismo nombre de la tabla le asigna a otras pequeñas tablas que tienen un rango definido


Eje: particion para julio otra para agosto, etc.

Esto acelera mucho las consultas, evita bloqueos cuando se consulta y se modifican muchos datos al mismo tiempo.


La partición es una tabla

No es posible crear llaves primarias en tablas particionadas, ya que la información esta toda dividida.

El uso de las tablas particionadas es para cuando queramos guardar información en masa como bitácoras y esta información debe hacer referencia a las tablas que si tienen llaves primarias, por eso no se hace uso y no es realmente necesaria.

1. Crear la tabla
	```sql
	CREATE TABLE public."Bitacora_viajes"
	(
		"bitacora_ID" serial,
		"viaje_ID" integer,
		fecha date
	) PARTITION BY RANGE (fecha);

	ALTER TABLE public."Bitacora_viajes"
		OWNER to postgres;
	```
2. Crear la particion
   ```sql
	CREATE TABLE bitacora_viaje201001 PARTITION OF bitacora_viaje FOR VALUES RANGE FROM ('2010-01-01') TO ('2019-01-31')
	```
3. probar las insersiones
	```sql
	INSERT INTO public.bitacora_viaje(id_viaje, fecha) VALUES (1, '2020-01-10')
	```


En que casos es recomendado usar el particionamiento de tablas?
> R/ En principio debes particionar tablas que tengan un alto movimiento de datos, muchas inserciones y consultas. Pero al final, si el proyecto llega a durar lo suficiente, terminarás con una cantidad enorme de datos que te obligarán a pariticionar casi todas las tablas de tu base de datos.


Si así es, no es posible particionar una tabla ya creada, deberás crear una tabla particionada y mover los datos de la tabla anterior a la nueva. El copiado, si no son muchos datos, se puede hacer con un simple INSERT … FROM … SELECT, si hay muchos datos (millones) se deberá hacer por partes, para no ir a sobrecargar la tabla, usando Limits o Cursores etc. 




## 14. Creación de Roles


AYUDA PARA CREAR ROL/USUARIO POR CONSOLA:
```
\h CREATE ROLE
```

> NOTA: CREATE ROLE y CREATE USUARIO son lo mismo desde la version 9.3 de postgres, simplemente es un alias de ROLE

CREAR ROL/USUARIO POR CONSOLA:
```sql
CREATE ROLE usuario_consulta ;
```

Ver las funciones del comando CREATE ROLE (help)
```sql
\h CREATE ROLE;
```
Creamos un ROLE (consultas -> lectura, insertar, actualizar)
```sql
CREATE ROLE usuario_consulta;
```
Mostrar todos los usuarios junto a sus atributos
```sh
\dg
```

Agregamos atributos al usuario o role
```sql
ALTER ROLE  usuario_consulta WITH LOGIN;
ALTER ROLE  usuario_consulta WITH SUPERUSER;
ALTER ROLE  usuario_consulta WITH PASSWORD'1234';
```

Elimanos el usuario o role
```sql
DROP ROLE usuario_consulta;
```

La mejor forma de crear un usuario o role por pgadmin
```sql
CREATE ROLE usuario_consulta WITH
LOGIN
NOSUPERUSER
NOCREATEDB
NOCREATEROLE
INHERIT
NOREPLICATION
CONNECTION LIMIT -1
PASSWORD'1234';
```

Para otorgar privilegios a nuestro usuario_consulta
```sql
GRANT INSERT, SELECT, UPDATE ON TABLE public.estacion TO usuario_consulta;
GRANT INSERT, SELECT, UPDATE ON TABLE public.pasajero TO usuario_consulta;
GRANT INSERT, SELECT, UPDATE ON TABLE public.trayecto TO usuario_consulta;
GRANT INSERT, SELECT, UPDATE ON TABLE public.tren TO usuario_consulta;
GRANT INSERT, SELECT, UPDATE ON TABLE public.viaje TO usuario_consulta;
```




## 15. Llaves foráneas


```sql
ALTER TABLE public." trayecto"
    ADD CONSTRAINT trayecto_estacion_fkey FOREIGN KEY (id_estacion)
    REFERENCES public.estacion (id) MATCH SIMPLE
    ON UPDATE CASCADE
    ON DELETE CASCADE
    NOT VALID;

ALTER TABLE public." trayecto"
    ADD CONSTRAINT trayecto_tren_fkey FOREIGN KEY (id_tren)
    REFERENCES public.tren (id) MATCH SIMPLE
    ON UPDATE CASCADE
    ON DELETE CASCADE
    NOT VALID;

ALTER TABLE public." trayecto"
    RENAME TO trayecto;

ALTER SEQUENCE public." trayecto_id_seq"
    RENAME TO trayecto_id_seq;

ALTER TABLE public.viaje
    ADD CONSTRAINT viaje_pasajero_fkey FOREIGN KEY (id_pasajero)
    REFERENCES public.pasajero (id) MATCH SIMPLE
    ON UPDATE CASCADE
    ON DELETE CASCADE
    NOT VALID;

ALTER TABLE public.viaje
    ADD CONSTRAINT viaje_trayecto_fkey FOREIGN KEY (id_trayecto)
    REFERENCES public.trayecto (id) MATCH SIMPLE
    ON UPDATE CASCADE
    ON DELETE CASCADE
    NOT VALID;
```



## 16. Inserción y consulta de datos

```sql
INSERT INTO public.estacion(
	id, nombre, direccion)
	VALUES (default, 'Estacion centro', 'Calle 25 132-66');

INSERT INTO public.estacion(
	id, nombre, direccion)
	VALUES (default, 'Estacion Norte', 'Calle 90 33-44');
```

> NOTA: cuando un campo ha sido creado solo permite el cambio de tipo de dato, entre los tipos compatibles, cuando no hay compatibilidad, toca borrar y volver a crear.

```sql
ALTER TABLE public.trayecto
    ADD COLUMN nombre character varying(100);

INSERT INTO public.tren(
	 capacidad, modelo)
	VALUES (100, 'Maseratti');


DELETE FROM public.tren
	WHERE id=1;
```

Se borra el tren y tambien se borra el trayecto puesto que el borrado esta configurado en cascada
```sql
INSERT INTO public.trayecto(
	id_tren, id_estacion, nombre)
	VALUES (2, 1, 'Ruta 2');
```




## 17. Inserción masiva de datos


[mockaroo](https://www.mockaroo.com/)

Para las fechas tener en cuenta el formato de fechas
```sql
select current_date;
```


Los que quieren limpiar las tablas:
```sql
TRUNCATE estacion  CASCADE;
TRUNCATE tren  CASCADE;
TRUNCATE trayecto  CASCADE;
TRUNCATE pasajero  CASCADE;
TRUNCATE viaje  CASCADE;
```
Comenzar el serial desde cero:
```sql
TRUNCATE TABLE tren, trayecto, viaje, estacion, pasajero RESTART IDENTITY;
```


si alguien quiere importar al archivo desde terminal psql es:

\i C:/Users/Yo/Desktop/pasajeros.sql
básicamente solo necesitas \i y el el path donde se encuentra tu archivo sql.



## 3. GENERAR CONSULTAS AVANZADAS
-------------- 



## 18. Cruzar tablas: SQL JOIN


### Teoria de conjuntos implentada en SQL
[Join e Inner Join son exactamente lo mismo](https://www.postgresqltutorial.com/postgresql-joins/)

- Saber que pasajeros han tomado viajes
	```sql
	select * from pasajero 
	join viaje on (viaje.id_pasajero = pasajero.id);
	```

- Saber quienes no han tomado viajes
	```sql
	select * from viaje
	left join pasajero on (viaje.id_pasajero = pasajero.id)
	where viaje is null;
	```



## 19. Funciones Especiales Principales


```sql

-- Funciones especiales
ON CONFLICT DO
RETURNING
LIKE / ILIKE
IS / IS NOT


-- Insercion de un dato que ya existe, no pasa nada
INSERT INTO public.estacion(id, nombre, direccion)
VALUES (1, 'Nombre', 'Dire')
ON CONFLICT DO NOTHING;


-- Insercion de un dato que ya existe, te cambia los campos de nombre y direccion
INSERT INTO public.estacion(id, nombre, direccion)
VALUES (1, 'Nombre', 'Dire')
ON CONFLICT (id) DO UPDATE SET nombre = 'Nombre', direccion = 'Dire';


-- Insertara una tupla y mostrara la tupla
INSERT INTO public.estacion(nombre, direccion)
VALUES ('RETU', 'RETDIRE')
RETURNING *;


-- LIKE|ILIKE
-- %: Uno o cualquier valor
-- _: Un valor
SELECT nombre FROM public.pasajero
WHERE nombre LIKE 'o%';

-- buscamos sin importar mayusculas o minusculas
SELECT nombre FROM public.pasajero
WHERE nombre ILIKE 'o%';


-- si una estacion o tren tiene un valor nulo
SELECT * FROM public.tren
WHERE modelo IS NULL;
```




## 20. Funciones Especiales avanzadas en PosgreSQL


- COALESCE: compara dos valores y retorna el que es nulo
- NULLIF: Compara 2 valores y Retorna null si son iguales
- GREATEST: Compara un arreglo y retorna el mayor
- LEAST: Compara un arreglo de valores y retorna el menor
- BLOQUES ANONIMOS: Ingresa condicionales dentro de una consulta de BD

```sql
SELECT id, coalesce (nombre, 'No aplica') as nombre, direccion
    FROM public.estacion
    where id=1;


SELECT NULLIF(0,0);
SELECT NULLIF(0,1);


SELECT GREATEST(5,5,8,95,75,4225,8,6,9,212,6);
SELECT LEAST(2,5,8,95,75,4225,8,6,9,212,6);


SELECT id, nombre, direccion_residencia, fecha_nacimiento,
CASE
WHEN fecha_nacimiento > '1995-01-01'
THEN
    'Niño'
ELSE
    'Mayor'
END
    FROM public.pasajero
```


## RETO

```sql
SELECT id, nombre, direccion_residencia, fecha_nacimiento,
CASE
WHEN nombre ILIKE 'c%' THEN
'Inicia con C'
ELSE
'Inicia con otra letra'
END AS Inicial,
CASE
WHEN ((CURRENT_DATE-fecha_nacimiento)/365) >= 18 THEN
'Mayor'
ELSE
'Menor'
END AS Edad
FROM pasajero;
```


## 21. Vistas


Una vista es una consulta que se repite mucho y convertirla en un solo nombre


**Existen 2 tipos de vistas:**

- Vista Volátil: Consulta información en tiempo real

- Vista Materializada: Consulta información guardada al momento de generar la vista.
Si se desea actualizar la vista Materializada se debe ejecutar lo siguiente:
REFRESH MATERIALIZED VIEW <Nombre de la vista materializada>

Las vistas son útiles porque nos ayudan a centralizar todos los esfuerzo en un solo lugar por otra parte las vistas volátil no guardan información de forma persistente, en cambio la vista materializada si, esto es útil cuando queremos consultar que datos ocurrieron el día ant.

```sql

-- Vista volatil:

CREATE OR REPLACE VIEW public.rango_view
 AS
SELECT *,
CASE
WHEN fecha_nacimiento > '2015-01-01' 
THEN
'Mayor'
ELSE
'Niño'
END AS tipo
FROM pasajero ORDER BY tipo;

ALTER TABLE public.rango_view
    OWNER TO postgres;



-- Vista materializada:

-- REFRESH MATERIALIZED VIEW <nombre_vista>: Para actualizar los datos de la vista materializada.


CREATE MATERIALIZED VIEW public.mview_viaje_2019_01_31
AS
-- ¿Viajes en el período 2019-01-1 hasta 2019-01-1?
SELECT * FROM viaje
WHERE  viaje.inicio >'2019-01-1' 
    AND  
       viaje.inicio <'2019-01-31'

WITH NO DATA;

ALTER TABLE public.mview_viaje_2019_01_31
    OWNER TO postgres;

-- con esta instrucción refrescamos los datos para que se creen en la vista
REFRESH MATERIALIZED VIEW "mview_viaje_2019_01_31";

SELECT * FROM "mview_viaje_2019_01_31";
```

Las vistas materializadas se crean para datos que ya no van a cambiar esto ayuda a quitar peso a la BD ya que se consulta una sola vez



## 22. PL/SQL 



### PL/pgSQL

- https://www.postgresql.org/docs/9.2/plpgsql.html
- https://www.postgresqltutorial.com/postgresql-plpgsql/
- https://www.postgresql.org/docs/current/plpgsql-overview.html



procedimientos almacenados

desarrollar codigo sobre la base de datos

declaracion
uso de variables
codigo y un fin
retorna o no valores y se ejecuta dentro de la BD

el bloque se ejecuta con la palabra DO y lueog la funcion y ya

DO '.....';

si tenemos una consulta y usamos comilla simple tendremos conflicto por tal motivo debemos usar $$ para abrir y cerrar:

RAISE NOTICE - Es para describir algo en el log de postgresql
DECLARE - Nos permite declarar variables

nombre de la variable a la izquierda y luego su valor
record es para almacenar informacion de una fila
:= es para asignar valores a variables
= esta reservado solo para las consultas
En nuestro ej. rec es una fila rec.nombre,  rec.direccion_residencia,   rec.id
% es un comodin para poder ingresar una variable externa

```sql
DO $$
DECLARE 
    rec record := NULL;
    contador integer := 0;
BEGIN
    FOR rec IN SELECT * FROM pasajero LOOP
        RAISE NOTICE 'ALGO esta pasando %', rec.nombre;
        contador := contador + 1;
    END LOOP;
    RAISE NOTICE 'El conteo es %', contador;
END
$$;
```

Para encpasular la funcion PL y luego poderla llamar hacemos lo siguiente:
Nombrar funcion 
indicar su valor de retorno
Indispensable que antes de terminar la ejecucion de la funcion indicar al sistema que lenguaje se esta usando. puesto que postgresql permite usar otros lenguajes de programacion como python, c++ o SQL basico

```sql
CREATE FUNCTION importantePL() 
    RETURNS void
    AS $$
DECLARE 
    rec record := NULL;
    contador integer := 0;
BEGIN
    FOR rec IN SELECT * FROM pasajero LOOP
        RAISE NOTICE 'ALGO esta pasando %', rec.nombre;
        contador := contador + 1;
    END LOOP;
    RAISE NOTICE 'El conteo es %', contador;
END
$$
LANGUAGE PLPGSQL;
```

Para llamar la funcion:
```sql
SELECT importantePL();
```
> Nota: con esta funcion no retonamos nada por el Data Output pero si por el Messages porque indicamos que su RETURNS sea void pero si quisieramos retornar algo se haria de la siguiente manera:

```sql
CREATE OR REPLACE FUNCTION importantePL() 
    RETURNS integer
    AS $$
DECLARE 
    rec record := NULL;
    contador integer := 0;
BEGIN
    FOR rec IN SELECT * FROM pasajero LOOP
        RAISE NOTICE 'ALGO esta pasando %', rec.nombre;
        contador := contador + 1;
    END LOOP;
    RAISE NOTICE 'El conteo es %', contador;
    RETURN contador;
END
$$
LANGUAGE PLPGSQL;
```
Si cambia el tipo de retorno puede generar conflicto

ERROR:  no se puede cambiar el tipo de retorno de una función existente
HINT:  Use DROP FUNCTION importantepl() primero.

Postgres nos sugiere borrar la funcion en este caso.

```sql
select importantePL();
```

Crear function por la GUI:

seguir los pasoss
En la pestaña options
Volatily - mantener cache de la funcion
returns a set - si retorna un arreglo de datos


Tener en cuenta que por aca el nos agrega el $BODY$ aunque tambien podriamos poner $PROCEDURE$ o solo $$


Si le ponemos mayusculas por la GUI la funcion se nombrara entre comillas asi:
```sql
SELECT public."importantPL"()
```



## 23. Triggers

Tambien conocidos como disparadores
ejecutar funciones dependiendo de acciones que se ejecuten sobre una tabla:, las acciones son insert, update, delete

se lanzan cuando pasa alguna accion de las mencionadas
```sql
select importantepl();

select * from cont_pasajero;
```

**** Vamos a crear una nueva PL de tipo trigger: ****

debemos de especificar el RETURNS trigger
COST 100    - valor predetermindado 
VOLATILE    - valor predetermindado  

```sql
CREATE OR REPLACE FUNCTION public.impl(
    )
    RETURNS TRIGGER
    LANGUAGE 'plpgsql'

    COST 100
    VOLATILE 
    
AS $BODY$
DECLARE 
    rec record := NULL;
    contador integer := 0;
BEGIN
    FOR rec IN SELECT * FROM pasajero LOOP
        RAISE NOTICE 'ALGO esta pasando %', rec.nombre;
        contador := contador + 1;
    END LOOP;
    INSERT INTO cont_pasajero (total, tiempo) 
    VALUES (contador, now());
    RETURN contador;
END
$BODY$;

ALTER FUNCTION public.impl()
    OWNER TO postgres;
```

impl() -> lo encontramos en pgAdmin en Trigger Functions

Las acciones sobre las cuales podemos adjuntar un trigger son: INSERT, UPDATE, DELETE Y TRUNCATE


INTEGRACION DE UN TRIGGER A UNA TABLA CON UNA PL 
[AFTER, BEFORE, INSTEAD OF]
```sql
CREATE TRIGGER mitrigger
AFTER INSERT
ON pasajero
FOR EACH ROW
EXECUTE PROCEDURE impl();

/*
mitrigger lo encontramos en PgAdmin, en los triggers de la tabla pasajero

Como el trigger tiene informacion de lo que se esta cambiando debemos retornarle al motor de la BD si el cambio se hace o no

los triggers tienen 2 variable glabales importantes

OLD (lo que estaba antes del cambio) Y NEW (el nuevo valor)

es decir lo que deberiamos retorna es NEW:
*/

RETURN NEW;

-- si no queremos que haga el cambio lo dejamos en OLD

RETURN OLD;

CREATE FUNCTION public.impl()
    RETURNS trigger
    LANGUAGE 'plpgsql'
    COST 100
    VOLATILE NOT LEAKPROOF
AS $BODY$
DECLARE 
    rec record := NULL;
    contador integer := 0;
BEGIN
    FOR rec IN SELECT * FROM pasajero LOOP
        RAISE NOTICE 'ALGO esta pasando %', rec.nombre;
        contador := contador + 1;
    END LOOP;
    INSERT INTO cont_pasajero (total, tiempo) 
    VALUES (contador, now());
    RETURN NEW;
END
$BODY$;

ALTER FUNCTION public.impl()
    OWNER TO postgres;
```


### Tarea hacer el trigger para cuando se eliminan pasajeros.



## 4. Integrar bases de datos con servicios externos 
------------


## 24. Simulando una conexión a Bases de Datos remotas


traer datos de servidores remotos con el servicio dblink, esta funcion permite conecternos as servidores remotos dentro de una consulta.

select tabla_local haciendo join a conexion con bd remota


**Vamos a crear una bd en nuestro servidor simulando que es una bd externa:**

```sql
CREATE DATABASE remota
    WITH 
    OWNER = postgres
    ENCODING = 'UTF8'
    CONNECTION LIMIT = -1;

CREATE TABLE public.vip
(
    id integer,
    fecha date
);

ALTER TABLE public.vip
    OWNER to postgres;

INSERT INTO public.vip(
    id, fecha)
    VALUES (50, '2018-02-01');


** HACEMOS LA CONSULTA 

-- en host iria obviamente la ip remota o el nombre de dominio
-- es recomentable ocultar la password puede ser con una vista o una vista materializada

select * from 
dblink('dbname=remota 
       port=5432 
       host=127.0.0.1 
       user=usuario_consulta 
       password=cvargas',
       'SELECT id, fecha FROM vip');

ERROR:  no existe la función dblink(unknown)
LINE 2: dblink('dbname=remota 
        ^
HINT:  Ninguna función coincide en el nombre y tipos de argumentos. Puede ser necesario agregar conversión explícita de tipos.
SQL state: 42883
Character: 16


-- Instalar la extension 

CREATE EXTENSION dblink;

con esto decimos a postgres que instale esta extencion de su repositorio de extensiones, pero que no ha sido instalado de manera predeterminada



debemos de especificar e formato, si esa consulta estuviera en nuestra bd local el motor ya sabria que tipo de datos son  pero lo que recibiremos es un arreglo de datos sin ningun tipo de caracteristica  

ERROR:  la lista de definición de columnas es obligatoria para funciones que retornan «record»
LINE 2: dblink('dbname=remota 

Solucion:

dblink(.....) as datos_remotos (id integer, fecha date);

ALTER ROLE usuario_consulta
    PASSWORD 'xxxxxx';



-- Dar permisos a usuario consulta

GRANT ALL ON TABLE public.vip TO usuario_consulta;


select * from 
dblink('dbname=remota 
       port=5432 
       host=127.0.0.1 
       user=usuario_consulta 
       password=cvargas',
       'SELECT id, fecha FROM vip') as datos_remotos (id integer, fecha date);


Consulta para traer todos los pasajeros VIP 

select * from pasajero
JOIN 
dblink('dbname=remota 
       port=5432 
       host=127.0.0.1 
       user=usuario_consulta 
       password=cvargas',
       'SELECT id, fecha FROM vip') as datos_remotos (id integer, fecha date)
ON pasajero.id = datos_remotos.id ;


PODEMOS REEMPLAZAR EL ON (pasajero.id = datos_remotos.id) POR USING;

select * from pasajero
JOIN 
dblink('dbname=remota 
       port=5432 
       host=127.0.0.1 
       user=usuario_consulta 
       password=cvargas',
       'SELECT id, fecha FROM vip') as datos_remotos (id integer, fecha date)
USING (id);
```

**EJERCICIO**
Hacer la consulta al reves, desde la base de datos remota hacia la de transporte y traer los pasajeros vip






## 25. Transacciones

Varias tareas que se deben ejecutar sino, se devuelven todos los cambios

```sql
BEGIN
    <consulta>
COMMIT | ROLLBACK;


BEGIN - Inicia al motor de db diciendole que tenemos que hacer lo suguiente en una sola transaccion
COMMIT - si llegamos al final, guarde todos los cambios
ROLLBACK - si algo fallo, devuelve todo lo que hicimos
```

De manera predeterminada PgAdmin tiene configurado el Auto commit, hay que desactivarlo ya que esto agrega un commit al final.


Esto asegura la integridad de informacion del modelo ACID


```sql
BEGIN;

INSERT INTO  public.estacion(nombre,direccion)
VALUES('Estación Transacción 3','lA 20');
 
INSERT INTO  public.tren(id, modelo,capacidad)
VALUES(100, 'Modelo Transacción 3', 123);
 
COMMIT | ROLLBACK;
```


Fuentes:
- [Comandos de transacciones en PostgreSQL](https://www.todopostgresql.com/comandos-de-transacciones-en-postgresql/)



## 26. Otras Extensiones para Postgres

En clases anteriores usamos la extension dblink para conectar 2 bd

hay muchas extensiones que vienen configuradas con postgresql pero tenemos activadas

Hay extensiones que sirven para calculo, prototipado y machine learning


Comparar 2 palabras letra por letra y como suenan en ingles
```sql
SELECT levenshtein ('oswaldo','osvaldo');

ERROR:  no existe la función levenshtein(unknown, unknown)
LINE 1: SELECT levenshtein ('oswaldo','osvaldo');
               ^
HINT:  Ninguna función coincide en el nombre y tipos de argumentos. Puede ser necesario agregar conversión explícita de tipos.
SQL state: 42883
Character: 8
```

> Este error se debe a que postgresq no sabe si es una extension o una pl, entonces debemos hacer lo siguiente:


```sql
CREATE EXTENSION fuzzystrmatch;
SELECT levenshtein ('oswaldo','osvaldo');

El numero retornado muestra la cantidad de letras que hay que cambiar para que las palabras sean iguales.



difference usa algoritmos de machine learning
SELECT difference ();


SELECT difference ('cristhian','cristian');
SELECT difference ('beard','bird');
SELECT difference ('oso','oso');
```

Fuentes: 
- [Appendix F. Additional Supplied Modules](https://www.postgresql.org/docs/11/contrib.html) -> extensiones de postgresql para la version 11
- [Extending SQL](https://www.postgresql.org/docs/12/extend.html)



## 5. Implementar mejores practicas 
------------


## 27. Backups y Restauración


### Backup por PgAdmin tiene cuatro FORMATOS 
- Custom - es un formato unico que usa postgresql para guardar la info de una BD
- Tar - Archivo comprimido de la BD
- Plain - Creacion de tablas, SQL plano
- Directory - Estructura sin comprimir


Custom esta hecha para pgadmin y es mas potente.


El radio de compresion es para que quede un archivo mas pequeño

- Encoding: UTF8
- Number of jobs - no podemos decidir nada, pero eso tiene que ver con la cantidad de hilos del procesador
- role - es el dueño del dump


## Dump options

solo la info, solo la estrutura, si queremos llaves, sino...
si queremos los dueños o no...


pg_dump: funcion estandar de postgresql para crear los backups


C:\Program Files\PostgreSQL\12\bin\pg_dump.exe --file "C:\\Users\\crist\\OneDrive\\DOCUME~1\\DUMP_2~1" --host "localhost" --port "5432" --username "postgres" --no-password --verbose --format=c --blobs --encoding "UTF8" "transporte_publico"
	```
	pg_dump -h localhost -Fc transporte_publico C:\Users\crist\OneDrive\backup_shell.sql
	```
## RESTAURAR

Si hemos creado el backup con el formato Plain debemos hacerlo con la herramienta de consulkta, sino no entonces por la GUI 


## pg_dump y pg_restore


> Notas de alumnos: es importante resaltar que cuando se hace un backup para ser restaurado en una versión diferente se debe de usar la opción plana dado que el custom varia de versión a versión.


```sql
pg_dump -U sisproing -W -h localhost sisproing > sisproing.sql
```


## 28. Mantenimiento



Postgres desarrolla el mantenimiento de manera activa y sin consentimiento del usuario. El mantenimiento consiste en quitar todas las filas, items y columnas que no están funcionando correctamente y postgres lo hace para optimizar todos los servicios ya por trabajar rápido ocurre


Postgres tiene dos niveles de limpieza son: 

1-Liviano que se ejecuta en segundo plano y lo hace constantemente. 
2-Full el cual es capaz de bloquear las tablas para hacer la limpieza y luego la desbloquea. En estas actividades no debemos involucrarnos al menos que sea necesario.


Una limpieza full es necesario cuando tengamos una tabla grande y tengamos problema de indexación, esto se refiere a que, En el momento de hacer la consulta se demore mucho tiempo.



- Vacuum: La más importante, con tres opciones, Vacuum, Freeze y Analyze.

- Full: la tabla quedará limpia en su totalidad, puede tumbar la bd
- Freeze: durante el proceso la tabla se congela y no permite modificaciones hasta que no termina la limpieza
- Analyze: No hace cambios en la tabla. Solo hace una revisión y la muestra.

- Reindex: Aplica para tablas con numerosos registros con indices, como por ejemplo las llaves primarias.

- Cluster: Especificamos al motor de base de datos que reorganice la información en el disco.






### Preguntas y respuestas alumnos:

Uno debe crear indices en postgres o el motor crea todos los indices que necesita la tabla para satisfacer las consultas? Se puede analiz...

> R/ Si , nosotros debemos crear los indices, Postgresql trata de hacer lo mejor que puede con la herramientas que les des, si no tiene ídices entonces no podrá usarlos. Para saber cuando crear índices puedes basarte en 2 consejos prácticos, úsalos en columnas q uses para crizar 2 tablas y en columnas que aparezcan en la mayoría de tus consultas.

https://www.eversql.com/


Fuentes:
- [El apagón de Platzi / Migramos de MySQL a PostgreSQL](https://platzi.com/blog/el-apagon-de-platzi-migramos-de-mysql-a-postgresql/)
- [Chapter 23. Routine Database Maintenance Tasks](https://www.postgresql.org/docs/9.0/maintenance.html)





## 29. Introducción a Réplicas



Son mecánismos que permiten evitar problemas de entrada y salida en los SO.
“Existen 2 tipos de personas, los que ya usan réplicas y los que las van a usar…” - Piensa siempre en modo réplica.
A medida que la DB crece encontraremos limitaciones físicas y de electrónica, si la DB aumenta tanto su tamaño, las limitaciones serán de procesamiento, RAM, almacenamiento.

Hemos visto que las consultas en local son muy rápidas, sin embargo, cuando la aplicación ha sido desplegada pueden ocurrir multiples peticiones de lectura y escritura. Todos los motores de DB pueden hacer una ejecución a la vez, por lo que recibir tantas peticiones de consulta al mismo tiempo puede hacer que regresar una consulta se demore demasiado y eso puede ser catastrófico, pero las réplicas son la solución a este tipo de problemas.

¿Cuál es la estrategia? Tener una base de datos principal donde se realizan todas las modificaciones, y una base de datos secundaria dónde se realiza las lecturas. 

Separar las tareas es altamente beneficioso en cuanto al rendimiento de la aplicación, así, cuando se modifica una DB automáticamente se lleva el cambio a la DB de lectura. Todo lo que hay que hacer es configurar 2 servidores de postgres, uno como maestro y otro como esclavo. 

Se debe modificar la aplicación para que todas las modificaciones se hagan sobre el maestro y la lectura sobre la replica, o la DB en caliente. Es imposible realizar cambios en la DB de réplica.


Se puede tener una cantidad ilimitada de replicas

IOPS - limitante servidor






## 31. Otras buenas prácticas

Ver archivo adjunto


https://github.com/rb-one/Curso_PostgreSQL/blob/master/Notes/notes.md