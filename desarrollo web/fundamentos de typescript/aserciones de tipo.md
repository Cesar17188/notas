# Aserciones de tipo

-   Cuando el programador puede conocer más que typescript sobre el valor de una variable
-   Es un mensaje al compilador: “Confia en mi, se lo que hago”
-   Se parece al casting de tipos en otros lenguajes de programación
-   Usa dos sintaxis: `Angle Bracket` y (variable `as` tipo)
	
	```ts
	export{} //<tipo> // Angle Bracket sintax 
	let username:any; 
	username = 'luixaviles'; 
	//tenemos una cadena, TS confia en mi! 
	//Queremos utilizar la funcion length pero la variable esta declarada con any 
	//Entonces lo que hacemos es utilizar <tipoDato> para indicarle que es un string 
	//Y poder utilizar length para conocer la longitud del string 
	let message:string = (<string>username).length > 5? `Welcome ${username}`: 'Username es muy corto'; console.log(message); let usernameWithId: any = 'luixviles 1'; 
	//Como obtener el username username = (<string>usernameWithId).substring(0,10); console.log(username); 
	//Sintaxis as 
	//Es otra forma de insertar tipos en ts 
	//En lugar de los <> podemos utilizar as dentro de los parentisis para especificarle 
	// Un tipo de dato a la variable 
	message = (username as string).length > 5? `Welcome ${username}`: 'Username es muy corto'; console.log(message); let helloUser: any; helloUser = "hello paparazzi"; username = (helloUser as string).substring(6);
	```
	
Aserciones de tipos: Mecanismo de conversión de tipos de datos. Se parece al casting de tipos en otros lenguajes de programación.  
Usa dos sintaxis.

```ts
//Angle Bracket: <Type>
let username : any;
username = (<string>'danijazzero').toUpperCase()
///as: variable as type
username = (username as string).toLowerCase()
```

[Documentación oficial sobre <> y ‘as’ en TS](https://www.typescriptlang.org/docs/handbook/release-notes/typescript-1-6.html#new-tsx-file-extension-and-as-operator)

Se recomienda más usar `as` ya que `<>` trae problemas con React