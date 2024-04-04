# Apunts de M04 en Markdown

![image](https://github.com/Domeneccc/M04/assets/165904493/1cb42b5f-6a84-4657-a8a7-14be1d0586e4)



## Index

1. XML
   - Explicació bàsica  el que farem amb XML
3. DOM
   - Que es ?
   - Les Propietats del DOM
   - Accedir a Nodes
   - Exemple DOM amb Python 
5. XSLT i XPath
   - Que es Xpath ?
   - Exemples de XPath
   - Explicació de XSLT amb teoria
   - Exemples de XSLT
   


# XML

## Explicació bàsica d'XML i el que farem

Para comenzar en la uf 2 de **XML** entra Dom que es fa amb python que hi hauran varis exemples de ejercicis, despres tambe hi ha **xslt** amb xpath cada un explicats 


# DOM
## Que es?

DOM són les sigles en anglès de "Document Object Model" (Model d'Objectes del Document). Serveix per a manipular objectes d'un document xml que permet accedir a les dades. I amb estructura d' arbre. Defineix un standar per a accedir als documents


![image](https://github.com/Domeneccc/M04/assets/165904493/d12e9ae6-e39b-45da-a151-0708da1b193b)


## Les Propietats del DOM


   - childNodes - Retorna una col·lecció dels fills de l'element especificat en forma d'objectes Node.
   - parentNode - Retorna l'element pare de l'element especificat.
   - firstChild - Retorna el primer fill de l'element especificat.
   - lastChild - Retorna l'últim fill de l'element especificat.
   - nodeName - Retorna el nom de l'etiqueta de l'element especificat.
   - nodeType - Retorna el tipus de node de l'element especificat.
   - nodeValue - Retorna o defineix el valor de l'atribut node.

Exemples: 
Aixo saca tots els nodes que tenen el nombre _nom_

`x.getElementByTagName("nom").firstChild.data`


## Accedir a Nodes

Per poder accedir als nodes es pot utilizar varias coses com:

   - x.getElementById
   - x.getElementsByTagName
   - x.getElementsByClassName

Puedes crear ua lista con `getElementsByTagName()` y te crea una _lista_ que con eso puedes trabajar.

`lista = getElementsByTagName(x)`


## Exemple DOM amb Python

```
from xml.dom import minidom

doc = minidom.parse("universitat.xml")

alumnas = {}

arrel = doc.documentElement.localName
lista_alumna = doc.getElementsByTagName("persona")




for person in lista_alumna:
    nom = person.getElementsByTagName("nom")[0].firstChild.data
    cognoms = person.getElementsByTagName("cognoms")[0].firstChild.data
    nom_complet = nom +"-"+ cognoms
    edad = person.getElementsByTagName("edat")[0].firstChild.data
    lista_asignatura = person.getElementsByTagName("assignatura")
    assignaturass = []
    for assignatura in lista_asignatura:
             assignaturass.append(assignatura.firstChild.data)
        
    alumnas[nom_complet] = {
                "Edat": edad,
                "assignaturas":assignaturass}
    
asignatura_a_buscar = input("Introduce el nombre de la asignatura que quieres consultar: ")

   
personas_matriculadas = []
for alumna, datos in alumnas.items():
    if asignatura_a_buscar in datos["assignaturas"]:
        personas_matriculadas.append(alumna)

if personas_matriculadas:
    print(f"Personas matriculadas en '{asignatura_a_buscar}':")
    for persona in personas_matriculadas:
        print(persona)
else:
    print(f"No hay personas matriculadas en '{asignatura_a_buscar}'.")

```
   

# XSLT i XPath

## Que es Xpath ?


L' [XPhath](http://xpather.com) (XML Path Language) és un llenguatge utilitzat per localitzar i seleccionar elements en documents XML o HTML. Es basa en l'expressió de camins o rutes com si fora linux amb cd


Considera un document XML com un arbre de nodes. En Informàtica, un arbre és una estructura de dades que equival a un arbre matemàtic. En Matemàtiques un arbre és un cas particular de graf. Els següents termes definits en teoria de grafs s'utilitzen també en Informàtica i en XPath


![image](https://github.com/Domeneccc/M04/assets/165904493/f864df55-e184-4049-9967-9adf800b5083)

## Exemples de XPath

```
<?xml version="1.0" encoding="UTF-8"?>
<biblioteca>
  <libro>
    <titulo>La vida está en otra parte</titulo>
    <autor>Milan Kundera</autor>
    <fechaPublicacion año="1973"/>
  </libro>
  <libro>
    <titulo>Pantaleón y las visitadoras</titulo>
    <autor fechaNacimiento="28/03/1936">Mario Vargas Llosa</autor>
    <fechaPublicacion año="1973"/>
  </libro>
  <libro>
    <titulo>Conversación en la catedral</titulo>
    <autor fechaNacimiento="28/03/1936">Mario Vargas Llosa</autor>
    <fechaPublicacion año="1969"/>
  </libro>
</biblioteca>

```




## Explicació de XSLT amb teoria

### Què és XSLT?

El **XSLT** ve de eXtensible Stylesheet Language Transformations que significa que es un lleguatge que serveix per donar estill a un document xml que es com el css del html per es oer al **xml**. Normalment el arxiu que son de entrada son xml, també poden ser altres tipus de formats. Hi ha processadors de XSLT en llenguatges com C, C++, Java, Python, Perl, Javascript.


![image](https://github.com/Domeneccc/M04/assets/165904493/192759e7-ea1d-42ea-93d3-c93855a6744a)






Els navegador webs més habituals (Safari, Chrome, Firefox, microsoft Edge, Opera,...) porten un processador de XSLT incorporat, pero hi ha que activar una opcio especial per poder ver-lo en els navegadors

Exemple Chrome:

   Google chrome: Obrim el navegador amb la instrucció
   google-chrome --disable-web-security --allow-file-access-from-files
   
Exemple Firefox:

   Firefox: accedim a about:config i canviem la directiva
   security.fileuri.strict_origin_policy -> false

### creació de un document xsl

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

L'element <xsl: template> s'utilitza per crear plantilles es a dir que es la base de un **XSL**, s'utilitza el match per asociar-se amb el _xml_.
Exemple:
```
<xsl:template match="/">
El codi que hi fagi falta
<xsl:template />`
```
L'element `<xsl:value-of>`

L'element <xsl: value-of> s'utilitza per extreure el valor d’un node seleccionat.

L'element `<xsl:for-each>`

L'element <xsl: for-each> ens permet fer bucles en XSLT es a dir que fa les iteraccions que hi hagi en el document xml
Tambe pot haber-hi condicions dindre del bucle es a dir que pot haber les seguents coses:
   - = (igual)
   - ! = (no és igual)
   - & lt; menys que
   - & gt; més gran que

L'element `<xsl:sort>`

Serveix per a ordenar de diferents formes tant alfabeticament com numerica.

L'element `<xsl:choose>`

L'element <xsl:choose> es fa servir junt amb el element `<xsl:when>` 

Hi ha mes imformacio en el  [w3school](https://www.w3schools.com/xml/xsl_intro.asp)

## Exemples de XSLT
```
<?xml version="1.0" encoding="UTF-8"?>
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
    <xsl:output method="html" indent="yes"/>
    <xsl:template match="/horari">
        <html>
            <head>
                <style>
                    .body {
                        background-color: rgb(230, 230, 230);
                    }
                    .foto_cabeza{
                        width: 100%;
                        height: 20%;
                    }
                    .tabla {
                        width: 100%;
                        text-align: center;
                        border-collapse: collapse;
                    }
                    .dias_semana{
                        background-color: rgb(200, 200, 200);
                        
                    }
                    .lista {
                        text-align: center;

                    }
                    .titol {
                        margin: 0px;
                    }
                    <xsl:for-each select="colors/color">
                        .<xsl:value-of select="@codi"/> {background-color: <xsl:value-of select="."/>; 
                        padding: 15px; 
                        margin: 3px; 
                        }
                     </xsl:for-each>
                     .links {
                        color: rgb(0, 0, 0)
                        
                     }
                     .links:visited  {
                        color: rgb(0, 0, 0)
                        
                     }
                     .lista_links {
                        padding: 5px;
                        list-style-type: none;
                     }
                </style>
            </head>
            <body class="body">
                <img src="{@header}" alt="Imagen de Encabezado" class="foto_cabeza" />
                <table class="tabla">
                    <tr>
                        <xsl:for-each select="setmana/dia">
                            <th class="dias_semana" >
                                <xsl:value-of select="@nom"/>
                            </th>
                        </xsl:for-each>
                    </tr> 
                    <tr>
                        <xsl:for-each select="setmana/dia">
                            <td>
                                <xsl:for-each select="modul">
                                    <p class="{codi}" xml:space="preserve">
                                        <xsl:value-of select="codi"/>  <xsl:value-of select="nom"/> 
                                    </p>
                                </xsl:for-each>
                            </td>
                        </xsl:for-each>
                    </tr>
                </table>
                <ul class="lista">
                    <h1 class="titol"><xsl:value-of select="links/@nom"/></h1>
                   <xsl:for-each select="/horari/links">
                            
                                <xsl:for-each select="link">
                                <xsl:sort select="nom"/>
                                    <li class="lista_links">
                                        <a href="{url}" class="links" target="_blank">
                                            <xsl:value-of select="nom"/> <br/>
                                        </a>
                                    </li>
                                </xsl:for-each>
                    </xsl:for-each>
                </ul>
            </body>
        </html>
    </xsl:template>
</xsl:stylesheet>
```

