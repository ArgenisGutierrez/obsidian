>[!summary] Resumen.
>Tambie conocido como Same-value equality determina si dos valores son funcionalmente identicos en todos los contextos. Es aun mas estricta que _===_.
>Ejemplos:
>- En === +0 y -0 son iguales mientras que en same-value no.
>- En === NaN y NaN no son iguales mientras en same-value si.

>[!example] Ejemplo.
```javascript
// Comparación de +0 y -0
console.log(+0 === -0);    // true
console.log(Object.is(+0, -0)); // false

// Comparación de NaN
console.log(NaN === NaN);  // false
console.log(Object.is(NaN, NaN)); // true

// Comparación de otros valores
console.log(5 === 5);      // true
console.log(Object.is(5, 5)); // true

console.log('hello' === 'hello'); // true
console.log(Object.is('hello', 'hello')); // true

console.log({} === {});    // false (diferentes referencias de objeto)
console.log(Object.is({}, {})); // false (diferentes referencias de objeto)
```

[[Value Comparison Operators]]