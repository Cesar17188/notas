# Instalación de Ionic y templates básicos
A partir de la versión 5 de ionic se utilizan los siguientes comandos:

```
$ npm install -g @ionic/cli.
$ npm uninstall -g ionic $ npm install -g @ionic/cli.
$ ionic start myApp tabs.
$ cd myApp $ ionic serve.
```

![[Pasted image 20220322203354.png]]

## IONIC 6

Voy a tomar el curso, pero haciéndolo en IONIC 6 y voy a ir dejando mis recomendaciones.

```
node -v
v16.13.0
.
npm -v
8.2.0
.
npm install -g @ionic/cli
.
ionic
CLI 6.18.1
.
ionic start platzi-music blank --type=angular
```

## templates basicos

-   `tabs`: A tabs based layout
-   `sidemenu`: A sidemenu based layout
-   `blank`: An empty project with a single page

para poder verlos

```
ionic start --list
```