>[!summary] Resumen.
>El Modelo IO de Luan permite no solo el ingreso y muestra de datos por consola, sino también la posibilidad de leer y modificar ficheros.
>También tiene los métodos de manejo de entrada y salida estándar io.stdin, io.stdout y io.stferr.

>[!example] Ejemplo.
>```Lua
>-- Abrir un archivo
>local file = io.open("archivo","r")
>-- Leer el contenido
>local contenido = file:read("*a")
>print(contenido)
>-- Cerramos el archivo
>file:close()
>--Escribir en un archivo
>local file = io.open("archivo.txt","w")
>--Escribimos
>file:write("Hola Mundo\n")
>file:wite("Otra linea de texto\n")
>-- Cerramos el archivo
>file:close()
>```

[[Lua]]