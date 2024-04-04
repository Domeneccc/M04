# Apunts de M04 en Markdown




## Index

1. XML
   - Explicació bàsica  el que farem amb XML
3. DOM
   - Explicació deL funcionament DOM
   - Exemples de minidom amb Python 
5. XSLT i XPath
   - Explicació de XPath
   - Exemples de XPath
   - Explicació de XSLT amb teoria
   - Exemples de XSLT
   


# XML

## Explicació bàsica d'XML i el que farem

Para comenzar en la uf 2 de **XML** entra Dom que es fa amb python que hi hauran varis exemples de ejercicis, despres tambe hi ha **xslt** amb xpath cada un explicats 


# DOM


# XSLT i XPath

## XSLT 

### Què és XSLT?

El **XSLT** ve de eXtensible Stylesheet Language Transformations que significa que es un lleguatge que serveix per donar estill a un document xml que es com el css del html per es oer al **xml**. Normalment el arxiu que son de entrada son xml, també poden ser altres tipus de formats. Hi ha processadors de XSLT en llenguatges com C, C++, Java, Python, Perl, Javascript.
![image](https://github.com/Domeneccc/M04/assets/165904493/4ca58661-f272-4cc6-bfe5-b6eacf3934a6)



Els navegador webs més habituals (Safari, Chrome, Firefox, microsoft Edge, Opera,...) porten un processador de XSLT incorporat, pero hi ha que activar una opcio especial per poder ver-lo en els navegadors

Exemple Chrome:

   Google chrome: Obrim el navegador amb la instrucció
   google-chrome --disable-web-security --allow-file-access-from-files
   
Exemple Firefox:

   Firefox: accedim a about:config i canviem la directiva
   security.fileuri.strict_origin_policy -> false

### CREACIÓ DOCUMENT XSL 

Per començar a fer un document **XML** es te que comenzar creant un document amb extenci xsl y posar el seguent codi
```
`<?xml version="1.0" encoding="UTF-8"?>
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
....
</xsl:stylesheet>`
```
Y despres hi ha que conectar el **XML** amb el **XSL**  posant-ho al **XML** amb el següent:

`<?xml version="1.0" encoding="UTF-8"?>
<xml-stylesheet type="text/xsl" href="fitxer.xsl"?>`

### Explicacio dels diferents elements d'un XSL

L'element `<xsl:template>`:

L'element <xsl: template> s'utilitza per crear plantilles es a dir que es la base de un **XSL**, s'utilitza el match per asociar-se amb el xml.
Exemple:
```
<xsl:template match="/">
El codi que hi fagi falta
<xsl:template match="/">`
```
L'element `<xsl:value-of>`

L'element <xsl: value-of> s'utilitza per extreure el valor d’un node seleccionat.

L'element `<xsl:for-each>`

L'element <xsl: for-each> ens permet fer bucles en XSLT es a dir que fa les iteraccions que hi hagi en el document xml
   -Tambe pot haber-hi condicions dindre del bucle es a dir que pot haber les seguents coses:
      - = (igual)
      - ! = (no és igual)
      - & lt; menys que
      - & gt; més gran que

L'element `<xsl:sort>`

Serveix per a ordenar de diferents formes tant alfabeticament com numerica.

L'element `<xsl:choose>`

L'element `<xsl:choose>` es fa servir junt amb el element `<xsl:when>` 

Hi ha mes imformacio en el ! w3schoolshttps://www.w3schools.com/xml/xsl_intro.asp
