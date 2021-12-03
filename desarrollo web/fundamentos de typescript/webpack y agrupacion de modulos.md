# Webpack y agrupación de Módulos

Es un empaquetador de módulos para aplicaciones web. se añade el package.json con: npm init -y  
Js super optimizado para la producción.

```npm
npm install typescript webpack webpack-cli --save-dev
```

![[Pasted image 20211101202423.png]]

-   [Curso de Webpack](https://platzi.com/clases/webpack/)
-   [Curso Práctico de Webpack](https://platzi.com/clases/webpack-practico/)


```ts
module.exports = {
	mode: 'production', 
	entry: './src/main.ts', 
	devtool: 'incline-source-map', 
	resolve: { extensions: ['.ts', '.js'], 
	}, 
	output: { 
	filename: 'bundle.js', 
	} 
}```