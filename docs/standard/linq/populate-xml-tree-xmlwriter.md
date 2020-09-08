---
title: Comment remplir une arborescence XML avec un LINQ to XML XmlWriter
description: Pour remplir une arborescence XML en C# et Visual Basic, créez un XMLWriter à l’aide de CreateWriter, puis écrivez dans XmlWriter.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: cd5674d1-5c54-4efc-ba68-e23b2875295f
ms.openlocfilehash: 3f8005eca009ae5f2102444a5494336d2caa2450
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553455"
---
# <a name="how-to-populate-an-xml-tree-with-an-xmlwriter-linq-to-xml"></a>Comment remplir une arborescence XML avec un XmlWriter (LINQ to XML)

L’une des manières de remplir une arborescence XML consiste à utiliser <xref:System.Xml.Linq.XContainer.CreateWriter%2A> pour créer un objet <xref:System.Xml.XmlWriter>, puis à écrire dans l’objet <xref:System.Xml.XmlWriter>. L’arborescence XML est remplie avec tous les nœuds écrits dans l’objet <xref:System.Xml.XmlWriter>.

En général, vous utilisez cette méthode lorsque vous utilisez LINQ to XML avec une autre classe qui s’attend à écrire dans un <xref:System.Xml.XmlWriter> , tel que <xref:System.Xml.Xsl.XslCompiledTransform> .

## <a name="example-create-an-xmlwriter-to-accept-the-output-of-an-xslt-transformation"></a>Exemple : créer un XmlWriter pour accepter la sortie d’une transformation XSLT

Vous pouvez utiliser <xref:System.Xml.Linq.XContainer.CreateWriter%2A> pour créer un <xref:System.Xml.XmlWriter> pour accepter la sortie d’une transformation XSLT. Cela est illustré dans l’exemple suivant, qui effectue les opérations suivantes :

- Crée une arborescence XML et un <xref:System.Xml.XmlReader> pour le lire.
- Crée un nouvel arbre et un <xref:System.Xml.XmlWriter> à écrire dans celui-ci.
- Appelle la transformation XSLT, en lui fournissant le  <xref:System.Xml.XmlReader> et le <xref:System.Xml.XmlWriter> .

La transformation remplit ensuite la nouvelle arborescence.

```csharp
string xslMarkup = @"<?xml version='1.0'?>
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
</xsl:stylesheet>";

XDocument xmlTree = new XDocument(
    new XElement("Parent",
        new XElement("Child1", "Child1 data"),
        new XElement("Child2", "Child2 data")
    )
);

XDocument newTree = new XDocument();
using (XmlWriter writer = newTree.CreateWriter())
{
    // Load the style sheet.
    XslCompiledTransform xslt = new XslCompiledTransform();
    xslt.Load(XmlReader.Create(new StringReader(xslMarkup)));

    // Execute the transformation and output the results to a writer.
    xslt.Transform(xmlTree.CreateReader(), writer);
}

Console.WriteLine(newTree);
```

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

- <xref:System.Xml.Linq.XContainer.CreateWriter%2A>
- <xref:System.Xml.XmlWriter>
- <xref:System.Xml.Xsl.XslCompiledTransform>
- [Arborescences XML](functional-construction.md)
