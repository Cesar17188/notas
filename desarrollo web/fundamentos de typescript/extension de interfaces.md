# Extensión de interfaces

Extendiendo Interfaces. Las interfaces pueden extenderse unas de otras. Esto permite copiar los miembros ya definidos en una interfaz a otra, ganando flexibilidad y reusabilidad de componentes.  
Utilizamos la palabra reservada extends para utilizar herencia.

```
interface Person {
name:string;
lastname:string;
}
interface Student extends Person {
person:Person
}
```

La herencia es un mecanismo para poder reutilzar código dentro de la programación orientada a objetos. TS provee esto con las interfaces. Las interfaces pueden extenderse de otras. Esto permite copiar los miembros ya definidos en una interfaz a otra, ganando flexibilidad y reusabilidad de componentes.

```typescript
export {}

enum PhotoOrientation{
  Landscape,
  Portrait,
  Square,
  Panorama
}

//*Herencia de interfaces

interface Entity {
  id: number,
  title: string,
}

interface Album  extends Entity{
  //*Copia de los atributos de Entity
  description: string
}

interface Picture extends Entity {
  orientation: PhotoOrientation
}

const album: Album = {
  id: 5,
  title: 'Meetups',
  description: 'Community events around the world'
}

const picture: Picture = {
  id: 10,
  title: 'Family',
  orientation: PhotoOrientation.Square
}

let newPicture = {} as Picture
newPicture.id = 2
newPicture.title = 'Moon'

console.table({album})
console.table({picture})
console.table({newPicture})
```