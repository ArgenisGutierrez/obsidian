>[!summary] Resumen.
>Es el proceso de convertir una estructura de datos u objeto en un formato que permita su almacenamiento o transferencia y pueda ser reconstruido mas tarde. 
>Propósitos:
>- Persistencia de datos: guardar el estado para ser recuperado mas tarde.
>- Transmitir Datos: enviar datos a través de redes en un formato que puede ser reconstruido.
>- Clonación de objetos: crear copias exactas de objetos o estructuras.
>- Interoperabilidad de objetos: facilitar la comunicación entre lenguajes de programación o sistemas mediante un formato común.

>[!example] Ejemplo.
```Lua
-- Serializacion
function serialize(o)
    if type(o) == "number" then
        return tostring(o)
    elseif type(o) == "string" then
        return string.format("%q", o)
    elseif type(o) == "table" then
        local result = "{"
        for k, v in pairs(o) do
            result = result .. "[" .. serialize(k) .. "]=" .. serialize(v) .. ","
        end
        result = result .. "}"
        return result
    else
        error("Cannot serialize type: " .. type(o))
    end
end

local exampleTable = {
    name = "John",
    age = 30,
    scores = {95, 88, 92}
}

local serialized = serialize(exampleTable)
print(serialized) -->{["age"]=30,["name"]="John",["scores"]={[1]=95,[2]=88,[3]=92,},}
--Deserializacion
function deserialize(str)
    local func = load("return " .. str)
    return func()
end

local deserializedTable = deserialize(serialized)
print(deserializedTable.name)  -- Imprime "John"
print(deserializedTable.age)   -- Imprime 30
```

[[Lua]]
