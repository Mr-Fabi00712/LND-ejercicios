# Ejercicio 3: Biblioteca Digital

```xml
<library>
  <book id="301">
    <title>The Catcher in the Rye</title>
    <author>J.D. Salinger</author>
    <genre>Fiction</genre>
    <available>true</available>
  </book>
  <book id="302">
    <title>To Kill a Mockingbird</title>
    <author>Harper Lee</author>
    <genre>Fiction</genre>
    <available>false</available>
  </book>
  <book id="303">
    <title>The Great Gatsby</title>
    <author>F. Scott Fitzgerald</author>
    <genre>Fiction</genre>
    <available>true</available>
  </book>
  <book id="304">
    <title>1984</title>
    <author>George Orwell</author>
    <genre>Dystopian</genre>
    <available>true</available>
  </book>
  <book id="305">
    <title>Moby Dick</title>
    <author>Herman Melville</author>
    <genre>Adventure</genre>
    <available>false</available>
  </book>
</library>
```

Preguntas:

__1.Selecciona todos los títulos de los libros.__

//book/title

__2.Selecciona todos los libros disponibles (con available="true").__

//book[available="true"]

//book[available="true"]/title/text()

__3.Selecciona el autor del libro "1984".__

//book[title="1984"]/author

//book[title="1984"]/author/text()

__4.Selecciona todos los géneros de libros únicos.__

//book/genre[not(. = preceding-sibling::genre)]

//book/genre[not(. = preceding-sibling::genre)]/text()

__5.Cuenta cuántos libros están disponibles.__

count(//book[available="true"])

__6.Selecciona los títulos de los libros que no están disponibles.__

//book[available="false"]/title/text()

__7.Selecciona los autores cuyos libros están disponibles.__

//book[available="true"]/author/text()

__8.Selecciona el ID del libro "The Great Gatsby".__

//book[title="The Great Gatsby"]/@id

__9.Selecciona todos los libros del género "Fiction".__

//book[genre="Fiction"]

//book[genre="Fiction"]/title/text()

__10.Selecciona los títulos de los libros cuyo autor es "Herman Melville".__

//book[author="Herman Melville"]/title/text()
