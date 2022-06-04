# Uso de Inputs

![[Pasted image 20220307112721.png]]

Funciona para pasar información desde el componente padre hacia el componente hijo

Modulo Padre
```ts
import { FormsModule } from '@angular/forms';

@NgModule({

 declarations: [

 AppComponent,

 ImgComponent

 ],

 imports: [

 BrowserModule,

 AppRoutingModule,

 FormsModule

 ],

 providers: [],

 bootstrap: [AppComponent]

})

export class AppModule { }

```

TS Padre
```ts
export class AppComponent {

 imgParent = 'https://www.w3schools.com/howto/img_avatar.png';

}
```

HTML Padre
```html
<p><input type="text" [(ngModel)]="imgParent"></p>

<app-img [img]="imgParent"></app-img>
```

TS Hijo
```ts

import { Component, OnInit, Input } from '@angular/core';

 @Input() img: string = 'valor init';
 

 elseImg: string = 'https://raw.githubusercontent.com/platzi/angular-componentes/2-step/src/assets/images/default.png';
 
 ```

HTML Hijo
```html
<img width="200px" [src]="img" *ngIf="img; else elseImage" alt="img">

<ng-template #elseImage>

 <img [src]="elseImg" alt="">

</ng-template>
```

