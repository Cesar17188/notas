# Index y su estructura básica: head

Tu primer archivo html siempre tiene que llamarse index.html. Index va ser nuestra pagina inicial que el servidor va a buscar al momento que tenga que abrir un proyecto. Si esta pagina no existe nosotros tendríamos que decirle al servidor cual es la pagina que tiene que tomar en cuenta como que es su página de inicio.  
Vamos a generar una línea de código que le va a decir al navegador que el código que está leyendo es html5 y esta es la línea de <!DOCTYPE html>, esta línea le dice al navegador todo lo que viene aquí es html5 así que entiende todas las etiquetas por html5. Existen etiquetas que se auto cierran.  
Después tenemos que hacer un contenedor principal al que se le conoce como contenedor padre que es <html Lang=”es”></html>, este contenedor va a llevar todas las etiquetas que tengamos en nuestro proyecto y este lleva un atributo especial que se llama lang=”es”, que es lo que le dice al navegador cual es el lenguaje que tiene este proyecto ya sea inglés, español, etc.  
Generaremos dos contenedores más, <head></head> y <body></body>. Estas dos etiquetas son contenedores hermanos, en la etiqueta head va a ir todo lo que es importante para el navegador para poder cargar el proyecto de la forma en la que nosotros lo construimos pero que no es visual para el usuario final. Esto quiere decir todas las dependencias, algunas librerías externas, por ejemplo, las fuentes, nuestro CSS tienen que ir ligados en el head, aquí es donde los vamos a mandar a llamar.  
El usuario va a ver todo lo que esta adentro del body, va a ir todo el texto, todas las imágenes, todos los videos, todas estas cosas interactivas que va a tener el proyecto con el usuario va ir a dentro de el body.  
En el head colocamos la etiqueta meta, esta etiqueta le va a dar cierta información al navegador para que sepa como tratar nuestro proyecto. Esta etiqueta se cierra sola. Esta etiqueta va a llevar un atributo que se llama charset, que va a llevar un valor que es UTF-8, que nos va a ayudar para que el navegador pueda entender caracteres especiales (ñ, ü, acentos, etc)  
<meta charset=“UTF-8” />

Otro meta que vamos a utilizar es el meta name description, esta parte del description es importante y esto nos va a ayudar, es parte de SEO, porque nos va a ayudar a que el navegador ayude a que cuando la gente busque cierta información en internet en la descripción que tengamos en nuestra pagina pueda salir esa información. Por ejemplo, podemos ponerle tipo content que es qué tipo de descripción queremos poner y nosotros podemos poner la descripción de nuestra página. Por ejemplo, si ponemos “Esta pagina te mostrara fotos de gatos” y si lo guardas es justo lo que te va a salir en la descripción cuando vayas a Google y busques la página.  
<meta name=“description” content=“Esta página te mostrara fotos de gatos” />

Tenemos otro meta, nos va a ayudar para la parte de los robots de posicionamiento de los navegadores, es decir cuando tu estas utilizando Google y estás haciendo una búsqueda si pones js o si pones aprendizaje en línea hay ciertos robots que nos ayudan a posicionar las paginas que tenga que ver con relación a esto, y nosotros podemos decirle a nuestro proyecto que le autorizamos a los robots poder ayudarnos a acomodar nuestra pagina para ese tipo de búsquedas, ese meta se va a llamar meta name robots, hablamos de muchos porque no solo existe el robot de Google existen otros buscadores en otro tipo de navegadores que podemos utilizar para poder hacer búsquedas específicas. Es decirles a todos los robots de los buscadores que estamos autorizando que puedan ayudar a colocar nuestra página con relación a la búsqueda que se hace. La forma de autorizarle es content index, follow. Quiere decir que en nuestro index tienes autorización de poder ayudarme a colocar nuestra pagina si hay alguna búsqueda que tenga que ver con nuestro contenido, esto es importante, si no queremos que esto salga se le pone un unfollow para que el robot no siga nuestro index.  
<meta name=“robots” content=“index, follow” />

Tenemos otro atributo que se llama title, es importante porque cuando vamos al navegador y entramos a una página, en la parte de arriba podemos ver el titulo de ese proyecto, ese titulo se coloca con el title.  
<title>Es mi página</title>

Tenemos otro meta, es muy importante para los proyectos que son responsive y actualmente todos los proyectos que tu hagas, todos los proyectos web tienen que ser 100% responsive, este meta es <meta name=””viewport”/>, viewport es simplemente el tamaño de la pantalla, es el widht de la pantalla completa y en la parte de content le vamos a decir al navegador que queremos que el widht sea igual a device-widht, initial-scale=1.0, es importante cuando inicies un proyecto ese meta exista, ya que nos va a ayudar a que si el proyecto se abre desde una pagina web pueda escalarse un poco el texto de las imágenes y la gente pueda verlo mejor desde un dispositivo mobile, si no tenemos esta línea y abrimos nuestra pagina en un dispositivo mobile se va a ver una letra muy chiquita y vamos a tener que darle zoom, esa es una super mala experiencia para el usuario.  
<meta name=“viewport” content=“widht=device-widht, initial-scale=1.0” />

Existen otras etiquetas que utilizamos para poder agregar el CSS, esa etiqueta se llama link, link va a tener dos atributos, el rel que le va a decir que el documento que va a cargar es una hoja de estilos y href que significa la referencia, en donde se encuentra ese documento, le ponemos la ruta. De esta forma ya tengo mi hoja de estilo incorporada a mi index.  
<link rel=“stylesheet” href="./css/style.css" />

Les comparto este PDF con todas las Etiquetas de HTML5 🤗  
[https://i.emezeta.com/weblog/html5-cheatsheet/html5-cheatsheet-2019.pdf](https://i.emezeta.com/weblog/html5-cheatsheet/html5-cheatsheet-2019.pdf)  
Creditos a // Emezeta  

![](https://i.emezeta.com/weblog/html5-cheatsheet/chuleta-html5-desarrollo-web.png)

```html
<!DOCTYPE html>

<html lang="es">

  

<head>

 <meta charset="UTF-8">

 <meta name="description" content="Esta página te mostrara fotos de gatos">

 <meta name="robots" content="index,follow">

 <title>Es mi página</title>

 <meta name="viewport" content="width=device-width, initial-scale=1.0">

 <link rel="stylesheet" href="./css/style.css">

</head>

  

<body>

  

</body>

  

</html>
```
