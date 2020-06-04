---
title: Récupération des paragraphes et de leurs styles
ms.date: 07/20/2015
ms.assetid: d9ed2238-d38e-4ad4-b88b-db7859df9bde
ms.openlocfilehash: ad904abf9bd94e83b981859662c22787652e294f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413404"
---
# <a name="retrieving-the-paragraphs-and-their-styles-visual-basic"></a><span data-ttu-id="ac8b1-102">Récupération des paragraphes et de leurs styles (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ac8b1-102">Retrieving the Paragraphs and Their Styles (Visual Basic)</span></span>
<span data-ttu-id="ac8b1-103">Dans cet exemple, nous écrivons une requête qui récupère les nœuds de paragraphe à partir d'un document WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="ac8b1-103">In this example, we write a query that retrieves the paragraph nodes from a WordprocessingML document.</span></span> <span data-ttu-id="ac8b1-104">Il identifie également le style de chaque paragraphe.</span><span class="sxs-lookup"><span data-stu-id="ac8b1-104">It also identifies the style of each paragraph.</span></span>  
  
 <span data-ttu-id="ac8b1-105">Cette requête est basée sur la requête de l’exemple précédent, [recherche du style de paragraphe par défaut (Visual Basic)](finding-the-default-paragraph-style.md), qui récupère le style par défaut à partir de la liste de styles.</span><span class="sxs-lookup"><span data-stu-id="ac8b1-105">This query builds on the query in the previous example, [Finding the Default Paragraph Style (Visual Basic)](finding-the-default-paragraph-style.md), which retrieves the default style from the list of styles.</span></span> <span data-ttu-id="ac8b1-106">Ces informations sont requises de manière que la requête puisse identifier le style des paragraphes pour lesquels aucun style n'est défini de façon explicite.</span><span class="sxs-lookup"><span data-stu-id="ac8b1-106">This information is required so that the query can identify the style of paragraphs that do not have a style explicitly set.</span></span> <span data-ttu-id="ac8b1-107">Les style de paragraphes sont définis par le biais de l'élément `w:pPr` ; si un paragraphe ne contient pas cet élément, il est mis en forme avec le style par défaut.</span><span class="sxs-lookup"><span data-stu-id="ac8b1-107">Paragraph styles are set through the `w:pPr` element; if a paragraph does not contain this element, it is formatted with the default style.</span></span>  
  
 <span data-ttu-id="ac8b1-108">Cette rubrique explique l'importance de certaines parties de la requête, puis illustre la requête dans le cadre d'un exemple fonctionnel complet.</span><span class="sxs-lookup"><span data-stu-id="ac8b1-108">This topic explains the significance of some pieces of the query, then shows the query as part of a complete, working example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ac8b1-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="ac8b1-109">Example</span></span>  
 <span data-ttu-id="ac8b1-110">La source de la requête permettant de récupérer tous les paragraphes dans un document et leurs styles est la suivante :</span><span class="sxs-lookup"><span data-stu-id="ac8b1-110">The source of the query to retrieve all the paragraphs in a document and their styles is as follows:</span></span>  
  
```vb  
xDoc.Root.<w:body>...<w:p>  
```  
  
 <span data-ttu-id="ac8b1-111">Cette expression est similaire à la source de la requête de l’exemple précédent, [recherche du style de paragraphe par défaut (Visual Basic)](finding-the-default-paragraph-style.md).</span><span class="sxs-lookup"><span data-stu-id="ac8b1-111">This expression is similar to the source of the query in the previous example, [Finding the Default Paragraph Style (Visual Basic)](finding-the-default-paragraph-style.md).</span></span> <span data-ttu-id="ac8b1-112">La différence principale est qu'elle utilise l'axe <xref:System.Xml.Linq.XContainer.Descendants%2A> au lieu de l'axe <xref:System.Xml.Linq.XContainer.Elements%2A>.</span><span class="sxs-lookup"><span data-stu-id="ac8b1-112">The main difference is that it uses the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis instead of the <xref:System.Xml.Linq.XContainer.Elements%2A> axis.</span></span> <span data-ttu-id="ac8b1-113">La requête utilise l'axe <xref:System.Xml.Linq.XContainer.Descendants%2A> car dans les documents qui ont des sections, les paragraphes ne sont pas les enfants directs de l'élément de corps, mais se trouvent deux niveaux au-dessous dans la hiérarchie.</span><span class="sxs-lookup"><span data-stu-id="ac8b1-113">The query uses the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis because in documents that have sections, the paragraphs will not be the direct children of the body element; rather, the paragraphs will be two levels down in the hierarchy.</span></span> <span data-ttu-id="ac8b1-114">Grâce à l'utilisation de la méthode <xref:System.Xml.Linq.XContainer.Descendants%2A>, le code fonctionnera, que le document utilise des sections ou non.</span><span class="sxs-lookup"><span data-stu-id="ac8b1-114">By using the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis, the code will work of whether or not the document uses sections.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ac8b1-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="ac8b1-115">Example</span></span>  
 <span data-ttu-id="ac8b1-116">La requête utilise une clause `Let` afin de déterminer l'élément qui contient le nœud de style.</span><span class="sxs-lookup"><span data-stu-id="ac8b1-116">The query uses a `Let` clause to determine the element that contains the style node.</span></span> <span data-ttu-id="ac8b1-117">S'il n'y a aucun élément, `styleNode` a la valeur `Nothing` :</span><span class="sxs-lookup"><span data-stu-id="ac8b1-117">If there is no element, then `styleNode` is set to `Nothing`:</span></span>  
  
