>[!summary] Resumen.
>Las capturas son una caracteristica de los patrones que permiten extraer y almacenar partes especificas de una cadena que coincidan con subpatrones. Se hace mediante el uso de _()_ dentro del patron.

>[!example] Ejemplo.
```Lua
local text = "Mi fecha de nacimiento es 17/12/1995"
local patron = "(%d%d)/(%d%d)/(%d%d%d%d)"
local dia,mes,ano = string.match(text,patron)
print(dia,mes,ano) --> 17 12 1995
```

[[Lua]]