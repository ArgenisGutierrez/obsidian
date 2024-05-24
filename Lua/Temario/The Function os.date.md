>[!summary] Resumen.
>Este metodo retorna la fecha en un formato mas comprensible para el ser humano y se puede modificar su formato con diferentes directivas y haciendo uso de patrones.

| %a  | Dia de la semana abreviado |
| --- | -------------------------- |
| %A  | Dia de la semana           |
| %b  | Abreviacion del mes        |
| %B  | Mes                        |
| %c  | Fecha y hora               |
| %d  | Dia del mes                |
| %H  | Hora en formato 24         |
| %I  | Hora en formato 12         |
| %j  | Dia del año                |
| %m  | Numero de mes              |
| %M  | Minuto                     |
| %p  | AM o PM                    |
| %S  | Segundos                   |
| %w  | Dia de la semana en numero |
| %W  | Semana del año en numero   |
| %x  | Fecha dd/mm/yy             |
| %X  | Hora.                      |
| %y  | Año 2 digitos              |
| %Y  | Año completo               |
| %z  | Zona horaria               |
| %%  | signo de porcentage        |

>[!example] Ejemplo.
```Lua
print(os.date("%Y-%m-%dT%H:%M:%S", t)) --> 1998-09-16T23:48:10
```

[[Lua]]