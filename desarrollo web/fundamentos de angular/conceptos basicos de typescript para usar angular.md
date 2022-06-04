# Conceptos básicos de TypeScript para usar Angular

Otro truco para las funciones en **typescript** es que pueden especificar que tipo de dato van a devolver de manera explicita  
despues de los parametros y antes de las flechas de la arrow function

```
const suma = ( a : number , b: number):number => a + b
const saludar = (nombre: string , edad: number ):string => `Hola me llamo ${nombre} y tengo ${edad} años`
```

Si tienes variables que vas a inicializar en el constructor y son publicas, puedes usar la abreviatura .

```
constructor ( public age: number, public lastName: string){}
```

Recuerden esta simple linea de código, puede ahorrar inicializar objetos gigantes en vacío.