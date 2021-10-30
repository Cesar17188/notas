# VisibilityChange

El **_visibilityChange_** forma parte del API del DOM llamado **Page Visibility** y nos deja saber si el elemento es visible, pude ser usado para ejecutar una acción cuando cambiamos de pestaña. Así podemos ahorrar batería y mejorar la UX.

Otros casos de uso para utilizar la [API Page Visibility](https://developer.mozilla.org/es/docs/Web/API/Page_Visibility_API):  
 

-   Un sitio tiene un carrusel de imágenes que no debería avanzar a la siguiente diapositiva a no ser que el usuario esté viendo la página.  
     
-   Una aplicación que muestra un panel de información y no se quiere que se actualice la información del servidor cuando la página no está visible.  
     
-   Una página quiere detectar cuando se está precargando para poder mantener un recuento preciso de las vistas de página.  
     
-   Un sitio desea desactivar los sonidos cuando el dispositivo está en modo de espera (el usuario presiona el botón de encendido para apagar la pantalla).

## Document: visibilitychange

E levento `visibilitychange` se dispara al documento cuando el contenido de su pestaña se ha hecho visible o se ha ocultado.

## Ejemplo

Este ejemplo comienza a reproducir una pista de música cuando el documento se hace visible, y pausa la música cuando el documento ya no es visible.

```js
document.addEventListener("visibilitychange", function() {
  if (document.visibilityState === 'visible') {
    backgroundMusic.play();
  } else {
    backgroundMusic.pause();
  }
});
```

## [Casos de uso](https://developer.mozilla.org/es/docs/Web/API/Page_Visibility_API#Casos_de_uso)

Consideremos algunos casos de uso para la API de Visibilidad de Página.

-   Un sitio tiene un carrusel de imágenes que no debería avanzar a la siguiente diapositiva a no ser que el usuario esté viendo la página.
-   Una aplicación que muestra un panel de información y no se quiere que se actualice la información del servidor cuando la página no está visible.
-   Una página quiere detectar cuando se está precargando para poder mantener un recuento preciso de las vistat de página.
-   Un sitio desea desactivar los sonidos cuando el dispositivo está en modo de espera (el usuario presiona el botón de encendido para apagar la pantalla).


![[Pasted image 20211012202257.png]]