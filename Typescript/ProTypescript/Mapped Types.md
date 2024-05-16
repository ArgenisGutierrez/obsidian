>[!summary] Resumen.
>Los tipos mapeados son una característica poderosa pero compleja para crear nuevos tipos basados en la estructura de otros tipos existentes y transformándooslos a través de una iteración de cada propiedad.

>[!example] Ejemplo.
>```typescript
>//Estructura
type NuevoTipo = {
  [PropiedadExistente in TipoExistente]: Transformación;
};
>//Tomamos un tipo al que le agregaremos 5 mas
type Edades = {
  alice: 30,
  bob: 25,
  charlie: 35
};
>//usando maptype
>type EdadesMas5 = {
>[Clave in keyof Edades]: Edades[Clave]+5;
>}
>```


[[Types]]