---
title: Sérialiser vers un XmlReader (Invoke XSLT)-LINQ to XML
description: Vous pouvez utiliser CreateReader pour créer un XmlReader qui fournit des nœuds d’une arborescence XML à une transformation XSLT.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 4cc3ee03-ef4c-429b-a408-fedd10b728cd
ms.openlocfilehash: e079627b5fe114438feabaa1a49f42a65afedf43
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552481"
---
# <a name="serialize-to-an-xmlreader-invoke-xslt-linq-to-xml"></a><span data-ttu-id="9fc02-103">Sérialiser vers un XmlReader (appeler XSLT) (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="9fc02-103">Serialize to an XmlReader (invoke XSLT) (LINQ to XML)</span></span>

<span data-ttu-id="9fc02-104">Lorsque vous utilisez les <xref:System.Xml?displayProperty=nameWithType> fonctionnalités d’interopérabilité de LINQ to XML, vous pouvez utiliser <xref:System.Xml.Linq.XNode.CreateReader%2A> pour créer un <xref:System.Xml.XmlReader> .</span><span class="sxs-lookup"><span data-stu-id="9fc02-104">When you use the <xref:System.Xml?displayProperty=nameWithType> interoperability capabilities of LINQ to XML, you can use <xref:System.Xml.Linq.XNode.CreateReader%2A> to create an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="9fc02-105">Le module qui lit à partir de cet objet <xref:System.Xml.XmlReader> lit les nœuds à partir de l’arborescence XML et les traite en conséquence.</span><span class="sxs-lookup"><span data-stu-id="9fc02-105">The module that reads from this <xref:System.Xml.XmlReader> reads the nodes from the XML tree and processes them accordingly.</span></span>

## <a name="example-invoke-an-xslt-transformation"></a><span data-ttu-id="9fc02-106">Exemple : appeler une transformation XSLT</span><span class="sxs-lookup"><span data-stu-id="9fc02-106">Example: Invoke an XSLT transformation</span></span>

<span data-ttu-id="9fc02-107">Une utilisation possible de cette méthode est lors de l'appel à une transformation XSLT.</span><span class="sxs-lookup"><span data-stu-id="9fc02-107">One possible use for this method is when invoking an XSLT transformation.</span></span> <span data-ttu-id="9fc02-108">Vous pouvez créer une arborescence XML, créer un objet <xref:System.Xml.XmlReader> à partir de l’arborescence XML, créer un nouveau document, puis créer un objet <xref:System.Xml.XmlWriter> pour écrire dans le nouveau document.</span><span class="sxs-lookup"><span data-stu-id="9fc02-108">You can create an XML tree, create an <xref:System.Xml.XmlReader> from the XML tree, create a new document, and then create an <xref:System.Xml.XmlWriter> to write into the new document.</span></span> <span data-ttu-id="9fc02-109">Ensuite, vous pouvez appeler la transformation XSLT, en passant <xref:System.Xml.XmlReader> et <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="9fc02-109">Then, you can invoke the XSLT transformation, passing in <xref:System.Xml.XmlReader> and <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="9fc02-110">Une fois la transformation terminée avec succès, la nouvelle arborescence XML est remplie avec les résultats de la transformation.</span><span class="sxs-lookup"><span data-stu-id="9fc02-110">After the transformation successfully completes, the new XML tree is populated with the results of the transformation.</span></span>

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
using (XmlWriter writer = newTree.CreateWriter()) {
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

<span data-ttu-id="9fc02-111">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="9fc02-111">This example produces the following output:</span></span>

```xml
<Root>
  <C1>Child1 data</C1>
  <C2>Child2 data</C2>
</Root>
```
