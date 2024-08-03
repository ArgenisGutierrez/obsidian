>[!summary] Resumen.
>Son una forma de manejar datos binarios de manera eficiente y estructurada. Estan diseñados para interactuar con datos binarios en bruto y son utiles cuando se requiere la manipulación directa de byte como en gráficos, sonido, redes y otros casos.
>Los typed arrays se componen de :
>- Array Buffer: Objeto generico para represetar un bloque de memoria cruda.
>- Typed Array: Son las vistas especificas sobre el Array Buffer que permiten leer y escribir datos en distintos formatos numericos.
>- Data View: Proporciona una vista mas flexible sobre un Array Buffer permitiendo leer y escribir en partes especificas del buffer en diferentes formatos.

>[!example] Ejemplo.
```javascript
// Crear un ArrayBuffer con una longitud de 16 bytes (128 bits)
let buffer = new ArrayBuffer(16);

// Crear una vista de Int32Array (enteros de 32 bits) sobre el buffer
let int32View = new Int32Array(buffer);

// Asignar valores a los elementos del Int32Array
int32View[0] = 42;
int32View[1] = 84;

// Crear una vista de Uint8Array (enteros de 8 bits sin signo) sobre el mismo buffer
let uint8View = new Uint8Array(buffer);

// Leer los bytes individuales del buffer
console.log(uint8View[0]); // Salida: 42 (primer byte de 42 en Int32Array)
console.log(uint8View[4]); // Salida: 84 (primer byte de 84 en Int32Array)

// Crear una vista de DataView para leer y escribir datos en el buffer
let dataView = new DataView(buffer);

// Leer un entero de 32 bits con signo desde el inicio del buffer
console.log(dataView.getInt32(0)); // Salida: 42

// Escribir un valor de punto flotante de 32 bits en la posición 8 del buffer
dataView.setFloat32(8, 3.14);

// Leer el valor de punto flotante de 32 bits desde la posición 8 del buffer
console.log(dataView.getFloat32(8)); // Salida: 3.14
```

[[Indexed Collections]]