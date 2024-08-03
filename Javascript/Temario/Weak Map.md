>[!summary] Resumen.
>La primer diferencia con el map es que las claves siempre tienen que ser objetos y no valores primitivos. La otra diferencia es que a diferencia del map en el weak map si se ve afectado por el [[Garbage Collection]].
>Solo tiene los siguientes metodos:
>- _weakMap.set(clave,valor)_.
>- _weakMap.get(clave)_.
>- _weakMap.delete(clave)_.
>- _weakMap.has(clave)_.

>[!example] Ejemplo
```javascript
let john = { name: "John" };

let map = new Map();
map.set(john, "...");

john = null; // sobreescribe la referencia

// john se almacena dentro de map,
// podemos obtenerlo usando map.keys ()

let weakMap = new WeakMap();

let obj = {};

weakMap.set(obj, "ok"); // funciona bien (la clave es un objeto)

// no puede usar un string como clave
weakMap.set("test", "Whoops"); // Error, porque "test" no es un objeto
```

>[!note] Nota.
>Si estamos trabajando con un objeto que “pertenece” a otro código (tal vez incluso una biblioteca de terceros), y queremos almacenar algunos datos asociados a él que solo deberían existir mientras el objeto esté vivo, entonces `WeakMap` es exactamente lo que se necesita.
>
>Ponemos los datos en un `WeakMap` utilizando el objeto como clave, y cuando el objeto sea recolectado por el recolector de basura, esos datos también desaparecerán automáticamente.

[[Keyed Collections]]