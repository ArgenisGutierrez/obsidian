>[!summary] Resumen.
>Al parecer Lua no ofrece una funcion completa de patrones con expresiones regulares como conocemos en otros lenguajes, sino que debido a su enfoque minimalista tiene sus propios métodos así como patrones propios.
>- string.find busca un patrón dentro de un objeto string y retorna la posición desde donde inicia hasta donde termina el patrón que coincide.
>- string.match al igual que find busca un patrón pero este retorna la parte del string que coincide con el patrón.
>- string.gsub sustituye el patrón dentro del string por otro.
>- string.gmatch retorna una función que itera sobre todas las coincidencias del patrón en un string.

>[!example] Ejemplos.
```Lua
-- find
s = "hello world"
print(string.find(s,"world")) --> 7 11

--match
print(string.match("hello world", "hello")) --> hello

--gsub
s = string.gsub("Lua is cute", "cute", "great")
print(s) --> Lua is great
s = string.gsub("all lii", "l", "x", 1)
print(s) --> axl lii

-- gmatch
s = "some string"
words = {}
for w in string.gmatch(s, "%a+") do
words[#words + 1] = w
end
```

[[Lua]]