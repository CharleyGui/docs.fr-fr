---
title: Collections de nœuds dans les transformations
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: ad034f0e-ff8b-4a71-9a4c-528c754263c4
ms.openlocfilehash: 2828b95f6a4050dd05b38e7ab6ef740ee4eb16b4
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710555"
---
# <a name="node-sets-in-transformations"></a>Collections de nœuds dans les transformations
Les collections de nœuds correspondent à l'un des quatre types de données de base qui sont retournés à partir des expressions XPath (XML Path Language). Une collection de nœuds, qui est une collection non triée de nœuds sans doublons, créée dans l'ordre du document, peut être attribué à une variable dans une feuille de style.  
  
> [!NOTE]
> La classe <xref:System.Xml.Xsl.XslTransform> est obsolète dans .NET Framework 2.0. Vous pouvez effectuer des transformations XSLT (Extensible Stylesheet Language Transformation) à l'aide de la classe <xref:System.Xml.Xsl.XslCompiledTransform>. Pour plus d'informations, consultez [Utilisation de la classe XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) et [Migration depuis la classe XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md).  
  
 Les collections de nœuds correspondent à l'un des quatre types de données de base qui sont retournés à partir des expressions XPath. Une collection de nœuds, qui est une collection non triée de nœuds sans doublons, créée dans l'ordre du document, peut être attribué à une variable dans une feuille de style. Cette collection de nœuds, qui résulte d'une expression XPath utilisée dans un attribut `select` dans une transformation, possède le même comportement qu'une collection de nœuds du DOM (Document Object Model) XML. Vous pouvez naviguer dans une collection de nœuds à l'aide d'un ensemble de méthodes répertoriées dans [Navigation dans la collection de nœuds à l’aide de XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md), contrairement à un fragment d'arborescence résultat, qui utilise l'objet <xref:System.Xml.XPath.XPathNodeIterator> pour naviguer.  
  
 L'exemple de code suivant montre comment itérer sur une collection de nœuds lorsqu'un élément `variable` ou `parameter` dans une feuille de style prend la valeur d'une collection de nœuds.  
  
## <a name="style-sheet"></a>Feuille de style  
  
```xml  
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">  
  
    <xsl:variable name="x" select="bookstore/book/title"></xsl:variable>  
  
    <xsl:template match="/">  
        <xsl:for-each select="$x">  
            ******  
            <xsl:value-of select="."></xsl:value-of>  
            ******  
        </xsl:for-each>  
    </xsl:template>  
  
</xsl:stylesheet>  
```  
  
## <a name="input"></a>Entrée  
  
```xml  
<bookstore>  
   <book style="autobiography">  
      <title>Seven Years in Trenton</title>  
   </book>  
  
   <book style="autobiography">  
      <title>Seven Years in Trenton2</title>  
   </book>  
  
   <book style="textbook">  
      <title>History of Trenton Vol 3</title>  
   </book>  
</bookstore>  
```  
  
## <a name="output"></a>Output  
  
```output  
******  
Seven Years in Trenton  
******  
  
******  
Seven Years in Trenton2  
******  
  
******  
History of Trenton Vol 3  
******  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Xml.XPath.XPathNodeIterator>
- [Transformations XSLT avec la classe XslTransform](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)
- [Implémentation du processeur XSLT par la classe XslTransform](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
