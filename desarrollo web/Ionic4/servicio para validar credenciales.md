# Servicio para validar credenciales

Creamos un servicio para autentificación
```
ionic generate service services/authenticate
```

y lo configuramos de la siguiente manera

authenticate.service.ts
```ts
import { Injectable } from '@angular/core';

@Injectable({
 providedIn: 'root'
})

export class AuthenticateService {

 constructor() { }

 loginUser(credentials) {
	 return new Promise((accept, reject) => {
		 if(credentials.email === 'test@test.com' 
		 && credentials.password === '12345') {
				accept('Login correcto');
			} else {
				reject('Login incorrecto');
			}
		});
	}
}
```

posteriormente lo importamos ern nuestro login page como una función de dependencia y finalmente creamos nuestra función loginUser

login.page.ts
```ts
import { NavController } from '@ionic/angular';
import { AuthenticateService } from '../services/authenticate.service';


errorMessage = '';


constructor(
	 private authService: AuthenticateService,
	 private navCtrl: NavController
 ) { }
 

loginUser(credentials) {
	 this.authService.loginUser(credentials).then(ress => {
	 this.errorMessage='';
	 this.navCtrl.navigateForward('/home');
	 });
 }
```



En Ionic 6 el servicio creado por el profesor funciona igual, toca realizar la integración con el backend pero eso le toca a cada uno.  
Respecto al NavController en la [documentación](https://ionicframework.com/docs/core-concepts/fundamentals#navigation) de Ionic recomiendan usar el Router, esto lo implementarían así en el archivo `login.page.ts`

Importar el Router

```
import { Router } from '@angular/router';
```

Inyectarlo en el constructor

```
constructor(private formBuilder: FormBuilder, private authenticateService: AuthenticateService, private router: Router) {
```

Implementar el método de autenticación

```
  loginUser(credentials) {
    this.authenticateService.loginUser(credentials).then((res) => {
      this.errorMessage = '';
      this.router.navigate(['/home']);
    });
  }

```


