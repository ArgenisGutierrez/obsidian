>[!summary] Resumen.
>La interseccion de tipos permite juntar diversos tipos in un solo super tipo.

>[!example] Ejemplo.
>``` typescript
>interface Skier {
>	slide(): void;
>}
>interface Shooter {
>	shoot(): void;
>}
>type Biathlete = skier & Shooter;
>```

[[Types]]