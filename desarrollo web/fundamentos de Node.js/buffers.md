# Buffers

## Buffer

---

Un buffer es un espacio de memoria (en la memoria ram), en el que se almacenan datos de manera temporal.

Es la forma mas cruda en la que se pueden almacenar los datos. (Se guardan en **bytes** y no se especifica el tipo de dato)

En la consola, **los datos se muestran en formato hexadecimal**.

---

## Creacion de un bufer básico

Para crear un buffer, con 4 espacios por ejemplo, podemos hacerlo con la siguiente sintaxis.

```javascript
let buffer = Buffer.alloc(4);
console.log(buffer); 
// Output:
//<Buffer 00 00 00 00>
```

<h3>Otras formas de crear un buffer</h3>

Datos en un arreglo

```javascript
let buffer2 = Buffer.from([1,2,3]);
console.log(buffer2);
```

Datos de tipo string

```javascript
let buffer3 = Buffer.from('Hola');
console.log(buffer3);
console.log(buffer3.toString());
```

Guardar el abecedario en un buffer

```javascript
let abc =  Buffer.alloc(26);
console.log(abc);

for (let i = 0; i< abc.length; i++){
  abc[i] = i + 97;
}

console.log(abc);
console.log(abc.toString())
```

Creo que es importante destacar que el buffer no almacena los datos en binario, ya que cada espacio tiene 2 dígitos (almacenamiento hexadecimal).

Es por ello que la palabra **Hola** equivale en hexadecimal a `48 6f 6c 61`

Link de convertidor a Hex: [https://www.browserling.com/tools/text-to-hex](https://www.browserling.com/tools/text-to-hex)

los objetos Buffer se usan para representar datos binarios en forma de una secuencia de bytes. Muchas API de Node.js, por ejemplo, flujos y operaciones del sistema de archivos, admiten Buffers, ya que las interacciones con el sistema operativo u otros procesos generalmente siempre ocurren en términos de datos binarios.