# Ejercicio 4

```xml

<musicCatalog>
  <album id="101">
    <title>Thriller</title>
    <artist>Michael Jackson</artist>
    <genre>Pop</genre>
    <price currency="USD">15.99</price>
    <stock>50</stock>
  </album>
  <album id="102">
    <title>The Dark Side of the Moon</title>
    <artist>Pink Floyd</artist>
    <genre>Rock</genre>
    <price currency="USD">20.99</price>
    <stock>30</stock>
  </album>
  <album id="103">
    <title>Back in Black</title>
    <artist>AC/DC</artist>
    <genre>Rock</genre>
    <price currency="USD">18.50</price>
    <stock>25</stock>
  </album>
  <album id="104">
    <title>21</title>
    <artist>Adele</artist>
    <genre>Pop</genre>
    <price currency="USD">12.99</price>
    <stock>100</stock>
  </album>
  <album id="105">
    <title>Abbey Road</title>
    <artist>The Beatles</artist>
    <genre>Rock</genre>
    <price currency="USD">19.99</price>
    <stock>10</stock>
  </album>
</musicCatalog>
```

__Pregunta 1.__ Selecciona todos los títulos de los álbumes.

//album/title

__Pregunta 2.__ Selecciona los títulos de los álbumes del género "Rock".

//album[genre='Rock']/title

__Pregunta 3.__ Selecciona el precio del álbum "21".

//album[title='21']/price

__Pregunta 4.__ Cuenta cuántos álbumes tienen más de 20 en stock.

count(//album[stock > 20])

__Pregunta 5.__ Selecciona los nombres de los artistas cuyos álbumes cuestan más de 18 USD.

//album[price > 18]/artist

__Pregunta 6.__ Selecciona el álbum más caro.

//album[price = max(//album/price)]

__Pregunta 7.__ Selecciona el género del álbum "Thriller".

//album[title='Thriller']/genre

__Pregunta 8.__ Selecciona el ID de todos los álbumes de la artista "Adele".

//album[artist='Adele']/@id

__Pregunta 9.__ Selecciona los álbumes con menos de 30 en stock.

//album[stock < 30]

__Pregunta 10.__ Selecciona todos los géneros únicos disponibles.

distinct-values(//album/genre)

//album/genre[not(. = preceding::genre)]
