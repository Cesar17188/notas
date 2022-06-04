# Qué es el Modelo Cliente/Servidor
Las tecnologías utilizadas en aplicaciones web son:

**Bases de datos**, MySQL es una base de datos relacionales y MongoDB es una base de datos no relacional

**Backend**, existen muchos lenguajes que puedes usar cómo Python, Ruby, JavaScript

**Servidores**, existen tecnologías como NGINX, Apache, Node

**Frontend**, son las tecnologías que corren en el navegador, HTML, CSS y JavaScript

A un grupo de tecnologías se les conoce como Stack

Recuerda:

-   Si tuvieras un código en el Frontend que se conectara a una base de datos, esta seria visible para todos.


![[Pasted image 20220206130251.png]]
![[Pasted image 20220206130300.png]]
**El proceso de un modelo Cliente/Servidor es así:**

-   **Cliente (Navegador que lee HTML, CSS y JS)** [[curso definitivo dobre html y css]]
-   Se envía una solicitud al **Backend (Python, Go, Node, Java, etc.)** a través de una URI
-   El Backend recibe la solicitud y toma decisiones en base a ella
-   El Backend consulta la **Base de Datos (MySQL, Oracle, MongoDB, etc.)** en caso de ser necesario
-   El Backend devuelve una respuesta que el navegador pueda leer, muchas veces datos en **formato JSON**
-   El Cliente recibe los datos JSON y los parsea para mostrarlos en **HTML, información presentada muy linda**