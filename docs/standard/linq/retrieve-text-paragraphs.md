---
title: Récupérer le texte des paragraphes-LINQ to XML
description: Apprenez à rechercher les nœuds de paragraphe dans un document WordprocessingML et à récupérer le texte de chaque nœud sous la forme d’une chaîne.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 127d635e-e559-408f-90c8-2bb621ca50ac
ms.openlocfilehash: f41e0206f91f022993ed2c48681f124bf84ec603
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553647"
---
# <a name="retrieve-the-text-of-the-paragraphs-linq-to-xml"></a><span data-ttu-id="60798-103">Récupérer le texte des paragraphes (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="60798-103">Retrieve the text of the paragraphs (LINQ to XML)</span></span>

<span data-ttu-id="60798-104">Cet exemple s’appuie sur l’exemple précédent, [récupère les paragraphes et leurs styles](retrieve-paragraphs-styles.md).</span><span class="sxs-lookup"><span data-stu-id="60798-104">This example builds on the previous example, [Retrieve the paragraphs and their styles](retrieve-paragraphs-styles.md).</span></span> <span data-ttu-id="60798-105">Ce nouvel exemple récupère le texte de chaque paragraphe en tant que chaîne.</span><span class="sxs-lookup"><span data-stu-id="60798-105">This new example retrieves the text of each paragraph as a string.</span></span>

<span data-ttu-id="60798-106">Pour récupérer le texte, cet exemple ajoute une requête supplémentaire qui itère au sein de la collection de types anonymes et projette une nouvelle collection d'un type anonyme avec l'ajout d'un nouveau membre, `Text`.</span><span class="sxs-lookup"><span data-stu-id="60798-106">To retrieve the text, this example adds an additional query that iterates through the collection of anonymous types and projects a new collection of an anonymous type with the addition of a new member, `Text`.</span></span> <span data-ttu-id="60798-107">Il utilise l'opérateur de requête standard <xref:System.Linq.Enumerable.Aggregate%2A> pour concaténer plusieurs chaînes dans une chaîne.</span><span class="sxs-lookup"><span data-stu-id="60798-107">It uses the <xref:System.Linq.Enumerable.Aggregate%2A> standard query operator to concatenate multiple strings into one string.</span></span>

<span data-ttu-id="60798-108">Cette technique (qui consiste à projeter vers une collection d’un type anonyme, puis à utiliser cette collection pour projeter vers une nouvelle collection d’un type anonyme) est une méthode courante et utile.</span><span class="sxs-lookup"><span data-stu-id="60798-108">This technique (that is, first projecting to a collection of an anonymous type, then using this collection to project to a new collection of an anonymous type) is a common and useful one.</span></span> <span data-ttu-id="60798-109">Cette requête pourrait avoir été écrite sans projeter vers le premier type anonyme.</span><span class="sxs-lookup"><span data-stu-id="60798-109">This query could have been written without projecting to the first anonymous type.</span></span> <span data-ttu-id="60798-110">Toutefois, en raison de l’évaluation différée, cette opération n’utilise pas une grande puissance de traitement.</span><span class="sxs-lookup"><span data-stu-id="60798-110">However, because of lazy evaluation, doing so doesn't use much additional processing power.</span></span> <span data-ttu-id="60798-111">La technique crée des objets plus éphémères sur le tas, mais cela ne dégrade pas sensiblement les performances.</span><span class="sxs-lookup"><span data-stu-id="60798-111">The technique does create more short-lived objects on the heap, but that doesn't substantially degrade performance.</span></span>

<span data-ttu-id="60798-112">Bien entendu, il serait possible d'écrire une requête unique contenant la fonctionnalité de récupération des paragraphes, du style de chaque paragraphe et du texte de chaque paragraphe.</span><span class="sxs-lookup"><span data-stu-id="60798-112">Of course, it would be possible to write a single query that contains the functionality to retrieve the paragraphs, the style of each paragraph, and the text of each paragraph.</span></span> <span data-ttu-id="60798-113">Toutefois, il est souvent utile de fractionner une requête plus complexe en plusieurs requêtes, car le code obtenu est plus modulaire et plus facile à gérer.</span><span class="sxs-lookup"><span data-stu-id="60798-113">However, it's often useful to break up a more complicated query into multiple queries because the resulting code is more modular and easier to maintain.</span></span> <span data-ttu-id="60798-114">De plus, si vous devez réutiliser une partie de la requête, il est plus facile de refactoriser si les requêtes sont écrites de cette manière.</span><span class="sxs-lookup"><span data-stu-id="60798-114">Further, if you need to reuse a portion of the query, it's easier to refactor if the queries are written in this manner.</span></span>

