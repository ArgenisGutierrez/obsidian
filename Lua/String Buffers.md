>[!summary] Resumen.
>Se utilizan para construir cadenas de forma eficiente cuando se tienen que haces varias concatenaciones, para ello en una tabla se guardan todas las cadenas para ser unidas al final.

>[!example] Ejemplo.
```Lua
local buffer = {}

-- Añadir cadenas al buffer
table.insert(buffer, "Hello, ")
table.insert(buffer, "world")
table.insert(buffer, "!")

-- Concatenar el contenido del buffer
local result = table.concat(buffer)
print(result)  -- Imprime "Hello, world!"
```

[[Lua]]