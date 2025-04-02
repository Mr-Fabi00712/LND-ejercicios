# Ejercicio 7. Crear un fichero JSON con los productos y sus respectivos precios

XML de entrada:

```xml

<products>
  <product>
    <name>Laptop</name>
    <price>1000</price>
  </product>
  <product>
    <name>Mouse</name>
    <price>25</price>
  </product>
</products>
```

Salida:

```json

[
  {
    "name": "Laptop",
    "price": 1000
  },
  {
    "name": "Mouse",
    "price": 25
  }
]
```

__Solución:__

```xslt

<?xml version="1.0" encoding="UTF-8"?>
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
  <xsl:output method="text" indent="no"/>

  <!-- Plantilla principal -->
  <xsl:template match="/">
    [
      <xsl:for-each select="products/product">
        <xsl:if test="position() > 1">, </xsl:if>
        {
          "name": "<xsl:value-of select="name"/>",
          "price": <xsl:value-of select="price"/>
        }
      </xsl:for-each>
    ]
  </xsl:template>

</xsl:stylesheet>
```
