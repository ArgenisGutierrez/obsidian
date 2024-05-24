>[!summary] Resume.
>Lua cuenta con un método que permite ejecutar comandos de sistema _os.execute_ que recibe un string con el comando a ejecutar y retorna:
>- Un string con la información obtenida.
>- Un boolean que indica que se ejecuto sin errores el comando.
>- Seguido de 2 posibles strings _exit_ si el programa termino normalmente o _signal_ si el programa fue interrumpido por alguna señal.
>- El numero de la señal al terminal el programa.

>[!note] Nota.
>Otro metodo util es _io.popen_ que al igual que execute te permite ejecutar comandos de sistema pero este permite conectar el output o input a un programa.

>[!example] Ejemplos.
```Lua
-- Execute
os.execute("ls") -- directorios true exit 0
-- Popen
local handle = io.popen("echo Hello, World!") 
local result = handle:read("*all") 
handle:close() 
print(result)  -- Imprime: Hello, World!`
```

[[Lua]]