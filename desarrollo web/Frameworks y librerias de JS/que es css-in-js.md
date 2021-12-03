# Qué es CSS-in-JS

CSS-in-JS es una técnica de diseño en la que se usa JavaScript para diseñar componentes. Cuando se analiza este JavaScript, se genera CSS y se adjunta al DOM. Permite abstraer CSS al nivel de componente en sí, usando JavaScript para describir estilos de una manera declarativa y mantenible.  
[Wikipedia](https://en.wikipedia.org/wiki/CSS-in-JS)

Es literalmente escribir CSS desde JS y no, no reemplaza a los estilos normales ya que al final CSS-in-JS genera un CSS normal, la diferencia esta en como lo escribimos cuando estamos desarrollando la aplicación y como aumenta la ventaja de trabajar con componentes.

También tenemos a los preprocesadores y postprocesadores de CSS que nos dejan escribir CSS de manera más sencilla usando variables, ciclos, mixins, filtros, funcione, etc. Los postprocesadores nos permiten usar las funcionalidades que CSS “tendrá” en el futuro y nos dejan usarlas desde ya, también compilan a CSS normal.

**Componentes y CSS-in-JS**

Logramos que no solo la estructura HTML y lógica en JS de cada componente este dentro de componentes, también logramos que el CSS este dentro del componente.

Otra ventaja es que podemos usar JS para programar nuestros estilos y hacerlos dinámicos.

“Los estilos globales no son una desventaja en CSS-in-JS”