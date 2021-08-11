# Errores (try / catch)

Cuando se genera un error, node propaga el error hacia arriba, hasta que esta es caputado. si el error no se captura node se detiene.

> Siempre que sea posible debemos capturar todos los errores que se puedan generar en nuestros hilos.

## Try/Catch

Non permite caputar los errores:

```js
const badfunction = () => 5 + z;
try {
    badfunction()
} catch (error) {
    console.log('bad function ha fallado')
    console.error(error.message)
}
console.log('continuamos...')
```

Si deseamos manejar errores asincronos:

```js
function badfunction() {
    setImmediate(() => {
        try {
            return 5 + z
        } catch (error) {
            console.log('bad function ha fallado')
            console.error(error.message)
            console.log('continuamos...')
        }
    });
}
badfunction()
```

Con Node podemos manejar los errores de una manera muy optima, pero primero debemos entender como Node maneja los errores por defecto.  
Cuando sucede un error en Node, él por defecto terminara todo el proceso de nuestro código para avisar que ha ocurrido un error, esto puede ser fatal para nuestros proyectos, los errores además se notifican por hilos, es decir, que si un error sucede en el hilo principal del event loop, es decir, el evento queue, el error se avisara desde este mismo hilo, pero si un error sucede antes desde otro hilo como el hilo de las funciones asíncronas, el error se avisara desde aquel hilo sin dejar mostrar el error del hilo principal.  
Nosotros podemos manejar este flujo de errores para que Node no se detenga al momento de que ocurra uno y lo podamos manejar según nuestros deseos, para esto usamos try y catch. Siendo try el bloque de código que ejecutara la función que puede o no fallar y siendo catch la función que atrapara el error y le especificaremos que hacer con él.
