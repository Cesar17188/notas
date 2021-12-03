# Clases públicas y privadas

-   TS define un modificador de acceso publico por defecto para los miembros de clase ( public )
-   TS define un modificador de acceso privado para los miembros que no se deseen ser leídos por fuera de la clase ( private )

-   con TS se tiene una sintaxis para métodos privados. Usando el signo # antes del nombre del miembro de clase: p.e. #atributo  
    Esto se hace debido a que ofrece garantías de aislamiento en miembros privados.  
    ( Private identifiers are only available when targeting ECMAScript 2015 and higher. )

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
    #id: number;
    #title: string;
    #orientation: PhotoOrientation;
    //constructor
    public constructor( id: number, title: string, orientation: PhotoOrientation ) {
        this.#id = id;
        this.#title = title;
        this.#orientation = orientation;
    }
    //Performance
    private toString() {
        return `[id: ${this.#id}, title: ${this.#title}, orientation: ${this.#orientation}]`
    }
}

class Album {
    #id: string;
    #title: string;
    #pictures: Picture[];

    public constructor( id: string, title: string ) {
        this.#id = id;
        this.#title = title;
        this.#pictures = [];
    }    

    private addPicture(picture: Picture) {
        this.#pictures.push(picture);
    }
}

let album: Album = new Album('stories-1', 'Photos of mine');
/** Don't care about commented code below. The classes has private members, the output will be empty  */
// const newPic: Picture = new Picture(2, 'my new pic!', PhotoOrientation.Panorama);
// const new2Pic: Picture = new Picture(3, 'my 2nd new pic!', PhotoOrientation.Portrait);
// const new3Pic: Picture = new Picture(4, 'my 3rd new pic!', PhotoOrientation.Portrait);
// album.addPicture(newPic); there's an error due to private class props
// album.addPicture(new2Pic); there's an error due to private class props
// album.addPicture(new3Pic);  there's an error due to private class props
console.log('album -> ', album);
```