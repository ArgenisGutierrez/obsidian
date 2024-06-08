>[!summary] Resumen.
>Los objetos son arreglos asociativos con varias características especiales:
>- Almacenas propiedades pares de clave-valor.
>	- Las claves pueden ser cadenas o símbolos.
>	- Los valores pueden ser de cualquier tipo.
>- Para acceder a propiedades se hace uso de:
>	- Notacion con punto _obj.propiedad_.
>	- Notacion de conchetes *obj\["propiedad"\]* principalmente se usada cuando la clave son palabras separadas por espacios.
>- Operadores especiales:
>	- Eliminar una propiedad _delete obj.propiedad_.
>	- Comprobar si exite una propiedad _"key" in obj_.
>	- Para iterar sobre un objeto se usa _for in_.

>[!example] Ejemplo.
```javascript
let persona = {
	nombre: "Arfhel",
	edad: 29,
}
console.log(persona.nombre) --> Arfhel
```

[regresar](Javascript)