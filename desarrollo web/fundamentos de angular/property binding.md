# Property Binding

-   Es una forma de controlar dinamamicamente algunos atributos html para que estos sean renderizados apartir una string, variable o atributo de un objeto de la capa logica.
    
-   Solo funcionan en una direccion desde la capa logica (conponent.ts) al objeto destino (atributo html), a esto se le conoce como flujo de datos.
    
-   Debemos vincular los valores del componente a los atributos html, esto logramos encerrando el atributo html entre “square brakets”.
    
-   Los corchetes [ ] (square brakets) hacen que Angular evalúe el lado derecho de la asignación como una expresión dinámica. Sin los corchetes, Angular trata el lado derecho como un literal de cadena y establece la propiedad en ese valor estático.
    
    ```html 
      <button disabled="false"></button> // dato fijo como string
      <button [disabled]="btnDisabled"></button> //dato dinamico
    ```
    
-   A menudo, “interpolation” y “Property Binding” pueden lograr los mismos resultados. Los siguientes pares de enlaces hacen lo mismo.
    
    ```html
      <p><img src="{{itemImageUrl}}"> is the <i>interpolated</i> image.</p>
      <p><img [src]="itemImageUrl"> is the <i>property bound</i> image.</p>
    ```
    
-   Utilice cualquiera de las formas cuando represente valores de datos como cadenas.
    
-   Es preferible el metodo de “interpolation” para facilitar la lectura.
    
-   Al establecer una propiedad de elemento en un valor de datos que no sea una cadena, debe usar “Property Binding”.
    
-   Se recomienda comprender los “Event binding” para entender el flujo de datos de la aplicacion y como este interactua con “interpolation” y “Property Binding”.


	 
```html
<h1>Propiedades</h1>

<button [disabled]="btnDisabled">Enviar</button>

<input type="text" [value]="person.name">

<progress max="100" [value]="person.age"></progress>

<img width="100rem" [src]="person.avatar" alt="imagen">
```

```ts
btnDisabled = true;

 person = {

 name: "Cesar",

 age: 28,

 avatar: 'https://dam.esquirelat.com/wp-content/uploads/2017/04/reglas-basicas-para-tomar-ron-marcas.jpg'

 }
```



-   Conceptos extraídos de:
    -   [https://angular.io/guide/property-binding-best-practices](https://angular.io/guide/property-binding-best-practices)
    -   [https://stackblitz.com/angular/xamvkonjydvn?file=src%2Fapp%2Fapp.component.ts](https://stackblitz.com/angular/xamvkonjydvn?file=src%2Fapp%2Fapp.component.ts)
    -   [https://gustavodohara.com/blogangular/agregar-componente-una-pagina-modulo-angular/](https://gustavodohara.com/blogangular/agregar-componente-una-pagina-modulo-angular/)
    -   [https://angular.io/guide/event-binding](https://angular.io/guide/event-binding)
    - [https://medium.com/@yonem9/angular-qu%C3%A9-narices-es-eso-del-data-binding-y-los-pipes-f1a094eefb7f](https://medium.com/@yonem9/angular-qu%C3%A9-narices-es-eso-del-data-binding-y-los-pipes-f1a094eefb7f)

