>[!summary] Resumen.
>Ademas de las funciones anterirormente mencionada tambien existen otra metodos que pueden resultar utiles:
>- io.tempfile crea un archivo temporal que se elimina cuando se cierra el archivo o cuando termina el programa.
>- io.flush fuerza que cualquier salida en búfer se escriba en el archivo.
>- io.setvbuf establece el modo búfer para el archivo(no,full,line).
>- io.seek establece u obtiene la posición actual en el archivo.

>[!example] Ejemplo.
```Lua
-- Abrir un archivo para escritura y establecer el búfer por líneas
local file = io.open("advanced_output.txt", "w")
file:setvbuf("line")

-- Escribir datos y forzar el volcado del búfer
file:write("Primera línea\n")
file:flush()

-- Escribir más datos sin volcar inmediatamente
file:write("Segunda línea\n")

-- Cerrar el archivo
file:close()

-- Abrir el archivo para lectura y leer línea por línea
file = io.open("advanced_output.txt", "r")
for line in file:lines() do
    print("Leído: " .. line)
end
file:close()

-- Crear y usar un archivo temporal
local tmpfile = io.tmpfile()
tmpfile:write("Datos temporales\n")
tmpfile:seek("set", 0)
print("Contenido temporal: " .. tmpfile:read("*all"))
tmpfile:close()

```


[[Lua]]