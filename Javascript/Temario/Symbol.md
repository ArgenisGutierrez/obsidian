>[!summary] Resumen
>Symbol a pesar de ser un [[Build In Objects]] cuyo constructor devuelve un [[Sting]] por lo cual es tratado como un dato primitivo y es usado a menudo para añadir claves de propiedades únicas a un objeto debido a que cada symbol es unico.

>[!exmaple] Ejemplo
>```javascript
>let sym1 = Symbol();
let sym2 = Symbol("foo");
let sym3 = Symbol("foo");
>console.log(sym2===sym3); //Esto es falso
>```

[[Primitive Types]]