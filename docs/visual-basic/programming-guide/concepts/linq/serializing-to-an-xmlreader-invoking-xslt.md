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
# <a name="serializing-to-an-xmlreader-invoking-xslt-visual-basic"></a><span data-ttu-id="d37bc-102">Sérialisation vers un XmlReader (appel de XSLT) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d37bc-102">Serializing to an XmlReader (Invoking XSLT) (Visual Basic)</span></span>
<span data-ttu-id="d37bc-103">Quand vous exploitez les fonctionnalités d’interopérabilité <xref:System.Xml?displayProperty=nameWithType> de [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], vous pouvez utiliser <xref:System.Xml.Linq.XNode.CreateReader%2A> pour créer un objet <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="d37bc-103">When you use the <xref:System.Xml?displayProperty=nameWithType> interoperability capabilities of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can use <xref:System.Xml.Linq.XNode.CreateReader%2A> to create an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="d37bc-104">Le module qui lit à partir de cet objet <xref:System.Xml.XmlReader> lit les nœuds à partir de l’arborescence XML et les traite en conséquence.</span><span class="sxs-lookup"><span data-stu-id="d37bc-104">The module that reads from this <xref:System.Xml.XmlReader> reads the nodes from the XML tree and processes them accordingly.</span></span>  
  
## <a name="invoking-an-xslt-transformation"></a><span data-ttu-id="d37bc-105">Appel d'une transformation XSLT</span><span class="sxs-lookup"><span data-stu-id="d37bc-105">Invoking an XSLT Transformation</span></span>  
 <span data-ttu-id="d37bc-106">Une utilisation possible de cette méthode est lors de l'appel à une transformation XSLT.</span><span class="sxs-lookup"><span data-stu-id="d37bc-106">One possible use for this method is when invoking an XSLT transformation.</span></span> <span data-ttu-id="d37bc-107">Vous pouvez créer une arborescence XML, créer un objet <xref:System.Xml.XmlReader> à partir de l’arborescence XML, créer un nouveau document, puis créer un objet <xref:System.Xml.XmlWriter> pour écrire dans le nouveau document.</span><span class="sxs-lookup"><span data-stu-id="d37bc-107">You can create an XML tree, create an <xref:System.Xml.XmlReader> from the XML tree, create a new document, and then create an <xref:System.Xml.XmlWriter> to write into the new document.</span></span> <span data-ttu-id="d37bc-108">Ensuite, vous pouvez appeler la transformation XSLT, en passant <xref:System.Xml.XmlReader> et <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="d37bc-108">Then, you can invoke the XSLT transformation, passing in <xref:System.Xml.XmlReader> and <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="d37bc-109">Une fois la transformation terminée avec succès, la nouvelle arborescence XML est remplie avec les résultats de la transformation.</span><span class="sxs-lookup"><span data-stu-id="d37bc-109">After the transformation successfully completes, the new XML tree is populated with the results of the transformation.</span></span>  
  
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
  
 <span data-ttu-id="d37bc-110">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="d37bc-110">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <C1>Child1 data</C1>  
  <C2>Child2 data</C2>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d37bc-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d37bc-111">See also</span></span>

- [<span data-ttu-id="d37bc-112">Sérialisation d’arborescences XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d37bc-112">Serializing XML Trees (Visual Basic)</span></span>](serializing-xml-trees.md)
