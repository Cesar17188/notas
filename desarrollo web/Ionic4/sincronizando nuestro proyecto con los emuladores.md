# Sincronizando nuestro proyecto con los emuladores

Es recomendable trabajar en dos terminales distintas, es una vamos a mantener el servidor de ionic funcionando

```
ionic serve
```

en otra terminal vamos a tener sincrinzada la aplicacion con los emuladores nativos.
Primero debemos ingresar todos los cambios en la carpeta www para lo cual corremos el código

```
ionic build
```

Para sincronizar con las plaformas de andriod o ios se debe correr el código
```
npx cap sync
```
esto va a copiar los archivos de la carpeta www y llevarlos a los emuladores para que despues los podamos utilizar.

Una vez que esto termine hay que darle play en el botón de las respectivas plataformas android studio o xcode

Adicionalmente hay otros comandos para emparejar las plataformas andriod y iod con el proyecto web

```
npx cap copy
```
si solo se modífica el html, css y js se puede utilizar este comando para no tocar ninguna otra dependencia nativa  y es mucho más rápido que el sync o el update



-   **ionic build**: _compilia y pone todo el código a la carpeta www_
-   **npx cap sync**: _copia e instala todo lo de www al android studio o emuladores_
-   **npx cap update**:_ realiza lo mismo q sync_
-   **npx cap copy**:_ si solo modificas html, css y js  
    _  
    Orden:

1.  ionic build
2.  npx cap sync | npx cap copy
3.  npx cap open ios | npx cap open android
4.  Play en tu editor