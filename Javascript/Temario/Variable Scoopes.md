>[!summary] Resumen
>El scope de la variables en pocas palabras se refiere al alcance que tienen y desde que partes del código pueden ser accedidas. Existen 3 tipos de scopes:
>- [[Global]]
>- [[Function]]
>- [[Block]]

## Description.
El Scope es el alcance que tiene una variable en el código, es decir hasta que parte del código puede ser accedida o re asignada, por lo general la forma mas fácil de ver el alcance de una variable es que las variables estan delimitadas por las llaves({}) que las contienen.
Para tenerlo mas claro veamos ejemplos:

>[!example] Ejemplo.
>```javascript
>function saludar(){
>	let nombre = 'Argenis';
>	console.log(`hola ${nombre}`)
>}
>```
>El scope de la variable nombre solo alcanza el contenido de la función puedes guiarte por las llaver({}).

Por desgracia tampoco es tan sencillo ya que el scope también aplica a bloques dentro de bloques, teniendo en cuenta que la regla se aplica solo hacia afuera y no adentro, pero veamos otro ejemplo para tenerlo mas claro:
>[!example] Ejemplo
>```javascript
>let nombre = 'Argenis';
>console.log(numero);//No puede usar la variable de adentro de otro bloque
>function saludar(){
>	let numero = 5;
>	console.log(`hola ${nombre}`); //puede usar la variable que esta afuera.
>}
>```

[[All about variables]]