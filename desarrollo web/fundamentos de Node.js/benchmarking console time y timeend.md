# Benchmarking (console time y timeEnd)

Aquí vamos a ver cómo hacer para descubrir de todas tus funciones cuando tienes un proceso largo, cuánto esta tardando en ejecutarse y poder detectar procesos que están tardándose más de lo que deberían.

```jsx
let suma = 0

console.time('bucle')

for (let i = 0; i < 1000000000; i++) {
    suma += 1
    
}
console.timeEnd('bucle')
```

-   `console.time(*nombre*)` → Nos encerrar un bloque de código y después evaluar cuánto tarda en ejecutarse.

Y también puedes trabajar esto con procesos asíncronos.

```jsx
console.time('bucle async')
console.log('Empieza el proceso asincrono')
asincrona()
    .then(() => console.timeEnd('bucle async'))

function asincrona() {
    return new Promise( resolve => {
        setTimeout( () => {
            console.log('Terimina el proceso asíncrono')
            resolve()
        }, 0)
    })
}
```

La función **console.time(‘nombre’)** inicia un temporizador que se puede usar para rastrear cuánto tiempo dura una operación. El temporizador sera identificado por el _nombre_ dado a la consola. Ese mismo nombre se utilizara cuando se llame a **console.timeEnd(_‘nombre’_)** para detener el temporizador y obtener el tiempo demorado durante el proceso.

```
console.time("Temporizador");
for (var i = 0; i < 10000; i++) {
  // Nuestro codigo entre los temporizadores puede ser cualquier cosa.
}
console.timeEnd("Temporizador");
```