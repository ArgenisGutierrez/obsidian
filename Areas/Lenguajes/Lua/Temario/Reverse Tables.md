>[!summary] Resumen.
>Las tablas inversas son tablas donde las claves y los valores estan intercambiados, son utiles cuando es necesario buscar claves basado en valores.

>[!example] Ejemplo.
```Lua
local original = {
    apple = "fruit",
    carrot = "vegetable",
    banana = "fruit"
}

-- Crear una tabla inversa
local reverse = {}
for key, value in pairs(original) do
    reverse[value] = reverse[value] or {}
    table.insert(reverse[value], key)
end

-- Imprimir la tabla inversa
for key, values in pairs(reverse) do
    print(key .. ": " .. table.concat(values, ", "))
end

-- Resultado:
-- fruit: apple, banana
-- vegetable: carrot

```

[[Lua]]