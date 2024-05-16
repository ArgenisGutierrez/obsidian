>[!summary] Resumen.
>Los diccionarios en typescript son un poco mas complejos pues se debe definir una interfas para el contenido y a su vez otra para el index del diccionario.

>[!example] Ejemplo.
>```typescript
>//Se crea la interfaz del contenido
>interface Cephalopodo {
>	hasInk:boolean;
>	arms:number;
>	tentacles:number;
>	}
>//Se crea la interfaz del diccionario
>interface CephalopodosDiccionary = {
>[index:string]:Cephalopodo;
>}
>//Se define el diccionario
>let diccionario: CephalopodoDiccionary ={};
>//Se agrega el contenido
>diccionario['octopus vulgaris'] = {hasInk: true, arms: 8, tentacles: 0}
>```

[[Types]]