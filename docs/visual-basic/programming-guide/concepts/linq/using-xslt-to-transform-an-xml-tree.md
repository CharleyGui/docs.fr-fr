---
title: Utilisation de XSLT pour transformer une arborescence XML
ms.date: 07/20/2015
ms.assetid: 3390ca68-c270-4e1d-b64b-6a063a77017c
ms.openlocfilehash: f8d7de508fb954148b8b16ddf24966289f191bbb
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350528"
---
# <a name="using-xslt-to-transform-an-xml-tree-visual-basic"></a>Utilisation de XSLT pour transformer une arborescence XML (Visual Basic)

Vous pouvez créer une arborescence XML, créer un objet <xref:System.Xml.XmlReader> à partir de l'arborescence XML, créer un nouveau document, puis créer un objet <xref:System.Xml.XmlWriter> qui écrira dans le nouveau document. Ensuite, vous pouvez appeler la transformation XSLT, en passant le <xref:System.Xml.XmlReader> et le <xref:System.Xml.XmlWriter> à la transformation. Une fois la transformation terminée avec succès, la nouvelle arborescence XML est remplie avec les résultats de la transformation.

## <a name="example"></a>Exemple

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

Dim xmlTree As XElement = _
    <Parent>
        <Child1>Child1 data</Child1>
        <Child2>Child2 data</Child2>
    </Parent>

Dim newTree As XDocument = New XDocument()

Using writer As XmlWriter = newTree.CreateWriter()
    ' Load the style sheet.
    Dim xslt As XslCompiledTransform = _
        New XslCompiledTransform()
    xslt.Load(xslMarkup.CreateReader())

    ' Execute the transform and output the results to a writer.
    xslt.Transform(xmlTree.CreateReader(), writer)
End Using

Console.WriteLine(newTree)
```

Cet exemple génère la sortie suivante :

```xml
<Root>
  <C1>Child1 data</C1>
  <C2>Child2 data</C2>
</Root>
```

## <a name="see-also"></a>Voir aussi

- <xref:System.Xml.Linq.XContainer.CreateWriter%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XNode.CreateReader%2A?displayProperty=nameWithType>
- [Visual Basic (Advanced LINQ to XML Programming)](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
