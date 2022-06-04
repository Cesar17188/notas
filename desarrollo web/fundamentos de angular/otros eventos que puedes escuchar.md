# Otros eventos que puedes escuchar

-   Una forma común de manejar eventos es pasar el “objeto de evento” $event, donde se capturan eleentos del DOM, por lo general este evento contiene la informacion que debemos procesar en el metodo.
    
-   Conviene conocer los objetos del evento DOM [Event reference](https://developer.mozilla.org/en-US/docs/Web/Events)
    
-   Tenga en cuenta el contexto de ejecución
    
-   Las propiedades de un $event (objeto) varían según el tipo de evento DOM. Por ejemplo, un evento de mouse incluye información diferente a la de un evento de edición de cuadro de entrada.
    
-   Podemos escuchar el scroll con el siguiente codigo
    
    ```js
      //en el html
      <div class="box" (scroll)="onScroll($event)"></div>
      // en la capa logica
      onScroll(event: Event) {
        const element = event.target as HTMLElement;
        console.log(element.scrollTop);
      }
    ```
    
-   Podemos leer las teclas que se estan digitando a medida que estas son digitadas, esto lo hacemos con el sigiente codigo
    
    ```js
      // en el html
      <input type="text" [value]="person.name" (keyup)="onKeyUp($event)" />
      <p>Name {{ person.name }}</p>
      // en la capa logica
      onKeyUp(event: Event) {
      const element = event.target as HTMLInputElement;
      this.person.name = element.value;
      }
    ```
    
-   Use un tipo de datos espesifico (no any) que pueda revelar las propiedades del objeto asociado al evento
    
    ```js
      // sin informacion de tipo ... simplifica el código al costo de no saber las propiedades del evento
      onK(event: any) {
        this.values += event.target.value + ' | ';
      }
      // define un tipo de dato para el evento que estamos capturando, lo que nos permite utilizar las propiedades adecuadas para el objeto
      onKey(event: KeyboardEvent) {
      this.values += (event.target as HTMLInputElement).value + ' | ';
      }
      // No todos los elementos tienen una value propiedad, por lo que se convierte target en un elemento de entrada. El método onKey expresa más claramente lo que espera y cómo debera interpretar el evento.
    ```
    
-   Tambien puedes capturar teclas como Ctr, Alt, Shift y sus conbinaciones
    
    ```
      <input (keyup.control)='...respond to ctrl/control...' />
      <input (keyup.alt)='...respond to alt/option...' />
      <input (keyup.shift)='...respond to shift...' />
      <input (keyup.meta)='...respond to command...' />
      <input (keydown.control.shift.z)='...'/>
      <input (keyup.enter)='...responds to enter...' />
      <input (keydown.esc)='...responds to escape...' />
      <input (keyup.shift.f)='...responds to shift+f...' />
    ```
    
-   Al utilizar el “$event” tenga en cuenta que este muestra mas infomacion de la necesaria, lo que rompe “la separacion de responsabilidaes” entre la plantilla ( lo que ve el usuario ) y el componente ( cómo la aplicación procesa los datos del usuario ), es mejor [usar variables de referencia](https://angular.io/guide/template-reference-variables) en la capa logica (componente) para abordar este problema.
    

-   Conceptos extraídos de:
    -   [https://developer.mozilla.org/en-US/docs/Web/Events](https://developer.mozilla.org/en-US/docs/Web/Events)
    -   [https://angular.io/guide/event-binding-concepts](https://angular.io/guide/event-binding-concepts)
    -   [https://medium.com/claritydesignsystem/angular-pseudo-events-d4e7f89247ee](https://medium.com/claritydesignsystem/angular-pseudo-events-d4e7f89247ee)
    -   [https://www.w3schools.com/angular/angular_events.asp](https://www.w3schools.com/angular/angular_events.asp)
    -   [https://angular.io/guide/user-input](https://angular.io/guide/user-input)
    -   [https://angular.io/guide/template-reference-variables](https://angular.io/guide/template-reference-variables)