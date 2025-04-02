# Ejercicio 2: Tienda de Electrónica

Copiar código:

```xml
<electronics>
  <item id="201">
    <name>Smartphone</name>
    <brand>BrandX</brand>
    <price currency="USD">699</price>
    <stock>50</stock>
  </item>
  <item id="202">
    <name>Laptop</name>
    <brand>BrandY</brand>
    <price currency="USD">999</price>
    <stock>10</stock>
  </item>
  <item id="203">
    <name>Tablet</name>
    <brand>BrandX</brand>
    <price currency="USD">399</price>
    <stock>25</stock>
  </item>
  <item id="204">
    <name>Headphones</name>
    <brand>BrandZ</brand>
    <price currency="USD">199</price>
    <stock>100</stock>
  </item>
</electronics>
```

Preguntas:

 __1.Selecciona todos los nombres de productos.__

//name/text

 __2.Selecciona los productos de la marca "BrandX".__

//item[brand="BrandX"]

 __3.Selecciona el producto más barato.__

//item[price = //item/price[not(. > //item/price)]]

 __4.Selecciona el producto más caro.__

//item[price = //item/price[not(. < //item/price)]]

 __5.Selecciona los nombres y precios de productos con más de 30 unidades en stock.__

//item[stock > 30]/name | //item[stock > 30]/price

 __6.Selecciona el atributo currency de todos los precios.__

//price/@currency

 __7.Cuenta cuántos productos hay en stock con menos de 20 unidades.__

count(//item[stock < 20])

 __8.Selecciona los nombres de todos los productos cuyo precio sea mayor a 500.__

//item[price > 500]/name

 __9.Selecciona los nombres de productos con el atributo id mayor a 202.__

//item[@id > 202]/name

 __10.Selecciona todos los nodos completos de productos con "BrandZ".__

//item[brand="BrandZ"]
