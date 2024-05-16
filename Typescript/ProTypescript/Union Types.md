>[!summary] Resumen.
>La unión de tipos permite especificar mas de un solo tipo a las variables permitiendo que puedan ser definida de uno de los tipos definidos.

>[!example] Ejemplo.
>```typescript
>let union: boolean | number;
>//OK
>union = 5;
>union true;
>//X
>union = 'hola';
>```

[[Types]]