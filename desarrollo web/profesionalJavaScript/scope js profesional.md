# Scope

**Scope** o **ámbito de una variable** [[scope]] representa el tiempo de vida en el que esta existe, puede ser una variable que hayamos definido o el argumento a un función. Eso es muy importante por que evite que reescribamos el valor de una variable que ya habíamos definido. Por desgracia [[javascript]] no siempre tuve el mejor sistema de scope de variables, en el libro [JavaScript: The Good Parts](https://www.amazon.es/JavaScript-Good-Parts-ebook/dp/B0026OR2ZY) de [Douglas Crockford](https://www.amazon.es/Douglas-Crockford/e/B002N3VYB6?ref_=dbs_p_ebk_r00_abau_000000) se dice que el **scope** y variables globales son de las cosas más horrible que tiene el lenguaje. Por suerte esto a mejorado muchísimo, ahora tenemos a `let` y `const` que nos ayuda a evitar estos problemas.

‌

## Scope global[](https://platzi.com/clases/1642-javascript-profesional/22159-scope/#scope-global)

‌

Vamos a hacer algunas pruebas en el código para experimentar con estas variables.

‌

Si declaramos un `var` de la siguiente forma lo estaríamos haciendo globalmente.

```
var message = "¡Hello, Platzi!";
```

‌

Si vamos a la consola y escribimos `windows.message` no da el mensaje que guardamos en la consola. `Windows` es nuestro ámbito global.

‌

Si agregamos una **CDN** externo como **jQuery** podremos acceder a ese código **globalmente**. El peligro está en cambiar alguna característica del CDN global que trajimos.

```
var message = "¡Hello, Platzi!";
var $ = function(message) {
    console.log("Say: " + message);
}
```

‌

Si escribimos en la consola lo siguiente no dará el resultado…

```
$('Hola')

 //  Say: Hola
```

‌

Vimos que cambiamos por completo el acceso a elementos de jQuery, pero también nos dimos cuanta de que el message no era: `¡Hello, Platzi!` si no `Hola`, a esto se le llama: **Scope definition**.

‌

Ahora hagamos otro ejemplo, una función que imprimirá números.

```
function printNumbers(params) {
          for (var i = 0; i < 10; i++) {
              setTimeout(() => {
                  console.log(i)
              }, 100);
          }
      }

printNumbers()
```

‌

Crea un siclo de **10** número del **0** al **9** y va a tener un retraso de **100ms**, pero si ejecutamos este código pasa algo extraño:

```
// (10) 10 
```

‌

Se imprime 10 veces 10 y eso no es lo que queremos.

‌

Esto pasa por **function scope**, algo pasa con la variables `var`, pasa que el lenguaje lo declara como variable global y cuando llega el turno de imprimir el valor de **i** resulta que ya tiene 10. Se soluciona llamando a una función en el ciclo que ejecute el **setTimeOut**.

```
function printNumbers(params) {
          for (var i = 0; i < 10; i++) {
              function eventuallyPrintNumbers(n) {
                  setTimeout(() => {
                  console.log(n)
              }, 100);
              }
              eventuallyPrintNumbers(i)
          }
      }

      printNumbers()
```

‌

Haciéndolo así `var` conserva su valor real por cada ciclo. El valor `i` paso a un scope `n` totalmente nuevo.

‌

## Block scope[](https://platzi.com/clases/1642-javascript-profesional/22159-scope/#block-scope)

‌

Con las nuevas actualizaciones tenemos acceso a una variable que trabaja en el bloque de ejecución, siempre recordando su valor.

```
function printNumbers(params) {
        for (let i = 0; i < 10; i++) {
          setTimeout(() => {
            console.log(i);
          }, 100);
        }
      }

      printNumbers();
```

‌

## Module scope[](https://platzi.com/clases/1642-javascript-profesional/22159-scope/#module-scope)

‌

Es probable que lo hayamos usado en `Node` o en `React` usando herramientas como `Babel`. Lo que hace es que el `scope` de esa variable se limite al archivo donde está definido.

```
<script  type="module"  src="./assets/index.js"></script>
```

‌

El `type="module"` declara que el archivo es un módulo. Esto no está en todos los navegadores pero sí en los más modernos. Ya no podemos acceder a las variables globales de este archivo desde la **consola**.

‌

## Importar y exportar[](https://platzi.com/clases/1642-javascript-profesional/22159-scope/#importar-y-exportar)

‌

Podemos separar código que esté en un archivo js usando _export_ e _import_.

‌

En nuestro archivo `./assets/index.js` separaremos el código que usar nuestro _media player_ en otro archivo llamado **MediaPlayer**.

![](https://blobscdn.gitbook.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-LlTyKe9xd6RJ6x5f2-z%2F-LnCp9qnZO5otXQYfGiF%2F-LnD2gOidag3AtKzIDkh%2FScreenshot_16.png?alt=media&token=0e591456-3c77-46ca-a14c-16f7730ba955)

‌

Nuestro archivo `index.js` tendrá:

```
import MediaPlayer from "./MediaPlayer.js";
const video = document.querySelector("video");
const button = document.querySelector("button");


const player = new MediaPlayer({ el: video });

button.onclick = () => player.play();
```

‌

Y el archivo `MediaPlayer.js`:

```
function MediaPlayer(config) {
  this.media = config.el;
}

MediaPlayer.prototype.play = function() {
  // if(this.media.paused){
  //   this.media.play();
  // } else {
  //   this.media.pause()
  // }
  // o podemos usar lo siguiente:
  this.media.paused ? this.media.play() : this.media.pause();
};

export default MediaPlayer;
```

‌

Si exportamos una variable del archivo importado, ejemplo: `export const foo = "hi"`, entonces tendríamos que importarlo de la siguiente forma:

```
import  MediaPlayer, { foo } from  "./MediaPlayer.js";
```

‌

Entre llaves.

‌

El **scope** es el lugar de vida de una variable y nos evita sobrescribir el valor de esta. En JavaScript tenemos cuatro:

‌

1.  **Global** scope.
    
2.  **Function** scope.
    
3.  **Block** scope.
    
4.  **Module** scope.

![[Pasted image 20210920164440.png]]
![[Pasted image 20210920164508.png]]