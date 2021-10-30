# Mi primer proyecto TypeScript

-   Ir al archivo tsconfig.json
-   Descomentar la linea “outDir”:"./"
-   Agregar a la linea anterior el directorio dist: `"outDir": "./dist",`
-   Compilar con `tsc`
-   Invocar al motor de Node acceder al directorio dist y al archivo para ejecutarlo: `node dist/hello.js`

Importantísimo aprender TypeScript para afrontar proyectos en Node Js, en Angular, en React.

TypeScript es un Lenguaje de Alto Nivel que al Transpilarse genera JavaScript.

Aprender Webpack es aun mejor, podemos impulsar a TypeScript mucho, incluso implementarlo con react, vue y Angular (pero este ya lo tiene 😃).

## ts-node

Si queremos ejecutar archivos de .ts sin transpilar, podemos usar una librería que se llama **ts-node**

Por ejemplo en el package.json

```
 "dev": "ts-node index.ts"
```

O directamente en consola con npx

```
npx ts-node index.ts
```

Su caso de uso común es probar que todo funcione antes de traspilar para ahorrar tiempo, un ejemplo de cuando se quiere monitorear Express usando TS

En el package.json

```
"dev": "nodemon --exec ts-node -- ./server.ts",
```