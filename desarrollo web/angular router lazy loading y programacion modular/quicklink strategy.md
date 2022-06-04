# QuickLink Strategy
## ngx-quicklink

quicklink implementation for Angular. It provides router preloading strategy which automatically downloads the lazy-loaded modules associated with all the visible links on the screen.

esta tecnica es usada de acuerdo al uso del usuario y es usada con una API nativa del browser que es observable API, esto observa los links que estan en pantalla, si estos usuarios hacen scrolling y aparace un link que envia a un módulo ese módulo se hace precarga.

Para instalar ngx-quicklink:

```
npm i ngx-quicklink --save
```

se le ingresa al app.module.ts el modulo de quicklink y se ingresa en el preloadstrategy el quicklink strategy