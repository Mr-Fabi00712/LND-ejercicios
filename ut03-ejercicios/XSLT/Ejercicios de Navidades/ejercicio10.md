# Ejercicio 10. Crear un fichero JSON con los titulos de secciones y su contenido

XML de entrada:

```xml

<document>
  <section>
    <title>Introduction</title>
    <content>Welcome to this tutorial.</content>
  </section>
  <section>
    <title>Chapter 1</title>
    <content>This is the first chapter.</content>
  </section>
</document>
```

Salida:

```json

[
  {
    "title": "Introduction",
    "content": "Welcome to this tutorial."
  },
  {
    "title": "Chapter 1",
    "content": "This is the first chapter."
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
      <xsl:for-each select="document/section">
        <xsl:if test="position() > 1">, </xsl:if>
        {
          "title": "<xsl:value-of select="title"/>",
          "content": "<xsl:value-of select="content"/>"
        }
      </xsl:for-each>
    ]
  </xsl:template>

</xsl:stylesheet>
```
