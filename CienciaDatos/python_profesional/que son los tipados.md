# ¿Qué son los tipados?

💻 Los tipados es una clasificación de los lenguajes de programación, tenemos cuatro tipos:

-   Estático
-   Dinámico
-   Débil
-   Fuerte

El tipado del lenguaje depende de cómo trata a los tipos de datos.

El tipado estático es el que levanta un error en el tiempo de compilación, ejemplo en JAVA:

```java
String str = "Hello" // Variable tipo String
str = 5 // ERROR: no se puede convertir un tipo de dato en otro de esta forma.
```

El tipado dinámico levantan el error en tiempo de ejecución, ejemplo en Python:

```python
str = "Hello" # Variable tipo String
str = 5 # La variable ahora es de tipo Entero, no hay error

## TIPADO FUERTE
x = 1
y = "2"
z = x + y # ERROR: no podemos hacer estas operaciones con tipos de datos distintos entre sí
```

El tipado débil es el que hace un cambio en un tipo de dato para poder operar con el, como lo hace JavaScript y PHP.

🐍 Python es un lenguaje de tipado 👾 Dinámico y 💪 Fuerte.

**Estático** →→ Detectan los errores en tiempo de compilación. No se ejecuta hasta corregir. Por ej, _Java_

**Dinámico** →→ Detectan el error en tiempo de ejecución. Nos dice el error cuando llega a la línea del código. Por ej, _Python_

**Strong** →→ Más severidad con los tipos de datos. Sumar un número + una letra arrojará error.

**Weak** →→ Menos severidad con los tipos de datos. Si quiero sumar número y letra, las concatenaría como strings. Castea tipos de datos automáticamente. Por ej, _PHP_