# Uso de *ngSwitch

ngSwitch  
El funcionamiento de esta directiva es exactamente igual que el de un switch de programación, donde el resultante de una expresión definirá cual es el elemento del DOM (el tag) que se mostrará. Para ello se utilizan los atributos [ngSwitch] igualado a una variable definida en código (la cual será la que cambie su valor) y los atributos *ngSwitchCase igualados a los posibles valores que puede tomar la variable. Cuando la variable tome el valor de uno de los *ngSwitchCase se mostrará el tag asignado. También se puede incluir un tag con el atributo *ngDefaultSwitch para que se muestre siempre y cuando el valor de la variable no está contemplado en ninguno de los casos.

```html
<h1>ngSwitch</h1>

<input type="text" [(ngModel)]="person.name">

<div [ngSwitch]="person.name">

 <p *ngSwitchCase="'cesar'">

 La persona es Cesar

 </p>

 <p *ngSwitchCase="'julian'">

 La persona es Julian

 </p>

 <p *ngSwitchCase="'camilo'">

 La persona es Camilo

 </p>

 <p *ngSwitchDefault>

 La persona no hace match

 </p>

</div>
```