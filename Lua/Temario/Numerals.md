>[!summary] Resumen.
>En lua tanto los integer como los float son englobados en el tipo number por lo tanto pueden ser numeros enteros, con punto decimal o con exponente.

>[!example] Ejemplo
>- 4 
>- 0.4
>- 4.57e-3 --> 0.00457
>- 0.3e12  --> 3000000000.0
>- 5E+20  --> 5e+20

>[!infot] Distinguir entre int y float
>Para poder distinguir entre ambos de ser necesario se debe hacer util del metodo Math.type.
>``` Lua
>math.type(3) ---> integer
>math.type(3.0) --> fload
>``` 

[[Lua]]