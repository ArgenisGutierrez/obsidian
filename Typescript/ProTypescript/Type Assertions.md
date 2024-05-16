>[!summary] Resumen.
>Las type Assetions son algo complicadas pero en pocas palabras se usan para obligar al compilador a tratar una variable como un tipo especifico cuando no sabe como tratarla con exactitud.

>[!example] Ejemplo.
>```typescript
>//suponiendo que tenemos un tipo any
>let usuario: any ={
>	nombre:'juan',
>	edad:30
>}
>//el compilador no sabe exactamente que tipo de variable es nombre
>let nombre: string = usuario.nombre as string;
>//otra forma de sintaxis
>let nombre: string = \<string\>usuario.nombre;
>```

[[Types]]