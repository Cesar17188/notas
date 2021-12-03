# Tipos de aplicaciones según su router: SPAs vs. SSR

-   SPA: Single Pages Aplication
-   SSR: Server Side Render

Antes de las aplicaciones web se utilizaba el SSR viejo, donde se utilizaba algun lenguaje de programacion para backend. Esa forma es rapida SOLAMENTE al principio ya que no le entrega la forma de interactuar con los usuarios. El JS que podia tener solo era para animacions.

Ahora renderizamos todo con JS desde el navegador. La carga inicial es lenta ya que necesita pedir toda la informacion o los scripts, pero ya cargado todo es rapido.

Para trabajar de esta forma se usan dos ROuter, un HASH y un BROWSER. Los Routers son herramientas para manejar las rutas de nuestra aplicacion. Si queremos que nuestra aplicacion solo con un archivo HTML y todo el codigo JS que se necesita, es porque no tenemos control del servidor y necesitamos que toda la aplicacion funcione en el mismo archivo HTML. Gracias a los # sabemos en que parte de la pagina estamos. 

El server Side Rendering Relodead en vez de enviar un documento HTML vacio al navegador y descargar todo, podemos desde el backend enviarle una version de la aplicacion en HTML que los usuarios puedan ver, mientras el navegador descarga los archivos de JS y vuelve al navegador.

Para esto se necesita NODEJS.

Los generaodres de sitios estaticos nos permiten hacer el SSR mientras desarrollamos el sitio, pero cuando lo compilamos nos dan paginas estaticas o SPA.

Otro punto importante sobre el SSR es que este es muy importante para SEO 👀. Cuando un robot de búsqueda examina tu página y no encuentra nada de contenido (SPA) estos pueden penalizarte en SEO, algunos crawlers soportan la ejecución de código JavaScript, sí, pero aun así sigue siendo recomendado mandar un HTML con datos ya pintados 😄

![[Pasted image 20211114141514.png]]