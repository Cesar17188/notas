# Tipos de Datos Personalizados

Siguiendo con las particularidades de Postgres tenemos una funcion que se puede considerar avanzada y que no todos los manejadores proveen y es **Tipos de dato definidos por el usuario** y que este lo pueda controlar, hay dos vertientes

-   JSON
-   Lista

En el ultimo nos ayuda a tener una lista predefinida de posibilidades entre las cuales elegir y cerrar el abanico de opciones y no se pueda meter cualquier tipo de dato en el campo que vamos a elegir, veamos con esto con un ejemplo.

![[Pasted image 20210718152933.png]]

![[Pasted image 20210718152939.png]]

```sql
CREATE TYPE humor as ENUM ('triste', 'normal', 'feliz');

CREATE TABLE persona_prueba(
    nombre text,
    humor_actual humor
);

INSERT INTO persona_prueba VALUES ('Pablo', 'molesto')

INSERT INTO persona_prueba VALUES ('Pablo', 'feliz')
```

Esto es util si usamos clasificaciones predefinidas como la clasificacion de juegos/peliculas o tenemos un menu drop down en una app.