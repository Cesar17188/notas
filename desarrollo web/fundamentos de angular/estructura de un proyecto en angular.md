# Estructura de un proyecto en Angular

— src  
Aqui se encuentra el corazón del proyecto, están los componentes, htm, css, etc.

— .browserslistrc  
Indica a angular en que versiones de navegadores tiene que ser compatible tu aplicación.

— .editorconfig  
Tiene que ver con el trabajo en el equipo, ver el mismo espacio de identación, etc.  
Para que este archivo funcione se debe tener un plugin en el VSCode: EditorConfig for VS Code

— tsconfig.json  
Tiene que ver con la configuración de angular con tipescript.  
Este archivo nos dice como va a compilar, hacia donde va a transpilar los archivos, que versión vamos a utilizar de JavaScript, ver algunos compiladores de angular.

— angular.json  
Aqui podemos manejar diferentes ambientes, como por ejemplo para realizar pruebas(tester), también para algunas configuraciones de compilación de angular.

— karma.conf.js  
Configuración para correr pruebas unitarias.

---

— .nvmrc  
Este archivo debemos agregarlo, indica cual es la versión de node recomendada para correr el proyecto.

---

PLUGIN+:  
-> Angular Language Service  
-> Ayuda que la experiencia con angular sea increible.


Si tienes diferentes versiones de node y además tienes el nvm (node version manager)  
puedes creas el fichero  
.nvmrc  
donde podrás indicar la versión recomendada de node para correr este proyecto.

Para ver que versión tienes en la consola pones

```
node -v
```

y copias y pegas este valor en el fichero, en mi caso es v14.17.6