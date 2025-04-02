# Ejercicio 2. Crear una tabla HTML de libros con las columnas "Título" y "Autor"

XML de entrada:

```xml

<library>
  <book>
    <title>1984</title>
    <author>George Orwell</author>
  </book>
  <book>
    <title>Brave New World</title>
    <author>Aldous Huxley</author>
  </book>
</library>
```

Salida:

```xml

<table border="1">
  <tr>
    <th>Title</th>
    <th>Author</th>
  </tr>
  <tr>
    <td>1984</td>
    <td>George Orwell</td>
  </tr>
  <tr>
    <td>Brave New World</td>
    <td>Aldous Huxley</td>
  </tr>
</table>
```

__Solución:__

```xslt

<?xml version="1.0" encoding="UTF-8"?>
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
  <xsl:output method="html" indent="yes"/>

  <!-- Plantilla principal -->
  <xsl:template match="/">
    <table border="1">
      <tr>
        <th>Title</th>
        <th>Author</th>
      </tr>
      <!-- Iterar sobre los elementos 'book' -->
      <xsl:for-each select="library/book">
        <tr>
          <td><xsl:value-of select="title"/></td>
          <td><xsl:value-of select="author"/></td>
        </tr>
      </xsl:for-each>
    </table>
  </xsl:template>

</xsl:stylesheet>
```
