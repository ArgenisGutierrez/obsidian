>[!summary] Resumen.
>Lua tiene la funcion _require_ sirve para importar paquetes o módulos, lo que hace es primero buscar por paquetes o módulos con el nombre indicado, si no la encuentra entonces busca un archivo .lua con ese nombre basandose en la variable package.path.
>Puedes renombrar módulos asignándolos a una variable con otro nombre.
>El package.path es una variable global que contiene todas las rutas para los módulos Lua mientras que package.cpath todas para módulos C.

>[!note] Nota.
>Los searchers son funciones que localizan y cargan los módulos, hay 4 definidos pero puedes crear personalizados.
>- Searcher Lua: Busca módulos Lua.
>- Searcher C: Busca módulos C.
>- Searcher Croot: Busca el modulo como una biblioteca C que retorna un constructor de modulo.
>- Searcher All-in-one: Busca el modulo en varias ubicaciones.

[[Lua]]