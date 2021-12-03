# Métodos Get y Set

TypeScript soporta los métodos accesores set y get como una forma de interceptar los accesos a los miembros privados de un objeto.

```tsx
export{}

enum PhotoOrientation {

  Landscape,
  Portrait,
  Square,
  Panorama
}

//Los moficadores de acceso get y set son metodos que nos permiten controlar
  //El acceso a cada uno de los miembros

class Picture {
  #id:number;
  #title:string;
  #orientation:PhotoOrientation;

 
  constructor(id:number,title:string,orientation:PhotoOrientation){

    this.#id = id;
    this.#title = title;
    this.#orientation = orientation;

  }
  //El nombre de una funcion accesora no debe coincidir con el nombre de un miembro
    //Podremos arreglar esto cambiando el nombre del miembro o el de la funcion
  get idH(){
    return this.#id;
  }
  set idH(id){

    this.#id = id;
  }

  get titleT(){

    return this.#title

  }
  set titleT(title:string){

    this.#title = title;

  }

  get orientationO(){

    return this.#orientation;
  }

  set orientationO(o:PhotoOrientation){

    this.#orientation = o;
  }

  public toString(){
    return `[id ${this.#id},
            title: ${this.#title},
            orientation: ${this.#orientation}]`;
  }

}

class Album{

  #id:number;
  #title:string;
  #pictures: Picture[];

  public constructor(id:number, title:string){

    this.#id = id;
    this.#title = title;
    this.#pictures = [];
  }
    public addPicture(picture:Picture){
      this.#pictures.push(picture);

    }

  }

  const album:Album = new Album(1, 'personal pictures');
  const picture: Picture = new Picture(1, 'Platzi session', PhotoOrientation)
  album.addPicture(picture);

  console.log(album);

//Cada vez que efectuamos un cambio accesando a los atributos de mi objeto heredado
  //Estamos aplicando por debajo los metodos get cuando solo solicitamos el valor
    //Y set cuando cambiamos el valor de el atributo
  console.log(picture.id)//get id()
  picture.id = 100;  //private, set id(100)
  picture.title = 'Otro titulo'; 
  album.title = 'Personal Activities';
  console.log(album);
```