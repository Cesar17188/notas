# Creando el CMS Module
con las vistas anidadas se puede crear algo que tiene más sentido, un módulo especifico un CMS (content management system) va a ser nuestro modulo que manejara el contenido.

crearemos un módulo llamado CMS desde la terminal, a este módulo lo crearemos con un router y le agregaremos 2 paginas: task, grid y el componente layout

modulo con routing creado
```
ng g m cms --routing
```

creación de la pagina task
```
ng g c cms/pages/tasks
```

creación de la pagina grid
```
ng g c cms/pages/grid
```

creación del componente layout
```
ng g c cms/components/layout
```

una vez creado hacemos los cambios en el component contenedor layout

dentro de csm

layout.component.html
```html
<div>

 <header>

 <h3>Title</h3>

 </header>

 <nav>

 <ul>

 <li><a routerLink="grid">Grid Page</a></li>

 <li><a routerLink="tasks">Tasks Page</a></li>

 </ul>

 </nav>

 <main>

 <router-outlet></router-outlet>

 </main>

</div>
```

layout.component.scss
```scss
div {

 display: grid;

 height: 100vh;

 grid-template-columns: 220px 1fr;

 grid-template-rows: auto 1fr;

 grid-template-areas:

 "header header header"

 "nav content content";

 header {

 grid-area: header;

 background-color: #3E51B5;

 color: white;

 padding: 1em;

 box-shadow: 1px 2px 4px 0 rgb(21 99 157 / 16%);

 border-bottom: 1px solid rgba(21, 99, 157, 0.16);

 }

 nav {

 grid-area: nav;

 border-right: 1px solid rgba(21, 99, 157, 0.16);

 background-color: #fff;

 a {

 margin: 0;

 padding: 1em;

 cursor: pointer;

 position: relative;

 display: block;

 text-decoration: none;

 color: #000;

 }

 }

 main {

 grid-area: content;

 background-color: #f3f8fb;

 padding: 1em;

 }

}
```

tambien hacemos cambios en el app-routing.module.ts general

app-routing.module.ts
```ts
const routes: Routes = [

  {

 path: 'cms',

 loadChildren: () => import('./cms/cms.module').then( m => m.CmsModule )

 },


];
```
cargando de esta manera un modulo completamente nuevo que tendra sus propios componentes