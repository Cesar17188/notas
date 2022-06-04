# Agilidad y consistencia a través de componentes

## ¿Qué es un componente?

Son elementos reutilizables que ayudan a:
* Lograr mayor consistencia
* Optimizar velocidad en los cambios

## Crear componentes
-> Pueden crearse a partir de:
* Frames
* Grupos
* Capas

-> (shift K)

## Cómo crear una instancia
* Option + Arrastrar componente
* ctrl c + ctrl v
* Drag desde vista de "Assets"

## Relación Padre-Hijo
* Propiedades del master component se traducen en todas las isntancias
* Cambios sobre las instancias se llaman "overrides" y existen para:
	* Texto
	* Fill
	* Stroke
	* Efectos

## No se pueden cambiar
* Tamaño
* Posición
* Rotación
* Constraints
* Jerarquía de Capas

## Pero las instancias pueden rebelarse
* (ctrl + Option + B) para separar una instancia de su maestro
* Click derecho y "Reset Instance" para cancelar todos los overrides que tiene una instancia y revertir al maestro

## Un componente no se puede convertir en un objeto
* Para "desapegar" los elementos de un componente maestro a un layer normal:
	* Crear una instancia
	* hacer detach de la instancia
	* Borrar al maestro