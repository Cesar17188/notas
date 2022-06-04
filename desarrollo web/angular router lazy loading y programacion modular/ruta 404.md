# Ruta 404

Cuando se quiere ingresar a una ruta que no esta definida debe salir el error 404 not found para ello implementar esto


app-routing.module.ts
```ts
const routes: Routes = [

 {

 path: '**',

 component: NotFoundComponent

 }

];
```


not.found.component.html
```html
<div>

 <img src="https://i.gifer.com/7iJb.gif" alt="">

</div>
```

not-found.component.scss
```scss
div {

 position: relative;

 width: 100%;

 height: 100%;

 display: flex;

 align-items: flex-start;

 justify-content: center;

}
```
