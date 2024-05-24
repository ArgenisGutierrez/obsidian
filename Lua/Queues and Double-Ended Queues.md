>[!summary] Resumen.
>Las colas igual se pueden implementar fácilmente con tablas.

>[!example] Ejemplo.
```Lua
local queue = {}

-- Añadir elementos a la cola
table.insert(queue, "element1")
table.insert(queue, "element2")

-- Quitar el primer elemento de la cola
local first = table.remove(queue, 1)

print(first)  -- Imprime "element1"

```

[[Lua]]