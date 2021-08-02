# Seguridad

La importancia de la seguridad dentro de nuestros proyectos es de gran relevancia como desarrolladores. Debemos garantizar que no posea ningun software malicioso y que todo este garantizado en seguridad para el equipo de trabajo. 
Con esto en mente para ganarantizar este estandar npm incluye una herramienta para revisar que paquete se esta instalando y verificar vulnerabilidades

Podemos revisar las vulnerabilidades de nuestro proyecto con:  
**npm audit**  
En caso de tener vulverabilidades, se recomienda usar el comando:  
**npm audit fix**  
Y en caso de que esto no lo solucione, podemos ir actualizandolos de uno en uno.

-   `npm audit` para ver las vulnerabilidades que tenemos en nuestro proyecto
-   `npm audit --json` nos genera un json con información un poco mas detallada de lo que esta pasando con estos paquetes que instalamos
-   una ves sepamos cual es la vulnerabilidad podemos proceder a actualizar cualquiera de los paquetes ejem: `npm update eslint-utils --depth 2` esto para instalar todas sus dependencias
-   `nom audit fix` es para solucionar las vulnerabilidades que tengamos en nuestro proyecto básicamente, actualiza a la ultima version nuestros paquetes con las dependencias que requieren, después de esto volvemos a correr `npm audit` para ver que ya no tenemos vulnerabilidades.
-   también hay una herramienta que garantiza que estemos siempre actualizados con nuestras dependencias del proyecto y es `snyk.io`