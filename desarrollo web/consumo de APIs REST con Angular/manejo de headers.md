# Manejo de headers

como ya se manejo el flujo para el login y la creación del usuario, veamos como se puede enviar el token a travez de la cabecera de la petición.

Gracias a esto podemos enviar la authorization. 
Lo importante es que aquí enviaremos el tipo de autenticacion que estamos manejando, luego enviaremos un espacio y luego el token

primero cambiaremos el servicio de auth para evitar el callback hell mediante switchmap

auth.service.ts
```ts
import { switchMap } from 'rxjs';

export class AuthService {

  

 // concatena la url de existir en cualquier ambiente

 private apiUrl = `${environment.API_URL}/api/auth`;

  

 constructor(

 private http: HttpClient

 ) { }

  

 login(email: string, password: string) {

 return this.http.post<Auth>(`${this.apiUrl}/login`, {email, password});

 }

  

 getProfile(token: string) {

 //  const headers = new HttpHeaders();

 //  headers.set('Authorization', `Bearer ${token}`);

 return this.http.get<User>(`${this.apiUrl}/profile`, {

 headers: {

 Authorization: `Bearer ${token}`,

 // 'Content-type': 'application/json'

 }

 });

 }

  

 loginAndGet(email: string, password:string) {

 return this.login(email, password)

 .pipe(

 switchMap(rta =>

 this.getProfile(rta.access_token)),

 )

 }

}
```

luego vamos al nav component ya que ahi necesitamos recibir el perfil de usuario con el token de autorización

nav.component.ts
```ts
import { User } from 'src/app/models/user.model';

import { StoreService } from '../../services/store.service';

import { AuthService } from '../../services/auth.service';

import { UsersService } from '../../services/users.service';


export class NavComponent implements OnInit {

  

 activeMenu = false;

 counter = 0;

 token = '';

 profile: User | null = null;

  

 constructor(

 private storeService: StoreService,

 private authService: AuthService,

 private usersService: UsersService

 ) { }

  

 ngOnInit(): void {

 this.storeService.myCart$.subscribe(products => {

 this.counter = products.length;

 })

 }

  

 toggleMenu() {

 this.activeMenu = !this.activeMenu;

 }

  

 login() {

 this.authService.loginAndGet('cesareli17188@mail.com', '40987931')

 .subscribe(user => {

 this.profile = user;

 this.token = '---';

 });

 }

  

 getProfile() {

 this.authService.getProfile(this.token)

 .subscribe(user=>{

 this.profile = user;

 });

 }

  
  

}

```


nav.component.html
```html
<div class="hide-mobile">

 <div>

 <nav>

 <a class="logo" href="">

 <img src="./assets/svg/logo_estancos.svg" alt="logo">

 </a>

 <ul>

 <li><a href="#">All</a></li>

 <li><a href="#">Clothes</a></li>

 <li><a href="#">Electronics</a></li>

 </ul>

 </nav>

 <div class="info">

 <button *ngIf="!token; else userProfile" (click)="login()">Login</button>

 <ng-template #userProfile>{{ profile?.email }}</ng-template>

 <div>

 <a href="#">

 <img src="./assets/svg/icon_shopping-cart.svg" alt="shopping_cart">

 <span class="counter">{{ counter }}</span>

 </a>

 </div>

 </div>

 </div>

</div>
```