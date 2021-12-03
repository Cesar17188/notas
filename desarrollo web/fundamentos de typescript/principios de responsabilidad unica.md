# Principios de responsabilidad única
Principio de responsabilidad unica. Idealmente un archivo deberia tener un proposito o responsabilidad unica: definir una clase, una interfaz, un enumerado, etc.  
Esto mejora la legibilidad de codigo, facilita la lectura, testing y favorece su mantenimiento.

Utilizamos archivos separados y la utilizacion de import, export para lograr un poco mas de mantenibiilidad. Podemos usar tambien carpetas para separar nuestros archivos.

Para observar una carpeta entera usamos:

```
tsc --project myFolder --watch
```

Con el metodo [filter](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/filter), se regresa un nuevo array como resultado de la funcion arrow dentro de esta.

El metodo [splice](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/splice) modifica el arreglo al que se le llama esta operacion.

Si quieres compararlo en terminos de performance, te recomiendo entiendas el concepto de complejidad de espacio (notacion Big O) que define el uso de memoria de tu programa, pero para fines practicos esto tambien es una nueva alternativa.

Ademas de esto, el SRP nos dice que una clase debe tener una sola responsabilidad unica y debe estar desacoplada. En este caso por ejemplo una mejora seria que el usuario no deberia saber como remover o agregar albumes, para esto creamos otra clase que se encarge solo de eso. [https://code.tutsplus.com/tutorials/solid-part-1-the-single-responsibility-principle--net-36074](https://code.tutsplus.com/tutorials/solid-part-1-the-single-responsibility-principle--net-36074)

-   **Como defender el Principio de Responsabilidad Única** :  
    Para defender el Principio de Responsabilidad Única en nuestro código podemos apoyarnos en mejorar dos aspectos del mismo. Estos son la cohesión y el acoplamiento, de forma que:

1.  Mantener una alta cohesión, es decir, mantener ‘unidas’ funcionalidades que estén relacionadas entre sí y mantener fuera aquello que no esté relacionado. El objetivo es aumentar la cohesión entre las cosas que cambian por las mismas razones.
    
2.  Mantener un bajo acoplamiento, es decir, reducir al máximo posible el grado de la relación de un clase o módulo con el resto, para favorecer crear código más fácilmente mantenible, extensible y testeable. El objetivo es disminuir el acoplamiento entre aquellas cosas que cambian de forma diferente.
    

Estos dos aspectos favorecerá un código con funcionalidades más concretas y mejor especificadas.  
_**Reúne las cosas que cambian por las mismas razones. Separa las cosas que cambian por diferentes razones.**_

fuente: [click acá](https://medium.com/@mpijierro/principios-solid-principio-de-responsabilidad-%C3%BAnica-13eb4d5537c1)