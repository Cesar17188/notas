# Componentes y Header

```html
<div class="show-mobile">

 <div>

 <button>

 <img src="./assets/svg/icon_menu.svg" alt="menu">

 </button>

 <a class="mobile_logo" href="#">

 <img src="./assets/svg/logo_estancos.svg" alt="logo">

 <span><h3>ESTANCOS</h3></span>

 </a>

 <a href="">

 <img src="./assets/svg/icon_shopping-cart.svg" alt="shopping_cart">

 </a>

 </div>

</div>

<div class="hide-mobile">

 <div>

 <nav>

 <a class="logo" href="">

 <img src="./assets/svg/logo_estancos.svg" alt="logo">

 </a>

 <ul>

 <li>

 <a href="#">All</a>

 <a href="#">Clothes</a>

 <a href="#">Electronics</a>

 </li>

 </ul>

 </nav>

 <div class="info">

 <div class="account">cesareli17188@gmail.com</div>

 <div>

 <a href="#">

 <img src="./assets/svg/icon_shopping-cart.svg" alt="shopping_cart">

 </a>

 </div>

 </div>

 </div>

</div>
```

SCSS
```scss
.show-mobile {

 display: block;

 padding: 0 5px;

 box-shadow: 0px 2px 5px rgb(#FBF3A9, .2);

 background-color: black;

 border-radius: 0 0 5px 5px;

 .mobile_logo {

 display: flex;

 justify-content: center;

 align-items: center;

 text-decoration: none;

 h3 {

 color: #FBF3A9;

 }

 }

 div {

 padding: 1em;

 display: flex;

 justify-content: space-between;

 align-items: center;

 button {

 border: 0;

 background: transparent;

 }

 }

}

  

.hide-mobile {

 display: none;

 padding: 0 5px;

 box-shadow: 0px 2px 5px rgb(#FBF3A9, .2);

 color: #FBF3A9;

 background-color: black;

 border-radius: 0 0 5px 5px;

 div {

 padding: 1em;

 display: flex;

 justify-content: space-between;

 align-items: center;

 }

 .logo {

 margin-right: 1em;

 }

 nav {

 display: flex;

 align-items: center;

 ul {

 display: flex;

 list-style: none;

 a {

 margin: 0 .2em;

 color: inherit;

 text-decoration: none;

 }

 }

 }

 .info {

 display: flex;

 align-items: center;

 .account {

 margin-right: .5em;

 }

 }

}

  
  

/* Medium only*/

@media screen and (min-width: 40em) and (max-width: 63.9375em) {

 .show-mobile {

 display: none;

 }

 .hide-mobile {

 display: block;

 width: 150%;

 margin: 5px;

 }

}

  

/* large and up */

@media screen and (min-width: 64em) {

 .show-mobile {

 display: none;

 }

 .hide-mobile {

 display: block;

 width: 99%;

 margin: 5px;

 }

}
```

HTML
app.component.ts
```html
<app-nav></app-nav>

<app-products></app-products>
```