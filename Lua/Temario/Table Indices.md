>[!summary] Resumen.
>Las tablas son las únicas estructuras de datos en Lua remplazando todas las demas estructuras de los demas lenguajes como los son los [[Array]], [[Object]], [[Set]], ect.
>La estructura de las tablas es parecida a la de los [[Object]] en [[Javascript]] o a los array asociativos.
>El indice de las tablas pueden ser tanto números como llaves.

>[!example] Ejemplo.
>```Lua
>a = {}
>a[1] = "hola"
>a["hola"] = 10
>a.x = "adios"
>print(a[1]) --> "hola"
>print(a["hola]) --> 10
>print(a.x) --> "adios"
>```

>[!warning] Nota
>Al parecer en lua los índices numéricos comienzan en 1 y no en 0 como los demás lenguajes.

[[Lua]]