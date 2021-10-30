# Implementación del patrón Singleton

## Singlenton con TS

Uno de los patrones de diseño de creación más populares es el patrón Singleton que restringe la creación de instancias de una clase a un objeto.

En esta publicación, le mostraré cómo usar el patrón junto con TypeScript.

---

## Es genial con TS

La biblia de los patrones de diseño, a saber, el libro de Gang of Four (GoF), presenta la aplicación de patrones utilizando el lenguaje C ++, un lenguaje estáticamente tipado.

**TypeScript permite implementar el patrón Singleton gracias a las siguientes características:**

-   **soporte para modificadores de acceso (privado, protegido, público),**
-   **soporte para métodos estáticos,**
-   **siendo un lenguaje estáticamente escrito.**

---

## Patrón Singleton

En el siguiente ejemplo, _creo la_ clase _ActionsBus_ que se supone que se instancia solo una vez, ya que debería haber un único punto para enviar una acción. Además, debe ser notificado sobre cada acción en el sistema simplemente suscribiéndose en un lugar.

```js
import { BehaviorSubject } from 'rxjs';

interface Action {
  type: string;
}

class ActionsBus {
  private static instance: ActionsBus;
  private actionsSubject = new BehaviorSubject<Action>(null);

  get actions$() {
    return this.actionsSubject.asObservable();
  }

  private constructor() {
  }

  static getInstance(): ActionsBus {
    if (!ActionsBus.instance) {
      ActionsBus.instance = new ActionsBus();
    }

    return ActionsBus.instance;
  }

  dispatch(action: Action) {
    this.actionsSubject.next(action);
  }
}
```

**Los puntos clave son:**

-   **_constructor_ con un modificador de acceso privado, para que no sea accesible fuera del cuerpo de la clase,**
-   **_instancia_ estática archivada que se supone que hace referencia a la instancia única de la clase,**
-   **Método _getInstance_ estático que se encarga de devolver la instancia de la clase. Además, sigue una estrategia de evaluación perezosa, por lo tanto, debe crear la instancia cuando se llama por primera vez.**

---

## Singleton en acción

Veamos si la clase _ActionsBus_ es un singleton, es decir, si solo hay una instancia de la clase.

```js
//illegal since the constructor is private
const illegalActionsBus = new ActionsBus();

const firstActionsBus = ActionsBus.getInstance();
const secondActionsBus = ActionsBus.getInstance();

//both constants reference the same object
console.log(firstActionsBus === secondActionsBus);

firstActionsBus.actions$.subscribe(console.log);
secondActionsBus.dispatch({ type: 'Fetch news' })

//console output
//{type: "Fetch news"}
```

Es ilegal crear la instancia de clase de forma tradicional fuera del cuerpo de la clase. **Para obtener una referencia a la instancia única de _ActionsBus_ , debe llamar al método estático _getInstance_ .** Ambas constantes ( _primer / segundo ActionsBus_ ) hacen referencia al mismo objeto, por lo tanto, la comparación lógica produce _verdadero_ . Por último, pero no menos importante, si se suscribe a la _acción $_ stream con la ayuda de la referencia _firstActionsBus_ , recibirá una acción enviada utilizando la referencia _secondActionsBus_ . Definitivamente confirma que solo hay una instancia de la clase _ActionsBus_ en el sistema.

---

## Conclusiones

Espero que les haya gustado la publicación y hayan aprendido algo nuevo. El patrón Singleton es uno de los patrones más fáciles de entender, por lo tanto, es un buen punto de partida para familiarizarse con los patrones. Recuerdo que cuando me uní al mundo de JavaScript, estaba un poco molesto porque, debido a la falta de tipeo, el conocimiento sobre los patrones de diseño no sería tan útil como en Java o C ++. Afortunadamente, TypeScript al rescate!