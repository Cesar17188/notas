# Clases

-   Las clases y a la POO, se puede conectar las diferentes entidades y se puede relacionar
-   Una clase es la asbtracción de un conjunto de objetos  
    ejemplo:  
    Para definir una entidad usuario, se hace uso de una clase: Se debe definir una clase que  
    dentro tenga una función que permita crear objetos a partir de esta Clase y poder interactuar con ellos.

```
export {}

enum PhotoOrientation {
    Landscape,
    Portrait,
    Square,
    Panorama,
};

class Picture {
    // properties
    id: number;
    title: string;
    orientation: PhotoOrientation;
    //constructor
    constructor( id: number, title: string, orientation: PhotoOrientation ) {
        this.id = id;
        this.title = title;
        this.orientation = orientation;
    }
    //Performance
    toString() {
        return `[id: ${this.id}, title: ${this.title}, orientation: ${this.orientation}]`
    }
}

class Album {
    id: string;
    title: string;
    pictures: Picture[];

    constructor( id: string, title: string ) {
        this.id = id;
        this.title = title;
        this.pictures = [];
    }    

    addPicture(picture: Picture) {
        this.pictures.push(picture);
    }
}

let album: Album = new Album('stories-1', 'Photos of mine');
const newPic: Picture = new Picture(2, 'my new pic!', PhotoOrientation.Panorama);
const new2Pic: Picture = new Picture(3, 'my 2nd new pic!', PhotoOrientation.Portrait);
const new3Pic: Picture = new Picture(4, 'my 3rd new pic!', PhotoOrientation.Portrait);
album.addPicture(newPic);
album.addPicture(new2Pic);
album.addPicture(new3Pic);
console.log('album -> ', album);
```

Definiendo Clases y Constructores

A partir de ECMAScript 2015 es posible construir clases y hacer uso del paradigma de la Programación Orientada a Objetos en Javascript

Typescript permite aplicar estas técnicas sin tener que es esperar por otra versión.

```tsx
export{}

enum PhotoOrientation {

  Landscape,
  Portrait,
  Square,
  Panorama
}

class Picture {

  //Propiedades
  id:number;
  title:string;
  orientation:PhotoOrientation;

  constructor(id:number,title:string,orientation:PhotoOrientation){

    this.id = id;
    this.title = title;
    this.orientation = orientation;

  }

  //Comportamiento de nuestra clase que estara definido por funciones

  toString(){
    return `[id ${this.id},
            title: ${this.title},
            orientation: ${this.orientation}]`;
  }

}

class Album{

  id:number;
  title:string;
  pictures: Picture[];

  //Usamos el constructor el cual nos permitira crear objetos de esta clase
  constructor(id:number, title:string){

    this.id = id;
    this.title = title;
    this.pictures = [];
  }
    addPicture(picture:Picture){
      this.pictures.push(picture);

    }

  }

  //Creamos un nuevo a partir de la instancia de la clase

  const album:Album = new Album(1, 'personal pictures');
  const picture: Picture = new Picture(1, 'Platzi session', PhotoOrientation)
  album.addPicture(picture);

  console.log(album);
```