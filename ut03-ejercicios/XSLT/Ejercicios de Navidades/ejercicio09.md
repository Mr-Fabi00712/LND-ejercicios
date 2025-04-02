# Ejercicio 9. Crear un fichero JSON con las categorías y los productos

XML de entrada:

```xml

<store>
  <category name="Electronics">
    <product>
      <name>Laptop</name>
      <price>1000</price>
    </product>
    <product>
      <name>Smartphone</name>
      <price>700</price>
    </product>
  </category>
  <category name="Books">
    <product>
      <name>1984</name>
      <price>15.99</price>
    </product>
    <product>
      <name>Brave New World</name>
      <price>12.49</price>
    </product>
  </category>
</store>
```

Salida:

```json

{
  "Electronics": [
    {
      "name": "Laptop",
      "price": 1000
    },
    {
      "name": "Smartphone",
      "price": 700
    }
  ],
  "Books": [
    {
      "name": "1984",
      "price": 15.99
    },
    {
      "name": "Brave New World",
      "price": 12.49
    }
  ]
}
```

__Solución:__

```xslt

<?xml version="1.0" encoding="UTF-8"?>
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
  <xsl:output method="text" indent="no"/>

  <!-- Plantilla principal -->
  <xsl:template match="/">
    {
      <xsl:for-each select="store/category">
        <xsl:if test="position() > 1">, </xsl:if>
        "<xsl:value-of select="@name"/>": [
          <xsl:for-each select="product">
            <xsl:if test="position() > 1">, </xsl:if>
            {
              "name": "<xsl:value-of select="name"/>",
              "price": <xsl:value-of select="price"/>
            }
          </xsl:for-each>
        ]
      </xsl:for-each>
    }
  </xsl:template>

</xsl:stylesheet>
```
