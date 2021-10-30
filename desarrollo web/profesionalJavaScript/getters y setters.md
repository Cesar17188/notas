# Getters y setters

Los getters y setters son funciones que podemos usar en un objeto para tener propiedades virtuales. Se usan los keywords _set_ y _get_ para crear estas propiedades.

Estas propiedades al ser funciones pueden llevar una validación de por medio y ser usadas con el operador de asignación como si fueran una variable más dentro del objeto.

Son funciones que se usan dentro de objetos para tener propiedades virtuales, podemos establecer valores que no existían en las funciones.

‌

## Getter[](https://platzi.com/clases/1642-javascript-profesional/22171-getters-y-setters/#getter)

‌

Enlaza la propiedad de un objeto con una función que será llamada cuando la propiedad es buscada.

‌

A veces es deseable permitir acceso a una propiedad que retorna un valor dinámicamente calculado, o si desea mostrar el estado de alguna variable interna sin requerir el uso de llamadas a métodos explícitos. En JavaScript, esto se puede lograr con el uso de un _getter_ (captador). No es posible tener simultáneamente un _getter_ ligado a una propiedad y que dicha propiedad tenga actualmente un valor, aunque es posible usar un _getter_ junto con un _setter_ para crear un tipo de pseudo-propiedad.

```
var o = {
  get latest () {
    if (this.log.length > 0) {
      return this.log[this.log.length - 1];
    }
    else {
      return null;
    }
  },
  log: []
}
```

‌

## Setter[](https://platzi.com/clases/1642-javascript-profesional/22171-getters-y-setters/#setter)

‌

La sintaxis **`set`** enlaza la propiedad de un objeto con una función que será llamada cada vez que se le asigne un valor.

```
var historial = {
  set actual(mensaje) {
    this.log.push(mensaje);
  },
  log: []
}
historial.actual='mensaje 1';
console.log(historial.log) //['mensaje 1']

historial.actual='mensaje 2';
console.log(historial.log)//['mensaje 1', 'mensaje 2']
```

‌

En JavaScript, un _setter_ puede ser usado para ejecutar una función para una propiedad especifica que será ejecutada al cambiar el valor. Los _setters_ se suelen usar con _getters_ para crear un tipo de pseudo-propiedad. No es posible tener un _setter_ para una propiedad que tiene un valor real.[`Promise.race(iterable)`](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Objetos_globales/Promise/race)

‌

Devuelve una promesa que se cumple o rechaza tan pronto como una de las promesas del iterable se cumple o rechaza, con el valor o razón de esa promesa.

![[Pasted image 20211001191032.png]]