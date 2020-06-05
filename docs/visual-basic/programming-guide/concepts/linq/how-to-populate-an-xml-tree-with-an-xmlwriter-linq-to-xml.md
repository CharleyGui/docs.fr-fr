---
title: 'Procédure : remplir une arborescence XML avec un XmlWriter (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 5792a0eb-94ee-440d-b601-58cca8c0ee0b
ms.openlocfilehash: b3a36326175eeba8cd692a2c71f1f9b0fde24b5f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397971"
---
# <a name="how-to-populate-an-xml-tree-with-an-xmlwriter-linq-to-xml-visual-basic"></a><span data-ttu-id="316db-102">Comment : remplir une arborescence XML avec un XmlWriter (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="316db-102">How to: Populate an XML Tree with an XmlWriter (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="316db-103">L’une des manières de remplir une arborescence XML consiste à utiliser <xref:System.Xml.Linq.XContainer.CreateWriter%2A> pour créer un objet <xref:System.Xml.XmlWriter>, puis à écrire dans l’objet <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="316db-103">One way to populate an XML tree is to use <xref:System.Xml.Linq.XContainer.CreateWriter%2A> to create an <xref:System.Xml.XmlWriter>, and then write to the <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="316db-104">L’arborescence XML est remplie avec tous les nœuds écrits dans l’objet <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="316db-104">The XML tree is populated with all nodes that are written to the <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="316db-105">Cette méthode est généralement utilisée quand [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] est utilisé avec une autre classe censée écrire dans un objet <xref:System.Xml.XmlWriter>, comme <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="316db-105">You would typically use this method when you use [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] with another class that expects to write to an <xref:System.Xml.XmlWriter>, such as <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="316db-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="316db-106">Example</span></span>  
 <span data-ttu-id="316db-107">Une utilisation possible de <xref:System.Xml.Linq.XContainer.CreateWriter%2A> est lors de l'appel à une transformation XSLT.</span><span class="sxs-lookup"><span data-stu-id="316db-107">One possible use for <xref:System.Xml.Linq.XContainer.CreateWriter%2A> is when invoking an XSLT transformation.</span></span> <span data-ttu-id="316db-108">Cet exemple crée une arborescence XML, crée un objet <xref:System.Xml.XmlReader> à partir de l’arborescence XML, crée un nouveau document, puis crée un objet <xref:System.Xml.XmlWriter> pour écrire dans le nouveau document.</span><span class="sxs-lookup"><span data-stu-id="316db-108">This example creates an XML tree, creates an <xref:System.Xml.XmlReader> from the XML tree, creates a new document, and then creates an <xref:System.Xml.XmlWriter> to write into the new document.</span></span> <span data-ttu-id="316db-109">Il appelle ensuite la transformation XSLT, en passant <xref:System.Xml.XmlReader> et <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="316db-109">It then invokes the XSLT transformation, passing in <xref:System.Xml.XmlReader> and <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="316db-110">Une fois la transformation terminée avec succès, la nouvelle arborescence XML est remplie avec les résultats de la transformation.</span><span class="sxs-lookup"><span data-stu-id="316db-110">After the transformation successfully completes, the new XML tree is populated with the results of the transformation.</span></span>  
  
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
  
 <span data-ttu-id="316db-111">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="316db-111">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <C1>Child1 data</C1>  
  <C2>Child2 data</C2>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="316db-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="316db-112">See also</span></span>

- <xref:System.Xml.Linq.XContainer.CreateWriter%2A>
- <xref:System.Xml.XmlWriter>
- <xref:System.Xml.Xsl.XslCompiledTransform>
- [<span data-ttu-id="316db-113">Création d’arborescences XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="316db-113">Creating XML Trees (Visual Basic)</span></span>](creating-xml-trees.md)
