---
title: Utilisation de XSLT pour transformer une arborescence XML-LINQ to XML
description: Apprenez à utiliser XSLT pour transformer une arborescence XML, en utilisant XmlReader pour lire et XmlWriter pour écrire.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 373a2699-d4c5-471b-9bda-c1f0ab73b477
ms.openlocfilehash: 9a8f85b4f563d177d00d41feeac6fd8cd61375a2
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552528"
---
# <a name="use-xslt-to-transform-an-xml-tree-linq-to-xml"></a><span data-ttu-id="199e3-103">Utiliser XSLT pour transformer une arborescence XML (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="199e3-103">Use XSLT to transform an XML tree (LINQ to XML)</span></span>

<span data-ttu-id="199e3-104">Vous pouvez utiliser XSLT pour transformer une arborescence XML, en utilisant <xref:System.Xml.XmlReader> pour lire et <xref:System.Xml.XmlWriter> écrire.</span><span class="sxs-lookup"><span data-stu-id="199e3-104">You can use XSLT to transform an XML tree, using <xref:System.Xml.XmlReader> to read and <xref:System.Xml.XmlWriter> to write.</span></span>

## <a name="example-use-xslt-to-transform-an-xml-tree-using-xmlreader-to-read-and-xmlwriter-to-write"></a><span data-ttu-id="199e3-105">Exemple : utilisation de XSLT pour transformer une arborescence XML, en utilisant `XMLReader` pour lire et `XMLWriter` écrire</span><span class="sxs-lookup"><span data-stu-id="199e3-105">Example: Use XSLT to transform an XML tree, using `XMLReader` to read and `XMLWriter` to write</span></span>

<span data-ttu-id="199e3-106">Cet exemple crée une arborescence XML et utilise XSLT pour la transformer.</span><span class="sxs-lookup"><span data-stu-id="199e3-106">This example creates an XML tree and uses XSLT to transform it.</span></span> <span data-ttu-id="199e3-107">Il utilise un <xref:System.Xml.XmlReader> pour lire l’arborescence d’origine et un <xref:System.Xml.XmlWriter> pour écrire la version transformée.</span><span class="sxs-lookup"><span data-stu-id="199e3-107">It makes use of an <xref:System.Xml.XmlReader> to read the original tree, and an <xref:System.Xml.XmlWriter> to write the transformed version.</span></span>

<span data-ttu-id="199e3-108">Il commence par créer :</span><span class="sxs-lookup"><span data-stu-id="199e3-108">It starts by creating:</span></span>

- <span data-ttu-id="199e3-109">Arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="199e3-109">An XML tree.</span></span>
- <span data-ttu-id="199e3-110"><xref:System.Xml.XmlReader>De l’arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="199e3-110">An <xref:System.Xml.XmlReader> of the XML tree.</span></span>
- <span data-ttu-id="199e3-111">Nouveau document destiné à contenir la sortie XSLT.</span><span class="sxs-lookup"><span data-stu-id="199e3-111">A new document to hold the XSLT output.</span></span>
- <span data-ttu-id="199e3-112"><xref:System.Xml.XmlWriter>Pour écrire l’arborescence transformée dans le nouveau document.</span><span class="sxs-lookup"><span data-stu-id="199e3-112">An <xref:System.Xml.XmlWriter> to write the transformed tree to the new document.</span></span>

<span data-ttu-id="199e3-113">Il appelle ensuite une transformation XSLT qui utilise <xref:System.Xml.XmlReader> pour lire l’arborescence XML d’origine et le <xref:System.Xml.XmlWriter> pour écrire l’arborescence transformée dans le nouveau document.</span><span class="sxs-lookup"><span data-stu-id="199e3-113">It then invokes an XSLT transformation that uses the <xref:System.Xml.XmlReader> to read the original XML tree, and the <xref:System.Xml.XmlWriter> to write the transformed tree to the new document.</span></span>

```csharp
string xslt = @"<?xml version='1.0'?>
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

var oldDocument = new XDocument(
    new XElement("Parent",
        new XElement("Child1", "Child1 data"),
        new XElement("Child2", "Child2 data")
    )
);

var newDocument = new XDocument();

using (var stringReader = new StringReader(xslt))
{
    using (XmlReader xsltReader = XmlReader.Create(stringReader))
    {
        var transformer = new XslCompiledTransform();
        transformer.Load(xsltReader);
        using (XmlReader oldDocumentReader = oldDocument.CreateReader())
        {
            using (XmlWriter newDocumentWriter = newDocument.CreateWriter())
            {
                transformer.Transform(oldDocumentReader, newDocumentWriter);
            }
        }
    }
}

string result = newDocument.ToString();
Console.WriteLine(result);
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

<span data-ttu-id="199e3-114">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="199e3-114">This example produces the following output:</span></span>

```xml
<Root>
  <C1>Child1 data</C1>
  <C2>Child2 data</C2>
</Root>
```

## <a name="see-also"></a><span data-ttu-id="199e3-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="199e3-115">See also</span></span>

- <xref:System.Xml.Linq.XContainer.CreateWriter%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XNode.CreateReader%2A?displayProperty=nameWithType>
