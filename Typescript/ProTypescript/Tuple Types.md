>[!summary] Resumen.
>La tupla es un tipo de arreglo un tanto especial pues indica no solo el tipo de dato que contiene, si no tambien el lugar ya que puede contener diferentes tipos.

>[!example] Ejemplo.
>```typescript
>let info: [string,number,boolean];
>//OK
>info = ['Arfhel',28,true];
>//X
>info = [true,'arfhel',29];
>```

[[Types]]