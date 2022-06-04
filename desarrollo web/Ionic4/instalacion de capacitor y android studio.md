# Instalación de Capacitor y uso en Android Studio

Cuando se inicia un nuevo proyecto en Ionic actualmente capacitor viene instalado por defecto por lo que solo se debe construir el proyecto con el comando

```
ionic build --prod
```
En mi caso ionic me pidio que instalara capacitor para android con el código

```
npm install @capacitor/android
```

posteriormente a esto se corre el comando 

```
npx cad add android 
```

y finalmente se abre el proyecto en android studio con

```
npx cap open android
```
Comandos utilizado en la clase:

```
-- npm install --save @capacitor/core @capacitor/cli --save-exact
-- npx cap init => lo agrega al proyecto
-- ionic build => genera carpeta www
-- npx cap add android => agrega android al proyecto
-- npx cap open android => abre android studio
```

[https://capacitor.ionicframework.com/docs/getting-started/](https://capacitor.ionicframework.com/docs/getting-started/)

Instalación npm install --save @capacitor/core @capacitor/cli  
Agregar al proyecto npx cap init  

![AddCapacitor.PNG](https://static.platzi.com/media/user_upload/AddCapacitor-bc221e55-1add-4373-bbb8-07642a71bf72.jpg)

Si al igual que a mi, Android Studio para Windows les indica un error en la sincronización y no aparece activo el botón de play, verifiquen el mensaje del error que sugiere la instalación de los SDK faltantes. Presionen el link para iniciar el instalador y al finalizar presionen el botón ‘Sync project with gradle files’ para volver a sincronizar. Con eso deberán poder correr la app.