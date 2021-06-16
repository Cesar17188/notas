# Virtualización

A diferencia de una máquina virtual, que es una abstracción del hardware y emula toda una computadora (o servidor), un contenedor es una abstracción del software y éste puede empaquetar el código, el runtime necesario y las dependencias de una aplicación

**Virtualizacion**  
Permite atacar en simultáneo los tres problemas del desarrollo de software profesional.

**Problemas de la virtualizacion**

-   PESO: En el orden de los GBs. Repiten archivos en común. Inicio lento.
-   COSTO DE ADMINISTRACION: Necesita mantenimiento igual que cualquier otra computadora.
-   MULTIPLES DE FORMATO: VDI, VMDK, VHD, raw, etc

**Containerización**  
El empleo de contenedores para construir y desplegar software.

-   Flexibles: sim importar la aplicación se puede meter en el contenedor
-   Livianos: Reutilizan el kernel del SO entre todas las aplicaciones
-   Portables: estan diseñados para correr de la misma manera en cualquier máquina
-   Bajo acoplamiento: Son autocontenidos, el contenedor tiene todo lo que necesite para correr la aplicación dentro del mismo
-   Escalables: Es muy facil agarrar en contenedor y crear muchos contenedores iguales para tener mucho más usuarios
-   Seguros: Las herramientas se aseguran que la aplicación solo pueda acceder a las demas herramientas del mismo cotenedor

**Virtualizacion vs Containerización**

-   Virtualización: A diferencia de un contenedor, las máquinas virtuales ejecutan un sistema operativo completo, incluido su propio kernel.
-   Containerización: Un contenedor es un silo aislado y ligero para ejecutar una aplicación en el sistema operativo host. Los contenedores se basan en el kernel del sistema operativo host (que puede considerarse la fontanería del sistema operativo), y solo puede contener aplicaciones y algunas API ligeras del sistema operativo y servicios que se ejecutan en modo de usuario.

![](https://www.redeszone.net/app/uploads/2016/02/docker-vs-virtual-machines.png)