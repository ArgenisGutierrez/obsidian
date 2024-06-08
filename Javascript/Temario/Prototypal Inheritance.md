>[!summary] Resumen.
>La herencia de prototipo es la forma a través de la cual podemos extender las propiedades o métodos de un objeto a otro.
>Para saber el prototipo en el cual se basa otro podemos hacer uso de 2 metodos de Object:
>- Object.getPrototypeOf.
>- Object.setPrototypeOf.
>O bien de la propiedad \_proto\_ que tienen los objetos.

>[!exmaple] Ejemplo.
```javascript
//Get Prototype
const object = { a: 1 };
Object.getPrototypeOf(object) === Object.prototype; // true

//Set Prototype
function Base() {}
function Derived() {}
// Set the `[[Prototype]]` of `Derived.prototype`
// to `Base.prototype`
Object.setPrototypeOf(Derived.prototype, Base.prototype);
const obj = new Derived();
// obj ---> Derived.prototype ---> Base.prototype ---> Object.prototype ---> null
```

[Regresar](Javascript)