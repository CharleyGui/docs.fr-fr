---
title: Récupération des paragraphes et de leurs styles (C#)
description: Découvrez comment écrire une requête qui récupère des paragraphes, puis identifie le style de chaque paragraphe.
ms.date: 07/20/2015
ms.assetid: c2f767f8-57b1-4b4b-af04-89ffb1f7067d
ms.openlocfilehash: 94d01a13485f70bc9d9cef55b5f390c3b30d7f14
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303398"
---
# <a name="retrieving-the-paragraphs-and-their-styles-c"></a>Récupération des paragraphes et de leurs styles (C#)
Dans cet exemple, nous écrivons une requête qui récupère les nœuds de paragraphe à partir d'un document WordprocessingML. Il identifie également le style de chaque paragraphe.  
  
 Cette requête est basée sur celle de l’exemple précédent, [Recherche du style de paragraphe par défaut (C#)](./finding-the-default-paragraph-style.md), qui récupère le style par défaut à partir de la liste de styles. Ces informations sont requises de manière que la requête puisse identifier le style des paragraphes pour lesquels aucun style n'est défini de façon explicite. Les style de paragraphes sont définis par le biais de l'élément `w:pPr` ; si un paragraphe ne contient pas cet élément, il est mis en forme avec le style par défaut.  
  
 Cette rubrique explique l'importance de certaines parties de la requête, puis illustre la requête dans le cadre d'un exemple fonctionnel complet.  
  
## <a name="example"></a>Exemple  
 La source de la requête permettant de récupérer tous les paragraphes dans un document et leurs styles est la suivante :  
  
```csharp  
xDoc.Root.Element(w + "body").Descendants(w + "p")  
```  
  
 Cette expression est similaire à la source de la requête dans l’exemple précédent, [Recherche du style de paragraphe par défaut (C#)](./finding-the-default-paragraph-style.md). La différence principale est qu'elle utilise l'axe <xref:System.Xml.Linq.XContainer.Descendants%2A> au lieu de l'axe <xref:System.Xml.Linq.XContainer.Elements%2A>. La requête utilise l'axe <xref:System.Xml.Linq.XContainer.Descendants%2A> car dans les documents qui ont des sections, les paragraphes ne sont pas les enfants directs de l'élément de corps, mais se trouvent deux niveaux au-dessous dans la hiérarchie. Grâce à l'utilisation de la méthode <xref:System.Xml.Linq.XContainer.Descendants%2A>, le code fonctionnera, que le document utilise des sections ou non.  
  
## <a name="example"></a>Exemple  
 La requête utilise une clause `let` afin de déterminer l'élément qui contient le nœud de style. S'il n'y a aucun élément, `styleNode` a la valeur `null` :  
  
```csharp  
let styleNode = para.Elements(w + "pPr").Elements(w + "pStyle").FirstOrDefault()  
```  
  
 La clause `let` utilise d'abord l'axe <xref:System.Xml.Linq.XContainer.Elements%2A> pour rechercher tous les éléments nommés `pPr`, puis utilise la méthode d'extension <xref:System.Xml.Linq.Extensions.Elements%2A> pour rechercher tous les éléments enfants nommés `pStyle`, et pour finir utilise l'opérateur de requête standard <xref:System.Linq.Enumerable.FirstOrDefault%2A> pour convertir la collection en singleton. Si la collection est vide, `styleNode` a la valeur `null`. Il s'agit d'un idiome utile pour rechercher le nœud descendant `pStyle`. Notez que si le nœud enfant `pPr` n'existe pas, le code n'échoue pas avec la levée d'une exception ; au lieu de cela, `styleNode` est définie à `null`, ce qui constitue le comportement souhaité de cette clause `let`.  
  
 La requête projette une collection d'un type anonyme avec deux membres, `StyleName` et `ParagraphNode`.  
  
## <a name="example"></a>Exemple  
 Cet exemple traite un document WordprocessingML et récupère les nœuds de paragraphes à partir d'un document WordprocessingML. Il identifie également le style de chaque paragraphe. Cet exemple se base sur les exemples précédents de ce didacticiel. Dans le code ci-dessous, la nouvelle requête figure dans des commentaires.  
  
 Vous trouverez des instructions pour créer le document source utilisé dans cet exemple dans [Création du document Office Open XML source (C#)](./creating-the-source-office-open-xml-document.md).  
  
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
  
 Quand il est appliqué au document décrit dans [Création du document Office Open XML source (C#)](./creating-the-source-office-open-xml-document.md), cet exemple produit la sortie suivante.  
  
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
  
## <a name="next-steps"></a>Étapes suivantes  
 Dans la rubrique suivante, [Récupération du texte des paragraphes (C#)](./retrieving-the-text-of-the-paragraphs.md), vous allez créer une requête pour récupérer le texte des paragraphes.  
  
## <a name="see-also"></a>Voir aussi

- [Didacticiel : manipulation de contenu dans un document WordprocessingML (C#)](./shape-of-wordprocessingml-documents.md)
