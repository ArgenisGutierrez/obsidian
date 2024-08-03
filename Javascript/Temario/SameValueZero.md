>[!summary] Resumen.
>Se parece al Strict equality con la diferencia de como trata a +0 y -0 al consideraras iguales, mientras que a NaN los considera iguales.

>[!example] Ejemplo.
```javascript
// Comparación de +0 y -0
console.log(+0 === -0);           // true
console.log(Object.is(+0, -0));   // false
console.log([+0].includes(-0));   // true

// Comparación de NaN
console.log(NaN === NaN);         // false
console.log(Object.is(NaN, NaN)); // true
console.log([NaN].includes(NaN)); // true

// Comparación de otros valores
console.log([5].includes(5));     // true
console.log(['hello'].includes('hello')); // true

const set = new Set([+0, -0]);
console.log(set.size);            // 1 (en Set, +0 y -0 son iguales)

const map = new Map();
map.set(+0, 'value');
console.log(map.get(-0));         // 'value' (en Map, +0 y -0 son iguales)
```

[[Equality Algorithms]]