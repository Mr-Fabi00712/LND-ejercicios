# Ejercicio 3. Archivo musica.xml

```xml

<catalogo>
  <album id="1" genero="Rock">
    <titulo>The Dark Side of the Moon</titulo>
    <artista>Pink Floyd</artista>
    <anio>1973</anio>
    <precio>20.00</precio>
  </album>
  <album id="2" genero="Pop">
    <titulo>Thriller</titulo>
    <artista>Michael Jackson</artista>
    <anio>1982</anio>
    <precio>18.00</precio>
  </album>
  <album id="3" genero="Rock">
    <titulo>Abbey Road</titulo>
    <artista>The Beatles</artista>
    <anio>1969</anio>
    <precio>25.00</precio>
  </album>
  <album id="4" genero="Jazz">
    <titulo>Kind of Blue</titulo>
    <artista>Miles Davis</artista>
    <anio>1959</anio>
    <precio>15.00</precio>
  </album>
</catalogo>
```

__Pregunta 1.__ Devuelve todos los títulos de los álbumes.

```XQuery
for $album in doc("musica.xml")/catalogo/album
return $album/titulo
```

__Pregunta 2.__ Devuelve los álbumes cuyo precio es mayor a 18.

```XQuery

for $album in doc("musica.xml")/catalogo/album
where xs:decimal($album/precio) > 18
return $album
```

__Pregunta 3.__ Lista los títulos y géneros de todos los álbumes.

```XQuery
for $album in doc("musica.xml")/catalogo/album
return <item>
           <titulo>{$album/titulo}</titulo>
           <genero>{$album/@genero}</genero>
       </item>
```

__Pregunta 4.__ Calcula el precio promedio de los álbumes (usa let).

```XQuery
let $precios := for $album in doc("musica.xml")/catalogo/album
                return xs:decimal($album/precio)
return sum($precios) div count($precios)
```

__Pregunta 5.__ Encuentra los álbumes de género "Rock".

```XQuery
for $album in doc("musica.xml")/catalogo/album
where $album/@genero = "Rock"
return $album
```

__Pregunta 6.__ Ordena los álbumes por año de lanzamiento.

```XQuery
for $album in doc("musica.xml")/catalogo/album
let $anio := xs:decimal($album/anio)
return <albumOrdenado>
           <titulo>{$album/titulo}</titulo>
           <artista>{$album/artista}</artista>
           <anio>{$album/anio}</anio>
           <precio>{$album/precio}</precio>
       </albumOrdenado>
order by $anio ascending
```

__Pregunta 7.__ Devuelve el álbum más caro.

```XQuery
for $album in doc("musica.xml")/catalogo/album
let $precio := xs:decimal($album/precio)
return <albumMasCaro>
           <titulo>{$album/titulo}</titulo>
           <artista>{$album/artista}</artista>
           <anio>{$album/anio}</anio>
           <precio>{$album/precio}</precio>
       </albumMasCaro>
order by $precio descending
limit 1
```

__Pregunta 8.__ Devuelve los títulos y los precios con un descuento del 20%.

```XQuery
for $album in doc("musica.xml")/catalogo/album
let $precioConDescuento := xs:decimal($album/precio) * 0.80
return <item>
           <titulo>{$album/titulo}</titulo>
           <precioConDescuento>{$precioConDescuento}</precioConDescuento>
       </item>
```

__Pregunta 9.__ Devuelve los álbumes lanzados antes de 1975.

```XQuery

for $album in doc("musica.xml")/catalogo/album
where xs:decimal($album/anio) < 1975
return $album
```

__Pregunta 10.__ Calcula el precio total de todos los álbumes.

```XQuery

let $precios := for $album in doc("musica.xml")/catalogo/album
                return xs:decimal($album/precio)
return sum($precios)
```