```vb  
Let styleNode As XElement = para.<w:pPr>.<w:pStyle>.FirstOrDefault()  
```  
  
 <span data-ttu-id="ac8b1-118">La clause `Let` utilise d'abord l'axe <xref:System.Xml.Linq.XContainer.Elements%2A> pour rechercher tous les éléments nommés `pPr`, puis utilise la méthode d'extension <xref:System.Xml.Linq.Extensions.Elements%2A> pour rechercher tous les éléments enfants nommés `pStyle`, et pour finir utilise l'opérateur de requête standard <xref:System.Linq.Enumerable.FirstOrDefault%2A> pour convertir la collection en singleton.</span><span class="sxs-lookup"><span data-stu-id="ac8b1-118">The `Let` clause first uses the <xref:System.Xml.Linq.XContainer.Elements%2A> axis to find all elements named `pPr`, then uses the <xref:System.Xml.Linq.Extensions.Elements%2A> extension method to find all child elements named `pStyle`, and finally uses the <xref:System.Linq.Enumerable.FirstOrDefault%2A> standard query operator to convert the collection to a singleton.</span></span> <span data-ttu-id="ac8b1-119">Si la collection est vide, `styleNode` a la valeur `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="ac8b1-119">If the collection is empty, `styleNode` is set to `Nothing`.</span></span> <span data-ttu-id="ac8b1-120">Il s'agit d'un idiome utile pour rechercher le nœud descendant `pStyle`.</span><span class="sxs-lookup"><span data-stu-id="ac8b1-120">This is a useful idiom to look for the `pStyle` descendant node.</span></span> <span data-ttu-id="ac8b1-121">Notez que si le nœud enfant `pPr` n'existe pas, le code n'échoue pas avec la levée d'une exception ; au lieu de cela, `styleNode` est définie à `Nothing`, ce qui constitue le comportement souhaité de cette clause `Let`.</span><span class="sxs-lookup"><span data-stu-id="ac8b1-121">Note that if the `pPr` child node does not exist, the code does nor fail by throwing an exception; instead, `styleNode` is set to `Nothing`, which is the desired behavior of this `Let` clause.</span></span>  
  
 <span data-ttu-id="ac8b1-122">La requête projette une collection d'un type anonyme avec deux membres, `StyleName` et `ParagraphNode`.</span><span class="sxs-lookup"><span data-stu-id="ac8b1-122">The query projects a collection of an anonymous type with two members, `StyleName` and `ParagraphNode`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ac8b1-123">Exemple</span><span class="sxs-lookup"><span data-stu-id="ac8b1-123">Example</span></span>  
 <span data-ttu-id="ac8b1-124">Cet exemple traite un document WordprocessingML et récupère les nœuds de paragraphes à partir d'un document WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="ac8b1-124">This example processes a WordprocessingML document, retrieving the paragraph nodes from a WordprocessingML document.</span></span> <span data-ttu-id="ac8b1-125">Il identifie également le style de chaque paragraphe.</span><span class="sxs-lookup"><span data-stu-id="ac8b1-125">It also identifies the style of each paragraph.</span></span> <span data-ttu-id="ac8b1-126">Cet exemple se base sur les exemples précédents de ce didacticiel.</span><span class="sxs-lookup"><span data-stu-id="ac8b1-126">This example builds on the previous examples in this tutorial.</span></span> <span data-ttu-id="ac8b1-127">Dans le code ci-dessous, la nouvelle requête figure dans des commentaires.</span><span class="sxs-lookup"><span data-stu-id="ac8b1-127">The new query is called out in comments in the code below.</span></span>  
  
 <span data-ttu-id="ac8b1-128">Pour obtenir des instructions sur la création du document source pour cet exemple, consultez [création du document Office Open XML source (Visual Basic)](creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="ac8b1-128">You can find instructions for creating the source document for this example in [Creating the Source Office Open XML Document (Visual Basic)](creating-the-source-office-open-xml-document.md).</span></span>  
  
 <span data-ttu-id="ac8b1-129">Cet exemple utilise des classes de l'assembly WindowsBase.</span><span class="sxs-lookup"><span data-stu-id="ac8b1-129">This example uses classes found in the WindowsBase assembly.</span></span> <span data-ttu-id="ac8b1-130">Il utilise des types dans l'espace de noms <xref:System.IO.Packaging?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ac8b1-130">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
```vb  
Imports <xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main">  
  
