# Herencia

Herencia y sus valores:  
**Inherit**. Este es un valor por medio de una _keyword_ que especifica que, a la propiedad que se la apliquemos debe de heredar los valores de su elemento padre. Podemos decir que la palabra **Inherit** significa “_Usa el valor de mi padre_”, si el elemento padre no tiene definido dicho valor el navegador seguirá el DOM hasta que encuentre un elemento superior que lo contenga, y en ultima instancia de no tenerlo ningún elemento superior se aplicara el valor por defecto.

**Initial**. Este valor pertenece a la especificación CSS3 y cuando aplicamos a una propiedad el valor _initial_ estamos dando el valor inicial y predefinido por el navegador en cuestión.

**Upset**. Este valor _unset_ es una combinación entre _inherit_ y _initial_, cuando utilizamos este valor en una propiedad esta tratara de heredar el valor de su elemento padre si este esta disponible, de no ser así este valor colocará el valor de la propiedad en su valor inicial, como si usáramos _inherit_ e _initial_ juntos.  

![](https://www.w3.org/wiki/images/2/2f/Inheritance.png)

![[Pasted image 20211130144409.png]]

•inherit: ya sabemos  
•initial: fuerza a no aplicar la herencia, lo contrario a inherit, es parte de especificidad, un tema que veremos adelante.  
•Unset: Es como un inherit flojo, ya que inherit inspecciona hasta encontrar un padre con un estilo, unset solo inspecciona el padre próximo, si encuentra estilo lo hereda, si no lo hay se resetea al su valor natural.  
• Revert: Pone su valor a la capa de estilo por defecto del navegador.

_SI cometí un error, diganlo, si lo explique bien denme ese corazón_