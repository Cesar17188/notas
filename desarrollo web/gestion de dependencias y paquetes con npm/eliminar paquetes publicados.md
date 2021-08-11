# Eliminar paquetes publicados

1 . Si quieres eliminar el paquete o versión publicada para los paquetes recién creados, siempre que ningún otro paquete en el Registro público de npm dependa de su paquete, puede anular la publicación en cualquier momento dentro de las primeras 72 horas después de la publicación, a menos que usted sea el único propietario del módulo con:

```
npm unpublish <package_name> --force
```

y si se quiere anular la publicación de una versión en específico:

```
npm unpublish <package_name>@<version>
```

2 . Para paquetes que tienen publicados más de 72 horas, independientemente de cuánto tiempo hace que se publicó un paquete, puede anular la publicación de un paquete que cumpla con lo siguiente:

-   ningún otro paquete en el Registro Público de npm depende de otro
-   tuvo menos de 300 descargas durante la última semana
-   tiene un solo propietario / mantenedor  
    npm tiene detalles de la política para anular la publicación de paquetes, más detalles aquí: [npm Unpublish Policy 😉](https://www.npmjs.com/policies/unpublish)