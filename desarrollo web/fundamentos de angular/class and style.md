# Class and style



app.component.TS
```ts
widthImg = 10;
```


HTML
```html
<h1>Class & Style</h1>

<input type="text" required #nameInput2="ngModel" [(ngModel)]="person.name">

<p class="message--error" [class.invalid]="nameInput2.invalid">El campo es requerido</p>

<label>Nombre</label>

<input type="text" required #nameInput3="ngModel" [(ngModel)]="person.name">

<p [style.font-style]="nameInput3.invalid ? 'italic' : 'normal'">Texto texto texto</p>

<div class="styles">

 <div>

 <input type="text" [(ngModel)]="widthImg">

 </div>

 <div>

 <img [style.width.rem]="widthImg" [src]="person.avatar" alt="imagen">

 </div>

</div>
```


CSS
```css
.message--error {

 background-color: red;

 color: white;

 opacity: 0;

 transition: all linear .2s;

 &.invalid {

 opacity: 1;

 }

}

  

.styles {

 display: grid;

 grid-template-columns: repeat(2, 1fr);

}
```