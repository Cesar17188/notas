# Categorías de patrones de diseño

**Creacionales**. Proveen diferentes mecanismos para crear objetos.

**Estructurales**. Describen formas de componer objetos para formar nuevas estructuras flexibles y eficientes.

**De Comportamiento**. Gestionan algoritmos y responsabilidades entre objetos.

## Relación de principales patrones _GoF_ (_Gang Of Four_)[[editar](https://es.wikipedia.org/w/index.php?title=Patr%C3%B3n_de_dise%C3%B1o&action=edit&section=5 "Editar sección: Relación de principales patrones GoF (Gang Of Four)")]

## Patrones creacionales[[editar](https://es.wikipedia.org/w/index.php?title=Patr%C3%B3n_de_dise%C3%B1o&action=edit&section=6 "Editar sección: Patrones creacionales")]

Corresponden a patrones de diseño de software que solucionan problemas de creación de instancias. Nos ayudan a encapsular y abstraer dicha creación:

-   [Object Pool](https://es.wikipedia.org/wiki/Object_Pool_(patr%C3%B3n_de_dise%C3%B1o) "Object Pool (patrón de diseño)") (no pertenece a los patrones especificados por GoF): se obtienen objetos nuevos a través de la clonación. Utilizado cuando el costo de crear una clase es mayor que el de clonarla. Especialmente con objetos muy complejos. Se especifica un tipo de objeto a crear y se utiliza una interfaz del prototipo para crear un nuevo objeto por clonación. El proceso de clonación se inicia instanciando un tipo de objeto de la clase que queremos clonar.
-   [Abstract Factory](https://es.wikipedia.org/wiki/Abstract_Factory_(patr%C3%B3n_de_dise%C3%B1o) "Abstract Factory (patrón de diseño)") (fábrica abstracta): permite trabajar con objetos de distintas familias de manera que las familias no se mezclen entre sí y haciendo transparente el tipo de familia concreta que se esté usando. El problema a solucionar por este patrón es el de crear diferentes familias de objetos, como por ejemplo, la creación de interfaces gráficas de distintos tipos (ventana, menú, botón, etc.).
-   [Builder](https://es.wikipedia.org/wiki/Builder_(patr%C3%B3n_de_dise%C3%B1o) "Builder (patrón de diseño)") (constructor virtual): abstrae el proceso de creación de un objeto complejo, centralizando dicho proceso en un único punto.
-   [Factory Method](https://es.wikipedia.org/wiki/Factory_Method_(patr%C3%B3n_de_dise%C3%B1o) "Factory Method (patrón de diseño)") (método de fabricación): centraliza en una clase constructora la creación de objetos de un subtipo de un tipo determinado, ocultando al usuario la casuística, es decir, la diversidad de casos particulares que se pueden prever, para elegir el subtipo que crear. Parte del principio de que las subclases determinan la clase a implementar. A continuación se muestra un ejemplo de este patrón:

```js
class ConcreteCreator extends Creator{
    protected Product factoryMethod(){
        return new ConcreteProduct();
    }
}

interface Product{...}

class ConcreteProduct implements Product{...}

public class Client{
    public static void main(String args[])
    {
        Creator unCreator = new ConcreteCreator();
        unCreator.factoryMethod();
    }
}
```

-   [Prototype](https://es.wikipedia.org/wiki/Prototype_(patr%C3%B3n_de_dise%C3%B1o) "Prototype (patrón de diseño)") (prototipo): crea nuevos objetos clonándolos de una instancia ya existente.
-   [Singleton](https://es.wikipedia.org/wiki/Patr%C3%B3n_de_dise%C3%B1o_Singleton "Patrón de diseño Singleton") (instancia única): garantiza la existencia de una única instancia para una clase y la creación de un mecanismo de acceso global a dicha instancia. Restringe la instanciación de una clase o valor de un tipo a un solo objeto. A continuación se muestra un ejemplo de este patrón:

```js
		public sealed class Singleton
		{
		    private static volatile Singleton instance;
		    private static object syncRoot = new Object();
		    private Singleton()
		    {
		        System.Windows.Forms.MessageBox.Show("Nuevo Singleton");
		    }
		    public static Singleton GetInstance
		    {
		        get
		        {
		            if (instance == null)
		            {
		                lock(syncRoot)
		                {
		                    if (instance == null)
		                    instance = new Singleton();
		                }
		            }
		            return instance;
		        }
		    }
		}
```

-   [Model View Controller (MVC)](https://es.wikipedia.org/wiki/Modelo_Vista_Controlador "Modelo Vista Controlador") **♙**En español: **_**Modelo Vista Controlador.**_** Es un patrón de arquitectura de software que separa los datos y la lógica de negocio de una aplicación de la interfaz de usuario y el módulo encargado de gestionar los eventos y las comunicaciones. Este patrón plantea la separación del problema en tres capas: la capa **model**, que representa la realidad; la capa **controller** **,** que conoce los métodos y atributos del modelo, recibe y realiza lo que el usuario quiere hacer; y la capa **vista**, que muestra un aspecto del modelo y es utilizada por la capa anterior para interactuar con el usuario.

## Patrones estructurales[[editar](https://es.wikipedia.org/w/index.php?title=Patr%C3%B3n_de_dise%C3%B1o&action=edit&section=7 "Editar sección: Patrones estructurales")]

Son los patrones de diseño software que solucionan problemas de composición (agregación) de clases y objetos:

-   [Adapter o Wrapper](https://es.wikipedia.org/wiki/Adapter_(patr%C3%B3n_de_dise%C3%B1o) "Adapter (patrón de diseño)") (Adaptador o Envoltorio): Adapta una interfaz para que pueda ser utilizada por una clase que de otro modo no podría utilizarla.
-   [Bridge](https://es.wikipedia.org/wiki/Bridge_(patr%C3%B3n_de_dise%C3%B1o) "Bridge (patrón de diseño)") (Puente): Desacopla una abstracción de su implementación.
-   [Composite](https://es.wikipedia.org/wiki/Composite_(patr%C3%B3n_de_dise%C3%B1o) "Composite (patrón de diseño)") (Objeto compuesto): Permite tratar objetos compuestos como si de uno simple se tratase.
-   [Decorator](https://es.wikipedia.org/wiki/Decorator_(patr%C3%B3n_de_dise%C3%B1o) "Decorator (patrón de diseño)") (Decorador): Añade funcionalidad a una clase dinámicamente.
-   [Facade](https://es.wikipedia.org/wiki/Facade_(patr%C3%B3n_de_dise%C3%B1o) "Facade (patrón de diseño)") (Fachada): Provee de una interfaz unificada simple para acceder a una interfaz o grupo de interfaces de un subsistema.
-   [Flyweight](https://es.wikipedia.org/wiki/Flyweight_(patr%C3%B3n_de_dise%C3%B1o) "Flyweight (patrón de diseño)") (Peso ligero): Reduce la redundancia cuando gran cantidad de objetos poseen idéntica información.
-   [Proxy](https://es.wikipedia.org/wiki/Proxy_(patr%C3%B3n_de_dise%C3%B1o) "Proxy (patrón de diseño)"): Proporciona un intermediario de un objeto para controlar su acceso.
-   [Module](https://es.wikipedia.org/wiki/Module_(patr%C3%B3n_de_dise%C3%B1o) "Module (patrón de diseño)"): Agrupa varios elementos relacionados, como clases, singletons, y métodos, utilizados globalmente, en una entidad única.

## Patrones de comportamiento[[editar](https://es.wikipedia.org/w/index.php?title=Patr%C3%B3n_de_dise%C3%B1o&action=edit&section=8 "Editar sección: Patrones de comportamiento")]

Se definen como patrones de diseño software que ofrecen soluciones respecto a la interacción y responsabilidades entre clases y objetos, así como los algoritmos que encapsulan:

-   [Chain of Responsibility](https://es.wikipedia.org/wiki/Chain_of_Responsibility_(patr%C3%B3n_de_dise%C3%B1o) "Chain of Responsibility (patrón de diseño)") (Cadena de responsabilidad): Permite establecer la línea que deben llevar los mensajes para que los objetos realicen la tarea indicada.
-   [Command](https://es.wikipedia.org/wiki/Command_(patr%C3%B3n_de_dise%C3%B1o) "Command (patrón de diseño)") (Orden): Encapsula una operación en un objeto, permitiendo ejecutar dicha operación sin necesidad de conocer el contenido de la misma.
-   [Interpreter](https://es.wikipedia.org/wiki/Interpreter_(patr%C3%B3n_de_dise%C3%B1o) "Interpreter (patrón de diseño)") (Intérprete): Dado un lenguaje, define una gramática para dicho lenguaje, así como las herramientas necesarias para interpretarlo.
-   [Iterator](https://es.wikipedia.org/wiki/Iterator_(patr%C3%B3n_de_dise%C3%B1o) "Iterator (patrón de diseño)") (Iterador): Permite realizar recorridos sobre objetos compuestos independientemente de la implementación de estos.
-   [Mediator](https://es.wikipedia.org/wiki/Mediator_(patr%C3%B3n_de_dise%C3%B1o) "Mediator (patrón de diseño)") (Mediador): Define un objeto que coordine la comunicación entre objetos de distintas clases, pero que funcionan como un conjunto.
-   [Memento](https://es.wikipedia.org/wiki/Memento_(patr%C3%B3n_de_dise%C3%B1o) "Memento (patrón de diseño)") (Recuerdo): Permite volver a estados anteriores del sistema.
-   [Observer](https://es.wikipedia.org/wiki/Observer_(patr%C3%B3n_de_dise%C3%B1o) "Observer (patrón de diseño)") (Observador): Define una dependencia de uno-a-muchos entre objetos, de forma que cuando un objeto cambie de estado se notifique y actualicen automáticamente todos los objetos que dependen de él.
-   [State](https://es.wikipedia.org/wiki/State_(patr%C3%B3n_de_dise%C3%B1o) "State (patrón de diseño)") (Estado): Permite que un objeto modifique su comportamiento cada vez que cambie su estado interno.
-   [Strategy](https://es.wikipedia.org/wiki/Strategy_(patr%C3%B3n_de_dise%C3%B1o) "Strategy (patrón de diseño)") (Estrategia): Permite disponer de varios métodos para resolver un problema y elegir cuál utilizar en tiempo de ejecución.
-   [Template Method](https://es.wikipedia.org/wiki/Template_Method_(patr%C3%B3n_de_dise%C3%B1o) "Template Method (patrón de diseño)") (Método plantilla): Define en una operación el esqueleto de un algoritmo, delegando en las subclases algunos de sus pasos, esto permite que las subclases redefinan ciertos pasos de un algoritmo sin cambiar su estructura.
-   [Visitor](https://es.wikipedia.org/wiki/Visitor_(patr%C3%B3n_de_dise%C3%B1o) "Visitor (patrón de diseño)") (Visitante): Permite definir nuevas operaciones sobre una jerarquía de clases sin modificar las clases sobre las que opera.

## Patrones de interacción[[editar](https://es.wikipedia.org/w/index.php?title=Patr%C3%B3n_de_dise%C3%B1o&action=edit&section=9 "Editar sección: Patrones de interacción")]

El primer intento por aplicar este concepto en el diseño de las interfaces de usuario se dio por Ward Cummingham y Kent Beck quienes adaptaron la propuesta de C. Alexander y crearon cinco patrones de interfaz: _Window per task_, _Few panes_, _Standard panes_, _Nouns and verbs_, y _Short Menu_. En años más recientes investigadores como Martin Van Welie, Jennifer Tidwell han desarrollado colecciones de patrones de interacción para la [World Wide Web](https://es.wikipedia.org/wiki/World_Wide_Web "World Wide Web"). En dichas colecciones captan la experiencia de programadores y diseñadores expertos en el desarrollo de interfaces usables y condensan esta experiencia en una serie de guías o recomendaciones, que puedan ser usadas por los desarrolladores novatos con el propósito de que en poco tiempo adquieran la habilidad de diseñar interfaces que incidan en la satisfacción de los usuarios. Los patrones de interacción buscan la reutilización de interfaces eficaces y un manejo óptimo de los recursos de las [páginas web](https://es.wikipedia.org/wiki/P%C3%A1gina_web "Página web"), haciendo más eficaz el consumo de tiempo en el diseño del [sitio web](https://es.wikipedia.org/wiki/Sitio_web "Sitio web") y permitiendo a los programadores novatos adquirir más experiencia.