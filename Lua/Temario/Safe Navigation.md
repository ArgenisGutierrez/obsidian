>[!summary] Resumen.
>La navegacion segura es el concepto de poder acceder a métodos o propiedades sin preocuparte si el objeto o tabla es nil, la expresión se evalúa como nil en lugar de lanzar un error.
>En lua debido a su naturaleza minimalista se debe implementar técnicas de forma manual.

>[!example] Ejemplo con funcion.
>```Lua
>function safeGet(t, ...)
>	local keys = { ... }
>	for _, key in ipairs(keys) do
>		if t == nil then
>			retunr nil
>		end
>		t = t[key]
>	end
>	return t
>end
>local data = {
>	user = {
>		profile = {
>			name = "Jhon Doe"
>		}
>	}
>}
>print(safeGet(data, "user", "profile", "name")) -- Imprime Jhon Doe
>print(safeGet(data, "user", "profile", "age")) -- Imprime nil
>```

[[Lua]]