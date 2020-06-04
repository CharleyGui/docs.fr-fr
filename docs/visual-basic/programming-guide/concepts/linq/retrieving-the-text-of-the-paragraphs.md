---
title: Récupération du texte des paragraphes
ms.date: 07/20/2015
ms.assetid: 095fa0d9-7b1b-4cbb-9c13-e2c9d8923d31
ms.openlocfilehash: 24167ade2d0326ef9382536f79f9e45eb22c89c5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413386"
---
# <a name="retrieving-the-text-of-the-paragraphs-visual-basic"></a><span data-ttu-id="8fa96-102">Récupération du texte des paragraphes (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8fa96-102">Retrieving the Text of the Paragraphs (Visual Basic)</span></span>
<span data-ttu-id="8fa96-103">Cet exemple s’appuie sur l’exemple précédent, [la récupération des paragraphes et de leurs styles (Visual Basic)](retrieving-the-paragraphs-and-their-styles.md).</span><span class="sxs-lookup"><span data-stu-id="8fa96-103">This example builds on the previous example, [Retrieving the Paragraphs and Their Styles (Visual Basic)](retrieving-the-paragraphs-and-their-styles.md).</span></span> <span data-ttu-id="8fa96-104">Ce nouvel exemple récupère le texte de chaque paragraphe en tant que chaîne.</span><span class="sxs-lookup"><span data-stu-id="8fa96-104">This new example retrieves the text of each paragraph as a string.</span></span>  
  
 <span data-ttu-id="8fa96-105">Pour récupérer le texte, cet exemple ajoute une requête supplémentaire qui itère au sein de la collection de types anonymes et projette une nouvelle collection d'un type anonyme avec l'ajout d'un nouveau membre, `Text`.</span><span class="sxs-lookup"><span data-stu-id="8fa96-105">To retrieve the text, this example adds an additional query that iterates through the collection of anonymous types and projects a new collection of an anonymous type with the addition of a new member, `Text`.</span></span> <span data-ttu-id="8fa96-106">Il utilise l'opérateur de requête standard <xref:System.Linq.Enumerable.Aggregate%2A> pour concaténer plusieurs chaînes dans une chaîne.</span><span class="sxs-lookup"><span data-stu-id="8fa96-106">It uses the <xref:System.Linq.Enumerable.Aggregate%2A> standard query operator to concatenate multiple strings into one string.</span></span>  
  
 <span data-ttu-id="8fa96-107">Cette technique (qui consiste à projeter vers une collection d’un type anonyme, puis à utiliser cette collection pour projeter vers une nouvelle collection d’un type anonyme) est un idiome commun et utile.</span><span class="sxs-lookup"><span data-stu-id="8fa96-107">This technique (that is, first projecting to a collection of an anonymous type, then using this collection to project to a new collection of an anonymous type) is a common and useful idiom.</span></span> <span data-ttu-id="8fa96-108">Cette requête pourrait avoir été écrite sans projeter vers le premier type anonyme.</span><span class="sxs-lookup"><span data-stu-id="8fa96-108">This query could have been written without projecting to the first anonymous type.</span></span> <span data-ttu-id="8fa96-109">Toutefois, en raison de l'évaluation différée, procéder ainsi n'utilise pas beaucoup de puissance de traitement supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="8fa96-109">However, because of lazy evaluation, doing so does not use much additional processing power.</span></span> <span data-ttu-id="8fa96-110">L'idiome crée davantage d'objets à courte durée de vie sur la pile, mais cela ne nuit pas énormément aux performances.</span><span class="sxs-lookup"><span data-stu-id="8fa96-110">The idiom creates more short lived objects on the heap, but this does not substantially degrade performance.</span></span>  
  
 <span data-ttu-id="8fa96-111">Bien entendu, il serait possible d'écrire une requête unique contenant la fonctionnalité de récupération des paragraphes, du style de chaque paragraphe et du texte de chaque paragraphe.</span><span class="sxs-lookup"><span data-stu-id="8fa96-111">Of course, it would be possible to write a single query that contains the functionality to retrieve the paragraphs, the style of each paragraph, and the text of each paragraph.</span></span> <span data-ttu-id="8fa96-112">Toutefois, il est souvent utile de découper une requête compliquée en plusieurs requêtes car le code obtenu sera plus modulable et plus facile à maintenir.</span><span class="sxs-lookup"><span data-stu-id="8fa96-112">However, it often is useful to break up a more complicated query into multiple queries because the resulting code is more modular and easier to maintain.</span></span> <span data-ttu-id="8fa96-113">En outre, si vous avez besoin de réutiliser une partie de la requête, il est plus facile de refactoriser si les requêtes sont écrites de cette manière.</span><span class="sxs-lookup"><span data-stu-id="8fa96-113">Furthermore, if you need to reuse a portion of the query, it is easier to refactor if the queries are written in this manner.</span></span>  
  
 <span data-ttu-id="8fa96-114">Ces requêtes, qui sont chaînées ensemble, utilisent le modèle de traitement examiné en détail dans la rubrique [Didacticiel : exécution différée (Visual Basic)](tutorial-deferred-execution.md).</span><span class="sxs-lookup"><span data-stu-id="8fa96-114">These queries, which are chained together, use the processing model that is examined in detail in the topic [Tutorial: Deferred Execution (Visual Basic)](tutorial-deferred-execution.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8fa96-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="8fa96-115">Example</span></span>  
 <span data-ttu-id="8fa96-116">Cet exemple traite un document WordprocessingML et détermine le nœud d'élément, le nom de style et le texte de chaque paragraphe.</span><span class="sxs-lookup"><span data-stu-id="8fa96-116">This example processes a WordprocessingML document, determining the element node, the style name, and the text of each paragraph.</span></span> <span data-ttu-id="8fa96-117">Cet exemple se base sur les exemples précédents de ce didacticiel.</span><span class="sxs-lookup"><span data-stu-id="8fa96-117">This example builds on the previous examples in this tutorial.</span></span> <span data-ttu-id="8fa96-118">Dans le code ci-dessous, la nouvelle requête figure dans des commentaires.</span><span class="sxs-lookup"><span data-stu-id="8fa96-118">The new query is called out in comments in the code below.</span></span>  
  
 <span data-ttu-id="8fa96-119">Pour obtenir des instructions sur la création du document source pour cet exemple, consultez [création du document Office Open XML source (Visual Basic)](creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="8fa96-119">For instructions for creating the source document for this example, see [Creating the Source Office Open XML Document (Visual Basic)](creating-the-source-office-open-xml-document.md).</span></span>  
  
 <span data-ttu-id="8fa96-120">Cet exemple utilise des classes de l'assembly WindowsBase.</span><span class="sxs-lookup"><span data-stu-id="8fa96-120">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="8fa96-121">Il utilise des types dans l'espace de noms <xref:System.IO.Packaging?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8fa96-121">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
```vb  
Imports <xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main">  
  
Module Module1  
    ' Following function is required because Visual Basic does not support short circuit evaluation  
    Private Function GetStyleOfParagraph(ByVal styleNode As XElement, _  
                                         ByVal defaultStyle As String) As String  
        If (styleNode Is Nothing) Then  
            Return defaultStyle  
        Else  
            Return styleNode.@w:val  
        End If  
    End Function  
  
    Sub Main()  
        Dim fileName = "SampleDoc.docx"  
  
        Dim documentRelationshipType = _  
          "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument"  
        Dim stylesRelationshipType = _  
          "http://schemas.openxmlformats.org/officeDocument/2006/relationships/styles"  
        Dim wordmlNamespace = _  
          "http://schemas.openxmlformats.org/wordprocessingml/2006/main"  
  
        Dim xDoc As XDocument = Nothing  
        Dim styleDoc As XDocument = Nothing  
        Using wdPackage As Package = Package.Open(fileName, FileMode.Open, FileAccess.Read)  
            Dim docPackageRelationship As PackageRelationship = _  
              wdPackage.GetRelationshipsByType(documentRelationshipType).FirstOrDefault()  
            If (docPackageRelationship IsNot Nothing) Then  
                Dim documentUri As Uri = PackUriHelper.ResolvePartUri(New Uri("/", UriKind.Relative), _  
                  docPackageRelationship.TargetUri)  
                Dim documentPart As PackagePart = wdPackage.GetPart(documentUri)  
  
                '  Load the document XML in the part into an XDocument instance.  
                xDoc = XDocument.Load(XmlReader.Create(documentPart.GetStream()))  
  
                '  Find the styles part. There will only be one.  
                Dim styleRelation As PackageRelationship = _  
                  documentPart.GetRelationshipsByType(stylesRelationshipType).FirstOrDefault()  
                If (styleRelation IsNot Nothing) Then  
                    Dim styleUri As Uri = _  
                      PackUriHelper.ResolvePartUri(documentUri, styleRelation.TargetUri)  
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
  
        ' Find all paragraphs in the document.  
        Dim paragraphs = _  
            From para In xDoc.Root.<w:body>...<w:p> _  
        Let styleNode As XElement = para.<w:pPr>.<w:pStyle>.FirstOrDefault _  
        Select New With { _  
            .ParagraphNode = para, _  
            .StyleName = GetStyleOfParagraph(styleNode, defaultStyle) _  
        }  
  
        ' Following is the new query that retrieves the text of  
        ' each paragraph.  
        Dim paraWithText = _  
            From para In paragraphs _  
            Select New With { _  
                .ParagraphNode = para.ParagraphNode, _  
                .StyleName = para.StyleName, _  
                .Text = para.ParagraphNode.<w:r>.<w:t> _  
                    .Aggregate(New StringBuilder(), _  
                               Function(s As StringBuilder, i As String) s.Append(CStr(i)), _  
                               Function(s As StringBuilder) s.ToString) _  
            }  
  
        For Each p In paraWithText  
            Console.WriteLine("StyleName:{0} >{1}<", p.StyleName, p.Text)  
        Next  
  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="8fa96-122">Cet exemple produit la sortie suivante lorsqu’elle est appliquée au document décrit dans [création du document Office Open XML source (Visual Basic)](creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="8fa96-122">This example produces the following output when applied to the document described in [Creating the Source Office Open XML Document (Visual Basic)](creating-the-source-office-open-xml-document.md).</span></span>  
  
```console  
StyleName:Heading1 >Parsing WordprocessingML with LINQ to XML<  
StyleName:Normal ><  
StyleName:Normal >The following example prints to the console.<  
StyleName:Normal ><  
StyleName:Code >Imports System<  
StyleName:Code ><  
StyleName:Code >Class Program<  
StyleName:Code >    Public Shared  Sub Main(ByVal args() As String)<  
StyleName:Code >        Console.WriteLine("Hello World")<  
StyleName:Code >   End Sub<  
StyleName:Code >End Class<  
StyleName:Normal ><  
StyleName:Normal >This example produces the following output:<  
StyleName:Normal ><  
StyleName:Code >Hello World<  
```  
  
## <a name="next-steps"></a><span data-ttu-id="8fa96-123">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="8fa96-123">Next Steps</span></span>  
 <span data-ttu-id="8fa96-124">L'exemple suivant montre comment utiliser une méthode d'extension, au lieu de <xref:System.Linq.Enumerable.Aggregate%2A>, pour concaténer plusieurs chaînes en une seule chaîne.</span><span class="sxs-lookup"><span data-stu-id="8fa96-124">The next example shows how to use an extension method, instead of <xref:System.Linq.Enumerable.Aggregate%2A>, to concatenate multiple strings into a single string.</span></span>  
  
- [<span data-ttu-id="8fa96-125">Refactorisation à l’aide d’une méthode d’extension (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8fa96-125">Refactoring Using an Extension Method (Visual Basic)</span></span>](refactoring-using-an-extension-method.md)  
  
## <a name="see-also"></a><span data-ttu-id="8fa96-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8fa96-126">See also</span></span>

- [<span data-ttu-id="8fa96-127">Didacticiel : manipulation de contenu dans un document WordprocessingML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8fa96-127">Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)</span></span>](tutorial-manipulating-content-in-a-wordprocessingml-document.md)
- [<span data-ttu-id="8fa96-128">Exécution et évaluation différées en LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8fa96-128">Deferred Execution and Lazy Evaluation in LINQ to XML (Visual Basic)</span></span>](deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
