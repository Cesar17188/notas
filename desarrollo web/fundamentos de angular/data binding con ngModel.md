# Data binding con ngModel

```html
  //comportamiento del ngModel sin etiqueta <form>
      	//html
      	<input [(ngModel)]="name" #ctrl="ngModel" required>
      	//capa logica
      	name: string = '';
    //Comportamiento dentro de un form
    	//html
    	<form #f="ngForm" (ngSubmit)="onSubmit(f)" novalidate>
    		<input name="first" ngModel required #first="ngModel">
    		<input name="last" ngModel>
        		<button>Submit</button>
    	</form>
      	//capa logica
    	onSubmit(f: NgForm) {
    	console.log(f.value);  // { first: '', last: '' }
    	console.log(f.valid);  // false
    	}
    
    En el contexto de un formulario principal, a menudo no es necesario incluir enlaces unidireccionales o bidireccionales, ya que el formulario principal se encarga de su  sincronizacion

```

```html

<h1>NgModel</h1>

<p>Nombre {{person.name}}</p>

<input type="text" required #nameInput="ngModel" [(ngModel)]="person.name">

<p>Valid: {{ nameInput.valid }}</p>

  

<p>Nombre {{person.age}}</p>

<input type="number" max="18" min="10" required #ageInput="ngModel" [(ngModel)]="person.age">

<p>Valid: {{ ageInput.valid }}</p>
```

-   Importante recalcar que para hacer uso de ngModel debemos importar el “FormModule” y habilitar el mismo en app.module.ts
    
-   ngModel raliza un seguimiento del valor y el estado de validación de un control de formulario individual debido a las propiedades que hereda de [FormControl](https://angular.io/api/forms/FormControl) es recomentado saber como funciona dicho proceso.
    
-   Podemos personalizar las validaciones que deberia tener un campo o el mismo formulario
    
-   Aqui utilizamos las variables de referencia (las que tienen el signo #) y debemos indicar que la variable debera tomar el valor del ngModel <<#nameInput=“ngModel”>>
    
-   Se pueden realizar las validaciones que normalmente encontramos en html y con “pattern” podemos especificar una comprobacion como exprecion regular
    
-   Podemos tener un flujo de datos unidireccional con [] o bidireccional con [()]
    
-   Acepta inputs
    
-   Cuando se utiliza el ngModel sin la etiqueta <form> es necesario proporcionar un “nombre de atributo” de manera que el control pueda ser registrado en el formulario padre bajo ese nombre.
    
-   Conceptos extraídos de:
    
    -   [https://developer.mozilla.org/es/docs/Learn/Forms/Form_validation](https://developer.mozilla.org/es/docs/Learn/Forms/Form_validation)
    -   [https://angular.io/api/forms/FormControl](https://angular.io/api/forms/FormControl)
    -   [https://angular.io/api/forms/NgModel](https://angular.io/api/forms/NgModel)