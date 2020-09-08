---
title: Récupérer les paragraphes et leurs styles-LINQ to XML
description: Découvrez comment récupérer des nœuds de paragraphe et leurs styles à partir d’un document WordprocessingML.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: c2f767f8-57b1-4b4b-af04-89ffb1f7067d
ms.openlocfilehash: 43c6173441dda841236a4397e28d0bb2c7c8d003
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553671"
---
# <a name="retrieve-the-paragraphs-and-their-styles-linq-to-xml"></a><span data-ttu-id="07df8-103">Récupérer les paragraphes et leurs styles (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="07df8-103">Retrieve the paragraphs and their styles (LINQ to XML)</span></span>

<span data-ttu-id="07df8-104">Dans cet exemple, nous écrivons une requête qui récupère les nœuds de paragraphe à partir d'un document WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="07df8-104">In this example, we write a query that retrieves the paragraph nodes from a WordprocessingML document.</span></span> <span data-ttu-id="07df8-105">Il identifie également le style de chaque paragraphe.</span><span class="sxs-lookup"><span data-stu-id="07df8-105">It also identifies the style of each paragraph.</span></span>

<span data-ttu-id="07df8-106">Cette requête est basée sur la requête de l’exemple précédent, [recherchez le style de paragraphe par défaut](find-default-paragraph-style.md), qui récupère le style par défaut dans la liste des styles.</span><span class="sxs-lookup"><span data-stu-id="07df8-106">This query builds on the query in the previous example, [Find the default paragraph style](find-default-paragraph-style.md), which retrieves the default style from the list of styles.</span></span> <span data-ttu-id="07df8-107">Ces informations sont nécessaires pour que la requête puisse identifier le style des paragraphes pour lesquels aucun style n’est défini explicitement.</span><span class="sxs-lookup"><span data-stu-id="07df8-107">This information is required so that the query can identify the style of paragraphs that don't have a style explicitly set.</span></span> <span data-ttu-id="07df8-108">Les styles de paragraphe sont définis par le biais de l' `w:pPr` élément ; si un paragraphe ne contient pas cet élément, il est mis en forme avec le style par défaut.</span><span class="sxs-lookup"><span data-stu-id="07df8-108">Paragraph styles are set through the `w:pPr` element; if a paragraph doesn't contain this element, it's formatted with the default style.</span></span>

<span data-ttu-id="07df8-109">Cet article explique l’importance de certaines parties de la requête, puis affiche la requête dans le cadre d’un exemple fonctionnel complet.</span><span class="sxs-lookup"><span data-stu-id="07df8-109">This article explains the significance of some pieces of the query, then shows the query as part of a complete working example.</span></span>

## <a name="example-retrieve-all-the-paragraphs-in-a-document-and-the-paragraph-styles"></a><span data-ttu-id="07df8-110">Exemple : récupérer tous les paragraphes d’un document et les styles de paragraphe</span><span class="sxs-lookup"><span data-stu-id="07df8-110">Example: Retrieve all the paragraphs in a document, and the paragraph styles</span></span>

<span data-ttu-id="07df8-111">Le code suivant est une requête permettant de récupérer tous les paragraphes d’un document et leurs styles :</span><span class="sxs-lookup"><span data-stu-id="07df8-111">The following code is a query to retrieve all the paragraphs in a document and their styles:</span></span>

```csharp
xDoc.Root.Element(w + "body").Descendants(w + "p")
```

```vb
xDoc.Root.<w:body>...<w:p>
```

<span data-ttu-id="07df8-112">Cette expression est similaire à la source de la requête dans l’exemple précédent, [recherchez le style de paragraphe par défaut](find-default-paragraph-style.md).</span><span class="sxs-lookup"><span data-stu-id="07df8-112">This expression is similar to the source of the query in the previous example, [Find the default paragraph style](find-default-paragraph-style.md).</span></span> <span data-ttu-id="07df8-113">La différence principale est qu'elle utilise l'axe <xref:System.Xml.Linq.XContainer.Descendants%2A> au lieu de l'axe <xref:System.Xml.Linq.XContainer.Elements%2A>.</span><span class="sxs-lookup"><span data-stu-id="07df8-113">The main difference is that it uses the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis instead of the <xref:System.Xml.Linq.XContainer.Elements%2A> axis.</span></span> <span data-ttu-id="07df8-114">La requête utilise l' <xref:System.Xml.Linq.XContainer.Descendants%2A> axe car dans les documents qui ont des sections, les paragraphes ne sont pas les enfants directs de l’élément Body ; au lieu de cela, les paragraphes se trouvent deux niveaux dans la hiérarchie.</span><span class="sxs-lookup"><span data-stu-id="07df8-114">The query uses the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis because in documents that have sections, the paragraphs won't be the direct children of the body element; rather, the paragraphs will be two levels down in the hierarchy.</span></span> <span data-ttu-id="07df8-115">En utilisant l' <xref:System.Xml.Linq.XContainer.Descendants%2A> axe, le code fonctionnera, que le document utilise des sections ou non.</span><span class="sxs-lookup"><span data-stu-id="07df8-115">By using the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis, the code will work whether or not the document uses sections.</span></span>

