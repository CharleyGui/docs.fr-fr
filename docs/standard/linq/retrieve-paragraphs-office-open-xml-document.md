---
title: Comment récupérer des paragraphes à partir d’un document Office Open XML-LINQ to XML
description: Cet article fournit un exemple qui ouvre un document Office Open XML et récupère une collection de tous les paragraphes du document.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: cc2687cf-d648-451e-88ac-3847c6c967c8
ms.openlocfilehash: 35e48defb2fa010a4403d50373f6e491fad6c293
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553689"
---
# <a name="how-to-retrieve-paragraphs-from-an-office-open-xml-document-linq-to-xml"></a><span data-ttu-id="b77f4-103">Comment récupérer des paragraphes à partir d’un document Office Open XML (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="b77f4-103">How to retrieve paragraphs from an Office Open XML document (LINQ to XML)</span></span>

<span data-ttu-id="b77f4-104">Cet article fournit un exemple qui ouvre un document Office Open XML et récupère une collection de tous les paragraphes du document.</span><span class="sxs-lookup"><span data-stu-id="b77f4-104">This article provides an example that opens an Office Open XML document and retrieves a collection of all of the paragraphs in the document.</span></span>

<span data-ttu-id="b77f4-105">Pour plus d’informations sur Office Open XML, consultez le [Kit de développement logiciel (SDK) Open XML](https://github.com/OfficeDev/Open-XML-SDK) et le [blog de Eric White](http://www.ericwhite.com/).</span><span class="sxs-lookup"><span data-stu-id="b77f4-105">For more information on Office Open XML, see [Open XML SDK](https://github.com/OfficeDev/Open-XML-SDK) and [Eric White's Blog](http://www.ericwhite.com/).</span></span>

## <a name="example-retrieve-the-paragraphs-from-an-office-open-xml-document"></a><span data-ttu-id="b77f4-106">Exemple : récupérer les paragraphes d’un document Office Open XML</span><span class="sxs-lookup"><span data-stu-id="b77f4-106">Example: Retrieve the paragraphs from an Office Open XML document</span></span>

<span data-ttu-id="b77f4-107">L’exemple ouvre un package Office Open XML et utilise les relations au sein du package pour rechercher le document et les parties de style.</span><span class="sxs-lookup"><span data-stu-id="b77f4-107">The example opens an Office Open XML package, and uses the relationships within the package to find the document and the style parts.</span></span> <span data-ttu-id="b77f4-108">Il interroge ensuite le document et projette une collection qui contient les informations de paragraphe.</span><span class="sxs-lookup"><span data-stu-id="b77f4-108">It then queries the document and projects a collection that has the paragraph information.</span></span> <span data-ttu-id="b77f4-109">Chaque objet de la collection représente un paragraphe et contient le nœud de paragraphe <xref:System.Xml.Linq.XElement> , le nom de style et le texte.</span><span class="sxs-lookup"><span data-stu-id="b77f4-109">Each object of the collection represents a paragraph, and contains the paragraph <xref:System.Xml.Linq.XElement> node, the style name, and the text.</span></span>

<span data-ttu-id="b77f4-110">L’exemple fonctionne sur le document Office Open XML décrit dans [créer le document Office Open XML source](create-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="b77f4-110">The example operates on the Office Open XML document described in [Create the source Office Open XML document](create-source-office-open-xml-document.md).</span></span>

<span data-ttu-id="b77f4-111">Il utilise les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="b77f4-111">It makes use of the following:</span></span>

- <span data-ttu-id="b77f4-112">`StringConcatenate`Méthode d’extension, définie dans le cadre de l’exemple.</span><span class="sxs-lookup"><span data-stu-id="b77f4-112">The `StringConcatenate` extension method, defined as part of the example.</span></span>
- <span data-ttu-id="b77f4-113">Classes trouvées dans l’assembly WindowsBase.</span><span class="sxs-lookup"><span data-stu-id="b77f4-113">Classes found in the WindowsBase assembly.</span></span>
- <span data-ttu-id="b77f4-114">Types dans l' <xref:System.IO.Packaging?displayProperty=nameWithType> espace de noms.</span><span class="sxs-lookup"><span data-stu-id="b77f4-114">Types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>

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
    public static string ParagraphText(XElement e)
    {
        XNamespace w = e.Name.Namespace;
        return e
               .Elements(w + "r")
               .Elements(w + "t")
               .StringConcatenate(element => (string)element);
    }

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
              wdPackage
              .GetRelationshipsByType(documentRelationshipType)
              .FirstOrDefault();
            if (docPackageRelationship != null)
            {
                Uri documentUri =
                    PackUriHelper
                    .ResolvePartUri(
                       new Uri("/", UriKind.Relative),
                             docPackageRelationship.TargetUri);
                PackagePart documentPart =
                    wdPackage.GetPart(documentUri);

                //  Load the document XML in the part into an XDocument instance.
                xDoc = XDocument.Load(XmlReader.Create(documentPart.GetStream()));

                //  Find the styles part. There will only be one.
                PackageRelationship styleRelation =
                  documentPart.GetRelationshipsByType(stylesRelationshipType)
                  .FirstOrDefault();
                if (styleRelation != null)
                {
                    Uri styleUri = PackUriHelper.ResolvePartUri(documentUri, styleRelation.TargetUri);
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
                Text = ParagraphText(para.ParagraphNode)
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

    Public Function ParagraphText(ByVal e As XElement) As String
        Dim w As XNamespace = e.Name.Namespace
        Return (e.<w:r>.<w:t>).StringConcatenate(Function(element) CStr(element))
    End Function

    ' The following function is required because Visual Basic doesn't support short circuit evaluation
    Private Function GetStyleOfParagraph(ByVal styleNode As XElement, ByVal defaultStyle As String) _
                As String
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
              wdPackage _
              .GetRelationshipsByType(documentRelationshipType) _
              .FirstOrDefault()
            If (docPackageRelationship IsNot Nothing) Then
                Dim documentUri As Uri = _
                  PackUriHelper _
                  .ResolvePartUri(New Uri("/", UriKind.Relative), docPackageRelationship.TargetUri)
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
                .Text = ParagraphText(para.ParagraphNode) _
            }

        For Each p In paraWithText
            Console.WriteLine("StyleName:{0} >{1}<", p.StyleName, p.Text)
        Next
    End Sub
End Module
```

<span data-ttu-id="b77f4-115">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="b77f4-115">This example produces the following output:</span></span>

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
