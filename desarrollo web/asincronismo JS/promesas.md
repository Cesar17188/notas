# Promesas
[[arrow functions, promesas y parámetros]]

Mes estaba preguntando por que somethingWillHappend lo declaraba como función y retornaba la promesa en lugar de declarar de una vez la promesa en la variable. Pues probando me di cuenta que para encapsular la promesa y que no se ejecute hasta que se llame a la función ya que si se declara la promesa directamente en la variable la promesa se ejecutara al cargar la variable.

```js
/**
 * Aqui la promesa se ejecuta al cargar el archivo
*/
const somethingWillHapped = new Promise( (resolve, reject) => {
    if (true) {
        console.log('Hey dude!');
        resolve('Hey!');
    } else {
        reject('Whoops!');
    }
});

/**
 *Aqui la promesa no se ejecuta hasta que se llame a la funcion
*/
const somethingWillHapped = () => {
    return new Promise( (resolve, reject) => {
        if (true) {
            console.log('Hey dude!');
            resolve('Hey!');
        } else {
            reject('Whoops!');
        }
    });
}
```