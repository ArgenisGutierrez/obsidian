>[!summary] Resumen.
>Funciones como valores de primer clase hace referencia a que las funciones pueden ser tratadas como valores de variables, guardadas en tablas, pasadas como argumentos de otras funciones o ser retornadas por otras. Todas las funciones en Lua son anonimas.

>[!example] Ejemplos.
```Lua
a = {p = print} -- 'a.p' refers to the 'print' function
a.p("Hello World") --> Hello World
print = math.sin -- 'print' now refers to the sine function
a.p(print(1)) --> 0.8414709848079
math.sin = a.p -- 'sin' now refers to the print function
math.sin(10, 20) --> 10 20
```

[[Lua]]