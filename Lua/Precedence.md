>[!summary] Resumen.
>La precedencia o como yo la conozco jerarquía de operaciones es la siguiente:
>- ^ (Exponente)
>- unary operators (- # ~ not)
>- \* / // %
>- + - 
>- .. (Concatenación)
>- \<\<  \>\> (bitwise shifts)
>- & (bitwise AND)
>- ~ (bitwise NOT)
>- | (bitwise OR)
>- < > <= >= ~= == 
>- and
>- or

>[!example] Ejemplo.
>``` Lua
>a+i < b/2+1      <--> (a+i) < ((b/2)+1)
5+x^2*8          <--> 5+((x^2)*8)
a < y and y <= z <--> (a < y) and (y <= z)
-x^2             <--> -(x^2)
x^y^z            <--> x^(y^z)
>```

[[Lua]]