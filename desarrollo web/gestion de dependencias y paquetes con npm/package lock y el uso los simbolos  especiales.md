# Package lock y el uso los símbolos ^ y ~

Una de las cosas que se pueden notar en las dependencias es el ${$


En esta imagen esta la forma de manejar versionado
![[Pasted image 20210801174503.png]]

el primero siempre va a hacer un cambio mayor es decir la version 1, la version 2, la version 3...
Despues vamos a tener cambios menores, es decir cambios que no son tan grandes como para decir que esto es una versión nueva
Despues tenemos parches, bug fixing o cambios menores que se han realizado

Dentro del package.json, si mantenemos el $caret(^)$ y la $tilde(~)$ garantizaremos que cuando se haga un cambio solo se cambien estas dos zonas y mantengamos la versión grande de trabajo

partiendo de esto varias veces nos queremos quedar en cierta versión de una dependencia, para nosotros controlar el avance del proyecto. Por lo que se recomienda eliminar el $^$ de el número de la versión de la dependencia ya que asi garantizaremos trabajar con una sola versión.


a partir de la versión 5 de npm, se creara una archivo que se llama package-lock.json, que nos permite tener ciertas configuraciones, que nos van a permitir a nosotros entender que esta sucediendo a lo largo de la construcción de este proyecto, que versiones hemos instalado, que paquetes y que dependencias se encuentran aqui. Esto nos permite tener un versionado un poco más establecido de lo que esta sucediendo. Vamos a poder compartir este documento con todos los demas desarrolladores y garantizar que las versiones que se están instalando sean las correctas