# Creando rutas

Lo primero es crear algunos **componentes** que sirvan para renderizar las páginas de contenidos

seran estos

```
ng g c pages/home  
ng g c pages/notFound  
ng g c pages/category  
ng g c pages/mycart  
ng g c pages/login  
ng g c pages/register  
ng g c pages/recovery  
ng g c pages/profile
```

posteriormente se debe realizar cambios en el html de app component

router-outlet realizara la navegación enrutada a las distinas paginas

app.component.html
```html
  

<app-nav></app-nav>

<router-outlet></router-outlet>
```

finalmente debemos enrutar las páginas en el app-routing.module.ts

app-routing.module.ts

```ts
import { NgModule } from '@angular/core';

import { RouterModule, Routes } from '@angular/router';

  
  

import { HomeComponent } from './pages/home/home.component';

import { NotFoundComponent } from './pages/not-found/not-found.component';

import { CategoryComponent } from './pages/category/category.component';

import { MycartComponent } from './pages/mycart/mycart.component';

import { LoginComponent } from './pages/login/login.component';

import { RegisterComponent } from './pages/register/register.component';

import { RecoveryComponent } from './pages/recovery/recovery.component';

import { ProfileComponent } from './pages/profile/profile.component';

  

const routes: Routes = [

 {

 path: 'home',

 component: HomeComponent

 },

 {

 path: 'category',

 component: CategoryComponent

 },

 {

 path: 'not-found',

 component: NotFoundComponent

 },

 {

 path: 'cart',

 component: MycartComponent

 },

 {

 path: 'login',

 component: LoginComponent

 },

 {

 path: 'register',

 component: RegisterComponent

 },

 {

 path: 'recovery',

 component: RecoveryComponent

 },

 {

 path: 'profile',

 component: ProfileComponent

 }

];

  

@NgModule({

 imports: [RouterModule.forRoot(routes)],

 exports: [RouterModule]

})

export class AppRoutingModule { }
```