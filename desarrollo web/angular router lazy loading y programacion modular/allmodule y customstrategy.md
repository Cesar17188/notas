# AllModules y CustomStrategy

como hacer para que en redes lentas nuestra chunk no se demore más de lo normal, haciendo precarga de módulos.

Angular puede aprovechar la inactividad del browser para precargar modulos, por lo que los precarga para que el usuario pueda hacer clic a otros modulos sin retardo

Para hacer precarga vamos a app-routing.module.ts y importamos del angular router PreloadAllModules para luego ir a imports alado de routes y aplicamos la precarga con preloadingStrategy

app-routing.module.ts
```ts
import { NgModule } from '@angular/core';

import { RouterModule, Routes, PreloadAllModules } from '@angular/router';

  

import { NotFoundComponent } from './not-found/not-found.component';

  

const routes: Routes = [

 {

 path: '',

 loadChildren: () => import('./website/website.module').then( m => m.WebsiteModule )

 },

 {

 path: 'cms',

 loadChildren: () => import('./cms/cms.module').then( m => m.CmsModule )

 },

 {

 path: '**',

 component: NotFoundComponent

 }

];

  

@NgModule({

 imports: [RouterModule.forRoot(routes, {

 preloadingStrategy: PreloadAllModules

 })],

 exports: [RouterModule]

})

export class AppRoutingModule { }
```

Esta técnica agiliza la carga siempre y cuando no haya muchos módulos que precargar.
Si es necesario percargar ciertos módulos se puede realizar una estrategía de precarga personalizada

primero vamos a crear un servicio para generar nuestra estrategia de precargar
```
ng g s services/custom-preload
```

en el servicio incorporamos una forma de que con el parametro load en true precarge ese modulo
custom-preload.service.ts
```ts
import { Injectable } from '@angular/core';

import { PreloadingStrategy, Route } from '@angular/router';

import { Observable, of } from 'rxjs';

  

@Injectable({

 providedIn: 'root'

})

export class CustomPreloadService implements PreloadingStrategy{

  

 constructor() { }

  

 preload(route: Route, load: () => Observable<any>): Observable<any>{

 if (route.data && route.data['preload']) {

 return load();

 }

 return of(null);

 }

}
```

para luego aplicar esto en los routing modules necesarios, importando en nuestro routing principal el servicio y cambiandolo en nuestro preloadingstrategy

app-routing.module.ts
```ts
import { NgModule } from '@angular/core';

import { RouterModule, Routes, PreloadAllModules } from '@angular/router';

  

import { NotFoundComponent } from './not-found/not-found.component';

  

import { CustomPreloadService } from './services/custom-preload.service';

  

const routes: Routes = [

 {

 path: '',

 loadChildren: () => import('./website/website.module').then( m => m.WebsiteModule ),

 data: {

 preload: true,

 }

 },

 {

 path: 'cms',

 loadChildren: () => import('./cms/cms.module').then( m => m.CmsModule )

 },

 {

 path: '**',

 component: NotFoundComponent

 }

];

  

@NgModule({

 imports: [RouterModule.forRoot(routes, {

 preloadingStrategy: CustomPreloadService

 })],

 exports: [RouterModule]

})

export class AppRoutingModule { }
```

website-routing.module.ts
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

 loadChildren: () => import ('./pages/category/category.module').then(m => m.CategoryModule),

 data: {

 preload: true

 }

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