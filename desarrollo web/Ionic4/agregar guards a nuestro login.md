# Agregar Guards a nuestro login

Agregar Guards a nuestro login  
Si el usuario ya sé hizo login no vamos a volver a solicitarlo  
Para esto vamos a usar guard de autenticación.  
**ionic g guard guards/login**  
Opera igual que el guard de intro  
.  
**Ingresamos al guard**  
copiamos lo que tenemos en el interior del guard intro,  
en la definición de la clase tenemos que escribir canActivate  
Preguntamos si el usuario hizo login con isUserLoggedIn  
si es true retornamos true,  
si es false dirigimos a /login

```
constructor(
    private storage: Storage,
    private router: Router
  ){}
 
  async canActivate(){
    const isUserLoggedIn = await this.storage.get('isUserLoggedIn');
    if(isUserLoggedIn){
      return true;
    }
    else{
      this.router.navigateByUrl('/login');
    }
  }
```

Importamos el Router de angular y el Storage.

```
import { Storage } from '@ionic/storage';
```

Para implementarlo.  
tenemos que agregarlo a app-routing.module.ts  
en canActivate

```
canActivate: [IntroGuard, LoginGuard]
```

```
import { LoginGuard } from './guards/login.guard';
```

Definimos isUserLoggedIn en login.page.ts  
Primero Inyectamos Storage

```
private storage: Storage
```

```
import { Storage } from '@ionic/storage';
```

luego antes de redirigir al home debemos setear isUserLoggedIn en verdadero

```
this.storage.set('isUserLoggedIn', true);
```

--- 
En el archivo login.page.ts deben hacer varios pasos, importar Storage

```
import { Storage } from '@ionic/storage-angular';
```

Inyectar el Storage al constructor

```
  constructor(
    private formBuilder: FormBuilder,
    private authenticateService: AuthenticateService,
    private router: Router,
    private storage: Storage
  ) {

```

Crear el Storage

```
  async ngOnInit() {
    await this.storage.create();
  }

```

Validar al usuario, modifique un poco el método con un try / catch.

```
  async loginUser(credentials) {
    try {
      await this.authenticateService.loginUser(credentials);
      this.storage.set('isUserLoggedIn', true);
      this.router.navigate(['/home']);
    } catch (error) {
      this.errorMessage = error;
    }
  }
```