---
title: Refactoriser à l’aide d’une méthode d’extension-LINQ to XML
description: Découvrez comment refactoriser la concaténation de chaînes à l’aide d’une fonction pure implémentée en tant que méthode d’extension.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: c5fc123d-af10-4a2f-b8e4-db921efb2639
ms.openlocfilehash: ea33bce2f534bce9e97d467c71df8a9474bbf6cd
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553826"
---
# <a name="refactor-using-an-extension-method-linq-to-xml"></a><span data-ttu-id="62bd0-103">Refactorisation à l’aide d’une méthode d’extension (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="62bd0-103">Refactor using an extension method (LINQ to XML)</span></span>

<span data-ttu-id="62bd0-104">Cet exemple s’appuie sur l’exemple précédent, [récupère le texte des paragraphes](retrieve-text-paragraphs.md), en refactorisant la concaténation des chaînes à l’aide d’une fonction pure implémentée en tant que méthode d’extension.</span><span class="sxs-lookup"><span data-stu-id="62bd0-104">This example builds on the previous example, [Retrieve the text of the paragraphs](retrieve-text-paragraphs.md), by refactoring the concatenation of strings using a pure function that's implemented as an extension method.</span></span>

<span data-ttu-id="62bd0-105">L'exemple précédent utilisait l'opérateur de requête standard <xref:System.Linq.Enumerable.Aggregate%2A> pour concaténer plusieurs chaînes dans une chaîne.</span><span class="sxs-lookup"><span data-stu-id="62bd0-105">The previous example used the <xref:System.Linq.Enumerable.Aggregate%2A> standard query operator to concatenate multiple strings into one string.</span></span> <span data-ttu-id="62bd0-106">Toutefois, il est plus commode d’écrire une méthode d’extension pour effectuer cette opération, car la requête résultante est plus petite et plus simple.</span><span class="sxs-lookup"><span data-stu-id="62bd0-106">However, it's more convenient to write an extension method to do this, because the resulting query is smaller and simpler.</span></span>

## <a name="example-retrieve-the-paragraphs-their-styles-and-their-text"></a><span data-ttu-id="62bd0-107">Exemple : récupérer les paragraphes, leurs styles et leur texte</span><span class="sxs-lookup"><span data-stu-id="62bd0-107">Example: Retrieve the paragraphs, their styles, and their text</span></span>

<span data-ttu-id="62bd0-108">Cet exemple traite un document WordprocessingML, en extrayant les paragraphes et le style et le texte de chaque paragraphe.</span><span class="sxs-lookup"><span data-stu-id="62bd0-108">This example processes a WordprocessingML document, retrieving the paragraphs and the style and text for each paragraph.</span></span> <span data-ttu-id="62bd0-109">Cet exemple se base sur les exemples précédents de ce didacticiel.</span><span class="sxs-lookup"><span data-stu-id="62bd0-109">This example builds on the previous examples in this tutorial.</span></span>

<span data-ttu-id="62bd0-110">L'exemple contient plusieurs surcharges de la méthode `StringConcatenate`.</span><span class="sxs-lookup"><span data-stu-id="62bd0-110">The example contains multiple overloads of the `StringConcatenate` method.</span></span>

