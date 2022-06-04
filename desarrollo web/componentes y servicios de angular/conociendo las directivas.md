# Conociendo las directivas

las directivas se usan solo para modificar el DOM, pero no es recomendable hacer estas modificaciones al DOM de está manera según la documentación de Angular. Lo que quiere decir que no tiene mucha utilidad crear directivas.

se deben crear o instalar desde npm

para crearla se corre el script

```
ng g d directives/highligh
```

y el código sería

```ts
import { Directive, ElementRef, HostListener } from '@angular/core';

  

@Directive({

 selector: '[appHighlight]'

})

export class HighlightDirective {

  

 @HostListener('mouseenter') onMouseEnter() {

 this.element.nativeElement.style.backgroundColor = 'red'

 }

  

 @HostListener('mouseleave') onMouseLeave() {

 this.element.nativeElement.style.backgroundColor = ''

 }

  

 constructor(

 private element: ElementRef

 ) {

 // this.element.nativeElement.style.backgroundColor = 'red';

 }

  

}
```


para poder ejecutarlas se debe ir a la parte del DOM que se desea cambiar y se le aplica dentro de la etiqueta.

```html
<p appHighlight>{{product.description}}</p>
```