<span data-ttu-id="60798-115">Ces requêtes, qui sont chaînées ensemble, utilisent le modèle de traitement examiné dans l’exemple de [requêtes de chaîne](chain-queries-example.md)d’article.</span><span class="sxs-lookup"><span data-stu-id="60798-115">These queries, which are chained together, use the processing model that's examined in the article [Chain queries example](chain-queries-example.md).</span></span>

## <a name="example-determine-the-element-node-style-name-and-text-of-each-paragraph"></a><span data-ttu-id="60798-116">Exemple : déterminer le nœud d’élément, le nom de style et le texte de chaque paragraphe</span><span class="sxs-lookup"><span data-stu-id="60798-116">Example: Determine the element node, style name, and text of each paragraph</span></span>

<span data-ttu-id="60798-117">Cet exemple traite un document WordprocessingML, en déterminant le nœud d’élément, le nom de style et le texte de chaque paragraphe.</span><span class="sxs-lookup"><span data-stu-id="60798-117">This example processes a WordprocessingML document, determining the element node, style name, and text of each paragraph.</span></span> <span data-ttu-id="60798-118">Cet exemple se base sur les exemples précédents de ce didacticiel.</span><span class="sxs-lookup"><span data-stu-id="60798-118">This example builds on the previous examples in this tutorial.</span></span> <span data-ttu-id="60798-119">Dans le code ci-dessous, la nouvelle requête figure dans des commentaires.</span><span class="sxs-lookup"><span data-stu-id="60798-119">The new query is called out in comments in the code below.</span></span>

<span data-ttu-id="60798-120">Les instructions pour créer le document source pour cet exemple sont dans [créer le document Office Open XML source](create-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="60798-120">The instructions for creating the source document for this example are in [Create the source Office Open XML document](create-source-office-open-xml-document.md).</span></span>

<span data-ttu-id="60798-121">Cet exemple utilise des classes de l'assembly WindowsBase.</span><span class="sxs-lookup"><span data-stu-id="60798-121">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="60798-122">Il utilise des types dans l'espace de noms <xref:System.IO.Packaging?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="60798-122">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>

```csharp
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
        where (string)style.Attribute(w + "type") == "paragraph"&&
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

// Following is the new query that retrieves the text of
// each paragraph.
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
               .Aggregate(
                   new StringBuilder(),
                   (s, i) => s.Append((string)i),
                   s => s.ToString()
               )
    };

foreach (var p in paraWithText)
    Console.WriteLine("StyleName:{0} >{1}<", p.StyleName, p.Text);
```

```vb
Imports <xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main">

Module Module1
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

<span data-ttu-id="60798-123">La version C# de cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="60798-123">The C# version of this example produces the following output:</span></span>

```conssole
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

<span data-ttu-id="60798-124">La version Visual Basic de cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="60798-124">The Visual Basic version of this example produces the following output:</span></span>

```output
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

<span data-ttu-id="60798-125">L’article suivant de ce didacticiel montre comment utiliser une méthode d’extension, au lieu de <xref:System.Linq.Enumerable.Aggregate%2A> , pour concaténer plusieurs chaînes en une seule chaîne :</span><span class="sxs-lookup"><span data-stu-id="60798-125">The next article in this tutorial shows how to use an extension method, instead of <xref:System.Linq.Enumerable.Aggregate%2A>, to concatenate multiple strings into a single string:</span></span>

- [<span data-ttu-id="60798-126">Refactoriser à l’aide d’une méthode d’extension</span><span class="sxs-lookup"><span data-stu-id="60798-126">Refactor using an extension method</span></span>](refactor-extension-method.md)

## <a name="see-also"></a><span data-ttu-id="60798-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="60798-127">See also</span></span>

- [<span data-ttu-id="60798-128">Didacticiel : manipuler du contenu dans un document WordprocessingML</span><span class="sxs-lookup"><span data-stu-id="60798-128">Tutorial: Manipulate content in a WordprocessingML document</span></span>](xml-shape-wordprocessingml-documents.md)
- [<span data-ttu-id="60798-129">Exécution différée et évaluation différée</span><span class="sxs-lookup"><span data-stu-id="60798-129">Deferred execution and lazy evaluation</span></span>](deferred-execution-lazy-evaluation.md)
