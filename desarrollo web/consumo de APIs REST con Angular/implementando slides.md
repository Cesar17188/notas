# Implementando slides

Una libreria muy utilizada para carrusel images es **Swiper** la cual se puede instalar por npm en angular y importarla en app.module

```
npm i swiper
```

```ts
import { SwiperModule } from 'swiper/angular';

@NgModule({
  imports: [SwiperModule],
})
export class YourAppModule {}
```

importamos en styles.scss
```scss
@import url(./styles/reset.scss);

@import '~swiper/css';
```

Enviar los datos del producto seleccionado por medio de una variable al componente products

products.component.ts
```ts
productChosen: Product = {

 id: 0,

 price: 0,

 images: [],

 title: '',

 description: '',

 category: {

 id: 0,

 name: '',

 typeImg: ''

 }

 };

 onShowDetail(id: number) {

 this.productsService.getProduct(id)

 .subscribe(data => {

 this.toggleProductDetail();

 this.productChosen = data;

 console.log(this.productChosen);

 })

 }
```

construir la visualización en products html
products.component.html
```html
<div class="product-detail" [class.active]="showProductDetail">

 <div class="productChosen" *ngIf="productChosen">

 <button class="closeToogleProduct" (click)="toggleProductDetail()">Close</button>

 <h1>{{ productChosen.title }}</h1>

 <div>

 <swiper

 [slidesPerView]="1"

 [navigation]="true"

 >

 <ng-template swiperSlide *ngFor="let img of productChosen.images">

 <img [src]="img" alt="">

 </ng-template>

 </swiper>

 </div>

 <p>{{ productChosen.description }}</p>

 <p>Precio: {{productChosen.price | currency}}</p>

 <h2>Categoria: {{productChosen.category.name}}</h2>

 <button class="shopButton" (click)="onAddtoShoppingCart(productChosen)">Añadir al carrito</button>

 </div>
 ```

dar estilos en products scss

product.component.scss
```scss
.product-detail {

 position: fixed;

 top: 0;

 bottom: 0;

 left: 50%;

 right: 0;

 background-color: white;

 display: flex;

 flex-direction: column;

 justify-content: flex-start;

 transition: all ease-in-out .5s;

 transform: translateX(100%);

 &.active {

 transform: translateX(0);

 }

}

.closeToogleProduct {

 font-size:1rem;

 width:140px;

 height:35px;

 border-width:1px;

 color:#fff;

 border-color:rgba(62, 20, 25, 1);

 font-weight:bold;

 border-top-left-radius:8px;

 border-top-right-radius:8px;

 border-bottom-left-radius:8px;

 border-bottom-right-radius:8px;

 box-shadow: 0px 10px 14px -7px rgba(156, 98, 98, 1);

 text-shadow: 0px 1px 0px rgba(10, 3, 3, 1);

 background:linear-gradient(rgba(208, 2, 27, 1), rgba(105, 25, 25, 1));

 &:hover {

 background: linear-gradient(rgba(105, 25, 25, 1), rgba(208, 2, 27, 1));

 }

}

.productChosen {

 display: flex;

 overflow-y: scroll;

 flex-direction: column;

 button {

 align-self: center;

 padding-bottom: 30px;

 }

 h1 {

 font-size: 2.4rem;

 padding-top: 15px;

 }

 p {

 padding-top: 15px;

 }

 .shopButton{

 font-size:15px;

 width:140px;

 height:35px;

 border-width:1px;

 color:#fff;

 border-color:rgba(23, 190, 187, 1);

 font-weight:bold;

 border-top-left-radius:8px;

 border-top-right-radius:8px;

 border-bottom-left-radius:8px;

 border-bottom-right-radius:8px;

 box-shadow: 0px 10px 14px -7px rgba(43, 129, 78, 1);

 text-shadow: 0px 1px 0px rgba(25, 133, 66, 1);

 background:linear-gradient(rgba(133, 237, 22, 1), rgba(88, 196, 45, 1));

 &:hover{

 background: linear-gradient(rgba(88, 196, 45, 1), rgba(133, 237, 22, 1));

 }

 }

}
```