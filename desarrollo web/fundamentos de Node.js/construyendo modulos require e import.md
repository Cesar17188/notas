# Construyendo módulos: Require e Import

En Node tenemos una forma de importar módulos la cual es con el método require, el cual es la forma por defecto de importar módulos, ya sean nuestros propios módulos como los de otras personas en nuestros proyectos JS, pero suele haber mucha confusión debido al import.  
Import es la forma de importar módulos en Ecmascript, el cual es un estándar de JavaScript para la web, esta forma de importar en teoría Node no la acepta oficialmente, a no ser que usemos su modo de .mjs.  
Pero gracias a compiladores como Babel, nosotros podremos utilizar estas normas de Ecmascript en nuestro código para cuando se ejecute se transforme en código que sea aceptable por Node.  
Se recomienda en la mayoría de veces la importación con require.

Node ya soporta los módulos de la sintáxis ES6 solo hay que agregar esta linea en el package.json  
"type": “module”,  
quedaria algo asi el archivo

```
  "name": "fundamentosnodejs",
  "version": "1.0.0",
  "description": "una descripción",
  "main": "index.js",
  "type": "module",
```

y con esto ya se podrá trabajar con los archivos en extencion .js en lugar de .mjs