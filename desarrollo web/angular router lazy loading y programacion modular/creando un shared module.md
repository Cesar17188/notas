# Creando un Shared Module

Un shared module es un modulo compartido entre todos, la funcionalidad de este modulo es acoplar en un solo modulo los componentes, pipes o directivas que otros modulos podrian utilzar.

Lo primero es crear un modulo llamado shared sin routing

```
ng g m shared
```

posteriormente pasamos los componentes que pueden ser usados en otros modulos
como el img, product, products. Nuestros pipes y directives al app.module

Una ves pasado esto hay que arreglar los modules desde donde salieron y a donde llegaron

shared.module.ts
```ts
import { NgModule } from '@angular/core';

import { CommonModule } from '@angular/common';

import { RouterModule } from '@angular/router';

  

import { ProductComponent } from './components/product/product.component';

import { ProductsComponent } from './components/products/products.component';

import { ImgComponent } from './components/img/img.component';

  

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

 ReversePipe,

 TimeAgoPipe,

 SwitchNumberStringPipe,

 HighlightDirective,

 ],

 imports: [

 CommonModule,

 RouterModule,

 SwiperModule

 ],

 exports: [

 ImgComponent,

 ProductComponent,

 ProductsComponent,

 ReversePipe,

 TimeAgoPipe,

 SwitchNumberStringPipe,

 HighlightDirective,

 ]

})

export class SharedModule { }
```

website.module.ts
```ts
import { NgModule } from '@angular/core';

import { CommonModule } from '@angular/common';

  

import { WebsiteRoutingModule } from './website-routing.module';

import { SharedModule } from '../shared/shared.module';

  

import { HomeComponent } from './pages/home/home.component';

import { CategoryComponent } from './pages/category/category.component';

import { MycartComponent } from './pages/mycart/mycart.component';

import { LoginComponent } from './pages/login/login.component';

import { RegisterComponent } from './pages/register/register.component';

import { RecoveryComponent } from './pages/recovery/recovery.component';

import { ProfileComponent } from './pages/profile/profile.component';

import { ProductDetailComponent } from './pages/product-detail/product-detail.component';

import { LayoutComponent } from './components/layout/layout.component';

  

import { NavComponent } from './components/nav/nav.component';

  

import { SwiperModule } from 'swiper/angular';

  

@NgModule({

 declarations: [

 NavComponent,

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

 SharedModule,

 SwiperModule

 ]

})

export class WebsiteModule { }
```