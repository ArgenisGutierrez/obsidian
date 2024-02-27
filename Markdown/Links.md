Los links se pueden usar para o bien redireccionar a otros archivos, notas o paginas.
La estructura es como las imagenes pero sin el signo !.
[Palabra que resalta] (link)
>[!info] Estructura
>\[Texto que se muestra\]\(url o dir\)

>[!example] Ejemplo
>[Link a google](www.google.com)
>[Link a otra nota](Markdown)

---
## Url y Correos.
Una forma fácil de crear link es encerrarlos en <>.
>[!info] Estructura
>\<correo o ulr\>

>[!example] Ejemplo con <>
><www.google.com>
><argenis.g.gtz@gmail.com>

---
## Dar formato a links.
Se puede dar formato a los links como a los demás textos con negritas o cursiva.
>[!info] Estructura
>\*\*\[texto\]\(url\)\*\*

>[!example] Ejemplo
>**[google](www.google.com)**

---
## Links de referencia.
Se pueden referenciar link para darles un mejor formato cuando o bien los links son muy largos o se hace mucho uso de ese link y posteriormente puede cambiarse.
>[!info] Estructura
>\[Texto\]\[referencia\]
>Para asignar el link:
>\[referencia\]\:url o dir

>[!Example] Ejemplo
>Tenemos un archivo con un link que se repite mucho como [este](link).
>Y este link debe cambiarse, lo que hace tediosa la tarea de cambiar el url en cada link del documento por lo tanto una mejor forma de usar los links es usar una referencia.
>[este][referencia]
>Se puede cambiar fácilmente así [referencia]:url

[Regreso](Markdown)