# Ejercicio 4. Generar un fichero HTML donde se resalten los productos con precio mayor a 500 en negrita 'b'

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

```HTML

<p><b>Laptop</b> - $1000</p>
<p>Mouse - $25</p>
```

__Solución:__

```xslt

<?xml version="1.0" encoding="UTF-8"?>
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
  <xsl:output method="html" indent="yes"/>

  <!-- Plantilla principal -->
  <xsl:template match="/">
    <xsl:for-each select="products/product">
      <p>
        <xsl:choose>
          <!-- Si el precio es mayor a 500, resaltar el nombre en negrita -->
          <xsl:when test="price &gt; 500">
            <b><xsl:value-of select="name"/></b> - $<xsl:value-of select="price"/>
          </xsl:when>
          <!-- Si el precio no es mayor a 500, mostrar normalmente -->
          <xsl:otherwise>
            <xsl:value-of select="name"/> - $<xsl:value-of select="price"/>
          </xsl:otherwise>
        </xsl:choose>
      </p>
    </xsl:for-each>
  </xsl:template>

</xsl:stylesheet>
```
