# NgClass y NgStyle

La NgClass directiva te permite configurar la clase CSS de forma dinámica para un elemento DOM .


La NgStyle directiva te permite establecer propiedades de estilo de elementos DOM determinados .

```html
<h1>NgClass & NgStyle</h1>

<input type="text" required #nameInput4="ngModel" [(ngModel)]="person.name">

<hr class="line-error"

[ngClass]="{

 'valid': nameInput4.valid,

 'invalid': nameInput4.invalid

}"/>

<p class="message--error" [class.invalid]="nameInput4.invalid">El campo es requerido</p>

<div class="styles">

 <div>

 <input type="number" [(ngModel)]="box.width">

 <input type="number" [(ngModel)]="box.height">

 <input type="color" [(ngModel)]="box.background">

 </div>

 <div>

 <div [ngStyle]="{

 'width.px': box.width,

 'height.px': box.height,

 'background-color': box.background,

 'display': 'block'

 }"></div>

 </div>

</div>

<hr>
```

```scss
.line-error {

 height: 0;

 border-bottom: 1px solid;

 &.invalid {

 border-color: red;

 }

 &.valid {

 border-color: green;

 }

}
```

```ts
 box = {

 width: 100,

 height: 100,

 background: 'red'

 }
```

