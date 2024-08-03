>[!summary] Resumen.
>El weak set se comporta forma similar a el weak map :
>- Solo se pueden agregar objetos.
>- Un objeto existe mientras sea accesible desde otro lugar.
>- Usa _add, has y delete_ pero no size, keys o iteracioes.

>[!example] Ejemplo.
```javascript
let visitedSet = new WeakSet();

let john = { name: "John" };
let pete = { name: "Pete" };
let mary = { name: "Mary" };

visitedSet.add(john); // John nos visita
visitedSet.add(pete); // luego Pete
visitedSet.add(john); // John otra vez

// visitedSet tiene 2 usuarios ahora

// comprobar si John nos visitó?
alert(visitedSet.has(john)); // true

// comprobar si Mary nos visitó?
alert(visitedSet.has(mary)); // false

john = null;

// visitedSet se limpiará automáticamente
```

[[Keyed Collections]]