>[!summary] Resumen.
>Las listas se implementan facilmente con una tabla y pueden crecer dinamicamente.

>[!example] Ejemplo.
```Lua
local list = {"first", "second", "third"}

-- Añadir elementos
table.insert(list, "fourth")

-- Eliminar el último elemento
table.remove(list)

-- Recorrer la lista
for i, item in ipairs(list) do
    print(i, item)
end

```

[[Lua]]