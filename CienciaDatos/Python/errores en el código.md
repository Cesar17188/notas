# Los errores en el código

## Cuando no nos avisa python
## Cuando python nos avisa donde esta el error

### SyntaxError
Cuando estamos escribiendo [[código]] y hay una palabra clave que escribimos mal (es decir un typo), python nos arroja un sintax error.
Los syntaxError hace que [[Python]] detenga el programa y no lo corre.

### Exception

Las excepciones puede destruir la lógica del programa y [[Python]] corre todas las lineas previas a la escepcion encontrada. Existen más de 50 tipos de excepciones pero las excepciones más vistas son:

* KeyboardInterrupt: cuando pulsamos ctrl + c y todo se cierra. [[Python]] crea un objeto de tipo excepcion y lo va moviendo en el programa en los bloques de código desde adentro hacia afuera lo que se denomina [ELEVAR].
* KeyError: Esto sucede cuando intentamos acceder a una llave en un diccionario que no existe. 
* IndexError: Esto sucede cuando estamos trabajando con listas e intentamos ingresar a un indice del elemeno que no existe
* FileNotFoundError: Cuando intentamos abrir un archivo en Python que no existe nos manda un error
* ZeroDivisionError: Cuando intentamos dividir por cero una expresión matemática
* ImportError: Cuando intentamos importar un módulo y hay un error en el módulo y Python envia un error

Como se muestra un mensaje de error en python

```Python
Traceback (most recent call last):
	File "<stdin>", line 1, in <module>
ZeroDivisionError: division by zero
```
 Para leer un error hay que leer desde el final hasta el principio. 
 La última linea nos muestra la explicación de la excepcion
 La penúltima linea nos muestra el archivo donde ocurrió el error, el segundo elemento nos muestra la linea donde ocurrio el error, y el último elemento nos muestra el módulo donde ocurrio el error.
 La primera linea nos muestra cuando paso el error.
 
 Para lograr un manejo de errores existen varias formas como por ejemplo:
 
 * [[debugging]]
 * [[manejo de excepciones]]