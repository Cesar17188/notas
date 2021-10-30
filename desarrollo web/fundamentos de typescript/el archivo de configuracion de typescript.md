# El archivo de configuración de TypeScript

## Configurar Typescript

`tsconfig.json`

-   Especifica la raiz de un proyecto TS
-   Permite configurar opciones para el compilador

Para crear este archivo en cualquier proyecto:

```bash
tsc --init
```

El archivo base es este:

```json
{
	"extends": "./config/base"
	"compilerOptions":{
		"target": "es6",
		"module": "commonjs"
		"strict": true,
		"removeComments": true
	},
	"include":[
		"src/**/*.ts"
	],
	"exclude": [
		"node_modules",
		"**/*.test.ts"
	]
}
```

Una vez que este archivo es generado, ejecutamos:

```json
tsc // Busa la configuracion dentro del proyecto
tsc --project platzi // Especifica el directorio donde esta la configuracion
tsc file.ts // Omite la configuracion
```

Para ver todas las configuraciones que podemos hacer:

[TSConfig Reference - Docs on every TSConfig option](https://www.typescriptlang.org/tsconfig)

Para ver todas las configuraciónes que tiene el compilador recomiendo ampliamente que revise la documentación donde detallan para qué sirve cada cosa, sera un buen complemento para el curso.

[https://www.typescriptlang.org/tsconfig](https://www.typescriptlang.org/tsconfig)