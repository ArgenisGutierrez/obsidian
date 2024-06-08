>[!summary] Resumen.
>En resumen para trabajar con unsigned integers en Lua que son números mayores a los que soporta que es 2^63-1 se tiene que hacer uso de los [[Bitwise Operators in Lua]], mientras que para imprimirlos se hace uso del metodo _string.format_.

>[!example] Ejemplo.
```Lua
x = 13835058055282163712 -- 3 << 62
x --> -4611686018427387904
string.format("%u", x) --> 13835058055282163712
string.format("0x%X", x) --> 0xC000000000000000
```

[[Lua]]