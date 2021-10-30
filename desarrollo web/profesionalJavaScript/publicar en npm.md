# Publicar en npm
[[crear un paquete para npm]] [[publicar un paquete en npm]]
## Publicar en NPM

## Paso 1: npm actualizado

Tener npm instalado y actualizado en tu sistema. Si no está actualizado ejecuta:

```bash
npm install npm@latest -g

```

Fuente: [https://docs.npmjs.com/getting-started/installing-node](https://docs.npmjs.com/getting-started/installing-node)

## Paso 2: github

Tener tu proyecto en Github. No obligatorio pero recomendable. Recuerda que solo puedes publicar gratis paquetes públicos. Para paquetes privados deberás sacar la tarjeta de crédito.

## Paso 3: package.json

Tu proyecto debe tener un archivo `package.json` en el directorio raíz. Si no lo tuviera, ejecuta `npm init` desde la consola y sigue los pasos.

## Paso 4: tu cuenta en [npmjs.com](https://npmjs.com/)

Ve a [npmjs.com](https://www.npmjs.com/) y crea una cuenta. Una vez creada tu cuenta no encontrarás ningún botón de subir proyecto, así que no pierdas tiempo buscándolo (como yo).

## Paso 5: publicar el proyecto

Ahora que tienes tu cuenta, ve a tu proyecto en local con la terminal y ejecuta:

```bash
npm login
// ingresa tus datos de usuario y contraseña de npmjs.com

```

Una vez que has iniciado sesión es tan simple como ejecutar:

```bash
npm publish
```