# Interfaces: propiedades opcionales

-   Dentro de las interfaces se declara un contrato. Un contrato que solo puede ser violado si las condiciones son opcionales.
-   De todo lo que puede declararse dentro de la interfaz, únicamente las propiedades que son opcionales pueden ir seteadas  
    por default o pasando un objeto (seg´´un su estructura) para sobreescribir sus valores.
-   Anteponiendo la palabra reservada `readonly` se define que algunas propiedades podrían no ser modificables.  
    .

```
interface User {
    readonly name?: string;
    readonly age?: number;
    isPro?: boolean;
}

let user: User;
user = {name: 'Andrés', age: 27, isPro: true}
user.name = 'Felipe'; // This will not change the object, so is the reason for readonly
 /** Error: (property) User.name?: string | undefined
   * Cannot assign to 'name' because it is a read-only property. 
   * 
   */
```

Propiedades opcionales : No todas las propiedades de una interfaz podrian ser requeridas. Usamos el simbolo ‘?’ luego del nombre de la propiedad.

```
interface PictureConfig {
	title: string;
	date?: string;
	orientation: PhotoOrientation
}

```

Propiedades de solo lectura: Algunas propiedades de la interfaz podrian no ser modificables una vez creado el objeto. Esto es posible usando **readonly** antes del nombre de la propiedad.

```
interface User {
	readonly id: number;
	username: string;
	readonly isPro:boolean;
}
```