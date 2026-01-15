>[!summary] Resumen.
>En Lua se pueden iterar todos los key-value con el iterador _pairs_ debido a que si la tabla tiene keys tanto numéricas como de string el\# no contara las key strings. Para iterar tablas con llaves solo numericas podemos hacer uso o bien de \# o del iterador _ipairs_.

>[!example] Ejemplo.
>```Lua
>t = {10, print, x = 12, k = "hi"}
for k, v in pairs(t) do
print(k, v)
end
--> 1 10
--> k hi
--> 2 function: 0x420610
--> x 1
>t = {10, print, 12, "hi"}
for k, v in ipairs(t) do
print(k, v)
end
--> 1 10
--> 2 function: 0x420610
--> 3 12
--> 4 hi
>```

[[Lua]]