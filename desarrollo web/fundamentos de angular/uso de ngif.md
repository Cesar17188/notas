# Uso de *ngIf

Las directivas *ngIf y *ngFor son atributos que podemos agregarle a los elementos HTML que nos permiten en el caso del *ngIf condicionar si dicha marca debe agregarse a la página HTML.

La directiva *ngFor nos permite generar muchos elementos HTML repetidos a partir del recorrido de un arreglo de datos.

```html
<h1>*ngIf</h1>

<input type="text" [(ngModel)]="person.name">

<p *ngIf="person.name === 'Cesar'">Soy Cesar</p>

<p *ngIf="person.name === 'Julian' && person.age === 18; else elseBlock">Soy Julian</p>

<ng-template #elseBlock>

 <p>Bloque de else</p>

</ng-template>
```