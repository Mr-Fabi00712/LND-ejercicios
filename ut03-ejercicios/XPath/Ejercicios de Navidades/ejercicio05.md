# Ejercicio 5

```xml

<inventory>
  <product id="P001">
    <name>Chair</name>
    <category>Furniture</category>
    <price currency="USD">49.99</price>
    <stock>200</stock>
  </product>
  <product id="P002">
    <name>Table</name>
    <category>Furniture</category>
    <price currency="USD">129.99</price>
    <stock>50</stock>
  </product>
  <product id="P003">
    <name>Lamp</name>
    <category>Lighting</category>
    <price currency="USD">19.99</price>
    <stock>100</stock>
  </product>
  <product id="P004">
    <name>Desk</name>
    <category>Furniture</category>
    <price currency="USD">249.99</price>
    <stock>20</stock>
  </product>
  <product id="P005">
    <name>Ceiling Light</name>
    <category>Lighting</category>
    <price currency="USD">79.99</price>
    <stock>30</stock>
  </product>
</inventory>
```

__Pregunta 1.__ Selecciona los nombres de todos los productos.

//product/name

__Pregunta 2.__ Selecciona todos los productos de la categoría "Furniture".

//product[category='Furniture']

__Pregunta 3.__ Selecciona el precio del producto "Lamp".

//product[name='Lamp']/price

__Pregunta 4.__ Cuenta cuántos productos tienen más de 50 en stock.

count(//product[stock > 50])

__Pregunta 5.__ Selecciona el producto más caro.

//product[price = max(//product/price)]

__Pregunta 6.__ Selecciona los nombres de los productos con menos de 30 en stock.

//product[stock < 30]/name

__Pregunta 7.__ Selecciona todos los precios en USD.

//product/price[@currency='USD']

__Pregunta 8.__ Selecciona el ID de todos los productos de la categoría "Lighting".

//product[category='Lighting']/@id

__Pregunta 9.__ Selecciona el precio del producto más barato.

//product[price = min(//product/price)]

__Pregunta 10.__ Selecciona los nombres y precios de todos los productos ordenados por precio.

XPath por sí solo no soporta ordenación de resultados, por lo que no se puede ordenar directamente con una consulta XPath. Sin embargo, con XQuery si se puede hacer, y sería de la siguiente manera:

```XQuery

for $product in //product
let $price := $product/price
order by $price
return <result>
  <name>{ $product/name }</name>
  <price>{ $price }</price>
</result>
```
