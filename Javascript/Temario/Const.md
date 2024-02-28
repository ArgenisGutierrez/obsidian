>[!summary] Resumen
>Las variables declaradas con _const_ son principalmente llamdas constantes y al igual que las variables let tienen un [block scope][^1] con la diferencia que las constantes no pueden ser reasignadas a diferencia de _let_ y son usadas para datos que no cambiaran es decir "constantes".
>

>[!info] Sintaxis
>const name1 = value1;
const name1 = value1, name2 = value2;
const name1 = value1, name2 = value2, /* …, */ nameN = valueN;

## Descripcion.
Las constantes son variables declaradas con la palabra _const_ y su principal diferencia respecto a _let_ es que las constantes una vez asignadas no pueden ser cambiadas o alteradas con excepción de algunos casos como ejemplo los [[Array]].

>[!example] Ejemplo
>const iva = 16;
>iva = 18 //Esta es un error una constante no se puede reasignar.
>const miArray = [1,2,3,4,5];
>miArray.push(6) // En caso de los arreglos se puede agregar mas valores pero no borrarlos.

>[!tip] Arreglo Inmutable
>Para crear un arreglo inmutable es decir que no se pueda ni agregar nuevos datos se necesitas usar el Object.freeze().

[[Variable Declarations]]