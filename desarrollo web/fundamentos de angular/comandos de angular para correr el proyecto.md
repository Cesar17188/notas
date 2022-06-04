# Comandos de Angular para correr tu proyecto

Crear proyecto: `ng new my-project`  
Lanzar servidor de desarrollo: `ng serve`  
Lanzar servidor de desarrollo y que abra el navegador automáticamente:`ng serve -o`  
Lanzar el servidor en un puerto especifico: `ng serve -o --port=3500`

> Si lanzamos el comando `ng version` desde la carpeta del proyecto podremos obtener mayor detalle de las tecnolog[ias utilizadas.

Un comando que me ha sido útil es

```
ng serve --host 0.0.0.0
```

Debido a que me ha tocado trabajar desde máquinas virtuales.

También cuando tienes un entorno extra, a parte de dev y prod. En mi caso, tengo un entorno que llamé `stag`

```
ng serve --configuration=stag
```


ng version dentro del proyeto

Angular CLI: 12.2.7  
Node: 14.17.6  
Package Manager: npm 6.14.15  
OS: linux x64

Angular: 12.2.7  
… animations, cli, common, compiler, compiler-cli, core, forms  
… platform-browser, platform-browser-dynamic, router

### Package Version

@angular-devkit/architect 0.1202.7  
@angular-devkit/build-angular 12.2.7  
@angular-devkit/core 12.2.7  
@angular-devkit/schematics 12.2.7  
@schematics/angular 12.2.7  
rxjs 6.6.7  
typescript 4.3.5