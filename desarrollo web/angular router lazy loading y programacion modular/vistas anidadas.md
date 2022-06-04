# Vistas anidadas

LAs vistas anidadas nos permiten empezar la parte de modularidad. 
Es decir tendremos una forma de controlar las partes que conforman la aplicación conforme lo necesitemos


primero crearemos una carpeta que va a tener toda la lógica del sitio web llamada website a donde moveremos los componentes, directivas, pages y pipes que controlan toda la navegación específica de la tienda.

Esto provocara muchos errores en las importaciones por la raiz de la posición de los archivos. Los errores apareceran en rojo en el editor de código y en la términal donde se corre el servidor.

Los errores deben ser corregidos uno a uno hasta arreglarlos todos.

Posteriormente se creara un nuevo componente llamado layout dentro de components. Este nuevo componente controlara la vista de home y las posteriores mientras nos mantegamos en el website.

```
ng g c website/components/layout
```

dentro del layout pondremos los elementos que queremos ver en el website que antes estaban en la ruta principal app.component.html

layout.component.html
```html
<app-nav></app-nav>

<router-outlet></router-outlet>
```

app.component.html
```html
<router-outlet></router-outlet>
```

finalmente cambiamos el archivo de rutas app-routing.module.ts, de esta forma el layout contendra a los componentes del website como componentes hijos
```ts
import { NgModule } from '@angular/core';

import { RouterModule, Routes } from '@angular/router';

  
  

import { HomeComponent } from './website/pages/home/home.component';

import { NotFoundComponent } from './website/pages/not-found/not-found.component';

import { CategoryComponent } from './website/pages/category/category.component';

import { MycartComponent } from './website/pages/mycart/mycart.component';

import { LoginComponent } from './website/pages/login/login.component';

import { RegisterComponent } from './website/pages/register/register.component';

import { RecoveryComponent } from './website/pages/recovery/recovery.component';

import { ProfileComponent } from './website/pages/profile/profile.component';

import { ProductDetailComponent } from './website/pages/product-detail/product-detail.component';

import { LayoutComponent } from './website/components/layout/layout.component';

  
  

const routes: Routes = [

 {

 path: '',

 component: LayoutComponent,

 children: [

 {

 path: '',

 redirectTo: '/home',

 pathMatch: 'full'

 },

 {

 path: 'home',

 component: HomeComponent

 },

 {

 path: 'category/:id',

 component: CategoryComponent

 },

 {

 path: 'product/:id',

 component: ProductDetailComponent

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

 },

 ]

 },

 {

 path: '**',

 component: NotFoundComponent

 }

];

  

@NgModule({

 imports: [RouterModule.forRoot(routes)],

 exports: [RouterModule]

})

export class AppRoutingModule { }
```