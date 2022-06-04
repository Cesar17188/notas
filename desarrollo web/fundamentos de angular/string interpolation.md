# String interpolation

String interpolation: La forma en la que desde la lógica de nuestro typeScript podemos pasar datos a renderizar a nuestro template(html). En otras palabras, con las {{ }} podemos usar typeScript en html.
Ejemplos como operaciones, variables o funciones

```ts
	{{ 1 + 1 }}
	{{ myVar }}
	{{ myFunction() }}
```


templateUrl: './app.component.html’  
asociamos el componente con el código ts a la template html correspondiente, lo que nos permite llamar las variables que creemos y mostrarlas en la plantilla con string interpolation (siempre y cuando sea publica)  

![Untitled.png](https://static.platzi.com/media/user_upload/Untitled-d51a84c3-33c1-43b5-bc6e-275a2fbf3f98.jpg)  
las variables por defecto son publicas a no ser que se les declare como privadas, lo que impicaría que el componente no podría acceder a esta variable.

```
private name = "umpalumpa"
```

```html
<h1>String Interpolation</h1>

<h2>{{ 'Hola Mundo'.repeat(5) }}</h2>

<p>3 + 3 = {{ 3 + 3 }}</p>

<h3>Hola, soy {{ name }} y tengo {{age}} años</h3>

<img width="100rem" src="{{ img }}" alt="imagen">
```

```ts
 name = 'Cesar';

 age = 28;

 img = 'https://dam.esquirelat.com/wp-content/uploads/2017/04/reglas-basicas-para-tomar-ron-marcas.jpg';
```