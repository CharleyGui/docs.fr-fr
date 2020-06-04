---
title: Refactorisation à l’aide d’une fonction pure
ms.date: 07/20/2015
ms.assetid: af0ea62f-4f57-4868-b624-a85524055935
ms.openlocfilehash: 675baa4eb07db7a798b9bd47877c8f019a7021e3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413445"
---
# <a name="refactoring-using-a-pure-function-visual-basic"></a><span data-ttu-id="14614-102">Refactorisation à l’aide d’une fonction pure (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="14614-102">Refactoring Using a Pure Function (Visual Basic)</span></span>
<span data-ttu-id="14614-103">L’exemple suivant refactorise l’exemple précédent, [refactorisation à l’aide d’une méthode d’extension (Visual Basic)](refactoring-using-an-extension-method.md), pour utiliser une fonction pure dans cet exemple, le code permettant de rechercher le texte d’un paragraphe est déplacé vers la méthode statique pure `ParagraphText` .</span><span class="sxs-lookup"><span data-stu-id="14614-103">The following example refactors the previous example, [Refactoring Using an Extension Method (Visual Basic)](refactoring-using-an-extension-method.md), to use a pure function In this example, the code to find the text of a paragraph is moved to the pure static method `ParagraphText`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="14614-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="14614-104">Example</span></span>  
 <span data-ttu-id="14614-105">Cet exemple traite un document WordprocessingML et récupère les nœuds de paragraphes à partir d'un document WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="14614-105">This example processes a WordprocessingML document, retrieving the paragraph nodes from a WordprocessingML document.</span></span> <span data-ttu-id="14614-106">Il identifie également le style de chaque paragraphe.</span><span class="sxs-lookup"><span data-stu-id="14614-106">It also identifies the style of each paragraph.</span></span> <span data-ttu-id="14614-107">Cet exemple se base sur les exemples précédents de ce didacticiel.</span><span class="sxs-lookup"><span data-stu-id="14614-107">This example builds on the previous examples in this tutorial.</span></span> <span data-ttu-id="14614-108">Dans le code ci-dessous, le code refactorisé figure dans des commentaires.</span><span class="sxs-lookup"><span data-stu-id="14614-108">The refactored code is called out in comments in the code below.</span></span>  
  
 <span data-ttu-id="14614-109">Pour obtenir des instructions sur la création du document source pour cet exemple, consultez [création du document Office Open XML source (Visual Basic)](creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="14614-109">For instructions for creating the source document for this example, see [Creating the Source Office Open XML Document (Visual Basic)](creating-the-source-office-open-xml-document.md).</span></span>  
  
 <span data-ttu-id="14614-110">Cet exemple utilise des classes de l'assembly WindowsBase.</span><span class="sxs-lookup"><span data-stu-id="14614-110">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="14614-111">Il utilise des types dans l'espace de noms <xref:System.IO.Packaging?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="14614-111">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
```vb  
Imports <xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main">  
Module Module1  
    <System.Runtime.CompilerServices.Extension()> _  
    Public Function StringConcatenate(ByVal source As IEnumerable(Of String)) As String  
        Dim sb = New StringBuilder()  
        For Each s In source  
            sb.Append(s)  
        Next  
        Return sb.ToString()  
    End Function  
  
    <System.Runtime.CompilerServices.Extension()> _  
    Public Function StringConcatenate(Of T)(ByVal source As IEnumerable(Of T), _  
    ByVal func As Func(Of T, String)) As String  
        Dim sb = New StringBuilder()  
        For Each item As T In source  
            sb.Append(func(item))  
        Next  
        Return sb.ToString()  
    End Function  
  
    <System.Runtime.CompilerServices.Extension()> _  
    Public Function StringConcatenate(Of T)(ByVal source As IEnumerable(Of T), _  
    ByVal separator As String) As String  
        Dim sb = New StringBuilder()  
        For Each s As T In source  
            sb.Append(s).Append(separator)  
        Next  
        Return sb.ToString()  
    End Function  
  
    <System.Runtime.CompilerServices.Extension()> _  
    Public Function StringConcatenate(Of T)(ByVal source As IEnumerable(Of T), _  
    ByVal func As Func(Of T, String), ByVal separator As String) As String  
        Dim sb = New StringBuilder()  
        For Each item As T In source  
            sb.Append(func(item)).Append(separator)  
        Next  
        Return sb.ToString()  
    End Function  
  
    ' This is a new method that assembles the paragraph text.  
    Public Function ParagraphText(ByVal e As XElement) As String  
        Dim w = e.Name.Namespace  
        Return (e.<w:r>.<w:t>).StringConcatenate(Function(element) CStr(element))  
    End Function  
  
    ' Following function is required because Visual Basic does not support short circuit evaluation  
    Private Function GetStyleOfParagraph(ByVal styleNode As XElement, _  
                                         ByVal defaultStyle As String) As String  
        If styleNode Is Nothing Then  
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
                If styleRelation IsNot Nothing Then  
                    Dim styleUri As Uri = _  
                      PackUriHelper.ResolvePartUri(documentUri, styleRelation.TargetUri)  
                    Dim stylePart As PackagePart = wdPackage.GetPart(styleUri)  
  
                    '  Load the style XML in the part into an XDocument instance.  
                    styleDoc = XDocument.Load(XmlReader.Create(stylePart.GetStream()))  
                End If  
            End If  
        End Using  
  
        Dim defaultStyle = _  
            ( _  
                From style In styleDoc.Root.<w:style> _  
                Where style.@w:type = "paragraph" And _  
                      style.@w:default = "1" _  
                Select style _  
            ).First().@w:styleId  
  
        ' Find all paragraphs in the document.  
        Dim paragraphs = _  
            From para In xDoc.Root.<w:body>...<w:p> _  
        Let styleNode = para.<w:pPr>.<w:pStyle>.FirstOrDefault _  
        Select New With { _  
            .ParagraphNode = para, _  
            .StyleName = GetStyleOfParagraph(styleNode, defaultStyle) _  
        }  
  
        ' Retrieve the text of each paragraph.  
        Dim paraWithText = _  
            From para In paragraphs _  
            Select New With { _  
                .ParagraphNode = para.ParagraphNode, _  
                .StyleName = para.StyleName, _  
                .Text = ParagraphText(para.ParagraphNode) _  
            }  
  
        For Each p In paraWithText  
            Console.WriteLine("StyleName:{0} >{1}<", p.StyleName, p.Text)  
        Next  
    End Sub  
End Module
```  
  
 <span data-ttu-id="14614-112">Cet exemple produit la même sortie qu'avant la refactorisation :</span><span class="sxs-lookup"><span data-stu-id="14614-112">This example produces the same output as before the refactoring:</span></span>  
  
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
  
### <a name="next-steps"></a><span data-ttu-id="14614-113">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="14614-113">Next Steps</span></span>  
 <span data-ttu-id="14614-114">L'exemple suivant montre comment projeter du code XML en une autre forme :</span><span class="sxs-lookup"><span data-stu-id="14614-114">The next example shows how to project XML into a different shape:</span></span>  
  
- [<span data-ttu-id="14614-115">Projection de code XML dans une autre forme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="14614-115">Projecting XML in a Different Shape (Visual Basic)</span></span>](projecting-xml-in-a-different-shape.md)  
  
## <a name="see-also"></a><span data-ttu-id="14614-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="14614-116">See also</span></span>

- [<span data-ttu-id="14614-117">Didacticiel : manipulation de contenu dans un document WordprocessingML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="14614-117">Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)</span></span>](tutorial-manipulating-content-in-a-wordprocessingml-document.md)
- [<span data-ttu-id="14614-118">Refactorisation à l’aide d’une méthode d’extension (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="14614-118">Refactoring Using an Extension Method (Visual Basic)</span></span>](refactoring-using-an-extension-method.md)
- [<span data-ttu-id="14614-119">Refactorisation dans des fonctions pures (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="14614-119">Refactoring Into Pure Functions (Visual Basic)</span></span>](refactoring-into-pure-functions.md)
