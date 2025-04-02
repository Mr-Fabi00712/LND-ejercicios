# Ejercicio 1

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

__Pregunta 1.__ Selecciona todos los títulos de los libros.

//book/title

//book/title/text()

__Pregunta 2.__ Selecciona los autores de los libros en el género "Programming".

//book[genre='Programming']/author

//book[genre='Programming']/author/text()

__Pregunta 3.__ Selecciona el precio del libro "The Art of War".

//book[title='The Art of War']/price

//book[title='The Art of War']/price/text()

__Pregunta 4.__ Cuenta cuántos libros tienen más de 20 en stock.

count(//book[stock > 20])

__Pregunta 5.__ Selecciona todos los géneros únicos disponibles en la tienda.

distinct-values(//book/genre)

__Pregunta 6.__ Selecciona el autor cuyo libro cuesta más.

//book[price = max(//price)]/author

//book[price = max(//price)]/author/text()

__Pregunta 7.__ Selecciona el título del libro más barato.

//book[price = min(//price)]/title

//book[price = min(//price)]/title/text()

__Pregunta 8.__ Selecciona todos los libros cuyo precio esté entre 10 y 30.

//book[price >= 10 and price <= 30]

//book[price >= 10 and price <= 30]/title

__Pregunta 9.__ Selecciona todos los libros que tengan menos de 20 unidades en stock.

//book[stock < 20]

//book[stock < 20]/title/text()

__Pregunta 10.__ Selecciona el atributo id de todos los libros.

//book/@id
