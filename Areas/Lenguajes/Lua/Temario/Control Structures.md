>[!summary] Resumen.
>Como los demás lenguajes Lua cuenta con algunas estructuras de control con su especifica nomenclatura.

>[!warning] Nota.
>Es importarte recordar que en Lua solo _false_ y _nil_ se consideran falso y todo lo demás se considera true.

>[!example] Ejemplos.
```Lua
-- If then else
if op == "+" then
	r = a + b
elseif op == "-" then
	r = a - b
else
	error("operacion invalida")
end

-- While
local i = 1
while i ~= 5 do
	print i
	i = i + 1
end

-- Repeat
local line
repeat
	line = io.read()
until line = ""
print(lin)

-- Numerical For
for var = 1, 5 , 1 do
	...
end

-- Generic For
local s = 0
for _, v in ipairs{...} do
	s = s + v
end

-- Goto
while some_condition do
	::redo::
	if some_other_condition then 
		goto continue
	else if yet_another_condition then 
		goto redo
	end
	some code
	::continue::
end
```

[[Lua]]