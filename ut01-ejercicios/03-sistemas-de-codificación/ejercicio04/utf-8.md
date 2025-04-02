# Ejercicio 4

Indica cuántos bytes tiene cada carácter de la siguiente frase para una codificación UTF-8 ¿Cuántos bytes en total tiene la frase?

```text
!Gracias por alegrarme el día!😀
```

__¡ACLARACIÓN!:__ Debido a que en los apuntes no se especifica bien, los carácteres que usen entre 3-4 bytes los consideraremos con un valor de 4 bytes.

## Número de bytes en la frase:

+ __Carácteres de 1 byte:__ "!"(x2) , "r"(x4) , "a"(x5) , "c" , "i" , "s" , "p" , "o" , "l"(x2) , "e"(x3) , "g" , "m" , "d"

24 (carácteres) x 1 (byte) = 24 bytes

+ __Carácteres de 4 bytes:__"í" y "😀"

2 (carácteres) x 4 (byte) = 8 bytes

## Resultado

24 + 8 = 32 bytes tiene la frase "!Gracias por alegrarme el día!😀"
