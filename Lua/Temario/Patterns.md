>[!summary] Resumen.
>Lua usa el simbolo _%_ en lugar del \ para escapar caracteres y tiene su propia nomenclatura para expresiones regulares:

| Caracter |        Significado         |
| -------- | :------------------------: |
| .        |       All Character        |
| %a       |          Letters           |
| %c       |     Control Characters     |
| %d       |           Digits           |
| %g       |    Printable characters    |
| %l       |     Lower-case Letters     |
| %p       |   Puntuation Characters    |
| %s       |      Space Characters      |
| %u       |   Upper-case Characters    |
| %w       |  Alphanumeric Characters   |
| %x       |     Hexadecimal Digits     |
| %b       |      Balanced strings      |
| +        |   1 Or More repetitions    |
| *        |   0 Or More Repetitions    |
| -        | 0 Or More Lazy repetitions |
| ?        |          Optional          |
>[!example] Ejemplos.
```Lua
--%b
s = "a (enclosed (in) parentheses) line"
print((string.gsub(s, "%b()", ""))) --> a line
```

[[Lua]]