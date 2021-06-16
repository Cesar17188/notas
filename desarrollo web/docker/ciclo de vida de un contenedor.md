# Ciclo de vida de un contenedor

![Ciclo de vida del contenedor docker | Código Electrónica](https://lh3.googleusercontent.com/proxy/SpTOC8aBKBhdAf7P51Xv1_MY3tv5leN7ekn80zKG9rtWkGj7DPSKeYH4fkCwOP-hCe0IOOVlOry9Aq-ZmDvPMWIRl4nPROv85EMnzN4xLrlW9A_cuyzTSRpo0pRcNSBgAHDLsjxJbZcUAI_PcsrGv0zyvCvsCw)

Cada vez que un contendor se ejecuta, en realidad lo que ejecuta es un proceso del sistema operativo. Este proceso se le conoce como **Main process**.

**Main process**  
Determina la vida del contenedor, un contendor corre siempre y cuando su proceso principal este corriendo.

**Sub process**  
Un contenedor puede tener o lanzar procesos alternos al main process, si estos fallan el contenedor va a seguir encedido a menos que falle el main.

**Ejemplos manejados en el video**

-   Batch como Main process
-   Agujero negro (/dev/null) como Main process

```
docker run --name alwaysup -d ubuntu tail -f /dev/null 
```

\_el ouput que te regresa es el ID del contentedor \_

Te puedes conectar al contenedor y hacer cosas dentro del él con el siguiente comando (sub proceso)

```
docker exec -it alwaysup bash
```

Se puede matar un Main process desde afuera del contenedor, esto se logra conociendo el id del proceso principal del contenedor que se tiene en la maquina. Para saberlo se ejecuta los siguientes comandos;

```
docker inspect --format '{{.State.Pid}}' alwaysup

```

\_El output del comando es el process ID (2474) \_

Para matar el proceso principal del contenedor desde afuera se ejecuta el siguiente comando (solo funciona en linux)

```
Kill  2474
```

Para detener el contenedor en windows o max el comando es

```
docker stop <nombre del contenedor>
```
