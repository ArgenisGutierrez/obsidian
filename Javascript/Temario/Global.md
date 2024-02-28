>[!summary] Resumen
>Las variables globales tienen un alcance en todo el código y suelen declararse comunmente con _var_ pero pueden ser declaradas con las _let_ o _const_. No es recomendable usar variables globales a menos que sea estrictamente necesario ya que pueden causar un comportamiento inesperado de nuestro codigo.

>[!example] Ejemplo
>```javascript
>//Todas son variables globales
>var x=2;
>let y=6;
>const z=7;
>
>function suma(num1,num2){
>	return num1 + num2;
>};
>```
>

[[Variable Scoopes]]