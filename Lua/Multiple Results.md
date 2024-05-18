>[!summarye] Resumen.
>En Lua las funciones a diferencia de otro lenguajes permite retornar multiples valores. Solo necesitan ser separador por _,_ al usar return.

>[!example] Ejemplo.
>```Lua
>function foo2()
>	return "a", "b"
>end
>print(foo2())
>```

>[!nota] Nota.
>Hay varios aspectos a tomar en cuenta con respecto a las funciones que retornan varios valores.
>```Lua
>function foo2 () return "a", "b" end -- returns 2 results
>x, y = foo2() -- x="a", y="b"
>x = foo2() -- x="a", "b" is discarded
>x, y, z = 10, foo2() -- x=10, y="a", z="b"
>x,y = foo0() -- x=nil, y=nil
>x,y = foo1() -- x="a", y=nil
>x,y,z = foo2() -- x="a", y="b", z=nil
>x,y = foo2(), 20 -- x="a", y=20 ('b' discarded)
>x,y = foo0(), 20, 30 -- x=nil, y=20 (30 is discarded)
>t = {foo0()} -- t = {} (an empty table)
>t = {foo1()} -- t = {"a"}
>t = {foo2()} -- t = {"a", "b"}
>t = {foo0(), foo2(), 4} -- t[1] = nil, t[2] = "a", t[3] = 4
>```

[[Lua]]