>[!summary] Resumen.
>Una función variadic en Lua hace referencia a una función que recibe un numero variable de argumentos. Esto haciendo uso de algo llamado _varag expression_ (...) que hace referencia al conjunto de argumentos que recibe la funcion.

>[!example] Ejemplo.
>```Lua
>function add(...)
>	local s = 0
>	for _, v in iparis{...} do
>		s = s + v
>	end
>	return s
>end
>print(add(3,4,10,25,12))   --> 54
>```

>[!note] Nota.
>La funcion select(index,...) hace uso de esto.
>```Lua
>print(selecet("#",1,2,3)) --> 3
>print(selecet("2",1,2,3)) --> 2 3
>```

[[Lua]]