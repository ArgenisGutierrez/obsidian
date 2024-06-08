>[!summary] Resumen.
>Lo de siempre arboles echos de nodos con aristas, en Lua se hacen de varias formas.

>[!example] Ejemplo.
```Lua
-- Listas adyacentes
local graph = {
    A = {"B", "C"},
    B = {"A", "D", "E"},
    C = {"A", "F"},
    D = {"B"},
    E = {"B", "F"},
    F = {"C", "E"}
}

-- Imprimir el grafo
for node, edges in pairs(graph) do
    print(node .. " is connected to " .. table.concat(edges, ", "))
end

-- Resultado:
-- A is connected to B, C
-- B is connected to A, D, E
-- C is connected to A, F
-- D is connected to B
-- E is connected to B, F
-- F is connected to C, E

-- Matrices adyacentes
local nodes = {"A", "B", "C", "D", "E", "F"}
local graph = {
    {0, 1, 1, 0, 0, 0},  -- A
    {1, 0, 0, 1, 1, 0},  -- B
    {1, 0, 0, 0, 0, 1},  -- C
    {0, 1, 0, 0, 0, 0},  -- D
    {0, 1, 0, 0, 0, 1},  -- E
    {0, 0, 1, 0, 1, 0}   -- F
}

-- Imprimir la matriz de adyacencia
for i, row in ipairs(graph) do
    local rowStr = ""
    for j, val in ipairs(row) do
        rowStr = rowStr .. val .. " "
    end
    print(nodes[i] .. ": " .. rowStr)
end

-- Resultado:
-- A: 0 1 1 0 0 0 
-- B: 1 0 0 1 1 0 
-- C: 1 0 0 0 0 1 
-- D: 0 1 0 0 0 0 
-- E: 0 1 0 0 0 1 
-- F: 0 0 1 0 1 0 

```

[[Lua]]