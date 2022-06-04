# Técnicas de alineamiento antes de CSS Grid: margin y line-height

El colapso de márgenes solo sucede con los márgenes de `top` y de `bottom`, y esto solo sucede cuando dos márgenes verticales se tocan, aún no comprendo bien el concepto, pero po si a alguien le sirve, aAquí está una explicación más detallada sobre el margin collapse 🤔:  
.  
[Entendiendo el colapso de margen](https://developer.mozilla.org/es/docs/Web/CSS/CSS_Modelo_Caja/Mastering_margin_collapsing)  
[El caso del colapso de márgenes en CSS](https://cybmeta.com/colapso-de-margenes-en-css)  
.  
En cuanto a la clase, una de las desventajas de usar este tipo de alienación es que necesitamos ser exactos con las medidas (px), por lo que si queremos trabajar con responsive o medidas relativas… buena suerte 😦  
.  
Por cierto, teff te manda a buscar un concepto que no conoces, mi cara al leer sobre ese concepto y nop entenderlo a la primera 😂👇:  
.  

![unu.png](https://static.platzi.com/media/user_upload/unu-ca511b1a-ef82-4bc7-a8b0-282337f77ddc.jpg)


**Margin Collapse**  
El colapso de márgenes ocurre cuando el margen top y bottom de 2 elementos colindan y el margen final es el que sea mayor. Es decir, si un elemento tiene `margin-bottom: 20px` y el otro elemento `margin-top: 10px`, el margen final entre ambos elementos no será de 30px, si no que será de solo 20px.  
Cabe aclarar que esto ocurre cuando usamos el `display` por defecto `block`.