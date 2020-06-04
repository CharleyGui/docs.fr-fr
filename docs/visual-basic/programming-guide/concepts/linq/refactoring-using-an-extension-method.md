---
title: Refactorisation à l’aide d’une méthode d’extension
ms.date: 07/20/2015
ms.assetid: d87ae99a-cfa9-4a31-a5e4-9d6437be6810
ms.openlocfilehash: 5bb3ed44c0c3f7616468f820428fe1a384ab6d45
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413432"
---
# <a name="refactoring-using-an-extension-method-visual-basic"></a><span data-ttu-id="c2094-102">Refactorisation à l’aide d’une méthode d’extension (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c2094-102">Refactoring Using an Extension Method (Visual Basic)</span></span>
<span data-ttu-id="c2094-103">Cet exemple s’appuie sur l’exemple précédent, [récupérant le texte des paragraphes (Visual Basic)](retrieving-the-text-of-the-paragraphs.md), en refactorisant la concaténation des chaînes à l’aide d’une fonction pure implémentée en tant que méthode d’extension.</span><span class="sxs-lookup"><span data-stu-id="c2094-103">This example builds on the previous example, [Retrieving the Text of the Paragraphs (Visual Basic)](retrieving-the-text-of-the-paragraphs.md), by refactoring the concatenation of strings using a pure function that is implemented as an extension method.</span></span>  
  
 <span data-ttu-id="c2094-104">L'exemple précédent utilisait l'opérateur de requête standard <xref:System.Linq.Enumerable.Aggregate%2A> pour concaténer plusieurs chaînes dans une chaîne.</span><span class="sxs-lookup"><span data-stu-id="c2094-104">The previous example used the <xref:System.Linq.Enumerable.Aggregate%2A> standard query operator to concatenate multiple strings into one string.</span></span> <span data-ttu-id="c2094-105">Toutefois, il est plus commode d'écrire une méthode d'extension pour cela, car la requête résultante est plus petite et plus simple.</span><span class="sxs-lookup"><span data-stu-id="c2094-105">However, it is more convenient to write an extension method to do this, because the resulting query smaller and more simple.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c2094-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="c2094-106">Example</span></span>  
 <span data-ttu-id="c2094-107">Cet exemple traite un document WordprocessingML, récupère les paragraphes, le style de chaque paragraphe et le texte de chaque paragraphe.</span><span class="sxs-lookup"><span data-stu-id="c2094-107">This example processes a WordprocessingML document, retrieving the paragraphs, the style of each paragraph, and the text of each paragraph.</span></span> <span data-ttu-id="c2094-108">Cet exemple se base sur les exemples précédents de ce didacticiel.</span><span class="sxs-lookup"><span data-stu-id="c2094-108">This example builds on the previous examples in this tutorial.</span></span>  
  
 <span data-ttu-id="c2094-109">L'exemple contient plusieurs surcharges de la méthode `StringConcatenate`.</span><span class="sxs-lookup"><span data-stu-id="c2094-109">The example contains multiple overloads of the `StringConcatenate` method.</span></span>  
  
 <span data-ttu-id="c2094-110">Pour obtenir des instructions sur la création du document source pour cet exemple, consultez [création du document Office Open XML source (Visual Basic)](creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="c2094-110">You can find instructions for creating the source document for this example in [Creating the Source Office Open XML Document (Visual Basic)](creating-the-source-office-open-xml-document.md).</span></span>  
  
 <span data-ttu-id="c2094-111">Cet exemple utilise des classes de l'assembly WindowsBase.</span><span class="sxs-lookup"><span data-stu-id="c2094-111">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="c2094-112">Il utilise des types dans l'espace de noms <xref:System.IO.Packaging?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c2094-112">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
```vb  
<System.Runtime.CompilerServices.Extension()> _  
Public Function StringConcatenate(ByVal source As IEnumerable(Of String)) As String  
    Dim sb As StringBuilder = New StringBuilder()  
    For Each s As String In source  
        sb.Append(s)  
    Next  
    Return sb.ToString()  
End Function  
  
<System.Runtime.CompilerServices.Extension()> _  
Public Function StringConcatenate(Of T)(ByVal source As IEnumerable(Of T), _  
ByVal func As Func(Of T, String)) As String  
    Dim sb As StringBuilder = New StringBuilder()  
    For Each item As T In source  
        sb.Append(func(item))  
    Next  
    Return sb.ToString()  
End Function  
  
<System.Runtime.CompilerServices.Extension()> _  
Public Function StringConcatenate(Of T)(ByVal source As IEnumerable(Of T), _  
ByVal separator As String) As String  
    Dim sb As StringBuilder = New StringBuilder()  
    For Each s As T In source  
        sb.Append(s).Append(separator)  
    Next  
    Return sb.ToString()  
End Function  
  
<System.Runtime.CompilerServices.Extension()> _  
Public Function StringConcatenate(Of T)(ByVal source As IEnumerable(Of T), _  
ByVal func As Func(Of T, String), ByVal separator As String) As String  
    Dim sb As StringBuilder = New StringBuilder()  
    For Each item As T In source  
        sb.Append(func(item)).Append(separator)  
    Next  
    Return sb.ToString()  
End Function  
```  
  
## <a name="example"></a><span data-ttu-id="c2094-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="c2094-113">Example</span></span>  
 <span data-ttu-id="c2094-114">Il existe quatre surcharges de la méthode `StringConcatenate`.</span><span class="sxs-lookup"><span data-stu-id="c2094-114">There are four overloads of the `StringConcatenate` method.</span></span> <span data-ttu-id="c2094-115">Une surcharge prend simplement une collection de chaînes et retourne une seule chaîne.</span><span class="sxs-lookup"><span data-stu-id="c2094-115">One overload simply takes a collection of strings and returns a single string.</span></span> <span data-ttu-id="c2094-116">Une autre surcharge prend une collection d'un type quelconque et un délégué qui projette depuis un singleton de la collection vers une chaîne.</span><span class="sxs-lookup"><span data-stu-id="c2094-116">Another overload can take a collection of any type, and a delegate that projects from a singleton of the collection to a string.</span></span> <span data-ttu-id="c2094-117">Il existe deux surcharges supplémentaires qui vous permettent de spécifier une chaîne de séparation.</span><span class="sxs-lookup"><span data-stu-id="c2094-117">There are two more overloads that allow you to specify a separator string.</span></span>  
  
 <span data-ttu-id="c2094-118">Le code suivant utilise les quatre surcharges.</span><span class="sxs-lookup"><span data-stu-id="c2094-118">The following code uses all four overloads.</span></span>  
  
```vb  
Dim numbers As String() = {"one", "two", "three"}  
  
Console.WriteLine("{0}", numbers.StringConcatenate())  
Console.WriteLine("{0}", numbers.StringConcatenate(":"))  
  
Dim intNumbers As Integer() = {1, 2, 3}  
Console.WriteLine("{0}", intNumbers.StringConcatenate(Function(i) i.ToString()))  
Console.WriteLine("{0}", intNumbers.StringConcatenate(Function(i) i.ToString(), ":"))  
```  
  
 <span data-ttu-id="c2094-119">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="c2094-119">This example produces the following output:</span></span>  
  
```console  
onetwothree  
one:two:three:  
123  
1:2:3:  
```  
  
## <a name="example"></a><span data-ttu-id="c2094-120">Exemple</span><span class="sxs-lookup"><span data-stu-id="c2094-120">Example</span></span>  
 <span data-ttu-id="c2094-121">À présent, l’exemple peut être modifié pour tirer parti de la nouvelle méthode d’extension :</span><span class="sxs-lookup"><span data-stu-id="c2094-121">Now, the example can be modified to take advantage of the new extension method:</span></span>  
  
```vb  
Imports <xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main">  
  
Module Module1  
    <System.Runtime.CompilerServices.Extension()> _  
    Public Function StringConcatenate(ByVal source As IEnumerable(Of String)) As String  
        Dim sb As StringBuilder = New StringBuilder()  
        For Each s As String In source  
            sb.Append(s)  
        Next  
        Return sb.ToString()  
    End Function  
  
    <System.Runtime.CompilerServices.Extension()> _  
    Public Function StringConcatenate(Of T)(ByVal source As IEnumerable(Of T), _  
    ByVal func As Func(Of T, String)) As String  
        Dim sb As StringBuilder = New StringBuilder()  
        For Each item As T In source  
            sb.Append(func(item))  
        Next  
        Return sb.ToString()  
    End Function  
  
    <System.Runtime.CompilerServices.Extension()> _  
    Public Function StringConcatenate(Of T)(ByVal source As IEnumerable(Of T), _  
    ByVal separator As String) As String  
        Dim sb As StringBuilder = New StringBuilder()  
        For Each s As T In source  
            sb.Append(s).Append(separator)  
        Next  
        Return sb.ToString()  
    End Function  
  
    <System.Runtime.CompilerServices.Extension()> _  
    Public Function StringConcatenate(Of T)(ByVal source As IEnumerable(Of T), _  
    ByVal func As Func(Of T, String), ByVal separator As String) As String  
        Dim sb As StringBuilder = New StringBuilder()  
        For Each item As T In source  
            sb.Append(func(item)).Append(separator)  
        Next  
        Return sb.ToString()  
    End Function  
  
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
  
        ' Retrieve the text of each paragraph.  
        Dim paraWithText = _  
            From para In paragraphs _  
            Select New With { _  
                .ParagraphNode = para.ParagraphNode, _  
                .StyleName = para.StyleName, _  
                .Text = para.ParagraphNode.<w:r>.<w:t>.StringConcatenate(Function(e) CStr(e)) _  
            }  
  
        For Each p In paraWithText  
            Console.WriteLine("StyleName:{0} >{1}<", p.StyleName, p.Text)  
        Next  
  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="c2094-122">Cet exemple produit la sortie suivante lorsqu’elle est appliquée au document décrit dans [création du document Office Open XML source (Visual Basic)](creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="c2094-122">This example produces the following output when applied to the document described in [Creating the Source Office Open XML Document (Visual Basic)](creating-the-source-office-open-xml-document.md).</span></span>
  
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
  
 <span data-ttu-id="c2094-123">Notez que cette refactorisation est une variante de la refactorisation dans une fonction pure.</span><span class="sxs-lookup"><span data-stu-id="c2094-123">Note that this refactoring is a variant of refactoring into a pure function.</span></span> <span data-ttu-id="c2094-124">La rubrique suivante présente le concept de factorisation dans des fonctions pures de manière plus détaillée.</span><span class="sxs-lookup"><span data-stu-id="c2094-124">The next topic will introduce the idea of factoring into pure functions in more detail.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="c2094-125">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="c2094-125">Next Steps</span></span>  
 <span data-ttu-id="c2094-126">L'exemple suivant montre comment refactoriser ce code d'une autre manière, à l'aide de fonctions pures :</span><span class="sxs-lookup"><span data-stu-id="c2094-126">The next example shows how to refactor this code in another way, by using pure functions:</span></span>  
  
- [<span data-ttu-id="c2094-127">Refactorisation à l’aide d’une fonction pure (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c2094-127">Refactoring Using a Pure Function (Visual Basic)</span></span>](refactoring-using-a-pure-function.md)  
  
## <a name="see-also"></a><span data-ttu-id="c2094-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c2094-128">See also</span></span>

- [<span data-ttu-id="c2094-129">Didacticiel : manipulation de contenu dans un document WordprocessingML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c2094-129">Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)</span></span>](tutorial-manipulating-content-in-a-wordprocessingml-document.md)
- [<span data-ttu-id="c2094-130">Refactorisation dans des fonctions pures (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c2094-130">Refactoring Into Pure Functions (Visual Basic)</span></span>](refactoring-into-pure-functions.md)
