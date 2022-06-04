# ngDestroy & SetInput

1.  OnInit crea y se suscribe a un obsevable que escucha cambios en un registro de la base de datos.
2.  OnDestroy cancela la suscripción a ese observable para que siga llamando a la bd infinitamente.

Ese es un uso muy común pero para alguien que está iniciando comprender sobre observables es complejo.

ngOnDestroy(): Se llama solo una vez, justo antes de que Angular destruya el componente, y sirve para prevenir memory leaks, eliminando por ejemplo suscripciones a Observables e event handlers

ngOnDestroy

img.component.ts
 ```ts
	counter = 0;

	counterFn: number | undefined;



  ngOnInit(): void {

 // before render

 // async - fetch -- one time

 console.log("ngOnInit", 'imgValue =>', this.img);

 this.counterFn = window.setInterval(() => {

 this.counter += 1;

 console.log(this.counter);

 }, 1000)

 }
 

ngOnDestroy(): void {

 // delete

 console.log("ngOnDestroy");

 window.clearInterval(this.counterFn);

 }
 ```

SetInput

imgComponent

```ts

import { Component, OnInit, Input, Output, EventEmitter, OnChanges, AfterViewInit, OnDestroy, SimpleChanges } from '@angular/core';

img: string = '';


 @Input('img')

 set changeImg(newImg: string) {

 this.img = newImg;

 console.log('change just img =>', this.img);

 }

 @Input() alt: string = '';

ngOnChanges(changes: SimpleChanges): void {

 // before - during - render

 // changes inputs -- times

 console.log("ngOnChanges", 'imgValue =>', this.img);

 console.log('changes ', changes);

 }
```