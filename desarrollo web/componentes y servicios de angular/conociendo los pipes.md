# Conociendo los pipes

https://aristotekean.medium.com/tipos-de-pipes-en-angular-d736079491b1

Los pipes son una herramienta de Angular que nos permite transformar visualmente la información, por ejemplo, cambiar un texto a mayúsculas o minúsculas, o darle formato de fecha y hora, formatos numéricos. El valor de la información transformada no cambia, sólo lo hace su aspecto.

como utilizarlos
https://www.acontracorrientech.com/pipes-en-angular-guia-completa/

```html

<p>

 total: {{total | currency}}

</p>

<p>

 Today: {{today | date: 'short' }}

</p>

<p>

 Otra fecha: {{date | date: 'yyyy.dd.MM'}}

</p>

<p>

 {{ 'hOLA BasCVaSas asSAS' | titlecase }}

</p>
```