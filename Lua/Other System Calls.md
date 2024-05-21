>[!summary] Resumen.
>Lua tiene una librería relacionada con el sistema operativo(os) que contiene diversos métodos que pueden ser útiles.
>- os.exit que termina la ejecución de un programa, este recibe 2 parámetros opcionales el primero indica del éxito de ejecución del programa(0 o true) o bien su fallo(1 o false) y el segundo parámetro si es true libera toda la memoria usada por el programa.
>- os.getenv obtiene las variables de entorno del sistema.
>- os.date obtiene la fecha del sistema.
>- os.clock obtiene el aproximado de segundos de cpu usado por el programa.
>- etc

>[!example] Ejemplo.
```Lua
print(os.date()) --> Mon May 20 18:01:20 2024
print(os.getenv("HOME")) --> /home/arfhel
```

[[Lua]]