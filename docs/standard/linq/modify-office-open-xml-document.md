---
title: Procédure de modification d’un document Office Open XML-LINQ to XML
description: Cet article présente un exemple de code C# et Visual Basic qui ouvre un document Office Open XML, le modifie et l’enregistre.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 467d489c-2b1b-453b-a757-8ac180e82a96
ms.openlocfilehash: 03cf760a7d591e9aa2f05007be299502581e4e2a
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552536"
---
# <a name="how-to-modify-an-office-open-xml-document-linq-to-xml"></a><span data-ttu-id="f8fcb-103">Modification d’un document Office Open XML (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="f8fcb-103">How to modify an Office Open XML document (LINQ to XML)</span></span>

<span data-ttu-id="f8fcb-104">Cet article présente un exemple de code C# et Visual Basic qui ouvre un document Office Open XML, le modifie et l’enregistre.</span><span class="sxs-lookup"><span data-stu-id="f8fcb-104">This article presents an example for C# and Visual Basic that opens an Office Open XML document, modifies it, and saves it.</span></span>

<span data-ttu-id="f8fcb-105">Pour plus d’informations sur Office Open XML, consultez [Open XML SDK](https://github.com/OfficeDev/Open-XML-SDK) et [www.ericwhite.com](http://ericwhite.com/).</span><span class="sxs-lookup"><span data-stu-id="f8fcb-105">For more information on Office Open XML, see [Open XML SDK](https://github.com/OfficeDev/Open-XML-SDK) and [www.ericwhite.com](http://ericwhite.com/).</span></span>

## <a name="example"></a><span data-ttu-id="f8fcb-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="f8fcb-106">Example</span></span>

<span data-ttu-id="f8fcb-107">Cet exemple recherche le premier élément de paragraphe dans le document.</span><span class="sxs-lookup"><span data-stu-id="f8fcb-107">This example finds the first paragraph element in the document.</span></span> <span data-ttu-id="f8fcb-108">Il récupère le texte du paragraphe et supprime toutes les séquences de texte.</span><span class="sxs-lookup"><span data-stu-id="f8fcb-108">It retrieves the text from the paragraph, and deletes all text runs.</span></span> <span data-ttu-id="f8fcb-109">Il crée une nouvelle exécution de texte qui se compose du texte du premier paragraphe converti en majuscules.</span><span class="sxs-lookup"><span data-stu-id="f8fcb-109">It creates a new text run that consists of the text of the first paragraph converted to upper case.</span></span> <span data-ttu-id="f8fcb-110">Il sérialise ensuite le code XML modifié dans le package Open XML et le ferme.</span><span class="sxs-lookup"><span data-stu-id="f8fcb-110">It then serializes the changed XML into the Open XML package and closes it.</span></span>

<span data-ttu-id="f8fcb-111">L’exemple fonctionne sur le document Office Open XML décrit dans [créer le document Office Open XML source](create-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="f8fcb-111">The example operates on Office Open XML document described in [Create the source Office Open XML document](create-source-office-open-xml-document.md).</span></span>

<span data-ttu-id="f8fcb-112">Il utilise les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="f8fcb-112">It makes use of the following:</span></span>

- <span data-ttu-id="f8fcb-113">`StringConcatenate`Méthode d’extension, définie dans le cadre de l’exemple.</span><span class="sxs-lookup"><span data-stu-id="f8fcb-113">The `StringConcatenate` extension method, defined as part of the example.</span></span>
- <span data-ttu-id="f8fcb-114">Classes trouvées dans l’assembly WindowsBase.</span><span class="sxs-lookup"><span data-stu-id="f8fcb-114">Classes found in the WindowsBase assembly.</span></span>
- <span data-ttu-id="f8fcb-115">Types dans l' <xref:System.IO.Packaging?displayProperty=nameWithType> espace de noms.</span><span class="sxs-lookup"><span data-stu-id="f8fcb-115">Types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>

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

        using (Package wdPackage = Package.Open(fileName, FileMode.Open, FileAccess.ReadWrite))
        {
            PackageRelationship docPackageRelationship =
              wdPackage.GetRelationshipsByType(documentRelationshipType).FirstOrDefault();
            if (docPackageRelationship != null)
            {
                Uri documentUri = PackUriHelper.ResolvePartUri(new Uri("/", UriKind.Relative),
                  docPackageRelationship.TargetUri);
                PackagePart documentPart = wdPackage.GetPart(documentUri);

                //  Load the document XML in the part into an XDocument instance.
                XDocument xDoc = XDocument.Load(XmlReader.Create(documentPart.GetStream()));

                //  Find the styles part. There will only be one.
                PackageRelationship styleRelation =
                  documentPart.GetRelationshipsByType(stylesRelationshipType).FirstOrDefault();
                PackagePart stylePart = null;
                XDocument styleDoc = null;

                if (styleRelation != null)
                {
                    Uri styleUri = PackUriHelper.ResolvePartUri(documentUri, styleRelation.TargetUri);
                    stylePart = wdPackage.GetPart(styleUri);

                    //  Load the style XML in the part into an XDocument instance.
                    styleDoc = XDocument.Load(XmlReader.Create(stylePart.GetStream()));
                }

                XElement paraNode = xDoc
                                    .Root
                                    .Element(w + "body")
                                    .Descendants(w + "p")
                                    .FirstOrDefault();

                string paraText = ParagraphText(paraNode);

                // remove all text runs
                paraNode.Descendants(w + "r").Remove();

                paraNode.Add(
                    new XElement(w + "r",
                        new XElement(w + "t", paraText.ToUpper())
                    )
                );

                //  Save the XML into the package
                using (XmlWriter xw =
                  XmlWriter.Create(documentPart.GetStream(FileMode.Create, FileAccess.Write)))
                {
                    xDoc.Save(xw);
                }

                Console.WriteLine("New first paragraph: >{0}<", paraText.ToUpper());
            }
        }
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

        Using wdPackage As Package = Package.Open(fileName, FileMode.Open, FileAccess.ReadWrite)
            Dim docPackageRelationship As PackageRelationship = wdPackage _
                    .GetRelationshipsByType(documentRelationshipType).FirstOrDefault()
            If (docPackageRelationship IsNot Nothing) Then
                Dim documentUri As Uri = PackUriHelper.ResolvePartUri(New Uri("/", _
                            UriKind.Relative), docPackageRelationship.TargetUri)
                Dim documentPart As PackagePart = wdPackage.GetPart(documentUri)

                '  Load the document XML in the part into an XDocument instance.
                Dim xDoc As XDocument = XDocument.Load(XmlReader.Create(documentPart.GetStream()))

                '  Find the styles part. There will only be one.
                Dim styleRelation As PackageRelationship = documentPart _
                        .GetRelationshipsByType(stylesRelationshipType).FirstOrDefault()
                Dim stylePart As PackagePart = Nothing
                Dim styleDoc As XDocument = Nothing

                If (styleRelation IsNot Nothing) Then
                    Dim styleUri As Uri = PackUriHelper.ResolvePartUri( _
                            documentUri, styleRelation.TargetUri)
                    stylePart = wdPackage.GetPart(styleUri)

                    ' Load the style XML in the part into an XDocument instance.
                    styleDoc = XDocument.Load(XmlReader.Create(stylePart.GetStream()))
                End If

                Dim paraNode As XElement = xDoc.Root.<w:body>...<w:p>.FirstOrDefault()

                Dim paraText As String = ParagraphText(paraNode)

                ' Remove all text runs.
                paraNode...<w:r>.Remove()

                paraNode.Add(<w:r><w:t><%= paraText.ToUpper() %></w:t></w:r>)

                ' Save the XML into the package.
                Using xw As XmlWriter = _
                  XmlWriter.Create(documentPart.GetStream(FileMode.Create, FileAccess.Write))
                    xDoc.Save(xw)
                End Using

                Console.WriteLine("New first paragraph: >{0}<", paraText.ToUpper())
            End If
        End Using
    End Sub
End Module
```

<span data-ttu-id="f8fcb-116">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="f8fcb-116">This example produces the following output:</span></span>

```output
New first paragraph: >PARSING WORDPROCESSINGML WITH LINQ TO XML<
```

<span data-ttu-id="f8fcb-117">Si vous ouvrez `SampleDoc.docx` après avoir exécuté ce programme, vous constatez que ce programme a converti le premier paragraphe du document en majuscules.</span><span class="sxs-lookup"><span data-stu-id="f8fcb-117">If you open `SampleDoc.docx` after running this program, you can see that this program converted the first paragraph in the document to upper case.</span></span>
