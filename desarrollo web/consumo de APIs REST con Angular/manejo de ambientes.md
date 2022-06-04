# Manejo de ambientes

Angular nos da varios ambientes y por defecto nos da dos ambientes uno de producción y uno de desarrollo ademas si se hace una configuración proxy da un arror si lo configuramos para producción.

Recorar el proxy no corre en producción solo en desarrollo.


Dentro de la carpeta environments estan los ambientes de produccion **environment.prod.ts** y el de desarrollo **environment.ts**

en la variable de desarrollo creamos el siguiente código

environment.ts
```ts
export const environment = {

 production: false,

 API_URL: '',

};
```

y en el de producción el siguiente código para que el backend pueda conectarse a la base de datos

environment.prod.ts
```ts
export const environment = {

 production: true,

 export class ProductsService {

  
// concatena la url de existir en cualquier ambiente
 private apiUrl = `${environment.API_URL}/api/products`;

  

 constructor(

 private http: HttpClient

 ) { }

};
```

Para poder utilizar el ambiente creado vamos al servicio donde lo consume y agregamos el siguiente código

product.service.ts
```ts
import { environment } from './../../environments/environment';

private apiUrl = `${environment.API_URL}/api/products`;
```

[Variables de entorno](https://parzibyte.me/blog/2019/11/25/variables-entorno-angular/)

Para que Angular sepa que estas en un ambiente de producción, debes compilar el proyecto con el comando:

```
ng build --prod
```

Si solo utilizas **ng build**, las variables de entorno no serán tomadas en cuenta.

**Nota importante**  
_Estas variables no serán tomadas en cuenta si solo haces un ng build; debes hacer un ng build --prod para crear un “build de producción”_


