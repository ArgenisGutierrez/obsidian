>[!summary] Resumen.
>Honestamente no se cuando trabajare con datos binarios pero Lua ofrece 2 métodos para convertir datos o valores básicos en datos binarios y viceversa:
>- string.pack toma un formato y una lista de valores y devuelve una cadena con los valores empaquetados con el formato especifico.
>- string.unpack toma un formato y una cadena empaquetada y devuelve los valores desempaquetados según el formato.

>[!example] Ejemplo.
```Lua
local packed = string.pack(format, v1, v2, ...)
local v1, v2, ..., nextpos = string.unpack(format, packed)
```

>[!error] Nota.
>Al parecer estos métodos están obsoletos en las nuevas versiones de lua.

[[Lua]]