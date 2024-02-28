>[!summary] Resumen
>El hoisting es el proceso que realiza el interprete a la hora de ejecutar nuestro código el cual consta de 2 fases:
>- Fase de Creación:
>	- Se escanea el código en busca de las variables, funciones, clases y módulos importados para ser agregadas al [entorno léxico][^1].
>	- Se reserva el espacio de memoria para las variables.
>	- Las definiciones de funciones de cargan en memoria.
>- Fase de Ejecución:
>	- El código se ejecuta línea a línea con la información recopilada en la fase anterior.
>	- Se asignan los valores a las variables.
>	- Se ejecutan las funciones.

## Descripción.
El concepto de hoisting en un principio es un concepto un tanto complicado ya que es un proceso realizado por el interprete de JS y no puedes observarlo a primera vista.
El hoisting es el proceso secuencial que pasa principalmente por 2 fases antes y a la hora de ejecutar código JS. 
La primera fase se ejecuta antes de correr el código y se encarga de revisar el código en busca de las variables y funciones declaradas, posteriormente crea el [léxico global][^1] donde guarda esta información para se usada durante la ejecución del código.
En la segunda fase el interprete ejecuta línea por línea el código con ayuda de la información recopilada en la fase anterior esto permite hacer uso de variables y funciones que fueron posteriormente declaradas.

>[!example] Ejemplo
>```javascript
>let num1 = 5;
>let num2 = 8;
>console.log(suma(num1,num2));
>const function suma(num1,num2){
>	return num1 + num2;
>}
>```

En el ejemplo anterior podemos hacer uso de la función sumar a pesar de estar definida después de su invocación debido al hoisting.

[[All about variables]]

[^1]: [[Lexical Scoping]]