# Ejercicio 5. Generar un fichero HTML con una lista de navegación 'nav'

XML de entrada:

```xml

<menu>
  <item>Home</item>
  <item>About</item>
  <item>Contact</item>
</menu>
```

Salida:

```HTML

<nav>
  <ul>
    <li>Home</li>
    <li>About</li>
    <li>Contact</li>
  </ul>
</nav>
```

__Solución:__

```xslt

<?xml version="1.0" encoding="UTF-8"?>
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
  <xsl:output method="html" indent="yes"/>

  <!-- Plantilla principal -->
  <xsl:template match="/">
    <nav>
      <ul>
        <xsl:for-each select="menu/item">
          <li><xsl:value-of select="."/></li>
        </xsl:for-each>
      </ul>
    </nav>
  </xsl:template>

</xsl:stylesheet>
```
