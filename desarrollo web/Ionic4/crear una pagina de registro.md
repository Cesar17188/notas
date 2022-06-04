# Crear una página de registro

primero generamos una nueva page para el formulario de registro

```
ionic generate page register
```

una vez generada importamos el fomulario reactivo en el module de la nueva page

register.module.ts
```ts
import { FormsModule, ReactiveFormsModule } from '@angular/forms';

@NgModule({
 imports: [
	 ReactiveFormsModule
	 ],
	 declarations: [
		 RegisterPage
		 ]
})

export class RegisterPageModule {}
```

posteriormente creamos el formulario y los controladores en la page de register

register.page.ts
```ts
import { Component, OnInit } from '@angular/core';
import { FormBuilder, FormControl, FormGroup, Validators } from '@angular/forms';
import { NavController } from '@ionic/angular';
import { Storage } from '@ionic/storage-angular';

import { AuthenticateService } from '../services/authenticate.service';

@Component({
 selector: 'app-register',
 templateUrl: './register.page.html',
 styleUrls: ['./register.page.scss'],
})

export class RegisterPage implements OnInit {

 registerForm: FormGroup;
 validationsMessages = {
 apellido: [
	{type: 'required', message: 'El apellido es requerido'},
	{type: 'minlength', message: 'El apellido es muy corto'},
 ],
 nombre: [
	 {type: 'required', message: 'El nombre es requerido'},
	 {type: 'minlength', message: 'Este nombre es muy corto'},
 ],
 email: [
	 {type: 'required', message: 'El email es requerido'},
	 {type: 'pattern', message: 'Este no es un email valido'},
 ],
 password: [
	 {type: 'required', message: 'El password es requerido'},
	 {type: 'minlength', message: 'Este password es muy corto'},
	 ],
 };

 errorMessage = '';

 constructor(
	 private formBuilder: FormBuilder,
	 private authService: AuthenticateService,
	 private navCtrl: NavController,
	 private storage: Storage
 ) {

	 this.registerForm = this.formBuilder.group({
		 nombre: new FormControl('', Validators.compose([
					 Validators.required,
					 Validators.minLength(3)
				])),
		 apellido: new FormControl('', Validators.compose([
					 Validators.required,
					 Validators.minLength(3)
				 ])),
		 email: new FormControl('', Validators.compose([
					 Validators.required,
					 Validators.pattern('^[a-zA-Z0-9_.+-]+@[a-zA-Z0-9-]+.[a-zA-Z0-9-.]+$')
				 ])),
		 password: new FormControl('', Validators.compose([
					 Validators.required,
					 Validators.minLength(5)
				 ]))
		 });
	 }
 
 ngOnInit(): void {}
}
```

finalmente creamos la vista de la page register

register.page.html
```html
<ion-content>
	 <figure class="ion-text-center ion-padding">
		 <img src="assets/img/logo.png" alt="logo platzi">
	 </figure>
 <form
	 [formGroup]="registerForm"
	 (ngSubmit)="register(registerForm.value)">
 <ion-item>
	 <ion-label>Nombre</ion-label>
	 <ion-input formControlName="nombre" type="text"></ion-input>
 </ion-item>
 <div class="validation-error">
	 <ng-container *ngFor="let validation of validationsMessages.nombre">
		 <div *ngIf="registerForm.get('nombre').hasError(validation.type) &&
 (registerForm.get('nombre').dirty ||
 registerForm.get('nombre').touched)">
			 {{validation.message}}
		 </div>
	</ng-container>
 </div>
 <ion-item>
	 <ion-label>Apellido</ion-label>
	 <ion-input formControlName="apellido" type="text"></ion-input>
 </ion-item>
 <div class="validation-error">
	 <ng-container *ngFor="let validation of validationsMessages.apellido">
		 <div *ngIf="registerForm.get('apellido').hasError(validation.type) &&
			 (registerForm.get('apellido').dirty ||
			 registerForm.get('apellido').touched)">
			 {{validation.message}}
		 </div>
	 </ng-container>
 </div>
 <ion-item>
	 <ion-label>Email</ion-label>
		 <ion-input formControlName="email" type="email"></ion-input>
		 </ion-item>
 <div class="validation-error">
	 <ng-container *ngFor="let validation of validationsMessages.email">
		 <div *ngIf="registerForm.get('email').hasError(validation.type) &&
			 (registerForm.get('email').dirty ||
			 registerForm.get('email').touched)">
					 {{validation.message}}
		 </div>
	 </ng-container>
 </div>
 <ion-item>
	 <ion-label>Password</ion-label>
		 <ion-input formControlName="password" type="password"></ion-input>
	 </ion-item>
 <div class="validation-error">
	 <ng-container *ngFor="let validation of validationsMessages.password">
		 <div *ngIf="registerForm.get('password').hasError(validation.type) &&
				 (registerForm.get('password').dirty ||
				 registerForm.get('password').touched)">
					 {{validation.message}}
		 </div>
	 </ng-container>
 </div>
	 {{ errorMessage }}
	 	 <ion-button expand="full" shape="round" color="success" [disabled]="!registerForm.valid" type="submit">Registrar!
		 </ion-button>
 </form>
</ion-content>
```