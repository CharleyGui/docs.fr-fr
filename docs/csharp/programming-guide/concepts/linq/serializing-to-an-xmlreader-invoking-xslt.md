---
title: Sérialisation vers un XmlReader (appel de XSLT) (C#)
description: Découvrez comment utiliser CreateReader pour créer un XmlReader en C#. Le module qui lit à partir de ce XmlReader lit les nœuds dans l’arborescence XML et les traite.
ms.date: 07/20/2015
ms.assetid: 4cc3ee03-ef4c-429b-a408-fedd10b728cd
ms.openlocfilehash: aa5a232c74c5314cb7f1cf03c2a8875ca1cd04df
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302410"
---
# <a name="serializing-to-an-xmlreader-invoking-xslt-c"></a><span data-ttu-id="f3e1b-104">Sérialisation vers un XmlReader (appel de XSLT) (C#)</span><span class="sxs-lookup"><span data-stu-id="f3e1b-104">Serializing to an XmlReader (Invoking XSLT) (C#)</span></span>
<span data-ttu-id="f3e1b-105">Quand vous exploitez les fonctionnalités d’interopérabilité <xref:System.Xml?displayProperty=nameWithType> de [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], vous pouvez utiliser <xref:System.Xml.Linq.XNode.CreateReader%2A> pour créer un objet <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="f3e1b-105">When you use the <xref:System.Xml?displayProperty=nameWithType> interoperability capabilities of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can use <xref:System.Xml.Linq.XNode.CreateReader%2A> to create an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="f3e1b-106">Le module qui lit à partir de cet objet <xref:System.Xml.XmlReader> lit les nœuds à partir de l’arborescence XML et les traite en conséquence.</span><span class="sxs-lookup"><span data-stu-id="f3e1b-106">The module that reads from this <xref:System.Xml.XmlReader> reads the nodes from the XML tree and processes them accordingly.</span></span>  
  
## <a name="invoking-an-xslt-transformation"></a><span data-ttu-id="f3e1b-107">Appel d'une transformation XSLT</span><span class="sxs-lookup"><span data-stu-id="f3e1b-107">Invoking an XSLT Transformation</span></span>  
 <span data-ttu-id="f3e1b-108">Une utilisation possible de cette méthode est lors de l'appel à une transformation XSLT.</span><span class="sxs-lookup"><span data-stu-id="f3e1b-108">One possible use for this method is when invoking an XSLT transformation.</span></span> <span data-ttu-id="f3e1b-109">Vous pouvez créer une arborescence XML, créer un objet <xref:System.Xml.XmlReader> à partir de l’arborescence XML, créer un nouveau document, puis créer un objet <xref:System.Xml.XmlWriter> pour écrire dans le nouveau document.</span><span class="sxs-lookup"><span data-stu-id="f3e1b-109">You can create an XML tree, create an <xref:System.Xml.XmlReader> from the XML tree, create a new document, and then create an <xref:System.Xml.XmlWriter> to write into the new document.</span></span> <span data-ttu-id="f3e1b-110">Ensuite, vous pouvez appeler la transformation XSLT, en passant <xref:System.Xml.XmlReader> et <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="f3e1b-110">Then, you can invoke the XSLT transformation, passing in <xref:System.Xml.XmlReader> and <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="f3e1b-111">Une fois la transformation terminée avec succès, la nouvelle arborescence XML est remplie avec les résultats de la transformation.</span><span class="sxs-lookup"><span data-stu-id="f3e1b-111">After the transformation successfully completes, the new XML tree is populated with the results of the transformation.</span></span>  
  
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
  
 <span data-ttu-id="f3e1b-112">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="f3e1b-112">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <C1>Child1 data</C1>  
  <C2>Child2 data</C2>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f3e1b-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f3e1b-113">See also</span></span>

- [<span data-ttu-id="f3e1b-114">Sérialisation d’arborescences XML (C#)</span><span class="sxs-lookup"><span data-stu-id="f3e1b-114">Serializing XML Trees (C#)</span></span>](serializing-to-files-textwriters-and-xmlwriters.md)
