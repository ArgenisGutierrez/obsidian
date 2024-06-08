>[!summary] Resumen.
>Manejo de errores tipico, pero Lua no cuenta con try-catch, sino con _assert_ que al capturar un error muestra un mensaje de error.

>[!example] Ejemplo.
```Lua
print "enter a number:"
n = assert(io.read("*n"), "invalid input")
```

[[Lua]]