# Ejercicio 6. Generar un fichero JSON con la lista de frutas

XML de entrada:

``` xml

<fruits>
  <fruit>Apple</fruit>
  <fruit>Banana</fruit>
  <fruit>Cherry</fruit>
</fruits>
```

Salida:

```json
[
  "Apple",
  "Banana",
  "Cherry"
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
      <xsl:for-each select="fruits/fruit">
        <xsl:if test="position() > 1">, </xsl:if>
        "<xsl:value-of select="."/>"
      </xsl:for-each>
    ]
  </xsl:template>

</xsl:stylesheet>

```
