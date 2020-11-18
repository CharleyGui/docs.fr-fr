---
title: XPathNodeIterator dans les transformations
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2bc6ddc6-674a-4f75-b264-abc35e4e5857
ms.openlocfilehash: cd8320071f1de15d503c94c138c02cab5742685c
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94818431"
---
# <a name="xpathnodeiterator-in-transformations"></a>XPathNodeIterator dans les transformations
L’objet <xref:System.Xml.XPath.XPathNodeIterator> fournit des méthodes pour itérer sur une collection de nœuds créée à la suite d’une requête XPath ou d’un fragment d’arborescence résultat converti en une collection de nœuds à l’aide de la méthode node-set. L'objet <xref:System.Xml.XPath.XPathNodeIterator> vous permet d'itérer sur les nœuds à l'intérieur de cette collection de nœuds. Dès qu'une collection de nœuds est extraite, la classe <xref:System.Xml.XPath.XPathNodeIterator> fournit un curseur avant uniquement en lecture seule à la collection de nœuds sélectionnée. La collection de nœuds étant créée dans l'ordre du document, l'appel de cette méthode permet un déplacement vers le prochain nœud dans l'ordre du document. <xref:System.Xml.XPath.XPathNodeIterator> ne construit pas une arborescence de nœuds de tous les nœuds de l'ensemble. Elle fournit à la place une seule fenêtre de nœuds dans les données, exposant le nœud sous-jacent vers lequel elle pointe lors du déplacement dans l’arborescence. Les méthodes et propriétés disponibles à partir de la classe <xref:System.Xml.XPath.XPathNodeIterator> vous permettent d'obtenir des informations à partir du nœud actuel. Pour obtenir la liste des méthodes et propriétés disponibles, voir <xref:System.Windows.Forms.ToolBar>.  
  
 Dans la mesure où un objet <xref:System.Xml.XPath.XPathNodeIterator> se déplace sur une collection de nœuds créée à partir d’une requête XPath et se déplace uniquement en avant, la méthode <xref:System.Xml.XPath.XPathNodeIterator.MoveNext%2A> permet de se déplacer. Le type de retour de cette méthode est `Boolean`, qui retourne `true` si elle se déplace vers le nœud sélectionné suivant, et `false` s’il n’y a plus de nœud sélectionné. Si elle retourne `true`, la liste suivante affiche les propriétés disponibles :  
  
- <xref:System.Xml.XPath.XPathNodeIterator.Current%2A>  
  
- <xref:System.Xml.XPath.XPathNodeIterator.CurrentPosition%2A>  
  
- <xref:System.Xml.XPath.XPathNodeIterator.Count%2A>  
  
 Lorsque vous examinez une collection de nœuds pour la premières fois, un appel à la méthode <xref:System.Xml.XPath.XPathNodeIterator.MoveNext%2A> doit être effectué pour placer l'objet <xref:System.Xml.XPath.XPathNodeIterator> sur le premier nœud de la collection sélectionnée. Cela permet l'écriture d'une boucle while.  
  
 L'exemple de code suivant illustre le passage d'un objet <xref:System.Xml.XPath.XPathNodeIterator> à un autre objet <xref:System.Xml.Xsl.XslTransform> en tant que paramètre dans l'objet <xref:System.Xml.Xsl.XsltArgumentList>. L'entrée du code est **books.xm** et la feuille de style est **text.xsl**. Le fichier **test.xml** est l'objet <xref:System.Xml.XPath.XPathDocument>.  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
Imports System.Xml.Xsl  
Imports System.Xml.XPath  
Imports System.Text  
  
Public Class sample  
  
   Public Shared Sub Main()  
      Dim Doc As New XPathDocument("books.xml")  
      Dim nav As XPathNavigator = Doc.CreateNavigator()  
      Dim Iterator As XPathNodeIterator = nav.Select("/bookstore/book")  
  
      Dim arg As New XsltArgumentList()  
      arg.AddParam("param1", "", Iterator)  
  
      Dim xslt As New XslTransform()  
      xslt.Load("test.xsl")  
  
      Dim xd As New XPathDocument("test.xml")  
  
      Dim strmTemp = New FileStream("out.xml", FileMode.Create, FileAccess.ReadWrite)  
      xslt.Transform(xd, arg, strmTemp, Nothing)  
   End Sub 'Main  
End Class 'sample  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
using System.Xml.Xsl;  
using System.Xml.XPath;  
using System.Text;  
  
public class sample  
{  
    public static void Main()  
    {  
        XPathDocument Doc = new XPathDocument("books.xml");  
        XPathNavigator nav = Doc.CreateNavigator();  
        XPathNodeIterator Iterator = nav.Select("/bookstore/book");  
  
        XsltArgumentList arg = new XsltArgumentList();  
        arg.AddParam("param1", "", Iterator);  
  
        XslTransform xslt = new XslTransform();  
        xslt.Load("test.xsl");  
  
        XPathDocument xd = new XPathDocument("test.xml");  
  
        Stream strmTemp = new FileStream("out.xml", FileMode.Create, FileAccess.ReadWrite);  
        xslt.Transform(xd, arg, strmTemp, null);  
    }  
}  
```  
  
## <a name="booksxml"></a>books.xml  
  
```xml  
<?xml version='1.0'?>  
<!-- This file represents a fragment of a book store inventory database. -->  
<bookstore specialty="novel">  
    <book style="autobiography">  
    <title>Seven Years in Trenton</title>  
        <author>  
            <first-name>Jay</first-name>  
            <last-name>Adams</last-name>  
            <award>Trenton Literary Review Honorable Mention</award>  
            <country>USA</country>  
        </author>  
        <price>12</price>  
    </book>  
    <book style="textbook">  
        <title>History of Trenton</title>  
        <author>  
            <first-name>Kim</first-name>  
            <last-name>Akers</last-name>  
            <publication>  
                Selected Short Stories of  
                <first-name>Scott</first-name>  
                <last-name>Bishop</last-name>  
                <country>US</country>  
            </publication>  
        </author>  
        <price>55</price>  
    </book>  
</bookstore>  
```  
  
## <a name="testxsl"></a>test.xsl  
  
```xml  
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform"  
xmlns:msxsl="urn:schemas-microsoft-com:xslt" exclude-result-prefixes="msxsl">  
  
<xsl:output method="xml" indent="yes"/>  
<xsl:param name="param1"/>  
  
<xsl:template match="/">  
    <out>  
        <xsl:for-each select="$param1/title">  
            <title><xsl:value-of select="."/></title>  
        </xsl:for-each>  
    </out>  
</xsl:template>  
  
</xsl:stylesheet>  
```  
  
## <a name="testxml"></a>test.xml  
  
```xml  
<Title attr="Test">this is a test</Title>  
```  
  
## <a name="output-outxml"></a>Sortie (out.xml)  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<out>  
  <title>Seven Years in Trenton</title>  
  <title>History of Trenton</title>  
</out>  
```  
  
## <a name="see-also"></a>Voir aussi

- [Implémentation du processeur XSLT par la classe XslTransform](xsltransform-class-implements-the-xslt-processor.md)
