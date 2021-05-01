# Testing del lado del servidor

## Configuración de un proyecto JavaScript utilizando npm [[jasmine]]

Pasos previos a las [[pruebas en el servidor]]

* Con el proyecto creado y el servidor montado lo primero es actualizar las dependencias y paquetes con el código $npm install$.
* Luego verificar si no existen errores de versionamiento, de existir es necesario instalar las versiones necesarias como por ejemplo en el caso de typscript utilizariamos el código $npm install typescript@"4.0.2" --legacy-peer-deps$. Utilizar este código para cualquier versionamiento
* En el $package.json$ verificar todas las veriones de dependencias en especial la de jasmine en las dependencias de desarrollo $devDependencies$. e instalar jasmine con $npm install jasmine --save-dev$.
* inicializamos jasmine con el código $node ./node_modules/jasmine/bin/jasmine.js init$
* Esto creara la carpeta spec y dentro de ella la carpeta support donde estara el archivo $jasmine.json$ entramos en el archivo $jasmine.json$ y escribimos el código dentro de *"spec_dir"*

	$$"spec_dir": "spec":
	"spec_files": [
	"../server/**/*[sS]pec.js",
	"**/*[sS]pec.js"
	],$$ 
* Dentro de la carpeta $server$ creamos un archivo $server.spec.js$ y escribimos el código de la prueba que va a aparecer
$$it("funciona", () => 
{expect(true).toBeTruthy();});$$

* Para correr la prueba escribir el código $node ./node_modules/jasmine/bin/jasmine.js$
* Se puede escribir este código dentro del archivo $package.json$ en la sección de scrips de la siguiente manera

$"test:server": "node ./node_modules/jasmine/bin/jasmine.js",$
* con el codigo en el $package.json$ se puede correr el siguiente código con el mismo resultado $npm run test:server$

## Agregar plugin a jasmine

* Dentro de la carpeta spec creamos un nuevo archivo con el nombre de $specs.js$
* dentro de este archivo creamos una nueva instancias de jasmine

$$const Jasmine = require("jasmine");

const JasmineConsoleReporter = require("jasmine-console-reporter");

  

const jasmine = new Jasmine();

jasmine.loadConfigFile("spec/support/jasmine.json");


const jasmineConsoleReporter = new JasmineConsoleReporter({

 colors: 1, // (0|false)|(1|true)|2

 cleanStack: 1, // (0|false)|(1|true)|2|3

 verbosity: 4, // (0|false)|1|2|(3|true)|4|Object

 listStyle: "indent", // "flat"|"indent"

 timeUnit: "ms", // "ms"|"ns"|"s"

 timeThreshold: { ok: 500, warn: 1000, ouch: 3000 }, // Object|Number

 activity: false, // boolean or string ("dots"|"star"|"flip"|"bouncingBar"|...)

 emoji: true,

 beep: true,

});

  

jasmine.addReporter(jasmineConsoleReporter);

jasmine.execute();$$

* Buscamos en google $jasmine console reporter$ y escojemos el archivo con instalador npm
* instalamos $jasmine console reporter$ siguiendo la guía de instalación y tomando en cuenta la versión necesaria de jasmine.
* En el package.json incluimos una nueva sección debajo de los test
	$"test:server:coverage": "nyc node spec/specs.js",$
	
## Instalación del sistema de cobertura 

* buscamos una libreria para visualizar que tanto hemos ejecutado las lineas de código y es $instanbul.js$ 
* Ademas con $instanbul.js$ vamos a tener una tabla que se mostrara en el cmd y un reporte en html
* seguimos los pasos de instalación de $istanbul.js$ y cambiamos el archivo creado en el spec