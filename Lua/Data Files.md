>[!summary] Resumen.
>Lo mas remarcables que menciono es la forma de ordenar la información en las estructuras de datos.

>[!example] Ejemplo.
```Lua
--No es lo mismo esto
Entry{"Donald E. Knuth",
	"Literate Programming",
	"CSLI",
	1992}
--Que esto
Entry{
author = "Donald E. Knuth",
title = "Literate Programming",
publisher = "CSLI",
year = 1992
}
```

[[Lua]]