# ¿Cómo contener tu aplicación en Docker?

Para contener nuestra aplicación en Docker y ejecutarla lo primero es asegurarnos que tenemos instalado Docker.

Podemos seguir las instrucciones para Windows en [https://docs.docker.com/docker-for-windows/install/](https://docs.docker.com/docker-for-windows/install/) o las instrucciones para Mac en [https://docs.docker.com/docker-for-mac/install/](https://docs.docker.com/docker-for-mac/install/).

Luego lo que debemos hacer es crear un nuevo archivo llamado `Dockerfile` y en el insertamos el siguiente contenido:

```docker
FROM node:10-alpine
WORKDIR /srv/app
COPY . .
RUN npm install
EXPOSE 3000
ENV NODE_ENV=production
CMD ["node", "index.js"]
```

Con el siguiente script creamos una imagen con nuestro de nuestro aplicativo.

`docker build -t movies-api .`

Con el siguiente script podemos ejecutar nuestra imagen en modo `detach`.

`docker run -d movies-api`

Si nos dirigimos a `http://localhost:3000` deberíamos ver nuestra API funcionando.

Si el contenedor les corre, pero no pueden acceder a la api mediante `http://localhost:3000`, deténganlo y corran el comando run de la siguiente manera:

`docker run -p 3000:3000 -d movies-api`

[Instrucciones](https://docs.docker.com/install/linux/docker-ce/ubuntu/) para la instalación de Docker en Ubuntu.