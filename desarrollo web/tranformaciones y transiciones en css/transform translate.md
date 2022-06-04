# Transform translate

Básicamente `translate()` te permite mover un elemento en el eje X o Y… ¡O ambos! 👀, básicamente este ejemplo que ya había puesto en una clase anterior, vas de un punto A a un punto B:

![animation](https://media.giphy.com/media/gCSOFQybTbM3pome6c/giphy.gif)

Ahora, ¡la propiedad transform usos muy interesantes! Un uso que a mí me encantó mucho cuando lo conocí es la posibilidad de poder centrar elementos, tanto verticalmente como horizontalmente, por ejemplo, suponiendo que tenemos un elemento padre con `position: relative;` y un elemento hijo con `position: absolute`…

![transform.png](https://static.platzi.com/media/user_upload/transform-04326ea9-9395-4220-8913-e80a912fee8b.jpg)

¡Podemos centrarlo usando `transform` y las propiedades `top` y `left`! ¿Cómo? Simplemente hay que decirle al elemento hijo que se muevan 50% en su `top` y su `left`:

![center-not.centered.png](https://static.platzi.com/media/user_upload/center-not.centered-222d8f24-03c6-4abe-9d6d-73ef7dfe4f4e.jpg)

🤔 Pero esto no está centrado… Aquí es donde podemos usar `transform` 😉 Simplemente le decimos que tanto en X como en Y se mueva `-50%`, es decir, que retroceda el 50% **de sí mismo**, de esa forma quedará totalmente centrado 😄

![centered.png](https://static.platzi.com/media/user_upload/centered-810822aa-bf74-47b9-bc32-5414b06f65b2.jpg)

De esa forma siempre se mantendrá centrado el elemento, esta forma de centrar me encanta cuando trabajamos con elementos posicionados absolutamente 😉.