## <a name="example-use-a-let-clause-to-determine-the-element-that-contains-the-style-node"></a><span data-ttu-id="07df8-116">Exemple : utilisation `let` d’une clause pour déterminer l’élément qui contient le nœud de style</span><span class="sxs-lookup"><span data-stu-id="07df8-116">Example: Use a `let` clause to determine the element that contains the style node</span></span>

<span data-ttu-id="07df8-117">La requête suivante utilise une `let` clause pour déterminer l’élément qui contient le nœud de style :</span><span class="sxs-lookup"><span data-stu-id="07df8-117">The following query uses a `let` clause to determine the element that contains the style node:</span></span>

```csharp
let styleNode = para.Elements(w + "pPr").Elements(w + "pStyle").FirstOrDefault()
```

 ```vb
Let styleNode As XElement = para.<w:pPr>.<w:pStyle>.FirstOrDefault()
```

<span data-ttu-id="07df8-118">La `let` clause ( `Let` dans la version Visual Basic) utilise d’abord l' <xref:System.Xml.Linq.XContainer.Elements%2A> axe pour rechercher tous les éléments nommés `pPr` , puis utilise la <xref:System.Xml.Linq.Extensions.Elements%2A> méthode d’extension pour rechercher tous les éléments enfants nommés `pStyle` , et enfin utilise l' <xref:System.Linq.Enumerable.FirstOrDefault%2A> opérateur de requête standard pour convertir la collection en Singleton.</span><span class="sxs-lookup"><span data-stu-id="07df8-118">The `let` clause (`Let` in the Visual Basic version) first uses the <xref:System.Xml.Linq.XContainer.Elements%2A> axis to find all elements named `pPr`, then uses the <xref:System.Xml.Linq.Extensions.Elements%2A> extension method to find all child elements named `pStyle`, and finally uses the <xref:System.Linq.Enumerable.FirstOrDefault%2A> standard query operator to convert the collection to a singleton.</span></span> <span data-ttu-id="07df8-119">Si la collection est vide, `styleNode` a la valeur `null` ( `Nothing` dans la version Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="07df8-119">If the collection is empty, `styleNode` is set to `null` (`Nothing` in the Visual Basic version).</span></span> <span data-ttu-id="07df8-120">Il s'agit d'un idiome utile pour rechercher le nœud descendant `pStyle`.</span><span class="sxs-lookup"><span data-stu-id="07df8-120">This is a useful idiom to look for the `pStyle` descendant node.</span></span> <span data-ttu-id="07df8-121">Notez que si le `pPr` nœud enfant n’existe pas, le code n’échoue pas en levant une exception ; `styleNode` à la place, a `null` la valeur ( `Nothing` ), qui est le comportement souhaité de cette `let` `Let` clause ().</span><span class="sxs-lookup"><span data-stu-id="07df8-121">Note that if the `pPr` child node doesn't exist, the code doesn't fail by throwing an exception; instead, `styleNode` is set to `null` (`Nothing`), which is the desired behavior of this `let`(`Let`) clause.</span></span>

<span data-ttu-id="07df8-122">S’il n’y a aucun élément, `styleNode` a la valeur `null` ( `Nothing` ).</span><span class="sxs-lookup"><span data-stu-id="07df8-122">If there is no element, then `styleNode` is set to `null` (`Nothing`).</span></span>

<span data-ttu-id="07df8-123">La requête projette une collection d'un type anonyme avec deux membres, `StyleName` et `ParagraphNode`.</span><span class="sxs-lookup"><span data-stu-id="07df8-123">The query projects a collection of an anonymous type with two members, `StyleName` and `ParagraphNode`.</span></span>

## <a name="example-retrieve-the-paragraph-nodes-from-a-wordprocessingml-document"></a><span data-ttu-id="07df8-124">Exemple : récupérer les nœuds de paragraphe à partir d’un document WordprocessingML</span><span class="sxs-lookup"><span data-stu-id="07df8-124">Example: Retrieve the paragraph nodes from a WordprocessingML document</span></span>

<span data-ttu-id="07df8-125">Cet exemple traite un document WordprocessingML et récupère les nœuds de paragraphe.</span><span class="sxs-lookup"><span data-stu-id="07df8-125">This example processes a WordprocessingML document, retrieving the paragraph nodes.</span></span> <span data-ttu-id="07df8-126">Il identifie également le style de chaque paragraphe.</span><span class="sxs-lookup"><span data-stu-id="07df8-126">It also identifies the style of each paragraph.</span></span> <span data-ttu-id="07df8-127">Cet exemple se base sur les exemples précédents de ce didacticiel.</span><span class="sxs-lookup"><span data-stu-id="07df8-127">This example builds on the previous examples in this tutorial.</span></span> <span data-ttu-id="07df8-128">Dans le code ci-dessous, la nouvelle requête figure dans des commentaires.</span><span class="sxs-lookup"><span data-stu-id="07df8-128">The new query is called out in comments in the code below.</span></span>

<span data-ttu-id="07df8-129">Les instructions pour créer le document source pour cet exemple sont dans [créer le document Office Open XML source](create-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="07df8-129">The instructions for creating the source document for this example are in [Create the source Office Open XML document](create-source-office-open-xml-document.md).</span></span>

<span data-ttu-id="07df8-130">Cet exemple utilise des classes de l'assembly WindowsBase.</span><span class="sxs-lookup"><span data-stu-id="07df8-130">This example uses classes found in the WindowsBase assembly.</span></span> <span data-ttu-id="07df8-131">Il utilise des types dans l'espace de noms <xref:System.IO.Packaging?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="07df8-131">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>

```csharp
const string fileName = "SampleDoc.docx";

const string documentRelationshipType = "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument";
const string stylesRelationshipType = "http://schemas.openxmlformats.org/officeDocument/2006/relationships/styles";
const string wordmlNamespace = "http://schemas.openxmlformats.org/wordprocessingml/2006/main";
XNamespace w = wordmlNamespace;

XDocument xDoc = null;
XDocument styleDoc = null;

using (Package wdPackage = Package.Open(fileName, FileMode.Open, FileAccess.Read))
{
    PackageRelationship docPackageRelationship = wdPackage.GetRelationshipsByType(documentRelationshipType).FirstOrDefault();
    if (docPackageRelationship != null)
    {
        Uri documentUri = PackUriHelper.ResolvePartUri(new Uri("/", UriKind.Relative), docPackageRelationship.TargetUri);
        PackagePart documentPart = wdPackage.GetPart(documentUri);

        //  Load the document XML in the part into an XDocument instance.
        xDoc = XDocument.Load(XmlReader.Create(documentPart.GetStream()));

        //  Find the styles part. There will only be one.
        PackageRelationship styleRelation = documentPart.GetRelationshipsByType(stylesRelationshipType).FirstOrDefault();
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

// Following is the new query that finds all paragraphs in the
// document and their styles.
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

foreach (var p in paragraphs)
    Console.WriteLine("StyleName:{0}", p.StyleName);
```

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

<span data-ttu-id="07df8-132">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="07df8-132">This example produces the following output:</span></span>

```output
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

<span data-ttu-id="07df8-133">L’article suivant de ce didacticiel montre comment créer une requête pour récupérer le texte des paragraphes :</span><span class="sxs-lookup"><span data-stu-id="07df8-133">The next article in this tutorial shows how to create a query to retrieve the text of paragraphs:</span></span>

- [<span data-ttu-id="07df8-134">Récupérer le texte des paragraphes</span><span class="sxs-lookup"><span data-stu-id="07df8-134">Retrieve the text of the paragraphs</span></span>](retrieve-text-paragraphs.md)

## <a name="see-also"></a><span data-ttu-id="07df8-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="07df8-135">See also</span></span>

- [<span data-ttu-id="07df8-136">Didacticiel : manipuler du contenu dans un document WordprocessingML</span><span class="sxs-lookup"><span data-stu-id="07df8-136">Tutorial: Manipulate content in a WordprocessingML document</span></span>](xml-shape-wordprocessingml-documents.md)
