# Ejercicio 8. Crear un Objeto JSON con los nombres de usuarios

XML de entrada:

```xml

<users>
  <user>
    <id>1</id>
    <name>John Doe</name>
    <email>john@example.com</email>
  </user>
  <user>
    <id>2</id>
    <name>Jane Smith</name>
    <email>jane@example.com</email>
  </user>
</users>
```

Salida:

```json
[
  {
    "id": "1",
    "name": "John Doe",
    "email": "john@example.com"
  },
  {
    "id": "2",
    "name": "Jane Smith",
    "email": "jane@example.com"
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
      <xsl:for-each select="users/user">
        <xsl:if test="position() > 1">, </xsl:if>
        {
          "id": "<xsl:value-of select="id"/>",
          "name": "<xsl:value-of select="name"/>",
          "email": "<xsl:value-of select="email"/>"
        }
      </xsl:for-each>
    ]
  </xsl:template>

</xsl:stylesheet>
```
