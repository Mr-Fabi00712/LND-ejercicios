1. Ejercicio: Crear una Lista HTML

XML de entrada:

<fruits>
  <fruit>Apple</fruit>
  <fruit>Banana</fruit>
  <fruit>Cherry</fruit>
</fruits>

Instrucciones:

Generar una lista HTML desordenada (<ul>) con los nombres de las frutas.

Solución:

<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">
  <xsl:output method="html" indent="yes"/>

  <xsl:template match="/">
    <html>
      <body>
        <ul>
          <xsl:for-each select="fruits/fruit">
            <li><xsl:value-of select="."/></li>
          </xsl:for-each>
        </ul>
      </body>
    </html>
  </xsl:template>
</xsl:stylesheet>

Resultado:

<ul>
  <li>Apple</li>
  <li>Banana</li>
  <li>Cherry</li>
</ul>