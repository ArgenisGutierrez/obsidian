>[!summary] Resumen.
>En lua también se pueden convertir los números de un tipo a otro con el detalle que de float a integer es un poco mas complicado y lleva pasos extras.

>[!example] De Integer a Float
>``` Lua
>3 + 0.0 --> 3.0
>199 + 0.0 --> 199.0 
>```

>[!example] De Float a Integer
>Para convertir un float a integer primero tenemos que saber si tiene decimales, si los tiene tenemos que redondearlo a 0 antes de usar el metodo math.tointeger(float).
>``` Lua
>//Supongamos que tenemos el numero 7.6
>num = 7.6
>num = math.floor(num) //Esto redondea a 7
>//Entonces ya podemos utilizar el metodo tointeger
>num = math.tointeger(num) //Esto retorn 7
>```

[[lua]]