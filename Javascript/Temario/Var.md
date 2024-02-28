>[!summary] Resumen
>La palabra reservada _var_ declara variables con un [scope global][^1] y opcionalmente inicializándola con un valor.

>[!info] Sintaxis
>var name1;
var name1 = value1;
var name1 = value1, name2 = value2;
var name1, name2 = value2;
var name1 = value1, name2, /* …, */ nameN = valueN;

## Descripción.
Las variables declaradas con la palabra _var_ sin importar el lugar donde sea declarada estará en un ámbito global. Es decir puede se accedida desde cualquier parte del código lo que puede crear que nuestro código se comporte de forma inesperada por lo cual es recomendado evitar su uso y en su lugar usar [[Let]] o [[Const]].

>[!example] Ejemplo de Var
>var nombre= 'Argenis';
>var edad = 28;

[[Variable Declarations]]

[^1]: [[Variable Scoopes]]