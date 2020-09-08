---
title: Rechercher le style de paragraphe par défaut-LINQ to XML
description: Découvrez comment rechercher le style par défaut des paragraphes dans un document WordprocessingML.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: be102177-8ab0-444a-b671-7023e555ffdb
ms.openlocfilehash: 0e66856a551410dd488148ff678b684489396d62
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552372"
---
# <a name="find-the-default-paragraph-style-linq-to-xml"></a><span data-ttu-id="ba753-103">Rechercher le style de paragraphe par défaut (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="ba753-103">Find the default paragraph style (LINQ to XML)</span></span>

<span data-ttu-id="ba753-104">La première tâche du [Didacticiel : manipuler du contenu dans un document WordprocessingML](xml-shape-wordprocessingml-documents.md) consiste à rechercher le style par défaut des paragraphes dans le document.</span><span class="sxs-lookup"><span data-stu-id="ba753-104">The first task in [Tutorial: Manipulate content in a WordprocessingML document](xml-shape-wordprocessingml-documents.md) is to find the default style of paragraphs in the document.</span></span>

## <a name="example-find-the-default-style-name"></a><span data-ttu-id="ba753-105">Exemple : Rechercher le nom du style par défaut</span><span class="sxs-lookup"><span data-stu-id="ba753-105">Example: Find the default style name</span></span>

<span data-ttu-id="ba753-106">L'exemple suivant ouvre un document WordprocessingML Office Open XML, recherche les parties document et style du package, puis exécute une requête qui recherche le nom du style par défaut.</span><span class="sxs-lookup"><span data-stu-id="ba753-106">The following example opens an Office Open XML WordprocessingML document, finds the document and style parts of the package, and then executes a query that finds the default style name.</span></span> <span data-ttu-id="ba753-107">Pour plus d’informations sur les packages de documents Office Open XML et les éléments qu’ils contiennent, consultez [Détails des documents WordprocessingML Office Open XML](wordprocessingml-document-styles.md).</span><span class="sxs-lookup"><span data-stu-id="ba753-107">For information about Office Open XML document packages, and the parts they comprise, see [Details of Office Open XML WordprocessingML documents](wordprocessingml-document-styles.md).</span></span>

<span data-ttu-id="ba753-108">La requête recherche un nœud nommé `w:style` qui possède un attribut nommé `w:type` avec la valeur « paragraph » et un attribut nommé `w:default` avec la valeur « 1 ».</span><span class="sxs-lookup"><span data-stu-id="ba753-108">The query finds a node named `w:style` that has an attribute named `w:type` with a value of "paragraph", and also has an attribute named `w:default` with a value of "1".</span></span> <span data-ttu-id="ba753-109">Étant donné qu'il n'y aura qu'un seul nœud XML avec ces attributs, la requête utilise l'opérateur <xref:System.Linq.Enumerable.First%2A?displayProperty=nameWithType> pour convertir une collection en singleton.</span><span class="sxs-lookup"><span data-stu-id="ba753-109">Because there will be only one XML node with these attributes, the query uses the <xref:System.Linq.Enumerable.First%2A?displayProperty=nameWithType> operator to convert a collection to a singleton.</span></span> <span data-ttu-id="ba753-110">Elle obtient ensuite la valeur de l'attribut avec le nom `w:styleId`.</span><span class="sxs-lookup"><span data-stu-id="ba753-110">It then gets the value of the attribute with the name `w:styleId`.</span></span>

<span data-ttu-id="ba753-111">Cet exemple utilise des classes de l'assembly WindowsBase.</span><span class="sxs-lookup"><span data-stu-id="ba753-111">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="ba753-112">Il utilise des types dans l'espace de noms <xref:System.IO.Packaging?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ba753-112">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>

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

// The following query finds all the paragraphs that have the default style.
string defaultStyle =
    (string)(
        from style in styleDoc.Root.Elements(w + "style")
        where (string)style.Attribute(w + "type") == "paragraph"&&
              (string)style.Attribute(w + "default") == "1"
              select style
    ).First().Attribute(w + "styleId");

Console.WriteLine("The default style is: {0}", defaultStyle);
```

```vb
Imports <xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main">

Module Module1

    Sub Main()

        Const fileName As String = "SampleDoc.docx"

        Const documentRelationshipType As String = _
          "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument"
        Const stylesRelationshipType As String = _
          "http://schemas.openxmlformats.org/officeDocument/2006/relationships/styles"

        Dim xDoc As XDocument = Nothing
        Dim styleDoc As XDocument = Nothing

        Using wdPackage As Package = Package.Open(fileName, FileMode.Open, FileAccess.Read)
            Dim docPackageRelationship As PackageRelationship = _
              wdPackage.GetRelationshipsByType(documentRelationshipType).FirstOrDefault()
            If docPackageRelationship IsNot Nothing Then
                Dim documentUri As Uri = PackUriHelper.ResolvePartUri(New Uri("/", UriKind.Relative), _
                  docPackageRelationship.TargetUri)
                Dim documentPart As PackagePart = wdPackage.GetPart(documentUri)

                ' Load the document XML in the part into an XDocument instance.
                xDoc = XDocument.Load(XmlReader.Create(documentPart.GetStream()))

                ' Find the styles part. There will only be one.
                Dim styleRelation As PackageRelationship = _
                  documentPart.GetRelationshipsByType(stylesRelationshipType).FirstOrDefault()
                If styleRelation IsNot Nothing Then
                    Dim styleUri As Uri = _
                      PackUriHelper.ResolvePartUri(documentUri, styleRelation.TargetUri)
                    Dim stylePart As PackagePart = wdPackage.GetPart(styleUri)

                    ' Load the style XML in the part into an XDocument instance.
                    styleDoc = XDocument.Load(XmlReader.Create(stylePart.GetStream()))
                End If
            End If
        End Using

        ' The following query finds all the paragraphs that have the default style.
        Dim defParas As IEnumerable(Of XElement) = _
            From style In styleDoc.Root.<w:style> _
            Where style.@w:type.Equals("paragraph") And _
                   style.@w:default.Equals("1") _
            Select style
        ' Then find the style of the first.
        Dim defaultStyle As String = defParas.First().@w:styleId

        Console.WriteLine("The default style is: " & defaultStyle)
    End Sub
End Module
```

<span data-ttu-id="ba753-113">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="ba753-113">This example produces the following output:</span></span>

```output
The default style is: Normal
```

<span data-ttu-id="ba753-114">Dans l’article suivant de ce didacticiel, vous allez créer une requête similaire qui recherche tous les paragraphes d’un document et leurs styles :</span><span class="sxs-lookup"><span data-stu-id="ba753-114">In the next article in this tutorial you'll create a similar query that finds all the paragraphs in a document and their styles:</span></span>

- [<span data-ttu-id="ba753-115">Récupérer les paragraphes et leurs styles</span><span class="sxs-lookup"><span data-stu-id="ba753-115">Retrieve the paragraphs and their styles</span></span>](retrieve-paragraphs-styles.md)

## <a name="see-also"></a><span data-ttu-id="ba753-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ba753-116">See also</span></span>

- [<span data-ttu-id="ba753-117">Didacticiel : manipuler du contenu dans un document WordprocessingML</span><span class="sxs-lookup"><span data-stu-id="ba753-117">Tutorial: Manipulate content in a WordprocessingML document</span></span>](xml-shape-wordprocessingml-documents.md)
