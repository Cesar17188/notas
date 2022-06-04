# Validar inputs del formulario de login

Las validaciones explicadas por el profesor deberían funcionar bien en Ionic 6, pero hay un error en el archivo `login.page.html`, el archivo completo debe quedar así:

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
 validationsMessages = {
 email: [
	 {type: 'required', message: 'El email es requerido'},
	 {type: 'pattern', message: 'Este no es un email valido'},
 ],
 password: [
	 {type: 'required', message: 'El password es requerido'},
	 {type: 'minlength', message: 'Este password es muy corto'},
 ],
 };
 
 constructor(
	 private formBuilder: FormBuilder
 ) {
 this.loginForm = this.formBuilder.group({
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

 ngOnInit() {
 }
}
```

login.page.html
```html
<ion-content>
  <figure class="ion-text-center ion-padding">
    <img src="../../assets/img/logo.png" alt="Logo Platzi Music">
  </figure>
  <form [formGroup]="loginForm" (ngSubmit)="loginUser(loginForm.value)">
    <ion-item>
      <ion-label>Email:</ion-label>
      <ion-input formControlName="email"></ion-input>
    </ion-item>
    <div class="validation- error">
      <ng-container *ngFor="let validation of validationMessages.email">
        <div *ngIf="loginForm.get('email').hasError(validation.type) && (loginForm.get('email').dirty || loginForm.get('email').touched)">
          {{ validation.message }}
        </div>
      </ng-container>
    </div>
    <ion-item>
      <ion-label>Password:</ion-label>
      <ion-input type="password" formControlName="password"></ion-input>
    </ion-item>
    <div class="validation-error">
      <ng-container *ngFor="let validation of validationMessages.password">
        <div *ngIf="loginForm.get('password').hasError(validation.type) && (loginForm.get('password').dirty || loginForm.get('password').touched)">
          {{ validation.message }}
        </div>
      </ng-container>
    </div>
  </form>
</ion-content>
```

Tengan en cuenta que la variable usada por el profesor `validation_messages`, la cambié por `validationMessages`
