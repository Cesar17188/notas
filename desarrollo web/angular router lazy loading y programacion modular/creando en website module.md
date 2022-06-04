# Creando en Website Module
para tener un website module es necesario convertir la carpeta website en un modulo

primero creamos el modulo de website
```
ng g m website --routing
```

posteriormente transladamos todas las importanciones de componentes del app.module.ts al websile.module.ts

website.module.ts
```ts
import { NgModule } from '@angular/core';

import { CommonModule } from '@angular/common';

  

import { WebsiteRoutingModule } from './website-routing.module';

import { HomeComponent } from './pages/home/home.component';

import { CategoryComponent } from './pages/category/category.component';

import { MycartComponent } from './pages/mycart/mycart.component';

import { LoginComponent } from './pages/login/login.component';

import { RegisterComponent } from './pages/register/register.component';

import { RecoveryComponent } from './pages/recovery/recovery.component';

import { ProfileComponent } from './pages/profile/profile.component';

import { ProductDetailComponent } from './pages/product-detail/product-detail.component';

import { LayoutComponent } from './components/layout/layout.component';

import { ImgComponent } from './components/img/img.component';

import { ProductComponent } from './components/product/product.component';

import { ProductsComponent } from './components/products/products.component';

import { NavComponent } from './components/nav/nav.component';

  

import { ReversePipe } from './pipes/reverse.pipe';

import { TimeAgoPipe } from './pipes/time-ago.pipe';

import { SwitchNumberStringPipe } from './pipes/switch-number-string.pipe';

  

import { HighlightDirective } from './directives/highlight.directive';

import { SwiperModule } from 'swiper/angular';

  

@NgModule({

 declarations: [

 ImgComponent,

 ProductComponent,

 ProductsComponent,

 NavComponent,

 ReversePipe,

 TimeAgoPipe,

 SwitchNumberStringPipe,

 HighlightDirective,

 HomeComponent,

 CategoryComponent,

 MycartComponent,

 LoginComponent,

 RegisterComponent,

 RecoveryComponent,

 ProfileComponent,

 ProductDetailComponent,

 LayoutComponent

 ],

 imports: [

 CommonModule,

 WebsiteRoutingModule,

 SwiperModule

 ]

})

export class WebsiteModule { }
```

y transladamos las rutas de los componentes dentro de website de app-routing.module.ts a website-routing.module.ts

website-routing.module.ts
```ts
import { NgModule } from '@angular/core';

import { RouterModule, Routes } from '@angular/router';

  

import { HomeComponent } from './pages/home/home.component';

import { CategoryComponent } from './pages/category/category.component';

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

];

  

@NgModule({

 imports: [RouterModule.forChild(routes)],

 exports: [RouterModule]

})

export class WebsiteRoutingModule { }
```

**Los cambios deben hacerce con mucho cuidado ya que los cambio de rutas genrara muchos errores y deben ser reparados individualmente**

finalmente cambiamos la ruta importando un load children al modulo de website desde app-routing.module.ts

app-routing.module.ts
```ts
import { NgModule } from '@angular/core';

import { RouterModule, Routes } from '@angular/router';

  

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

 imports: [RouterModule.forRoot(routes)],

 exports: [RouterModule]

})

export class AppRoutingModule { }
```