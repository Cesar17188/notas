# Interfaces

Se constituyen como forma de contratos para el codigo que vaya a implementarla.

Es una forma de definir que propiedades y metodos deben implementar si o si las propiedades que se declaren de este tipo de interfas

[Documentación oficial sobre interfaces en TS](https://www.typescriptlang.org/docs/handbook/2/objects.html#interfaces-vs-intersections)

[Interfaces en TS explicado en TutorialsTeacher](https://www.tutorialsteacher.com/typescript/typescript-interface)

[Interfaces en TS explicado en Desarrollo Web](https://desarrolloweb.com/articulos/definicion-interfaces-typescript.html)

[Interfaces en TS explicado en TutorialsPoint](https://www.tutorialspoint.com/typescript/typescript_interfaces.htm)

```tsx
interface Picture{
	title: string,
	date: string,
	orientation: PhotoOrientation // Enum
}

// el parametro picture va a verificar si el valor recibido cumple con la interface
function showPicture(picture: Picture){
	console.log(`[title: ${picture.title},
								date: ${picture.date}
								orientation: ${picture.orientation}]`
}
```

en POO, una interfaz definia unicamente los METODOS de un objeto y no las propiedades como lo muestra el ejemplo que nos da el profesor. Tanto de las propiedades como los metodos se encargan las clases. Aqui es donde entra Typescript, en TS podemos tambien definir propiedades, no unicamente metodos.

Y si es util, creo que esta definicion de interfaz es un poco mas clara: Una interfaz (En TypeScript) es un tipo (como string, boolean, number, etc) mas “complejo”, en el cual defines (como enun contrato) las propiedades y metodos que se deben cumplir de cualquier objeto que lo instancie.

La diferencia entre una interfaz y una clase es que en la interfaz solo hacemos mencion de que esperamos de un objeto, en una clase mencionamos las propiedades (igual que una interfaz) pero **definimos** los metodos (osea, especificamos que hara ese metodo, en la interfaz solo mencionamos el nombre de la funcion)