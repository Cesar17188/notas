# Utilizando inmutabilidad en nuestras funciones

Otra característica de las funciones puras es la inmutabilidad. Si necesitamos modificar el valor de los parámetros que reciben nuestras funciones, debemos copiar el valor de los argumentos y modificar estas nuevas variables, así evitamos modificar innecesariamente variables con las que nuestras funciones puras no tienen nada que ver.

Ejemplo:

```js
// Con mutaciones
const addToList = (list, item, quantity) => {
	list.push({ // modificamos el argumento `list`
		item,
		quantity
	})
	return list
}

//  Sin mutaciones (inmutabilidad)
const addToList = (list, item, quantity) => {
	const newList = JSON.parse(JSON.stringify(list))
	newList.push({ // modificamos la copia del argumento
		item,
		quantity
	})

	return newList
}
```

La _inmutabilidad_ en las propiedades o atributos de un objeto es fundamental para poder predecir su comportamiento o valor (estado) en el futuro. Al crear nuevos objetos cambiados (mutados), sin alterar el objeto original, nos aseguramos de estar siendo muy explícitos al hacer modificaciones, reduciendo el riesgo de cambios indeseados o hechos por simple descuido o desconocimiento. Esta característica es especialmente útil en todo lo relacionado a las pruebas de software o _testings_.