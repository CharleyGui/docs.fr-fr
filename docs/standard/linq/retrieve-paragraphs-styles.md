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
# <a name="retrieve-the-paragraphs-and-their-styles-linq-to-xml"></a>Récupérer les paragraphes et leurs styles (LINQ to XML)

Dans cet exemple, nous écrivons une requête qui récupère les nœuds de paragraphe à partir d'un document WordprocessingML. Il identifie également le style de chaque paragraphe.

Cette requête est basée sur la requête de l’exemple précédent, [recherchez le style de paragraphe par défaut](find-default-paragraph-style.md), qui récupère le style par défaut dans la liste des styles. Ces informations sont nécessaires pour que la requête puisse identifier le style des paragraphes pour lesquels aucun style n’est défini explicitement. Les styles de paragraphe sont définis par le biais de l' `w:pPr` élément ; si un paragraphe ne contient pas cet élément, il est mis en forme avec le style par défaut.

Cet article explique l’importance de certaines parties de la requête, puis affiche la requête dans le cadre d’un exemple fonctionnel complet.

## <a name="example-retrieve-all-the-paragraphs-in-a-document-and-the-paragraph-styles"></a>Exemple : récupérer tous les paragraphes d’un document et les styles de paragraphe

Le code suivant est une requête permettant de récupérer tous les paragraphes d’un document et leurs styles :

```csharp
xDoc.Root.Element(w + "body").Descendants(w + "p")
```

```vb
xDoc.Root.<w:body>...<w:p>
```

Cette expression est similaire à la source de la requête dans l’exemple précédent, [recherchez le style de paragraphe par défaut](find-default-paragraph-style.md). La différence principale est qu'elle utilise l'axe <xref:System.Xml.Linq.XContainer.Descendants%2A> au lieu de l'axe <xref:System.Xml.Linq.XContainer.Elements%2A>. La requête utilise l' <xref:System.Xml.Linq.XContainer.Descendants%2A> axe car dans les documents qui ont des sections, les paragraphes ne sont pas les enfants directs de l’élément Body ; au lieu de cela, les paragraphes se trouvent deux niveaux dans la hiérarchie. En utilisant l' <xref:System.Xml.Linq.XContainer.Descendants%2A> axe, le code fonctionnera, que le document utilise des sections ou non.

## <a name="example-use-a-let-clause-to-determine-the-element-that-contains-the-style-node"></a>Exemple : utilisation `let` d’une clause pour déterminer l’élément qui contient le nœud de style

La requête suivante utilise une `let` clause pour déterminer l’élément qui contient le nœud de style :

```csharp
let styleNode = para.Elements(w + "pPr").Elements(w + "pStyle").FirstOrDefault()
```

 ```vb
Let styleNode As XElement = para.<w:pPr>.<w:pStyle>.FirstOrDefault()
```

La `let` clause ( `Let` dans la version Visual Basic) utilise d’abord l' <xref:System.Xml.Linq.XContainer.Elements%2A> axe pour rechercher tous les éléments nommés `pPr` , puis utilise la <xref:System.Xml.Linq.Extensions.Elements%2A> méthode d’extension pour rechercher tous les éléments enfants nommés `pStyle` , et enfin utilise l' <xref:System.Linq.Enumerable.FirstOrDefault%2A> opérateur de requête standard pour convertir la collection en Singleton. Si la collection est vide, `styleNode` a la valeur `null` ( `Nothing` dans la version Visual Basic). Il s'agit d'un idiome utile pour rechercher le nœud descendant `pStyle`. Notez que si le `pPr` nœud enfant n’existe pas, le code n’échoue pas en levant une exception ; `styleNode` à la place, a `null` la valeur ( `Nothing` ), qui est le comportement souhaité de cette `let` `Let` clause ().

S’il n’y a aucun élément, `styleNode` a la valeur `null` ( `Nothing` ).

La requête projette une collection d'un type anonyme avec deux membres, `StyleName` et `ParagraphNode`.

## <a name="example-retrieve-the-paragraph-nodes-from-a-wordprocessingml-document"></a>Exemple : récupérer les nœuds de paragraphe à partir d’un document WordprocessingML

Cet exemple traite un document WordprocessingML et récupère les nœuds de paragraphe. Il identifie également le style de chaque paragraphe. Cet exemple se base sur les exemples précédents de ce didacticiel. Dans le code ci-dessous, la nouvelle requête figure dans des commentaires.

Les instructions pour créer le document source pour cet exemple sont dans [créer le document Office Open XML source](create-source-office-open-xml-document.md).

Cet exemple utilise des classes de l'assembly WindowsBase. Il utilise des types dans l'espace de noms <xref:System.IO.Packaging?displayProperty=nameWithType>.

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

Cet exemple produit la sortie suivante :

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

L’article suivant de ce didacticiel montre comment créer une requête pour récupérer le texte des paragraphes :

- [Récupérer le texte des paragraphes](retrieve-text-paragraphs.md)

## <a name="see-also"></a>Voir aussi

- [Didacticiel : manipuler du contenu dans un document WordprocessingML](xml-shape-wordprocessingml-documents.md)
