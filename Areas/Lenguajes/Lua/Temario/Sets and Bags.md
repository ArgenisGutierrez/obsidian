>[!summary] Resumen.
>Los sets o conjuntos se implementan usando tablas donde los valores de las claves representan los elementos y los valores son "true".

>[!example] Ejemplo.
```Lua
local set = {}

-- Añadir elementos al conjunto
set["apple"] = true
set["banana"] = true

-- Verificar si un elemento está en el conjunto
if set["apple"] then
    print("Apple is in the set")
end

-- Recorrer el conjunto
for element in pairs(set) do
    print(element)
end

```

[[Lua]]