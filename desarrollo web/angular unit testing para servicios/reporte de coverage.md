# Reporte de coverage

Para poder generar un reporte de covertura (más visual y específico) que no estará en modo escucha continua, lo que se debe hacer es correr el sigueinte comando en la términal

```
ng test --no-watch --code-coverage
```

Ahora que se ha generado este coverage podras ver en tu sistema de carpetas del proyecto una carpeta con el nombre de coverage.

Al entrar nos vamos al archivo index.html, damos clic derecho, seleccionamos la opción *Reveal in Explorer* y abrimos el archivo index.html en nuestro navegador para ver el reporte gráficamente.

Al ver el reporte podemos darnos cuenta cuantas veces se ha corrido cada prueba unitaria 

### Si corremos pruebas unitaria masivas no podremos saber cual es la que esta bien o mal
por lo que es recomendable colocar una fdescribe para hacer **Focus** a la prueba que se esta realizando.

Esto hará que el reporte de covertura sea más bajo y por tanto solo selecciona partes específicas del código.

Si no estuvieramos realizando una prueba de alguna parte de nuestro código con **FOCUS** el reporte de coverge gráfico nos avisa. Por lo que es necesario cubrir todas las posibles pruebas

---

para poder forzar una cantidad de pruebas mínima podemos cambiar el archivo de karma y así si no realizamos una cantidad de pruebas mínima el reporte de coverage y el testing nos devolvera un error

El cambio en el archivo karma.conf.js es el siguiente

karma.conf.js


```js
coverageReporter: {
      check: {
        global: {
          statements: 80,
          branches: 80,
          functions: 80,
          lines: 80
        }
      }
    }
```

Al hacer este cambio todas las opciones que te da el reporte de coverage deben superar el 80% para poder aceptar las pruebas. Eso solo se logra si hacemos la prueba de funcionalidad general es decir sin hacer **FOCUS** en componentes específicos. 