>[!summary] Resumen.
>Lua a diferencia de otros lenguajes puede contener un gran numero de carateres en un string como por ejemplo hasta un libro completo.
>Tambien no tiene problemas en conterner datos binario, Unicode y cualquier otra representacion como UTF-8.

>[!warning] Nota.
>En Lua los strings son inmutables, es decir no podemos cambiar los caracteres de un string, solo crear otro nuevo string.

>[!example] Uso del \# 
>Se puede obtener el largo de un string solo con el uso de \#.
>``` Lua
>a = "hello"
print(#a) --> 5
print(#"good bye") --> 8
>```

>[!note] Secuencias de escape.
>Lua tiene las mismas secuencias que C, y el uso de comillas es indistinto en simples y dobles.
>

| Secuncia | Significado     |
| -------- | --------------- |
| \a       | Bell            |
| \b       | Back Space      |
| \f       | Form Feed       |
| \n       | New Line        |
| \r       | Carriage Return |
| \t       | Horizontal Tab  |
| \v       | Vertical Tab    |
| \\\\     | Backslash       |
| \\"      | Doble Quote     |
| \\'      | Single Quote    |

[[Lua]]