>[!summary] Resumen.
>Las matrices se pueden implementar con tablas dentro de tablas.

>[!example] Ejemplo.
```Lua
local matrix = {
    {1, 2, 3},
    {4, 5, 6},
    {7, 8, 9}
}

-- Acceder a elementos
print(matrix[2][3])  -- Imprime 6

-- Recorrer la matriz
for i = 1, #matrix do
    for j = 1, #matrix[i] do
        print(matrix[i][j])
    end
end

```

[[Lua]]