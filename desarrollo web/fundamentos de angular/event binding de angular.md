# Introducción al Event Binding de Angular

-   El Event Binding le permite escuchar y responder a las acciones del usuario, como pulsaciones de teclas, movimientos del mouse, clics y toques (Atributos HTML y propiedades DOM).
    
-   Para vincular un elemento html a un evento, debemos indicar el nombre del evento entre paréntesis a la izquierda de un signo igual y el nombre de una funcion entre comillas a la derecha, recuerda indicar que se trata de una funcion con los parentecis “nameFunction()” .
    
    ```js
      <button (click)="onSave()">Save</button>
    ```
    
-   Usar () en el template html es sinonimo de llamar “addEventListener()”
    
-   Podemos realizar eventos personalizados con “EventEmitter”
    
-   Podemos llamar multiples eventos de la siguiente forma
    
    ```html
      <button (click)="clickEvent()" (mouseenter)="mouseEnterEvent()">Click Me</button>
    ```
    
-   Podemos determinar un objetivo de evento de la siguiente manera
    
    ```html
      <button (click)="handleClick($event)">Save</button>
    ```


```html
<h1>Eventos</h1>

<button [disabled]="btnDisabled">Enviar</button>

<button (click)="toggleButton()">Toggle Button</button>

<div style="display: flex;">

 <button (click)="addAge()"> + </button><p> Edad {{ person.age }} </p><button (click)="subsAge()"> - </button>

</div>
```

```ts
toggleButton() {

 // if (this.btnDisabled === true) {

 //   this.btnDisabled = false;

 // } else {

 //   this.btnDisabled = true;

 // }

  

 // this.btnDisabled === true ?

 // this.btnDisabled = false :

 // this.btnDisabled = true;

  

 this.btnDisabled = !this.btnDisabled;

 }

  

 addAge() {

 this.person.age = this.person.age+1;

 }

 subsAge() {

 this.person.age > 0 ? this.person.age-- : alert("No se puede restar");

 }
```
	 
-   Se recomienda comprender el flujo de datos de la aplicacion y como este interactua con la misma, existen tres tipos de enlaces:
    
    -   Enlace unidireccional [] para enlazar desde la capa logica (component.ts) a la vista (html).
    -   Enlace unidireccional () para enlazar de la vista (html) a la capa logica (component.ts).
    -   Enlace bidireccional [()] para enlazar una secuencia de vista bidireccional a la capa logica (component.ts).

-   Conceptos extraídos de:
    -   [https://angular.io/guide/event-binding](https://angular.io/guide/event-binding)
    -   [https://angular.io/api/core/EventEmitter](https://angular.io/api/core/EventEmitter)
    -   [https://blog.bitsrc.io/event-binding-mechanism-in-angular-b38f0e46d2ed](https://blog.bitsrc.io/event-binding-mechanism-in-angular-b38f0e46d2ed)
    -   [https://medium.com/claritydesignsystem/four-ways-of-listening-to-dom-events-in-angular-part-1-event-binding-3ec7e9f51a1d](https://medium.com/claritydesignsystem/four-ways-of-listening-to-dom-events-in-angular-part-1-event-binding-3ec7e9f51a1d)
    -   [https://angular.io/guide/binding-syntax](https://angular.io/guide/binding-syntax)