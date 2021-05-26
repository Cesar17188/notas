# Let y const, multilinea, spread operator y desestructuración

![const-vs-let-vs-var.png](https://static.platzi.com/media/user_upload/const-vs-let-vs-var-f3270d36-0e39-4e0d-8ed1-2681991b84b2.jpg)

En el siguiente fragmento de código se comentará lo visto en clase, para ejecutar el plugin Code Runner, puedes usar: ctrl+alt+n

```js
//Forma Normal
let hello= "Hello";
let world="Mundo";
let frase = hello+" "+world;
console.log(frase);

//Template literal es6
let fraseTemplateLiteral = `${hello}${world}`;
console.log(fraseTemplateLiteral);


//Forma normal separaciones de línea.

//Antes para realizar multilíneas se usaba  backslash (alt+92) 
//+ n + "" continuar una línea
let Frase ="KANSClnclnsnspan pscapo apso  \n" //Multilíneas
+ "ljsndljnvsjd"

//Con los Template literals `` se puede sencillamente realizar
//un enter para pasar de línea.
let Frase_es6 = `Lknlasknlncs
dksvñsnkvlksnnldkvsnd`;

console.log(Frase);
console.log(Frase_es6);

// Destructuración de elementos:

//Antes los objetos podía ser creados así:

let person ={
    'name':'Alejandro',
    'nick':'Etrx',
    'num':'12314125'
};

//Si queríamos llamar  lo que componía ese objeto utilizabamos:
console.log(person.name,person.nick,person.num);

//Ahora con la destrucción de elementos, sucede una especie de
//resumen, donde se extrae un factor común del nombre del objeto, así:
let {name,nick, num} = person;

//Si queremos llamar  lo que compone este 
//objeto utilizamos en ES6:
console.log(name,nick);


//Operador de prolongación: Permite expandir varios elementos. 
//Tenemos varios elementos en arreglos que queremos 
//unir en un solo elemento para presentarlos.

let conjunto1= ['a','b','c'];
let conjunto2= ['x','y','z'];

let conjunto_union=['l','m','n',...conjunto1,...conjunto2]
console.log(conjunto_union);

//Asiganciones mediante let se pueden inicilizar variables 
//cuyo scope está solo en el bloque de código en el 
//que está llamada, en otras palabras, solo puede 
//existir las variables let dentro de las llaves 
//en que se llaman. Var se seguirá usando para 
//variables globales y locales.
 

{
    var VariableGlobal= "...";
}

{
    let VariableLocal= "***";
    console.log(VariableLocal); 
	 // Al estar dentro de las llaves o el 
	 //bloque de código console se ejecutará con normalidad
}

console.log(VariableGlobal);
console.log(VariableLocal); 
// Al ejecutar esta arroja error al
//estar fuera del scope donde fue declarada.



//Const, nos permitirá establecer una variable como una constante, donde el valor declarado no podrá cambiar.

const a = "Soy constante";
a = "No soy constante" ; // Al ejecutar arroja error porque no puede cambiarse una constante luego de declararse.

console.log(a);

```