Module Module1  
    Private Function GetStyleOfParagraph(ByVal styleNode As XElement, ByVal defaultStyle As String) As String  
        If (styleNode Is Nothing) Then  
            Return defaultStyle  
        Else  
            Return styleNode.@w:val  
        End If  
    End Function  
  
    Sub Main()  
        Dim fileName = "SampleDoc.docx"  
  
        Dim documentRelationshipType = "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument"  
        Dim stylesRelationshipType = "http://schemas.openxmlformats.org/officeDocument/2006/relationships/styles"  
        Dim wordmlNamespace = "http://schemas.openxmlformats.org/wordprocessingml/2006/main"  
  
        Dim xDoc As XDocument = Nothing  
        Dim styleDoc As XDocument = Nothing  
        Using wdPackage As Package = Package.Open(fileName, FileMode.Open, FileAccess.Read)  
            Dim docPackageRelationship As PackageRelationship = wdPackage.GetRelationshipsByType(documentRelationshipType).FirstOrDefault()  
            If (docPackageRelationship IsNot Nothing) Then  
                Dim documentUri As Uri = PackUriHelper.ResolvePartUri(New Uri("/", UriKind.Relative), docPackageRelationship.TargetUri)  
                Dim documentPart As PackagePart = wdPackage.GetPart(documentUri)  
  
                '  Load the document XML in the part into an XDocument instance.  
                xDoc = XDocument.Load(XmlReader.Create(documentPart.GetStream()))  
  
                '  Find the styles part. There will only be one.  
                Dim styleRelation As PackageRelationship = documentPart.GetRelationshipsByType(stylesRelationshipType).FirstOrDefault()  
                If (styleRelation IsNot Nothing) Then  
                    Dim styleUri As Uri = PackUriHelper.ResolvePartUri(documentUri, styleRelation.TargetUri)  
                    Dim stylePart As PackagePart = wdPackage.GetPart(styleUri)  
  
                    '  Load the style XML in the part into an XDocument instance.  
                    styleDoc = XDocument.Load(XmlReader.Create(stylePart.GetStream()))  
                End If  
            End If  
        End Using  
  
        Dim defaultStyle As String = _  
            ( _  
                From style In styleDoc.Root.<w:style> _  
                Where style.@w:type = "paragraph" And _  
                      style.@w:default = "1" _  
                Select style _  
            ).First().@w:styleId  
  
        ' Following is the new query that finds all paragraphs in the  
        ' document and their styles.  
        Dim paragraphs = _  
            From para In xDoc.Root.<w:body>...<w:p> _  
        Let styleNode As XElement = para.<w:pPr>.<w:pStyle>.FirstOrDefault() _  
        Select New With { _  
            .ParagraphNode = para, _  
            .StyleName = GetStyleOfParagraph(styleNode, defaultStyle) _  
        }  
  
        For Each p In paragraphs  
            Console.WriteLine("StyleName:{0}", p.StyleName)  
        Next  
  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="ac8b1-131">Cet exemple produit la sortie suivante lorsqu’elle est appliquée au document décrit dans [création du document Office Open XML source (Visual Basic)](creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="ac8b1-131">This example produces the following output when applied to the document described in [Creating the Source Office Open XML Document (Visual Basic)](creating-the-source-office-open-xml-document.md).</span></span>  
  
```console  
StyleName:Heading1  
StyleName:Normal  
StyleName:Normal  
StyleName:Normal  
StyleName:Code  
StyleName:Code  
StyleName:Code  
StyleName:Code  
StyleName:Code  
StyleName:Code  
StyleName:Code  
StyleName:Normal  
StyleName:Normal  
StyleName:Normal  
StyleName:Code  
```  
  
## <a name="next-steps"></a><span data-ttu-id="ac8b1-132">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="ac8b1-132">Next Steps</span></span>  
 <span data-ttu-id="ac8b1-133">Dans la rubrique suivante, [extraction du texte des paragraphes (Visual Basic)](retrieving-the-text-of-the-paragraphs.md), vous allez créer une requête pour récupérer le texte des paragraphes.</span><span class="sxs-lookup"><span data-stu-id="ac8b1-133">In the next topic, [Retrieving the Text of the Paragraphs (Visual Basic)](retrieving-the-text-of-the-paragraphs.md), you'll create a query to retrieve the text of paragraphs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac8b1-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ac8b1-134">See also</span></span>

- [<span data-ttu-id="ac8b1-135">Didacticiel : manipulation de contenu dans un document WordprocessingML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ac8b1-135">Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)</span></span>](tutorial-manipulating-content-in-a-wordprocessingml-document.md)
