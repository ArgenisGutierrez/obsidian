>[!summary] Resumen.
>Los operadores aritmeticos son los mismos que en otros lenguajes con algunos ligeros cambios y unos extras.

>[!note] Suma.
>La suma de 2 numeros de tipo igual da el mismo resultado per si es mixto entonces se combierte en float.
>``` Lua
>14 + 11 --> 25
>14.0 + 11.0 --> 25.0
>14.0 + 11 --> 25.0
>```

>[!note] Divicion.
>La división siempre terminara con un numero float incluso si los 2 números son integers. Tambien incluye algo llamado *floor division* (//) que redondea el resultado hacia abajo.
>``` Lua
> 3 // 2 --> 1
> 6.0 // 2.0 --> 3.0
> 6 // 2 --> 3
>```

[[Lua]]