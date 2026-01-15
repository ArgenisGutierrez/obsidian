>[!summary] Resumen.
>Cuando llamamos a una funcion al final de otra creando una cadena se le denimina _tail calls_, pero debe cumplirse con ciertas condiciones:
>- La llamada a la función es la ultima acciona antes de retornar.
>- No se realiza ninguna operación adicional con el resultado de la llamada antes de retornarlo.
>Esto permite al interprete optimizar la cola de funciones al no tener que mantener el marco de la primera función evitando agregar mas elementos en la pila de llamadas.

>[!example] Ejemplo.
>```Lua
>//Tail Calls
>function f(x)
>	x = x + 1
>	return g(x)
>end
>//No Tail Calls
>function f(n)
>	g(x)
>end
>```

[[Lua]]