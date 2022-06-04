# Uso de Outputs

El decorador @Output nos permite enviar información desde el componente hijo en dirección al componente padre por medio de un Event Emitter, para declarar un output lo hacemos de la siguiente manera:

```ts
@Output miOutput = new EventEmitter();
```

Si ademas queremos tipear este output para ser mas especificos con la información que vamos a enviar entonces declaramos:

```ts
@Output miOutput = new EventEmitter<string>();
```

Lo siguiente es emitir esa información desde el componente hijo por medio de la función emit() de nuestro EventEmitter declarado, en este caso ‘miOutput’ por lo cual emitimos la información de la forma siguiente:

```ts
this.miOutput.emit('mi string proveniente desde componente hijo')
```

Para recibir esa información desde el componente padre utilizamos el event binding dentro del tag del componente hijo y hacemos referencia al nombre del event emitter del componente hijo, ejemplo:

```html
<componente-hijo (miOutput)="funcionQueRecibeElOutput($event)" ></componente-hijo>
```

En el componente padre tendremos que recibir la información por medio de una función, en este caso es funcionQueRecibeElOutput($event) donde “$event” es la información que emite el componente hijo, y esta función se encargara de procesar la información que le llegue desde el event emitter