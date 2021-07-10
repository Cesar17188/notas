# El editor de texto moderno
Se trabaja todo el día en el editor  y al mismo tiempo se usan otras herramientas como GitHub Jira Slack email. Cambios de contexto reducen la productividad

![codestream.PNG](https://static.platzi.com/media/user_upload/codestream-5b42425e-3885-420a-a8c4-bdee1b6e16b9.jpg)

Lo que se busca al integrar las herramientas en el editor de texto es **evitar el cambio de contexto** lo que esto significa es no cambiar de ventanas, porque esto puede ocasionar una distracción ademas se busca el ** reducir pasos** para eficientar el tiempo para realizar las tareas.

Los beneficios son:

-   Ahorrar tiempo
-   Reducir Distracciones
-   Tener acceso a el código en todo momento
-   Mejorar la calidad
-   Mejorar la comunicación
-   No tener que cambiar de herramientas


Sin integración de las herramientas en el editor de código nos demoramos 20 pasos en el flujo de trabajo integrado que son:
1. Escribir código
2. Alt-tab a terminal
3. Git status
4. Verificar los cambios archivo por archivo en el editor
5. Git diff
6. Git branch -b feature/new-branch
7. Alt-tab a Chrome
8. Encontrar la lengüeta en Jira
9. Ir a la lista de issues
10. Encontrar el issue en cuestión
11. Copiar Alt-tab, back to terminal
12. Git commit -am ' commit message goes here #JIRA-TICKET'.
13. Git pull
14. Git push
15. Copiar el URL de la terminal
16. Alt-tab a Chrome. Pegar
17. Crear un título para el PR y una descripción, RETURN
18. Agregar un revisor al PR
19. Alt-tab a Slack
20. @mention al revisor para avisarle qué estás esperando.

Ademas de ineficiencia puede aparecer muchisimas distracciones

A diferencia de esto el flujo con integración solo requiere de 6 pasos que son:
1. Hacer clic en el ticket para generar una rama y empezar a trabajar
2. Escribir código
3. Realizar revisión, agragar y commit a cada archivo en el panel SCM del editor
4. Sincrinizar los cambios a GitHub
5. Hacer clic en New Pull Request (el título y descripción se crean automáticamente con referencia al ticket de Jira)
6. Agregar el revisor al PR

Ejemplo 2 Github para el revisor sin integración nos demoramos 14 pasos que son:
1. Recibir notificación
2. Clic para cargar PR en github.com
3. Examinar el reviw, darte cuenta que tiene que mirar el código en contexto para entender los cambios
4. copiar el nombre de la rama
5. Alt-tab a terminal, encontrar el directorio donde está el repositorio
6. Git fetch
7. Git checkout branch-name
8. Git pull
9. Alt-tab a tu editor, donde puedes ver el código
10. Alt-tab de vuelta a github.com, navegar a cualquier archivo en el queq uieras hacer un comentario, y agrgar el comentario
11. Seguir alternando ida y vuelta entre el editor y github.com
12. Terminar la revisión
13. Alt-tab a Slack
14. @mention al autor para avisarle que has terminado la revisión

mientras que con integración en el editor de código solo tienes 4 pasos que son:
1. Recibir notificación en el editor, click
2. Click para hacer un pull & checkout a la rama
3. Realizar la revisión de código en contecto y comentar en cualquier para que te parezca, sin restricciones
4. Terminar la revisión



