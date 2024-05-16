>[!summary] Resumen.
>El interprete de lua admite diferentes flags para las opciones asi como argumentos como un script de bash.
>lua \[options\] \[script \[args\]\]
>Flags:
>- -i modo interactivo
>- -l carga una libreria
>
>Argumentos:
>lua - e "sin=math.sin" script ab
>arg[-3] = "lua"
>arg[-2] = "-e"
>arg[-1] = "sin=math.sin"
>arg[0] = "script"
>arg[1] = "a"
>arg[2] = "b"

[[Lua]]