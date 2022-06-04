# Estado de login

Para poder mantener el estado del usuarios (login, logout) es decir mantener la sesión a travez de toda la aplicación, utilizando la reactividad, manteniendo al usuario en un estado global y obtener la información del usuario. 

Dejamos el estado en un store global

vamos a obtener reactividad del usuario en el auth service, con el observable BehaviorSubject y poniendolo como un observable.

Una vez tengamos ese observable lo posicionamos en el método getProfile()  el cual actualizara nuestro estado de sesión actual.

auth.service.ts
```ts
import { BehaviorSubject, switchMap, tap } from 'rxjs';


private user = new BehaviorSubject<User | null>(null);

 user$ = this.user.asObservable();



getProfile() {

 return this.http.get<User>(`${this.apiUrl}/profile`)

 .pipe(

 tap(user => this.user.next(user))

 );

 }
```


para no preguntar el token si no que ya tenemos un usuario nos dirigimos al guardian de auth. Vamos a traer al observable de auth para verificar por medio de un map si el usuario existe en loggin o no

auth.guard.ts
```ts
import { map } from 'rxjs/operators';
import { AuthService } from '../services/auth.service';

constructor(

 private authService: AuthService,

 private router: Router

 ) { }


canActivate(

 route: ActivatedRouteSnapshot,

 state: RouterStateSnapshot): Observable<boolean | UrlTree> | Promise<boolean | UrlTree> | boolean | UrlTree {

 return this.authService.user$

 .pipe(

		 map(user => {

			 if(!user) {

				 this.router.navigate(['/home']);

				 return false;

			 }

			 return true;

		 })

	 )

  }
```

con este observable se puede saber el estado actual de la sesión de usuario desde cualquier componente como el profile por ejemplo

profile.component.ts
```ts 
ngOnInit(): void {

 this.authService.user$

 .subscribe(data => {

 this.user = data;

 })

 }
```

tambien en nav

nav.component.ts
```ts

ngOnInit(): void {

 this.storeService.myCart$.subscribe(products => {

 this.counter = products.length;

 });

 this.authService.user$

 .subscribe(data => {

	 this.profile = data;

	 })

 }


login() {

 this.authService.loginAndGet('cesareli17188@mail.com', '40987931')

 .subscribe(() => {

	 this.router.navigate(['/profile']);

	 });

 }
```


en nuestro servicio de auth tenemos que el estado inicial es en null, lo cual es una desventaja ya que si el usuario recarga otra vez estaria con el estado en null. 

Para detectar que el usuario ya tenia una sesión vamos a hacer cambios en el app component por que es el punto inicial de nuestra aplicación. Solicitamos una vez el estado del perfil y lo dejamos en un store de la aplicación por lo que cualquier componente o servicio que este conectado al authService tendra ese estado actual

app.component.ts
```ts
import { Component, OnInit } from '@angular/core';

import { AuthService } from './services/auth.service';

import { TokenService } from './services/token.service';

export class AppComponent implements OnInit{

 constructor(

	 private authService: AuthService,

	 private tokenService: TokenService

 ) { }

 ngOnInit() {

 const token = this.tokenService.getToken();

	 if (token) {

		 this.authService.getProfile()

		 .subscribe()

		 }

	 }
 }
```






