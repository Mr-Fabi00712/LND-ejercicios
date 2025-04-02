# Ejercicio 2. Archivo tienda.xml

```xml

<tienda>
  <producto id="1" categoria="Computadoras">
    <nombre>Portátil</nombre>
    <marca>HP</marca>
    <precio moneda="USD">800</precio>
  </producto>
  <producto id="2" categoria="Accesorios">
    <nombre>Monitor</nombre>
    <marca>Dell</marca>
    <precio moneda="USD">200</precio>
  </producto>
  <producto id="3" categoria="Accesorios">
    <nombre>Ratón</nombre>
    <marca>Logitech</marca>
    <precio moneda="USD">25</precio>
  </producto>
  <producto id="4" categoria="Computadoras">
    <nombre>Escritorio</nombre>
    <marca>Lenovo</marca>
    <precio moneda="USD">600</precio>
  </producto>
  <producto id="5" categoria="Impresoras">
    <nombre>Impresora</nombre>
    <marca>Canon</marca>
    <precio moneda="USD">150</precio>
  </producto>
</tienda>
```

__Pregunta 1.__ Devuelve los nombres de todos los productos.

```XQuery

for $producto in doc("tienda.xml")/tienda/producto
return $producto/nombre
```

__Pregunta 2.__ Devuelve los productos de la categoría "Accesorios".

```XQuery

for $producto in doc("tienda.xml")/tienda/producto
where $producto/@categoria = "Accesorios"
return $producto
```

__Pregunta 3.__ Calcula el precio total de todos los productos.

```XQuery

let $precios := for $producto in doc("tienda.xml")/tienda/producto
                return xs:decimal($producto/precio)
return sum($precios)
```

__Pregunta 4.__ Encuentra productos con un precio mayor a 500 USD.

```XQuery

for $producto in doc("tienda.xml")/tienda/producto
where xs:decimal($producto/precio) > 500
return $producto
```

__Pregunta 5.__ Devuelve los productos y sus precios con un descuento del 10%.

```XQuery

for $producto in doc("tienda.xml")/tienda/producto
let $precioOriginal := xs:decimal($producto/precio)
let $precioConDescuento := $precioOriginal * 0.9
return <productoConDescuento>
           <nombre>{$producto/nombre}</nombre>
           <precioOriginal>{$producto/precio}</precioOriginal>
           <precioConDescuento>{$precioConDescuento}</precioConDescuento>
       </productoConDescuento>
```

__Pregunta 6.__ Lista los productos ordenados por precio de menor a mayor.

```XQuery

for $producto in doc("tienda.xml")/tienda/producto
let $precio := xs:decimal($producto/precio)
return <productoOrdenado>
           <nombre>{$producto/nombre}</nombre>
           <precio>{$producto/precio}</precio>
       </productoOrdenado>
order by $precio ascending
```

__Pregunta 7.__ Devuelve los productos de la marca "HP".

```XQuery

for $producto in doc("tienda.xml")/tienda/producto
where $producto/marca = "HP"
return $producto
```

__Pregunta 8.__ Devuelve los nombres y categorías de los productos como elementos <'item'>.

```XQuery

for $producto in doc("tienda.xml")/tienda/producto
return <item>
           <nombre>{$producto/nombre}</nombre>
           <categoria>{$producto/@categoria}</categoria>
       </item>
```

__Pregunta 9.__ Encuentra el producto más barato.

```XQuery

for $producto in doc("tienda.xml")/tienda/producto
let $precio := xs:decimal($producto/precio)
return <productoMasBarato>
           <nombre>{$producto/nombre}</nombre>
           <precio>{$producto/precio}</precio>
       </productoMasBarato>
order by $precio ascending
limit 1
```

__Pregunta 10.__ Calcula el precio promedio de los productos en la categoría "Computadoras".

```XQuery

let $precios := for $producto in doc("tienda.xml")/tienda/producto
                where $producto/@categoria = "Computadoras"
                return xs:decimal($producto/precio)
return sum($precios) div count($precios)
```
