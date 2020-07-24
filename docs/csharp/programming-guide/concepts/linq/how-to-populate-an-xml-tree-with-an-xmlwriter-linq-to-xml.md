---
title: Comment remplir une arborescence XML avec un XmlWriter (LINQ to XML) (C#)
description: Découvrez comment remplir une arborescence XML à l’aide de CreateWriter pour créer un XmlWriter, puis écrire dans XmlWriter en LINQ to XML en C#.
ms.date: 07/20/2015
ms.assetid: cd5674d1-5c54-4efc-ba68-e23b2875295f
ms.openlocfilehash: 9639c5947583bccf4f8ba427fc8611e181ef1536
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104804"
---
# <a name="how-to-populate-an-xml-tree-with-an-xmlwriter-linq-to-xml-c"></a><span data-ttu-id="460c5-103">Comment remplir une arborescence XML avec un XmlWriter (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="460c5-103">How to populate an XML tree with an XmlWriter (LINQ to XML) (C#)</span></span>
<span data-ttu-id="460c5-104">L’une des manières de remplir une arborescence XML consiste à utiliser <xref:System.Xml.Linq.XContainer.CreateWriter%2A> pour créer un objet <xref:System.Xml.XmlWriter>, puis à écrire dans l’objet <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="460c5-104">One way to populate an XML tree is to use <xref:System.Xml.Linq.XContainer.CreateWriter%2A> to create an <xref:System.Xml.XmlWriter>, and then write to the <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="460c5-105">L’arborescence XML est remplie avec tous les nœuds écrits dans l’objet <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="460c5-105">The XML tree is populated with all nodes that are written to the <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="460c5-106">Cette méthode est généralement utilisée quand [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] est utilisé avec une autre classe censée écrire dans un objet <xref:System.Xml.XmlWriter>, comme <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="460c5-106">You would typically use this method when you use [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] with another class that expects to write to an <xref:System.Xml.XmlWriter>, such as <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="460c5-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="460c5-107">Example</span></span>  
 <span data-ttu-id="460c5-108">Une utilisation possible de <xref:System.Xml.Linq.XContainer.CreateWriter%2A> est lors de l'appel à une transformation XSLT.</span><span class="sxs-lookup"><span data-stu-id="460c5-108">One possible use for <xref:System.Xml.Linq.XContainer.CreateWriter%2A> is when invoking an XSLT transformation.</span></span> <span data-ttu-id="460c5-109">Cet exemple crée une arborescence XML, crée un objet <xref:System.Xml.XmlReader> à partir de l’arborescence XML, crée un nouveau document, puis crée un objet <xref:System.Xml.XmlWriter> pour écrire dans le nouveau document.</span><span class="sxs-lookup"><span data-stu-id="460c5-109">This example creates an XML tree, creates an <xref:System.Xml.XmlReader> from the XML tree, creates a new document, and then creates an <xref:System.Xml.XmlWriter> to write into the new document.</span></span> <span data-ttu-id="460c5-110">Il appelle ensuite la transformation XSLT, en passant <xref:System.Xml.XmlReader> et <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="460c5-110">It then invokes the XSLT transformation, passing in <xref:System.Xml.XmlReader> and <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="460c5-111">Une fois la transformation terminée avec succès, la nouvelle arborescence XML est remplie avec les résultats de la transformation.</span><span class="sxs-lookup"><span data-stu-id="460c5-111">After the transformation successfully completes, the new XML tree is populated with the results of the transformation.</span></span>  
  
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
  
 <span data-ttu-id="460c5-112">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="460c5-112">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <C1>Child1 data</C1>  
  <C2>Child2 data</C2>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="460c5-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="460c5-113">See also</span></span>

- <xref:System.Xml.Linq.XContainer.CreateWriter%2A>
- <xref:System.Xml.XmlWriter>
- <xref:System.Xml.Xsl.XslCompiledTransform>
- [<span data-ttu-id="460c5-114">Création d’arborescences XML (C#)</span><span class="sxs-lookup"><span data-stu-id="460c5-114">Creating XML Trees (C#)</span></span>](./linq-to-xml-overview.md)
