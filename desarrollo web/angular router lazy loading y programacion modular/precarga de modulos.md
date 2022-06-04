# Precarga de módulos

Gracias a la aplicación de lazy loading se va a poder aplicar otra gran caracteristica que es la precarga de módulos

primero vamas a crear un nuevo modulo o chunk de carga para category

```
ng g m website/pages/category
```

para luego enviar el category component al category module. Para que funcione la renderización de productos tambien se debe importar el modulo compartido shared module
category.module.ts
```ts
import { NgModule } from '@angular/core';

import { CommonModule } from '@angular/common';

  

import { CategoryRoutingModule } from './category-routing.module';

import { CategoryComponent } from './category.component';

  

import { SharedModule } from '../../../shared/shared.module';

  

@NgModule({

 declarations: [

 CategoryComponent

 ],

 imports: [

 CommonModule,

 CategoryRoutingModule,

 SharedModule

 ]

})

export class CategoryModule { }
```

finalmente hay que cambiar el routing de website y de category
category-routing.module.ts
```ts
import { NgModule } from '@angular/core';

import { RouterModule, Routes } from '@angular/router';

  

import { CategoryComponent } from './category.component';

  

const routes: Routes = [

 {

 path: ':id',

 component: CategoryComponent

 }

];

  

@NgModule({

 imports: [RouterModule.forChild(routes)],

 exports: [RouterModule]

})

export class CategoryRoutingModule { }
```

website-routing.ts
```ts
import { NgModule } from '@angular/core';

import { RouterModule, Routes } from '@angular/router';

  

import { HomeComponent } from './pages/home/home.component';

import { MycartComponent } from './pages/mycart/mycart.component';

import { LoginComponent } from './pages/login/login.component';

import { RegisterComponent } from './pages/register/register.component';

import { RecoveryComponent } from './pages/recovery/recovery.component';

import { ProfileComponent } from './pages/profile/profile.component';

import { ProductDetailComponent } from './pages/product-detail/product-detail.component';

import { LayoutComponent } from './components/layout/layout.component';

  
  

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

 path: 'category',

 loadChildren: () => import ('./pages/category/category.module').then(m => m.CategoryModule)

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

];

  

@NgModule({

 imports: [RouterModule.forChild(routes)],

 exports: [RouterModule]

})

export class WebsiteRoutingModule { }
```

esto reducira los tiempos de carga al solo carga un chunk por renderizado