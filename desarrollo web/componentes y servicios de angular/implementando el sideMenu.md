# Implementando el sideMenu

Se crea la carpeta reset en el nivel de app y se ingresa los estilos básicos

reset.scss

```scss
html, body, div, span, applet, object, iframe,

h1, h2, h3, h4, h5, h6, p, blockquote, pre,

a, abbr, acronym, address, big, cite, code,

del, dfn, em, img, ins, kbd, q, s, samp,

small, strike, strong, sub, sup, tt, var,

b, u, i, center,

dl, dt, dd, ol, ul, li,

fieldset, form, label, legend,

table, caption, tbody, tfoot, thead, tr, th, td,

article, aside, canvas, details, embed,

figure, figcaption, footer, header, hgroup,

menu, nav, output, ruby, section, summary,

time, mark, audio, video {

 margin: 0;

 padding: 0;

 border: 0;

 font-size: 100%;

 font: inherit;

 vertical-align: baseline;

}

/* HTML5 display-role reset for older browsers */

article, aside, details, figcaption, figure,

footer, header, hgroup, menu, nav, section {

 display: block;

}

body {

 line-height: 1;

}

ol, ul {

 list-style: none;

}

blockquote, q {

 quotes: none;

}

blockquote:before, blockquote:after,

q:before, q:after {

 content: '';

 content: none;

}

table {

 border-collapse: collapse;

 border-spacing: 0;

}
```

se importa los estilos básicos, una nueva tipografía y se cambia la tipografía en el scss general

styles.css
```scss
@import url(./styles/reset.scss);

@import url('https://fonts.googleapis.com/css2?family=Amiri:ital,wght@0,400;0,700;1,400;1,700&family=DM+Sans:ital,wght@0,500;0,700;1,400&family=Inter:wght@300;500&display=swap');

  

* {

 font-family: 'Amiri', serif;

}

.products--grid {

 app-img {

 img {

 border-radius: 10px;

 }

 }

}
```

dentro del componente nav se incrementa un div que sera nuestro menú lateral

nav.component.html

```html
<div class="side-menu" [class.active]="activeMenu">

 <button (click)="toggleMenu()">Close</button>

 <ul>

 <li><a href="#">All</a></li>

 <li><a href="#">Clothes</a></li>

 <li><a href="#">Electronics</a></li>

 </ul>

 </div>
```

se le da estilos con transform y translate para lograr la transición entre menu y página

nav.component.scss
```scss

.side-menu {

 position: fixed;

 top: 0;

 left: 0;

 bottom: 0;

 right: 0;

 background-color: black;

 display: flex;

 flex-direction: column;

 justify-content: flex-start;

 transform: translateX(-100%);

 transition: all ease-out .5s;

 &.active {

 transform: translateX(0);

 }

 button {

 font-size: 15px;

 font-family: Arial;

 width: 140px;

 height: 50px;

 border-width: 1px;

 color: #fff;

 border-color: #d02718;

 font-weight: bold;

 border-top-left-radius: 6px;

 border-top-right-radius: 6px;

 border-bottom-left-radius: 6px;

 border-bottom-right-radius: 6px;

 box-shadow: inset 0px 1px 0px 0px #f5978e;

 text-shadow: inset 0px 1px 0px #810e05;

 background: linear-gradient(#f24537, #c62d1f);

 }

 button:hover {

 background: linear-gradient(#c62d1f, #f24537);

 }

  

 ul li {

 list-style: none;

 a {

 text-decoration: none;

 color: #FBF3A9;

 }

 }
 ```

Se hace un función para controlar el cambio de estado del menu de visible a escondido en el ts de nav

nav.component.ts

```ts
activeMenu = false;

toggleMenu() {

 this.activeMenu = !this.activeMenu;

 }
 
```