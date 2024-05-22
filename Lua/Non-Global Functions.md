>[!summary] Resumen.
>En resumen las funciones no solo se pueden almacenar en baribales locales sino también en locales y es gracias a esto que se pueden crear librerías al guardar funciones en tablas para usar como métodos estáticos que vemos en otros lenguajes.

>[!example] Ejemplo.
```Lua
--Libreria
Lib = {}
Lib.foo = function (x,y) return x + y end
Lib.goo = function (x,y) return x - y end
print(Lib.foo(2, 3), Lib.goo(2, 3)) --> 5 -1
--Local function
local fact
fact = function (n)
if n == 0 then return 1
else return n*fact(n-1)
end
end
```

[[Lua]]