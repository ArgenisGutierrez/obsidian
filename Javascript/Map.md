>[!summary] Resumen.
>Los map son en esencia iguales a los objetos pero con la diferencia que map permite que sus claves sean de cualquier tipo y no solo strings y simbolos.
>Sus metodo y propiedades son:
>- _new Map()_ Crea el map.
>- _map.set(calve,valor)_ Almacena el valor.
>- _map.get(clave)_ Devuelve el valor de la clave y false si no existe.
>- _map.has_ Devuelve true si la clave existe.
>- _map.delete(clave)_ Elimina el elemento con esa clave.
>- _map.clear()_ Elimina todo de map.
>- _map.size_ Devuelve la cantidad total de elementos.

>[!example] Ejemplo.
```javascript
let map = new Map();

map.set('1', 'str1');   // un string como clave
map.set(1, 'num1');     // un número como clave
map.set(true, 'bool1'); // un booleano como clave

// ¿recuerda el objeto regular? convertiría las claves a string.
// Map mantiene el tipo de dato en las claves, por lo que estas dos son diferentes:
alert( map.get(1)   ); // 'num1'
alert( map.get('1') ); // 'str1'

alert( map.size ); // 3
```

[[Keyed Collections]]