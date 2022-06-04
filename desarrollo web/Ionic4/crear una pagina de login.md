# Crear una página de login
vamos a generar un fómulario reactivo con los siguientes pasos

primero vamos a importar el módulo de reactive forms de angular en el modulo ts del componente

login.module.ts
```ts
import { FormsModule, ReactiveFormsModule } from '@angular/forms';

@NgModule({

 imports: [

 CommonModule,

 FormsModule,

 ReactiveFormsModule,

 IonicModule,

 LoginPageRoutingModule

 ],

 declarations: [LoginPage]

})

export class LoginPageModule {}
```

la ventaja de utilizar formularios reactivos es que a medida que los usuarios llenen el fomulario angular lo valida mientras lo escribe, esto nos ayuda para que el fluido del uso de la aplicación sea mejor y el usuario entienda en que punto se encuentra su formulario y que le falta para completarlo.

ahora podemos ir al page.ts de login y configurar nuestro fomulario

login.page.ts
```ts
import { Component, OnInit } from '@angular/core';

import { FormBuilder, FormControl, FormGroup, Validators } from '@angular/forms';

  

@Component({

 selector: 'app-login',

 templateUrl: './login.page.html',

 styleUrls: ['./login.page.scss'],

})

export class LoginPage implements OnInit {

  

 loginForm: FormGroup;

 constructor(

 private formBuilder: FormBuilder

 ) {

 this.loginForm = this.formBuilder.group({

 email: new FormControl('', Validators.compose([

 Validators.required,

 Validators.pattern('^[a-zA-Z0-9_.+-]+@[a-zA-Z0-9-]+.[a-zA-Z0-9-.]+$')

 ]))

 });

 }

  

 ngOnInit() {

 }

}
```

ademas de configurar en nuestro html

login.page.html
```html
<ion-content>

 <figure class="ion-text-center ion-padding">

 <img src="assets/img/logo.png" alt="logo platzi">

 </figure>

 <form

 [formGroup]="loginForm"

 (ngSubmit)="loginUser(loginForm.value)">

 <ion-item>

 <ion-label>Email</ion-label>

 <ion-input formControlName="email"></ion-input>

 </ion-item>

 </form>

</ion-content>
```