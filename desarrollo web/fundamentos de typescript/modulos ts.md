# Módulos

Módulos en TypeScript: Los módulos en typescript proveen un mecanismo para una mejor organización del código y promueven su reutilización  
A partir de ECMAScript 2015 los módulos son parte nativa del lenguaje Javascript

Importando y exportando modulos: Generalmente se define un modulo con la idea de agrupar codigo relacionado. Podemos tomar criterios en torno a la funcionalidad, features, utilitarios, modelos, etc.

Los miembros de modulo interactúan con el uso de las palabras reservadas **import** y **export**

```
export enum PhotoOrientation {
	Landscape,
	Portrait,
	Square,
	Panorama
}

export class Item {
	constructor(public readonly id: number, protected title: string) {}
}

export class User {
	private album: Album[];

	constructor(private id: number, private username: string, private firstName: string, private isPro: boolean) {
		this.album = [];
	}

	addAlbum(album: Album) {
		this.album.push(album);
	}
}

export class Album extends Item {
	private pictures: Picture[];

	public constructor(id: number, title: string) {
		super(id, title);
		this.pictures = [];
	}
	public addPicture(picture: Picture) {
		this.pictures.push(picture);
	}
}

export class Picture extends Item {
	public constructor(id: number, title: string, private _date: string, private _orientation: PhotoOrientation) {
		super(id, title);
	}
	public toString() {
		return `[id: ${this.id},
                 title: ${this.title},
                 orientation: ${this._orientation}]`;
	}
}
```

_main.ts_

```
import { User, Album, Picture, PhotoOrientation } from './photo-app';

const user = new User(1, 'Erickowski', 'Erick', true);
const album = new Album(10, 'Platzi Album');
const picture = new Picture(1, 'Foto', '2020-08', PhotoOrientation.Landscape);

// Creamos relaciones
user.addAlbum(album);
album.addPicture(picture);

console.log('user', user);
```