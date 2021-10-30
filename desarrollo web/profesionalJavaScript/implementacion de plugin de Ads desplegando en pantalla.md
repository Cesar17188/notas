# Implementación de plugin de Ads: Desplegando en pantalla

## Node.insertBefore()

El método `Node.insertBefore()` inserta un nodo antes del nodo de referencia como hijo de un nodo padre indicado. Si el nodo hijo es una referencia a un nodo ya existente en el documento, `insertBefore()` lo mueve de la posición actual a la nueva posición (no hay necesidad de eliminar el nodo de su nodo padre antes de agregarlo al algún nodo nuevo).

Esto significa que el nodo no puede estar en dos puntos del documento al simultáneamente. Por lo que si el nodo ya tiene un padre, primero se elimina el nodo, y luego se inserta en la nueva posición. [`Node.cloneNode()`](https://developer.mozilla.org/es/docs/Web/API/Node/cloneNode "El método Node.cloneNode() devuelve un duplicado del nodo en el que este método fue llamado.") puede utilizarse para hacer una copia de un nodo antes de insertarlo en un nuevo padre. Ten en cuenta que las copias hechas con `cloneNode()` no se mantendrán sincronizadas automáticamente.

Si el nodo de referencia es `null`, el nodo indicado se añadirá al final de la lista de hijos del nodo padre especificado.

Si el hijo proporcionado es un [`DocumentFragment`](https://developer.mozilla.org/es/docs/Web/API/DocumentFragment "La documentación acerca de este tema no ha sido escrita todavía . ¡Por favor  considera contribuir !"), el contenido completo del `DocumentFragment` se moverá a la lista de hijos del nodo padre indicado.

## Sintaxis

```js
var _insertedNode_ = _parentNode_.insertBefore(_newNode_, _referenceNode_);
```

-   `insertedNode` El nodo que esta siendo insertado, es decir, `newNode`
-   `parentNode` El padre del nodo recién insertado.
-   `newNode` El nodo a insertar.
-   `referenceNode` El nodo antes del cual se inserta `newNode`.

Si `referenceNode` es `null`, el `newNode` se insertará al final de la lista de nodos hijos.

`referenceNode` **no** es un parámetro opcional – debes pasar explícitamente un `Node` o `null`. No proporcionándolo o pasando valores no válidos podría provocar un [comportamiento](https://code.google.com/p/chromium/issues/detail?id=419780) [distinto](https://bugzilla.mozilla.org/show_bug.cgi?id=119489) en diferentes versiones de navegadores.

## Valor devuelto

El valor devuelto es el hijo añadido excepto cuando `newNode` es un [`DocumentFragment`](https://developer.mozilla.org/es/docs/Web/API/DocumentFragment "La documentación acerca de este tema no ha sido escrita todavía . ¡Por favor  considera contribuir !"), en cuyo caso se devuelve un [`DocumentFragment`](https://developer.mozilla.org/es/docs/Web/API/DocumentFragment "La documentación acerca de este tema no ha sido escrita todavía . ¡Por favor  considera contribuir !").

## element.innerHTML

## Resumen

La propiedad **`Element.innerHTML`** devuelve o establece la sintaxis HTML describiendo los descendientes del elemento.

Al establecerse se reemplaza la sintaxis HTML del elemento por la nueva.

**Nota:** Si un nodo tiene un texto secundario que incluye los caracteres `(&), (<),` o `(>)`, `innerHTML` devuelve estos caracteres como &amp, &lt y &gt respectivamente. Use [`Node.textContent`](https://developer.mozilla.org/es/docs/Web/API/Node/textContent "La propiedad textContent establece o devuelve el contenido de texto del nodo especificado. Al devolver, también devuelve el contenido de texto de todos sus descendientes.") para conseguir una copia correcta del contenido de estos nodos de texto.

Para **insertar el código HTML** en el documento en lugar de cambiar el contenido de un elemento, use el método [insertAdjacentHTML().](https://developer.mozilla.org/es/docs/Web/API/Element/insertAdjacentHTML)


```
 private renderAd(){
    if (this.currentAd) {
      return 
    }
    const ad = this.ads.getAd()
    this.currentAd = ad
    this.adsContainer.innerHTML = `
      <div class="ads">
        <a class="ads__link" href="${this.currentAd.url}" target="_blank">
          <img class="ads__img" src="${this.currentAd.imageUrl}" />
          <div class="ads__info">
            <h5 class="ads__title">${this.currentAd.title}</h5>
            <p class="ads__body">${this.currentAd.body}</p>
          </div>
        </a>
      </div>
    `
  }

```