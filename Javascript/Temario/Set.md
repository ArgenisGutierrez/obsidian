>[!summary] Resumen.
>El set es un conjunto de solo valores sin claves donde cada valor aparece solo 1 vez.
>Sus principales métodos son:
>- _new Set([iterable])_ Crea el set.
>- _set.add(valor)_ Agrega un valor al set.
>- _set.delete(valor)_ Elimina el valor y devuelve true si el valor existia.
>- _set.has(valor)_ Devuelve true si el valor existe en el set.
>- _set.clear()_ Elimina todo el contenido del set.
>- _set.size_ Devuelve la cantidad de elementos del set.

>[!example] Ejemplo.
```javascript
let set = new Set();

let john = { name: "John" };
let pete = { name: "Pete" };
let mary = { name: "Mary" };

// visitas, algunos usuarios lo hacen varias veces
set.add(john);
set.add(pete);
set.add(mary);
set.add(john);
set.add(mary);

// set solo guarda valores únicos
alert( set.size ); // 3

for (let user of set) {
  alert(user.name); // John (luego Pete y Mary)
}
```

[[Keyed Collections]]