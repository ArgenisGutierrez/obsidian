>[!summary] Resumen.
>Es la acciona de reemplazar partes de una cadena que coinciden con un patrón especifico, es decir reemplazar segmentos de texto de acuerdo a un patrón por otro segmento de texto.
>Para esto se usa la funcion _string.gsub_.

>[!example] Ejemplo.
>
```Lua
local text = "Mi número es 123-456-7890"
local pattern = "(%d%d%d)-(%d%d%d)-(%d%d%d%d)"
local function replace_function(area, prefix, line)
    return area .. "." .. prefix .. "." .. line
end
local result = string.gsub(text, pattern, replace_function)
print(result)  -- Imprime "Mi número es 123.456.7890"
```

[[Lua]]