<span data-ttu-id="62bd0-111">Les instructions pour créer le document source pour cet exemple sont dans [créer le document Office Open XML source](create-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="62bd0-111">The instructions for creating the source document for this example are in [Create the source Office Open XML document](create-source-office-open-xml-document.md).</span></span>

<span data-ttu-id="62bd0-112">Cet exemple utilise des classes de l'assembly WindowsBase.</span><span class="sxs-lookup"><span data-stu-id="62bd0-112">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="62bd0-113">Il utilise des types dans l'espace de noms <xref:System.IO.Packaging?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="62bd0-113">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>

```csharp
public static class LocalExtensions
{
    public static string StringConcatenate(this IEnumerable<string> source)
    {
        StringBuilder sb = new StringBuilder();
        foreach (string s in source)
            sb.Append(s);
        return sb.ToString();
    }

    public static string StringConcatenate<T>(this IEnumerable<T> source,
        Func<T, string> func)
    {
        StringBuilder sb = new StringBuilder();
        foreach (T item in source)
            sb.Append(func(item));
        return sb.ToString();
    }

    public static string StringConcatenate(this IEnumerable<string> source, string separator)
    {
        StringBuilder sb = new StringBuilder();
        foreach (string s in source)
            sb.Append(s).Append(separator);
        return sb.ToString();
    }

    public static string StringConcatenate<T>(this IEnumerable<T> source,
        Func<T, string> func, string separator)
    {
        StringBuilder sb = new StringBuilder();
        foreach (T item in source)
            sb.Append(func(item)).Append(separator);
        return sb.ToString();
    }
}
```

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

## <a name="example-use-all-four-overloads-of-the-stringconcatenate-method"></a><span data-ttu-id="62bd0-114">Exemple : utiliser les quatre surcharges de la `StringConcatenate` méthode</span><span class="sxs-lookup"><span data-stu-id="62bd0-114">Example: Use all four overloads of the `StringConcatenate` method</span></span>

<span data-ttu-id="62bd0-115">Il existe quatre surcharges de la méthode `StringConcatenate`.</span><span class="sxs-lookup"><span data-stu-id="62bd0-115">There are four overloads of the `StringConcatenate` method.</span></span> <span data-ttu-id="62bd0-116">Une surcharge prend simplement une collection de chaînes et retourne une seule chaîne.</span><span class="sxs-lookup"><span data-stu-id="62bd0-116">One overload simply takes a collection of strings and returns a single string.</span></span> <span data-ttu-id="62bd0-117">Une autre surcharge prend une collection d'un type quelconque et un délégué qui projette depuis un singleton de la collection vers une chaîne.</span><span class="sxs-lookup"><span data-stu-id="62bd0-117">Another overload can take a collection of any type, and a delegate that projects from a singleton of the collection to a string.</span></span> <span data-ttu-id="62bd0-118">Il existe deux surcharges supplémentaires qui vous permettent de spécifier une chaîne de séparation.</span><span class="sxs-lookup"><span data-stu-id="62bd0-118">There are two more overloads that allow you to specify a separator string.</span></span>

<span data-ttu-id="62bd0-119">Le code suivant utilise les quatre surcharges suivantes :</span><span class="sxs-lookup"><span data-stu-id="62bd0-119">The following code uses all four overloads:</span></span>

```csharp
string[] numbers = { "one", "two", "three" };

Console.WriteLine("{0}", numbers.StringConcatenate());
Console.WriteLine("{0}", numbers.StringConcatenate(":"));

int[] intNumbers = { 1, 2, 3 };
Console.WriteLine("{0}", intNumbers.StringConcatenate(i => i.ToString()));
Console.WriteLine("{0}", intNumbers.StringConcatenate(i => i.ToString(), ":"));
```

```vb
Dim numbers As String() = {"one", "two", "three"}

Console.WriteLine("{0}", numbers.StringConcatenate())
Console.WriteLine("{0}", numbers.StringConcatenate(":"))

Dim intNumbers As Integer() = {1, 2, 3}
Console.WriteLine("{0}", intNumbers.StringConcatenate(Function(i) i.ToString()))
Console.WriteLine("{0}", intNumbers.StringConcatenate(Function(i) i.ToString(), ":"))
```

<span data-ttu-id="62bd0-120">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="62bd0-120">This example produces the following output:</span></span>

```output
onetwothree
one:two:three:
123
1:2:3:
```

## <a name="example-use-the-new-extension-method"></a><span data-ttu-id="62bd0-121">Exemple : utiliser la nouvelle méthode d’extension</span><span class="sxs-lookup"><span data-stu-id="62bd0-121">Example: Use the new extension method</span></span>

<span data-ttu-id="62bd0-122">À présent, l’exemple peut être modifié pour tirer parti de la nouvelle méthode d’extension :</span><span class="sxs-lookup"><span data-stu-id="62bd0-122">Now the example can be modified to take advantage of the new extension method:</span></span>

```csharp
public static class LocalExtensions
{
    public static string StringConcatenate(this IEnumerable<string> source)
    {
        StringBuilder sb = new StringBuilder();
        foreach (string s in source)
            sb.Append(s);
        return sb.ToString();
    }

    public static string StringConcatenate<T>(this IEnumerable<T> source,
        Func<T, string> func)
    {
        StringBuilder sb = new StringBuilder();
        foreach (T item in source)
            sb.Append(func(item));
        return sb.ToString();
    }

    public static string StringConcatenate(this IEnumerable<string> source, string separator)
    {
        StringBuilder sb = new StringBuilder();
        foreach (string s in source)
            sb.Append(s).Append(separator);
        return sb.ToString();
    }

    public static string StringConcatenate<T>(this IEnumerable<T> source,
        Func<T, string> func, string separator)
    {
        StringBuilder sb = new StringBuilder();
        foreach (T item in source)
            sb.Append(func(item)).Append(separator);
        return sb.ToString();
    }
}

class Program
{
    static void Main(string[] args)
    {
        const string fileName = "SampleDoc.docx";

        const string documentRelationshipType =
          "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument";
        const string stylesRelationshipType =
          "http://schemas.openxmlformats.org/officeDocument/2006/relationships/styles";
        const string wordmlNamespace =
          "http://schemas.openxmlformats.org/wordprocessingml/2006/main";
        XNamespace w = wordmlNamespace;

        XDocument xDoc = null;
        XDocument styleDoc = null;

        using (Package wdPackage = Package.Open(fileName, FileMode.Open, FileAccess.Read))
        {
            PackageRelationship docPackageRelationship =
              wdPackage.GetRelationshipsByType(documentRelationshipType).FirstOrDefault();
            if (docPackageRelationship != null)
            {
                Uri documentUri = PackUriHelper.ResolvePartUri(new Uri("/", UriKind.Relative),
                  docPackageRelationship.TargetUri);
                PackagePart documentPart = wdPackage.GetPart(documentUri);

                //  Load the document XML in the part into an XDocument instance.
                xDoc = XDocument.Load(XmlReader.Create(documentPart.GetStream()));

                //  Find the styles part. There will only be one.
                PackageRelationship styleRelation =
                  documentPart.GetRelationshipsByType(stylesRelationshipType).FirstOrDefault();
                if (styleRelation != null)
                {
                    Uri styleUri =
                      PackUriHelper.ResolvePartUri(documentUri, styleRelation.TargetUri);
                    PackagePart stylePart = wdPackage.GetPart(styleUri);

                    //  Load the style XML in the part into an XDocument instance.
                    styleDoc = XDocument.Load(XmlReader.Create(stylePart.GetStream()));
                }
            }
        }

        string defaultStyle =
            (string)(
                from style in styleDoc.Root.Elements(w + "style")
                where (string)style.Attribute(w + "type") == "paragraph" &&
                      (string)style.Attribute(w + "default") == "1"
                select style
            ).First().Attribute(w + "styleId");

        // Find all paragraphs in the document.
        var paragraphs =
            from para in xDoc
                         .Root
                         .Element(w + "body")
                         .Descendants(w + "p")
            let styleNode = para
                            .Elements(w + "pPr")
                            .Elements(w + "pStyle")
                            .FirstOrDefault()
            select new
            {
                ParagraphNode = para,
                StyleName = styleNode != null ?
                    (string)styleNode.Attribute(w + "val") :
                    defaultStyle
            };

        // Retrieve the text of each paragraph.
        var paraWithText =
            from para in paragraphs
            select new
            {
                ParagraphNode = para.ParagraphNode,
                StyleName = para.StyleName,
                Text = para
                       .ParagraphNode
                       .Elements(w + "r")
                       .Elements(w + "t")
                       .StringConcatenate(e => (string)e)
            };

        foreach (var p in paraWithText)
            Console.WriteLine("StyleName:{0} >{1}<", p.StyleName, p.Text);
    }
}
```

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

    ' Following function is required because Visual Basic doesn't support short circuit evaluation
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

 <span data-ttu-id="62bd0-123">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="62bd0-123">This example produces the following output:</span></span>

```output
StyleName:Heading1 >Parsing WordprocessingML with LINQ to XML<
StyleName:Normal ><
StyleName:Normal >The following example prints to the console.<
StyleName:Normal ><
StyleName:Code >using System;<
StyleName:Code ><
StyleName:Code >class Program {<
StyleName:Code >    public static void (string[] args) {<
StyleName:Code >        Console.WriteLine("Hello World");<
StyleName:Code >    }<
StyleName:Code >}<
StyleName:Normal ><
StyleName:Normal >This example produces the following output:<
StyleName:Normal ><
StyleName:Code >Hello World<
```

<span data-ttu-id="62bd0-124">Cette refactorisation est une variante de la refactorisation dans une fonction pure.</span><span class="sxs-lookup"><span data-stu-id="62bd0-124">This refactoring is a variant of refactoring into a pure function.</span></span> <span data-ttu-id="62bd0-125">L’article suivant de ce didacticiel explique plus en détail comment Refactoriser ce code en fonctions pures :</span><span class="sxs-lookup"><span data-stu-id="62bd0-125">The next article in this tutorial shows in more detail how to refactor this code into pure functions:</span></span>

- [<span data-ttu-id="62bd0-126">Refactoriser à l’aide d’une fonction pure</span><span class="sxs-lookup"><span data-stu-id="62bd0-126">Refactor using a pure function</span></span>](refactor-pure-function.md)

## <a name="see-also"></a><span data-ttu-id="62bd0-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="62bd0-127">See also</span></span>

- [<span data-ttu-id="62bd0-128">Didacticiel : manipuler du contenu dans un document WordprocessingML</span><span class="sxs-lookup"><span data-stu-id="62bd0-128">Tutorial: Manipulate content in a WordprocessingML document</span></span>](xml-shape-wordprocessingml-documents.md)
- [<span data-ttu-id="62bd0-129">Refactoriser dans des fonctions pures</span><span class="sxs-lookup"><span data-stu-id="62bd0-129">Refactor into pure functions</span></span>](refactor-pure-functions.md)
