# Navegación entre login y registro

para esto primero ingresaeremos la funcionalidad de revisar el user actual en el servicio de authenticate

authenticate.serrvice.ts
```ts
import { Storage } from '@ionic/storage-angular';


export class AuthenticateService {
 userData;

 constructor(
 private storage: Storage
 ) { }

 async loginUser(credentials) {
	 this.userData = await this.storage.get('user');
	 return new Promise((accept, reject) => {
		 credentials.password = btoa(credentials.password);
		 console.log(credentials);
		 console.log(this.userData);
		 if(credentials.email === this.userData.email && 
		 credentials.password === this.userData.password) {
			 accept('Login correcto');
		 } else {
			 reject('Login incorrecto');
		 }
	 });
 }
}
```

posteriormente incluimos esta funcionalidad en nuestra pagina de login

login.page.ts
```ts
loginUser(credentials) {
 this.authService.loginUser(credentials).then(ress => {
	 this.errorMessage='';
	 this.storage.set('isUserLoggedIn', true);
	 this.navCtrl.navigateForward('/home');
	 }).catch(err => {
		 this.errorMessage = err;
	 });
 }
 
 goToRegister() {
 this.navCtrl.navigateForward('/register');
 }
```

login.page.html
```html
<ion-button expand="full" shape="round" color="success" [disabled]="!loginForm.valid" type="submit">Login!

 </ion-button>
```



