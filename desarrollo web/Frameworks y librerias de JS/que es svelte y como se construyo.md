# Qué es Svelte y cómo se construyó

TheGuardian creo Reactive JS una libreria para desarrollar interfaces con componentes, una persona que trabajaba en este proyecto creo Svelte ya que se le hace que todos los demas son muy complicados y Svelte fuera sencillo. Svelte es espectacular para sitios web pero malo para aplicaciones web, ese no fue su objetivo. Svelt y su desarrollo no cuenta con tantas actualizaciones ya que no cuenta con una empresa.

No hay un recurso oficial que nos explique como funciona SVELTE por dentro. Dustin Deus escribio un issue acerca de la documentacion de Svelte.

Svelte es un compilador que necesita generar un AST. Para esta compilacion necesita 3 parsers, uno para HTML, CSS Y JS. En el momento de renderizado SVELTE envuelve todo el codigo en Fragment que no afecta a la interfaz de la pagina. No se transforman en algo que los usuarios puedan ver, es como un nodo imaginario que no se puede ver pero tiene todas las caracteristicas de un nodo.

**Rich Harris** creó SVELTE

-   La principal característica es que no crea **intermediarios** entre el código que se escribe en **SVELTE** y el **DOM**.
-   A diferencia de React, SVELTE no usa el VirtualDOM.
-   SVELTE es Espectacular para desarrollar **sitios WEB**
-   SVELTE No es tan fuerte en **Aplicaciones WEB**  
    **ARQUITECTURA DE SVELTE:**
-   No hay un recurso oficial que nos explique como funciona SVELTE por dentro.
-   Dustin Deus: escribió un issue acerca de la Documentación:
-   Resumen del Resumen del Resumen :0  
    1.- SVELTE es un Compilador, por tanto, necesita generar un AST(Abstract Syntax Tree), adjunto clase del curso profesional de JavaScript Acerca de ello: [Clase](https://platzi.com/clases/1642-javascript-profesional/22166-parsers-y-el-abstract-syntax-tree/)  
    2.- Para esto necesita 3 Parsers: **HTML**, **CSS**, y **JavaScript**  
    COMBINA ESTOS 3 ARBOLES.  
    3.- Envuelve como un envoltura de chocolate 😄, todos los componentes en **FRAGMENTS**, Una interfaz API del Navegador.  
    4.- Esa interfaz sirve para **ENCAPSULAR**: Nodos, y pedazos del DOM, esto no **afecta** la interfaz de la Página.  
    5.- Los **FRAGMENTS** es como un nodo imaginario(No es visible para los usuarios), pero si tiene todos las características de un nodo.**(Crear, Actualizar, Borrar)**