# Ejercicio 1: Tienda de Libros

```xml
<bookstore>
  <book id="101">
    <title>Clean Code</title>
    <author>Robert C. Martin</author>
    <genre>Programming</genre>
    <price currency="USD">32.99</price>
    <stock>20</stock>
  </book>
  <book id="102">
    <title>The Pragmatic Programmer</title>
    <author>Andrew Hunt</author>
    <genre>Programming</genre>
    <price currency="USD">40.50</price>
    <stock>15</stock>
  </book>
  <book id="103">
    <title>1984</title>
    <author>George Orwell</author>
    <genre>Fiction</genre>
    <price currency="USD">12.99</price>
    <stock>50</stock>
  </book>
  <book id="104">
    <title>The Art of War</title>
    <author>Sun Tzu</author>
    <genre>Philosophy</genre>
    <price currency="USD">9.99</price>
    <stock>30</stock>
  </book>
  <book id="105">
    <title>Thinking, Fast and Slow</title>
    <author>Daniel Kahneman</author>
    <genre>Psychology</genre>
    <price currency="USD">20.00</price>
    <stock>10</stock>
  </book>
</bookstore>
```

Preguntas

__1.Selecciona todos los títulos de los libros.__

//title/text()

__2.Selecciona los autores de los libros en el género "Programming".__

//book[genre="Programming"]/author/text()

__3.Selecciona el precio del libro "The Art of War".__

//book[title="The Art of War"]/price/text()

__4.Cuenta cuántos libros tienen más de 20 en stock.__

//book[stock < 20]

__5.Selecciona todos los géneros únicos disponibles en la tienda.__

distinct-values(//genre/text())

__6.Selecciona el autor cuyo libro cuesta más.__

//book/price[not(. < //book/price)]

//book[price = max(//price)]/author/text()

__7.Selecciona el título del libro más barato.__

//book/price[not(. > //book/price)]

//book[price = min(//price)]/title/text()

__8.Selecciona todos los libros cuyo precio esté entre 10 y 30.__

//book[price >= 10 and price <= 30]

__9.Selecciona todos los libros que tengan menos de 20 unidades en stock.__

//book[stock < 20]

se le puede añadir /title/text()

__10.Selecciona el atributo id de todos los libros.__

//book/@id
