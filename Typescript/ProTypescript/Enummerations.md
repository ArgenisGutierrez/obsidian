>[!summary] Resumen
>Los Enum son una coleccion de datos parecida a los [[Arrays]] pero no estan indexados por un numero pero pueden hacer uso de banderas para estar indexados por distintos valores.

>[!example] Ejemplos
> ``` TypeScript
> enum Days {
> 	Lunes,
> 	Martes,
> 	Miercoles,
> 	Jueves,
> 	Viernes}
>Days.Lunes
>```
>```Typescript
>enum Flags {
>Small = 0,
>Medium = 1,
>Big = 2
>}
>Flags.Medium = 1
>```

[[Types]]