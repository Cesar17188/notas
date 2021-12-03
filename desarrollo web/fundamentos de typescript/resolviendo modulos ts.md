# Resolviendo módulos

Resolviendo Modulos: Typescript resuelve la ubicacion de modulos observando referencias relativas y no relativas.  
Posteriormente intenta localizar el modulo usando una estrategia de resolucion de modulos.

```
tsc --moduleResolution node
tsc --moduleResolution classic
```

diferencias  
node: Modulos CommonJs o UMD, mas opciones de configuración  
classic: Modulos AMD, System, ES2015, poco configurable

en tsconfig.json

```
"moduleResolution": "node|classic"
"traceResolution":true
```

existen los path alias para que no tengamos que lidiar con esa mano de puntos y slash en nuestros proyectos.  
Esta configuración la pueden poner en el ts.config.json dentro de compilerOptions y así pueden acceder al shortcut @item para llegar a esa carpeta en específico que están buscando.  
Para el ejemplo yo tengo una carpeta item y dentro el archivo index.ts.

```
"paths": { 
      "@item": ["item/index.ts"],
    }

```

y así se podría importar

```
import { Item }  from  '@item'
```