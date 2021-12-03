# Qué es React y cómo se construyó

Al programar de forma **imperativa** debemos escribir código que nos indica paso a paso cómo evoluciona nuestra aplicación. En cambio, al programar de forma **declarativa** le damos más importancia a qué vamos hacer, luego nos encargaremos de cómo lo debemos hacer.  
– [useState vs. useReducer: cómo evitar el código espagueti](https://platzi.com/blog/usestate-vs-usereducer/)

ECMAScript es estándar en el que se basa JavaScript, es la especificación del lenguaje de programación JavaScript; y lo que conocemos como Javascript es la implementación que hace cada navegador de esta especificación.

En 2005 surgió ECMAScript for XML, un estándar para agregar soporte nativo de ECMAScript a XML. Era una alternativa a la forma en la que se trabaja con el DOM.

En 2010, inspirados en ECMAScript for XML, Facebook estaba trabajando en XHP, una “mejora” a PHP con la que pretendían crear componentes personalizados y reutilizables de HTML y lo integraron a su Stack.

En 2011, bajo la influencia de XHP y los problemas que tenía Facebook, se creó el prototipo de React JS. Una herramienta para desarrollar aplicaciones con la que pudieran mejorar la eficiencia del los desarrolladores y seguir ofreciendo una buena UX.

En 2012 React se volvió Open Source.

En 2014 llegaron las React Developer Tools, un conjunto de herramientas para depurar componentes de React.

En 2015 apareció React Native, y con él muchas empresas grandes empezaron a utilizar React.

<h3>Objetivos de React</h3>

-   Declarativo: Se refiere a que sea fácil de leer.
-   Basado en componentes: Que todo este formado por componentes.
-   Multiplataforma: Significa que podremos utilizar React en cualquier plataforma con solo pequeños cambios.

Existe un gran ecosistema de herramientas relacionadas con React, algunas desarrolladas por Facebook y otras por creadas por la comunidad. Por ejemplo:

-   React DOM: Se utiliza para renderizar los componentes de React en el navegador.
-   React Native: Usado generalmente para crear aplicaciones móviles.

---

Hay dos formas de crear componentes con React: con una clase y con una función

Al crear componentes con una clase esta usa un función render y dentro una función return. Dentro de esta ultima se encuentra el código JSX para crear el componente. Además, React utiliza las llamadas props para presentar ciertas partes del componente de manera dinámica.

React también cuenta con el state, que nos sirve para cambiar el contenido de las variables dependiendo de la interacción del usuario. Este estado es un objeto donde podemos definir propiedades para después hacer uso de ellas. Cuando React detecta un cambio dentro del state automáticamente se vuelve a renderizar el componente mostrando los nuevos datos.