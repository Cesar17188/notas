# Cómo estructurar un componente

🆎 Atomic Design es una metodología de diseño (y una forma de modelar nuestro pensamiento) para trabajar con componentes: [¿Por qué usar Atomic Design?](https://platzi.com/blog/por-que-atomic-design/)  
.  

![Atomic Design](https://static.platzi.com/media/user_upload/0B052198-E473-4908-8866-43780AB15729-f589b505-81e5-4457-a014-793fe19ac768.jpg)

### 3.-¿Cómo estructurar un componente?

Podemos identificar componentes que tienen un mismo objetivo, entonces podemos hacer composición de componentes, en el caso del ejemplo visto en clase sería:

-   Logo: Esta construido por el logo de Platzi y el banner del logo (el que nos avisa si hay un live).
-   Navbar: cada enlace es su propio componente y además juntos forman el navbar.
-   Componente de autenticación: Engloba a los botones de iniciar plan e inicio de sesión.
-   Componente de búsqueda: Compuesto por un input y un botón diseñados especialmente para estar juntos.

Hechos estos componentes podemos llegar a lo que es el menú que es otro componente que está formado por el conjunto de todo el resto de componentes que acabamos de ver. Menú cambia, es diferente dependiendo del usuario, si es nuevo le mostramos los botones de login o suscripciones, pero si ya es un estudiante entonces debemos mostrarle los puntos, notificaciones y todo lo demás.

Al igual que con el menú los componentes internos puedan variar dependiendo de lo que necesitemos, para esto nos ayuda tratarlos como funciones a las cuales les pediremos lo que necesitamos en especial.

Podemos darle atributos a un componente usando otros componentes.

NOTA: Si se tienen muchos tipos de un solo componente es señal de desorden, hay que estandarizar las cantidades de componentes.