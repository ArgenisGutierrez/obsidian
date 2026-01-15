>[!summary] Resumen.
>En Lua se puede manipular la fecha y tiempo con los métodos anteriormente vistos para saber por ejemplo cual es la fecha 40 días después o 6 meses después de la fecha actual.

>[!example] Ejemplo.
```Lua
t = os.date("*t") -- get current time
print(os.date("%Y/%m/%d", os.time(t))) --> 2015/08/18
t.month = t.month + 6 -- six months from now
print(os.date("%Y/%m/%d", os.time(t))) --> 2016/02/18
```

[[Lua]]