>[!summary] Resumen.
>Los tipos literales te permiten definir valores específicos a las variables en lugar de tipos.

>[!example] Ejemplo.
>```typescript
>type Nombres = 'Juan' | 'Paco' | 'Pedro' | 'Dela' | 'Mar';
>let nombre: Nombres;
>//OK
>nombre = 'Juan';
>nombre = 'Pedro';
>//X
>nombre = 'Alex';
>nombre = 'Felix';
>type Random = 'less' | 12 | false
>```
>

[[Types]]