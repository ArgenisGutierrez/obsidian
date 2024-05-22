>[!summary] Resumen.
>El lexical scoping es igual que en otros lenguajes como Javascript es el alcance que tienen las variables en los distintos bloques de codigo.

>[!example] Ejemplo.
```Lua
function makeCounter()
    local count = 0
    
    return function()
        count = count + 1
        return count
    end
end

local counter1 = makeCounter()
local counter2 = makeCounter()

print(counter1())  -- Imprime 1
print(counter1())  -- Imprime 2
print(counter2())  -- Imprime 1
print(counter2())  -- Imprime 2

```

[[Lua]]