>[!summary] Resumen.
>La funcion table.unpack transforma un tabla en una lista de valores, mientras que su contraparte table.pack hace lo contrario.

>[!example] Ejemplo.
>```Lua
>print(table.unpack{10,20,30}) --> 10 20 30
>a,b = table.unpack{10,20,30} -- a=10, b=20, 30 is discarded
>print(table.unpack({"Sun", "Mon", "Tue", "Wed"}, 2, 3))
--> Mon Tue
>```

[[Lua]]