# Ejercicio 1. Archivo biblioteca.xml

```xml

<biblioteca>
  <libro id="1" genero="Ficción">
    <titulo>1984</titulo>
    <autor pais="Reino Unido">George Orwell</autor>
    <precio moneda="USD">19.99</precio>
  </libro>
  <libro id="2" genero="Ciencia Ficción">
    <titulo>Brave New World</titulo>
    <autor pais="Reino Unido">Aldous Huxley</autor>
    <precio moneda="USD">14.99</precio>
  </libro>
  <libro id="3" genero="Distopía">
    <titulo>Fahrenheit 451</titulo>
    <autor pais="EE.UU.">Ray Bradbury</autor>
    <precio moneda="USD">12.50</precio>
  </libro>
  <libro id="4" genero="Ficción">
    <titulo>To Kill a Mockingbird</titulo>
    <autor pais="EE.UU.">Harper Lee</autor>
    <precio moneda="USD">18.99</precio>
  </libro>
  <libro id="5" genero="Ficción">
    <titulo>The Great Gatsby</titulo>
    <autor pais="EE.UU.">F. Scott Fitzgerald</autor>
    <precio moneda="USD">10.99</precio>
  </libro>
</biblioteca>
```

__Pregunta 1.__ Devuelve todos los títulos de los libros.

```XQuery

for $libro in doc("biblioteca.xml")/biblioteca/libro
return $libro/titulo
```

__Pregunta 2.__ Devuelve los títulos de libros cuyo precio es mayor a 15.

```XQuery

for $libro in doc("biblioteca.xml")/biblioteca/libro
where xs:decimal($libro/precio) > 15
return $libro/titulo
```

__Pregunta 3.__ Lista los autores y sus países de origen.

```XQuery

for $libro in doc("biblioteca.xml")/biblioteca/libro
return <autorPais>
  {$libro/autor}, {$libro/autor/@pais}
</autorPais>
```

__Pregunta 4.__ Calcula el precio promedio de los libros.

```XQuery

let $precios := for $libro in doc("biblioteca.xml")/biblioteca/libro
                return xs:decimal($libro/precio)
return avg($precios)
```

__Pregunta 5.__ Devuelve los títulos ordenados alfabéticamente.

```XQuery

for $libro in doc("biblioteca.xml")/biblioteca/libro
let $titulo := $libro/titulo
return $titulo
order by $titulo
```

__Pregunta 6.__ Devuelve los títulos y precios de los libros en formato XML.

```XQuery

for $libro in doc("biblioteca.xml")/biblioteca/libro
return <libroInfo>
           <titulo>{$libro/titulo}</titulo>
           <precio>{$libro/precio}</precio>
       </libroInfo>
```

__Pregunta 7.__ Encuentra libros del género "Ficción".

```XQuery

for $libro in doc("biblioteca.xml")/biblioteca/libro
where $libro/@genero = "Ficción"
return $libro
```

__Pregunta 8.__ Devuelve los libros cuyo autor sea de "EE.UU.".

```XQuery

for $libro in doc("biblioteca.xml")/biblioteca/libro
where $libro/autor/@pais = "EE.UU."
return $libro
```

__Pregunta 9.__ Lista los libros y su precio total (precio + 5 USD de impuesto).

```XQuery

for $libro in doc("biblioteca.xml")/biblioteca/libro
let $precio := xs:decimal($libro/precio) + 5
return <libroTotal>
           <titulo>{$libro/titulo}</titulo>
           <precioOriginal>{$libro/precio}</precioOriginal>
           <precioConImpuesto>{$precio}</precioConImpuesto>
       </libroTotal>
```

__Pregunta 10.__ Devuelve el libro más caro en el catálogo.

```XQuery

for $libro in doc("biblioteca.xml")/biblioteca/libro
let $precio := xs:decimal($libro/precio)
return <libroMasCaro>
           <titulo>{$libro/titulo}</titulo>
           <precio>{$libro/precio}</precio>
       </libroMasCaro>
order by $precio descending
limit 1
```
