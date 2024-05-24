>[!summary] Resumen.
>El mismo concepto de scope de otros lenguajes solo que en lua se usa la palabra reservada _local_ para declarar variables locales en un bloque o [[Chunks]] como los llama lua.
>El extra que tiene lua es poder declara un bloque cuando es necesario limitar variables con las palabras _do_ y _end_.

>[!example] Ejemplo.
```Lua
local x1, x2
do
	local a2 = a*2
	local d = (b^2 - 4*a*c)
	x1 = (-b + d)/a2
	x2 = (-b - d)/a2 --> scope de a2 y d
end
print(x1,x2) --> nil
```

[[Lua]]