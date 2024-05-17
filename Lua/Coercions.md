>[!summary] Resumen.
>Lua tiene coerción para transformar números a strings y viceversa, principalmente cuenta con 2 métodos: tostring() y tonumber(), pero el interprete de lua también puede hacer una coerción automática.

>[!example] Ejemplos.
>``` Lua
>tonumber("-3") --> -3
>tonumber("10e4") --> 100000.0
>tostrng(10) --> "10"
>"10" + 1 --> 11.0
>```

[[Lua]]