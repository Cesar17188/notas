# Implementación del patrón Decorator

## PATRÓN ESTRUCTURAL

El patrón decorator está diseñado para solucionar problemas donde la jerarquía con subclasificación no puede ser aplicada, o se requiere de un gran impacto en todas las clases de la jerarquía con el fin de poder lograr el comportamiento esperado. Decorator permite al usuario añadir nuevas funcionalidades a un objeto existente sin alterar su estructura, mediante la adición de nuevas clases que envuelven a la anterior dándole funcionamiento extra.

![](https://reactiveprogramming.io/public/books/patterns/img/patterns-articles/decorator-diagram.png)

Estructura del patrón Decorator.

En la imagen podemos apreciar los distintos componentes que conforman el patrón de diseño Decorator los cuales se explican a continuación:

-   **IComponent:** Interface que define la estructura minina del componente o componentes que pueden ser decorados.
-   **ConcreteComponent:** Implementación de IComponent y define un objeto concreto que puede ser decorado.
-   **ComponentDecorator:** Por lo general es una clase abstracta que define la estructura mínima de un Decorador, el cual mínimamente deben de heredar de IComponent y contener alguna subclase de IComponent al cual decorarán.
-   **ComponentDecoratorImpl:** Representan todos los decoradores concretos que heredan de ComponentDecorator.

![](https://reactiveprogramming.io/public/books/patterns/img/patterns-articles/decorator-sequence.png)

Diagrama de secuencia del patrón Decorator.

1.  El _Cliente_ realiza una operación sobre el _DecoratorA_.
2.  El _DecoratorA_ realiza la misma operación sobre _DecoradorB_.
3.  El _decoradorB_ realiza una acción sobre _ConcreteComponente_.
4.  El _DecoradorB_ ejecuta una operación de decoración.
5.  El _DecoradorA_ ejecuta una operación de decoración.
6.  El _Cliente_ recibe como resultado un objeto decorado por todos los Decoradores, los cuales encapsularon el _Component_ en varias capas.

## EJEMPLO DEL MUNDO REAL

Mediante la implementación del patrón de diseño _Decorator_ crearemos una aplicación que nos permite procesar un mensaje en capas, donde cada capa se encargará de procesar un mensaje a diferente nivel. primero convertiremos un Objeto en XML, seguido, lo envolveremos en un mensaje SOAP para después encriptar el mensaje, finalmente obtendremos un mensaje SOAP totalmente encriptado, el cual podrá ser enviado de forma segura a un destinatario. Cada capa de procesamiento será implementada con un decorador, y cada decorador podrá cambiar de posición para obtener un resultado diferente, de la misma manera, podrá ser agregados nuevos decoradores en medio de cualquier paso.

![](https://reactiveprogramming.io/public/books/patterns/img/patterns/decorator.png)


_**Para todos los que desean el código antes de comenzar**_

**Index.html**

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Decorator</title>
</head>
<body>
    <a href="/ejercicios/">Go back</a>

    <div style="margin-top: 3rem;">
        <label for="email">Email</label>
        <input id="email">
    </div>
    <script src="/ejercicios/decorator/index.ts"></script>
</body>
</html>
```

**index.ts**

```
class Field{
    errors : string[]
    input: HTMLInputElement

    constructor(input:HTMLInputElement){
        this.input=input
        this.errors=[]

        let errorMessage = document.createElement('p')
        errorMessage.className='text-danger'
        this.input.parentNode.insertBefore(errorMessage,this.input.nextSibling)

        this.input.addEventListener('input',()=>{
            this.errors=[]
            this.validate()
            errorMessage.innerText=this.errors[0]||''
        })
    }
    validate(){}
}

function RequiredFieldDecorator(field:Field){
    return field
}

let field = new Field(document.querySelector('#email'))
RequiredFieldDecorator(field)
```