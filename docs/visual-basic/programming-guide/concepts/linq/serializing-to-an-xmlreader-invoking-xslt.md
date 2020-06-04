---
title: Sérialisation vers un XmlReader (appel de XSLT)
ms.date: 07/20/2015
ms.assetid: 8b64f95a-e8f6-40f7-99f9-a8002c63af96
ms.openlocfilehash: e51bfc031ad6d5d0eb98718f5d547fb18eb45295
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84357372"
---
# <a name="serializing-to-an-xmlreader-invoking-xslt-visual-basic"></a>Sérialisation vers un XmlReader (appel de XSLT) (Visual Basic)
Quand vous exploitez les fonctionnalités d’interopérabilité <xref:System.Xml?displayProperty=nameWithType> de [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], vous pouvez utiliser <xref:System.Xml.Linq.XNode.CreateReader%2A> pour créer un objet <xref:System.Xml.XmlReader>. Le module qui lit à partir de cet objet <xref:System.Xml.XmlReader> lit les nœuds à partir de l’arborescence XML et les traite en conséquence.  
  
## <a name="invoking-an-xslt-transformation"></a>Appel d'une transformation XSLT  
 Une utilisation possible de cette méthode est lors de l'appel à une transformation XSLT. Vous pouvez créer une arborescence XML, créer un objet <xref:System.Xml.XmlReader> à partir de l’arborescence XML, créer un nouveau document, puis créer un objet <xref:System.Xml.XmlWriter> pour écrire dans le nouveau document. Ensuite, vous pouvez appeler la transformation XSLT, en passant <xref:System.Xml.XmlReader> et <xref:System.Xml.XmlWriter>. Une fois la transformation terminée avec succès, la nouvelle arborescence XML est remplie avec les résultats de la transformation.  
  
```vb  
Dim xslMarkup As XDocument = _  
    <?xml version='1.0'?>  
    <xsl:stylesheet xmlns:xsl='http://www.w3.org/1999/XSL/Transform' version='1.0'>  
        <xsl:template match='/Parent'>  
            <Root>  
                <C1>  
                    <xsl:value-of select='Child1'/>  
                </C1>  
                <C2>  
                    <xsl:value-of select='Child2'/>  
                </C2>  
            </Root>  
        </xsl:template>  
    </xsl:stylesheet>  
  
Dim xmlTree As XDocument = _  
    <?xml version='1.0'?>  
    <Parent>  
        <Child1>Child1 data</Child1>  
        <Child2>Child2 data</Child2>  
    </Parent>  
  
Dim newTree As XDocument = New XDocument()  
Using writer As XmlWriter = newTree.CreateWriter()  
    ' Load the style sheet.  
    Dim xslt As XslCompiledTransform = New XslCompiledTransform()  
    xslt.Load(xslMarkup.CreateReader())  
  
    ' Execute the transformation and output the results to a writer.  
    xslt.Transform(xmlTree.CreateReader(), writer)  
End Using  
  
Console.WriteLine(newTree)  
```  
  
 Cet exemple produit la sortie suivante :  
  
```xml  
<Root>  
  <C1>Child1 data</C1>  
  <C2>Child2 data</C2>  
</Root>  
```  
  
## <a name="see-also"></a>Voir aussi

- [Sérialisation d’arborescences XML (Visual Basic)](serializing-xml-trees.md)
