# Ejercicio 5. Archivo pedidos.xml

```xml

<pedidos>
  <pedido id="1" cliente="Juan">
    <producto>Televisor</producto>
    <cantidad>1</cantidad>
    <precio>400</precio>
  </pedido>
  <pedido id="2" cliente="María">
    <producto>Teléfono</producto>
    <cantidad>2</cantidad>
    <precio>200</precio>
  </pedido>
  <pedido id="3" cliente="Pedro">
    <producto>Ratón</producto>
    <cantidad>5</cantidad>
    <precio>25</precio>
  </pedido>
  <pedido id="4" cliente="Ana">
    <producto>Teclado</producto>
    <cantidad>3</cantidad>
    <precio>30</precio>
  </pedido>
</pedidos>
```

__Ejercicio 1.__ Devuelve los nombres de los clientes.

```XQuery
for $pedido in doc("pedidos.xml")/pedidos/pedido
return $pedido/@cliente
```

__Ejercicio 2.__ Devuelve los productos con precio total (cantidad × precio).

```XQuery
for $pedido in doc("pedidos.xml")/pedidos/pedido
let $precioTotal := xs:decimal($pedido/cantidad) * xs:decimal($pedido/precio)
return <item>
           <producto>{$pedido/producto}</producto>
           <precioTotal>{$precioTotal}</precioTotal>
       </item>
```

__Ejercicio 3.__ Filtra los pedidos cuyo precio total sea mayor a 100.

```XQuery
for $pedido in doc("pedidos.xml")/pedidos/pedido
let $precioTotal := xs:decimal($pedido/cantidad) * xs:decimal($pedido/precio)
where $precioTotal > 100
return <item>
           <cliente>{$pedido/@cliente}</cliente>
           <producto>{$pedido/producto}</producto>
           <precioTotal>{$precioTotal}</precioTotal>
       </item>
```

__Ejercicio 4.__ Calcula el precio promedio de todos los pedidos.

```XQuery
let $totalPrecio := 
    sum(
        for $pedido in doc("pedidos.xml")/pedidos/pedido
        return xs:decimal($pedido/cantidad) * xs:decimal($pedido/precio)
    )
let $totalPedidos := count(doc("pedidos.xml")/pedidos/pedido)
return $totalPrecio div $totalPedidos
```

__Ejercicio 5.__ Devuelve el pedido más caro.

```XQuery
for $pedido in doc("pedidos.xml")/pedidos/pedido
let $precioTotal := xs:decimal($pedido/cantidad) * xs:decimal($pedido/precio)
return <item>
           <cliente>{$pedido/@cliente}</cliente>
           <producto>{$pedido/producto}</producto>
           <precioTotal>{$precioTotal}</precioTotal>
       </item>
order by $precioTotal descending
limit 1
```

__Ejercicio 6.__ Ordena los pedidos por cliente alfabéticamente.

```XQuery
for $pedido in doc("pedidos.xml")/pedidos/pedido
return <item>
           <cliente>{$pedido/@cliente}</cliente>
           <producto>{$pedido/producto}</producto>
           <cantidad>{$pedido/cantidad}</cantidad>
           <precio>{$pedido/precio}</precio>
       </item>
order by $pedido/@cliente ascending
```

__Ejercicio 7.__ Calcula el precio total de todos los pedidos.

```XQuery
let $totalPrecio := 
    sum(
        for $pedido in doc("pedidos.xml")/pedidos/pedido
        return xs:decimal($pedido/cantidad) * xs:decimal($pedido/precio)
    )
return $totalPrecio
```

__Ejercicio 8.__ Devuelve los nombres de los clientes que compraron más de 3 unidades.

```XQuery
for $pedido in doc("pedidos.xml")/pedidos/pedido
let $totalCantidad := xs:decimal($pedido/cantidad)
where $totalCantidad > 3
return $pedido/@cliente
```

__Ejercicio 9.__ Devuelve los productos y sus precios con un descuento del 15% (usa let).

```XQuery
for $pedido in doc("pedidos.xml")/pedidos/pedido
let $precioConDescuento := xs:decimal($pedido/precio) * 0.85
return <item>
           <producto>{$pedido/producto}</producto>
           <precioConDescuento>{$precioConDescuento}</precioConDescuento>
       </item>
```

__Ejercicio 10.__ Cuenta el número total de pedidos.

```XQuery
let $totalPedidos := count(doc("pedidos.xml")/pedidos/pedido)
return $totalPedidos
```
