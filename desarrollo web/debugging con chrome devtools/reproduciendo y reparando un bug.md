# Reproduciendo y reparando un bug

> para hacer debuggin podemos ir a la siguiente ventana.

![image-20200503025145758.png](https://static.platzi.com/media/user_upload/image-20200503025145758-627158a6-7bb9-4573-b9af-d21112e1438f.jpg)

> vemos que tenemos una sección de **Event Listener Breakpoints** ahí podemos captura eventos en especifico de nuestra pagina web y una ves que suceda el evento que seleccionamos nos posicione en que parte del código sucede y a partir de ahí pode debuggear.


**DEBUGGING JS**

-   En javascript **typeof** retorna el tipo de dato que tiene una variable.
-   El panel **Scope** te muestra las variables locales y globales actualmente definidas, junto con el valor de cada variable.

Otra forma de hace la coerción expplícita de un String a Número es usar la función Number() y pasar la variable dentro de los paréntesis.

**`Coerción explicita`**

Es la forma en que nosotros obligamos a que un valor de un tipo cambie a otro valor de otro tipo, si necesitamos que ese valor sea de un tipo distinto.

```jsx
4 + "7"; // 47 (string, porque JS hace la concatenación con elímbolo de +)
4 * "7" // 28 (Número, porque no se realiza ninguna concatenación)
2 + true; // 3 (porque, true equivale a un valor de 1) 
2 + false; // 2 (al contrario de true, false equicale a un valor de 0)
```

¿Cómo hacemos la coerción explícita?

```jsx
var a = 20;
var b = a + "";
//typeof b --> sería un string
var c = String(a);
//typeof c --> sería un string
var d = Number(c);
//typeof d --> sería un número

```


Con Angular:

![Screen Shot 2020-09-23 at 21.08.58.png](https://static.platzi.com/media/user_upload/Screen%20Shot%202020-09-23%20at%2021.08.58-47b14609-c05e-4eb4-a067-9a116c9a3cba.jpg)