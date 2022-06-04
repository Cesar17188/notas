# Login y manejo de Auth

Como hacer un login con una API y como mantener activa la seción
La siguiente API tiene un modo de autenticación por JWT  

Lo primero a tener en cuanta es que se tiene la aplicación y la API. Se va a ingresar por el endpoint de **/login** ahi estaran algunos usuarios que se pueden usar o se puede crear un propio usuario, ahi se enviara el **login** con el password. 

Una vez se haga esto y si el usuario y el password es correcto, el backend nos va a devolver un token que es de JWT (Jason Web Token). 

Una vez tengamos el token se debe almacenarlo en algún lugar y luego para alguna petición que este protegida es decir por ejemplo **/profile** necesitamos tener ese token, en caso de no enviar el token el back-end negara la petición y no se podra ingresar al perfil de usuario.


Para completar la tarea primero crearemos 3 servicios nuevos

auth.service.ts
```
ng g s services/auth
```

users.service.ts
```
ng g s services/users
```

token.service.ts
```
ng g s services/auth
```

Crearemos modelos de datos para auth y users

user.model.ts
```ts
export interface User {

 id: string;

 name: string;

 email: string;

 password: string;

}

  
  

export interface CreateUserDTO extends

Omit<User, 'id'>{}
```

auth.model.ts
```ts
export interface Auth {

 access_token: string;

}
```

en user service vamos a incluir las funciones de obtener todos los usuarios y crear un usuario

auth.service.ts
```ts
import { Injectable } from '@angular/core';

import { HttpClient, HttpHeaders } from '@angular/common/http';

  

import { environment } from 'src/environments/environment';

import { Auth } from '../models/auth.model';

  
  

@Injectable({

 providedIn: 'root'

})

export class AuthService {

	 // concatena la url de existir en cualquier ambiente

	 private apiUrl = `${environment.API_URL}/api/auth`;


 constructor(

	 private http: HttpClient

 ) { }

  

 login(email: string, password: string) {

	 return this.http.post<Auth>(`${this.apiUrl}/login`, {email, password});

 }

  

 getProfile() {

	 return this.http.get(`${this.apiUrl}/profile`);

 }

}
```


users.service.ts
```ts
import { Injectable } from '@angular/core';

import { HttpClient } from '@angular/common/http';


import { environment } from 'src/environments/environment';

import { User, CreateUserDTO } from '../models/user.model';

  
  

@Injectable({

 providedIn: 'root'

})

export class UsersService {

  

	 // concatena la url de existir en cualquier ambiente

	 private apiUrl = `${environment.API_URL}/api/users`;

  

 constructor(

	 private http: HttpClient

 ) { }

  

 create(dto: CreateUserDTO) {

	 return this.http.post<User>(this.apiUrl, dto)

 }

  

 getAll() {

	 return this.http.get<User[]>(this.apiUrl);

 }

}
```

Finalmente incluimos el login en app component

app.component.ts
```ts
import { AuthService } from './services/auth.service';

import { UsersService } from './services/users.service';


constructor(

 private authService: AuthService,

 private usersService: UsersService

 ) { }


createUser() {

	 this.usersService.create({

	 name: 'Cesar',

	 email: 'cesareli17188@mail.com',

	 password: '40987931'

 })

 .subscribe( rta => {

	 console.log(rta);

	 })

 }

  

 login() {

	 this.authService.login('cesareli17188@mail.com', '40987931')

	 .subscribe(rta => {

	 console.log(rta.access_token);

	 })

 }
```