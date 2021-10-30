# Funciones en TypeScript

-   Los parámetros en las funciones son tipados
-   Se pueden definir parámetros opcionales
-   El tipo de retorno puede ser un tipo básico, enum, alias, tipo literal o una combinación de ellos

```typescript
//*Crear una fotografía
//*Usando TS, definimos tipos para parámetros

type SquareSize = '100x100' | '500x500' | '1000x1000'

function createPicture(title:string, date:string, size: SquareSize) {
  //*Se crea la fotografía
  console.log('Create picture using: ', title, date, size)
}

createPicture('My picture', '2021/10/22', '1000x1000')
//!createPicture('Disney Vacation', '2018-03-12') //!Esto da un error porque necesita 3 parámetros

//*Parámetros opcionales
//*Solo hace falta escribir '?' al lado del parámetro
function createPhoto(title:string, date:string, size?: SquareSize) {
  //*Se crea la fotografía
  console.log('Create photo using: ', title, date, size)
}

createPhoto('Foto1', '2020-10-10') //! El tercer parámetro es undefined


//* Flat array function
let createPic = (title:string, date:string, size:SquareSize):object => {
  return { title, date, size }
}

const picture = createPic('Platzi session', '2020-03-10', '100x100')
console.log('Picture: ', picture)
```