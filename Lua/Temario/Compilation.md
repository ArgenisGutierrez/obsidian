>[!summary] Resumen.
>Es el proceso de convertir codigo en bytecode y se puede invocar el compilador con las funciones _load_ y _loadfile_.

>[!example] Ejemplo.
```Lua
local func, err = load("print('Hello, World!')")
if func then
    func()  -- Ejecuta el bytecode
else
    print("Error de compilación: " .. err)
end
```

[[Lua]]