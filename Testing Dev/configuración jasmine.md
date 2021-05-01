# Configuración para ambiente de pruebas

## configuración de jasmine directa
ingresamos a 
https://jasmine.github.io/
* Get Started
* En Jasmine Standalone damos clic en more information
* Copiamos los scripts de [[jasmine]] **(puede variar con el tiempo)**
* vamos al html que carga la aplicación visual
* pegamos los scripts dentro de la etiqueta **head** antes de los scripts que controlan las funcionalidades que vamos a probar y el archivo de prueba spec
* vamos al buscador y escribimos cdn [[jasmine]] libraries
* entramos a https://cdnjs.com/libraries/jasmine
* copiamos la primera dirección -   https://cdnjs.cloudflare.com/ajax/libs/jasmine/3.7.1/jasmine.min.js
* reemplazamos la dirección de los archivos script de jasmine en el documento html por los que copiamos del cdn de[[ jasmine]] hasta su versión 
* corremos el documento

## configuración de jasmine utilizando Node.js

Se necesita abrir una consola por lo que es necesario que el proyecto tenga un package es decir que sea inicializado con un npm y disponga de estos archivos. por lo que:
1. abrimos un cdm
2. ubicamos la carpeta del proyecto
3. escribimos el comando: npm init
4. dejar todo por defecto (por el momento), es recomendable tener una cuenta de git activa y algún manejador web de versionamiento
5. dentro de la página de jasmine https://jasmine.github.io/pages/getting_started.html
6. ir a **JASMINE FOR NODE.JS**
7. seguir las instrucciones de la sección
8. instalar jasmine dentro de la carpeta
9. iniciar jasmine
10. dentro de la carpeta ir a package.json y poner dentro de la sección de script en test el nombre de **"[[jasmine]]"**
11. correr las pruebas con **npm start test** en un cmd

## Funcionalidades de Jasmine

para poder realizar pruebas con tipos de variables primitivas es decir tipo boolean, string o number es posible utilizar la funcionalidad toBe() o toEqual

$$ var(x) = false$$
$$ it('X es false', () => {$$
$$ expect(x).toBe(false);$$
$$ expect(x).toEqual(false);$$
$$});$$

mientras que si utilizamos variables tipo objeto hay que tener cuidado ya que no queremos comprobar si son el mismo objeto si no más bien si son iguales por lo que debemos realizar una busqueda a profundidad y utilizamos to equal

$$ var a = {}$$
$$ var b = {}$$
$$ it("objetos iguales", () => {$$
$$ expect(a).toEqual(b);$$
$$});$$

ejemplo de un [[set de pruebas con jasmine]]