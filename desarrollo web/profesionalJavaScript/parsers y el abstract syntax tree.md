# Parsers y el Abstract Syntax Tree

El JS Engine recibe el código fuente y lo procesa de la siguiente manera:

-   El **parser** descompone y crea tokens que integran el **AST**.
-   Se compila a **bytecode** y se ejecuta.
-   Lo que se pueda se **optimiza a machine code** y se reemplaza el código base.

Un **SyntaxError** es lanzado cuando el motor JavaScript encuentra partes que no forman parte de la sintaxis del lenguaje y esto lo logra gracias a que se tiene un AST generado por el parser.

El _parser_ es del 15% al 20% del proceso de ejecución por lo que hay que usar parser del código justo en el momento que lo necesitamos y no antes de saber si se va a usar o no.

Para que el código llegue al navegador tiene que pasar muchas cosas, agarra el código, lo analiza, lo descontruye, lo construye nuevamente, lo ejecuta y lo optimiza. Vamos a hablar de todo esto.

‌

## La web[](https://platzi.com/clases/1642-javascript-profesional/22166-parsers-y-el-abstract-syntax-tree/#la-web)

‌

Ha cambiado mucho, cuando empezó a leer JavaScript lo hacía con `Netscape` que hacía cosas muy simples, se leía línea por línea, un paso a la vez. Hoy es igual, pero ahora de una forma diferente, ahora **Google** lo ha cambiado, ellos necesitaban a un navegador que ejecutara todo eficientemente. Por eso reinventó el funcionamiento del motor de `JavaScipt`. En resumen esto es lo que hace:

![](https://blobscdn.gitbook.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-LlTyKe9xd6RJ6x5f2-z%2F-LoBMLhD1_J2PtZzvrDo%2F-LoBMn-8Q8TceF9mxDoZ%2FScreenshot_10.png?alt=media&token=7e948d8a-471c-454b-b00b-99dd75fccb14)

‌

Este es el proceso que realiza JavaScript para lograr ejecutar su código de la mejor forma posible. Ahora veamos un gráfico donde se explica mejor.

![](https://blobscdn.gitbook.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-LlTyKe9xd6RJ6x5f2-z%2F-LoBMLhD1_J2PtZzvrDo%2F-LoBMsLB7cpFBtb-EZ9L%2FScreenshot_11.png?alt=media&token=bc179ac3-ae0f-4c89-b10c-b1fae0986f80)

‌

-   **Bytecode**: es un código de más bajo nivel que permite que se ejecute mucho más rápido.
    
-   **Profiling data**: encuentra todos los puntos optimizables del código para luego dar paso al _optimizer compiler_
    
-   **Optimized code**
    

‌

Aveces este proceso falla y se quita la optimización.

‌

## Parser[](https://platzi.com/clases/1642-javascript-profesional/22166-parsers-y-el-abstract-syntax-tree/#parser)

‌

Este agarra tu código fuente y lo lee, pero tiene que descomponerlo primero, a estos pedazos se les llama _tokens_, identifica que significa cada palabra o símbolo. Una vez teniendo esta información se pasa al _**Abstract Syntax Tree**_.

![](https://blobscdn.gitbook.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-LlTyKe9xd6RJ6x5f2-z%2F-LoBMLhD1_J2PtZzvrDo%2F-LoBMwAgrV-aWtsbRwjx%2FScreenshot_12.png?alt=media&token=a4d41b94-1e5b-4de6-8f33-7e6a061a195d)

‌

Cuando sucede un error en esta lectura es donde sucede el `syntaxError`. No se puede leer tu código y no tiene sentido, los lenguajes de programación son muy formales, no se puede violar las reglas. Este proceso tiene que hacerse muy bien. Veamos que dice **Google** sobre este tema.

![](https://blobscdn.gitbook.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-LlTyKe9xd6RJ6x5f2-z%2F-LoBMLhD1_J2PtZzvrDo%2F-LoBN0Y_a0Moc2i_Vocu%2FScreenshot_13.png?alt=media&token=fbf8b78c-6af5-4904-98b9-794f320a4daa)

‌

La mayoría del código no se ejecuta, por esto tenemos que empaquetar nuestro código de forma eficiente, a esto se le llama _bunding_ y _code splitting_, separaremos el código y lo cargaremos cuando sea necesario solamente. Esto se ve mucho en la **SPA**.

‌

Existen forma de hacer, concretamente dos, veamos cómo lo hace el **V8**.

![](https://blobscdn.gitbook.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-LlTyKe9xd6RJ6x5f2-z%2F-LoBMLhD1_J2PtZzvrDo%2F-LoBN4CAxmGYvGfV_Gp0%2FScreenshot_14.png?alt=media&token=961d63a2-209a-4c71-85be-635948944a4e)

‌

Cuando se hace el _Eager Parsing_ es donde se ve los errores y crea el **AS**T, el árbol se lectura de nuestro programa, también se construye los scopes para leer las variables globales o privadas.

‌

Cuando hacemos _Lazy Parsing_ retrasamos alguna parte del código, logrando un **x2** de rápido en la lectura, no se crea el **AST** y los **scopes** se construyen parcialmente.

‌

## Tokens[](https://platzi.com/clases/1642-javascript-profesional/22166-parsers-y-el-abstract-syntax-tree/#tokens)

‌

Te compartiré un **link** donde puedes experimentar con los _tokens_ para ver cómo funciona.

‌

-   [Tokens | Demo](https://esprima.org/demo/parse.html)

‌

Allí veremos como nos arroja los tokens de una declaración.

```
> var answer = 6 * 7;
< [
	    {
	        "type": "Keyword",
	        "value": "var"
	    },
	    {
	        "type": "Identifier",
	        "value": "answer"
	    },
	    {
	        "type": "Punctuator",
	        "value": "="
	    },
	    {
	        "type": "Numeric",
	        "value": "6"
	    },
	    {
	        "type": "Punctuator",
	        "value": "*"
	    },
	    {
	        "type": "Numeric",
	        "value": "7"
	    },
	    {
	        "type": "Punctuator",
	        "value": ";"
	    }
	]
```

‌

Esto nos da el tipo y el valor que tiene cada palabra, símbolo o número. Tendremos cada uno de los caracteres clasificados para poder manipular y leer cada uno de ellos.

‌

## AST[](https://platzi.com/clases/1642-javascript-profesional/22166-parsers-y-el-abstract-syntax-tree/#ast)

‌

Esta es una estructura en forma de árbol, _**Abstract Syntax Tree**_. Este empieza desde una raíz y se desploma en partes.

![](https://blobscdn.gitbook.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-LlTyKe9xd6RJ6x5f2-z%2F-LoBMLhD1_J2PtZzvrDo%2F-LoBN86xTwwuf5tX7KfZ%2FScreenshot_15.png?alt=media&token=194427bf-c15b-4884-96ee-cb56bb2f8a63)

‌

Se puede usar en muchos lugares, para corregir el código, para compilar, entre otras funciones. Podemos experimentar en el siguiente enlace.

‌

-   [AST | Example](https://astexplorer.net/)

‌

Allí veremos como se va ramificando nuestro programa y va haciéndolo en forma de patrón anidado profundo, aparece valores que nuestro programa terminará ejecutando.

![[Pasted image 20210929230817.png]]