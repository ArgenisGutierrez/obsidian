>[!summary] Resumen.
>Lua cuenta con la librería _io_ para interactuar con el exterior del código, esto se traduce en recibir y mostrar datos por consola.
>Las funciones básicas de la librería son read y write para recibir datos y mostrarlos en pantalla.
>El método read hace uso de 5 parámetros para recibir datos:
>- "a" : Leer el archivo completo.
>- "l" : Leer la siguiente linea y se mantiene en ella
>- "L" : Leer la siguiente linea realiza un salto de linea.
>- "n" : Leer un numero.
>- num : Leer un numero como un string.

>[!example] Ejemplo
>```Lua
>print("Ingresa tu nombre:)
>nombre = io.read("\*L")
>io.write("Hola " .. nombre)
>print(nombre)
>--[[
>Hola juan
>juan
>]]
>```

[[Lua]]