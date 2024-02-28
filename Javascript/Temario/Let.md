>[!summary] Resumen
>La palabra reservada _let_ declara variables de alcance local es decir con un [block scope][^1], la cual puede ser inicializada o no.

>[!info] Sintaxis
>let name1;
let name1 = value1;
let name1 = value1, name2 = value2;
let name1, name2 = value2;
let name1 = value1, name2, /* …, */ nameN = valueN;

## Descripción.
Las variables declaradas con _let_ te permiten limitar su alcance al bloque o expresión donde fue declarada a diferencia de _var_ la cual las define en un ámbito global.
Las variables declaradas con _let_ se pueden reasignar para cambiar su valor.

>[!example] Ejemplo
>let nombre = 'Argenis';
>nombre = 'Arfhel';
>let edad = 28;

[[Variable Declarations]]

[^1]: [[Variable Scoopes]]