# Uso de *ngFor

Sirve para iterar un array  (que este dentro de nuestra lógica de app.component.ts) de elementos dentro del html en Angular

```html
<h1>*ngFor</h1>

<ul>

 <li *ngFor="let name of names">{{ name }}</li>

</ul>

<hr>
```

app.components.ts

 ```ts
  names: string[] = ['Nicolas', 'Cesar', 'Samanta'];
```