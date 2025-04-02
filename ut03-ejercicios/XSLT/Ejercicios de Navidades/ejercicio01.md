# Ejercicio 1. Generar mediante XSLT una lista HTML desordenada 'ul' con los nombres de las frutas. a partir del siguiente HTML

XML de entrada:

```xml

<fruits>
  <fruit>Apple</fruit>
  <fruit>Banana</fruit>
  <fruit>Cherry</fruit>
</fruits>
```

Salida:

```xml

<ul>
  <li>Apple</li>
  <li>Banana</li>
  <li>Cherry</li>
</ul>
```

__Solución:__

```xml

<?xml version="1.0" encoding="UTF-8"?>
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
  <xsl:output method="html" indent="yes"/>

  <!-- Plantilla principal -->
  <xsl:template match="/">
    <ul>
      <!-- Iterar sobre los elementos 'fruit' -->
      <xsl:for-each select="fruits/fruit">
        <li><xsl:value-of select="."/></li>
      </xsl:for-each>
    </ul>
  </xsl:template>

</xsl:stylesheet>
```
