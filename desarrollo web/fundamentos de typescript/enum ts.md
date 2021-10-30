# Enum
-   Los enumerados permiten definir un conjunto de **constantes con nombre**
-   Tienen la ventaja de adapartse al contexto de la aplicación

[Documentación oficial de enums en TS](https://www.typescriptlang.org/docs/handbook/enums.html)

```typescript
//* Orientación para fotografías
/* const landscape = 0
const portrait = 1
const square = 2
const panorama = 3 */

//*Una forma más inteligente de declarar constantes
enum PhotoOrientation {
  Landscape = 'cero', //* Podemos asignar un valor en particular
  Portrait = 1, //* 1
  Square = 2, //* 2
  Panorama = 3 //* 3
}

const landscape: PhotoOrientation = PhotoOrientation.Landscape
const square: PhotoOrientation = PhotoOrientation.Square

console.log('landscape: ', landscape) //* Accede al valor
console.log('Square: ', PhotoOrientation[square]) //* Accede al nombre

//*Siempre tenemos valores consecutivos que incrementan de 1 en 1
enum PictureOrientation {
  Landscape = 10,
  Portrait, //* 11
  Square, //* 12
  Panorama,// *13
}

console.log('Portrait: ', PictureOrientation.Portrait) //* valor 11

//* Es la misma lógica que: { key, value }
enum Country {
  Bolivia = 'BOL',
  Colombia = 'COL',
  Mexico = 'MEX',
  EEUU = 'USA',
  Espana = 'ESP'
}

const mexico:Country = Country.Mexico
console.log('México: ', mexico)

//! Country.Mexico = 'MX' //!Esto da un error, no podemos modificar su valor
```