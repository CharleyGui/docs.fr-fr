---
title: Récupération du texte des paragraphes (C#)
ms.date: 07/20/2015
ms.assetid: 127d635e-e559-408f-90c8-2bb621ca50ac
ms.openlocfilehash: d1f526374c56a5195438be72748ba15d0ab6741c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64595711"
---
# <a name="retrieving-the-text-of-the-paragraphs-c"></a>Récupération du texte des paragraphes (C#)
Cet exemple s’appuie sur l’exemple précédent, [Récupération des paragraphes et de leurs styles (C#)](../../../../csharp/programming-guide/concepts/linq/retrieving-the-paragraphs-and-their-styles.md). Ce nouvel exemple récupère le texte de chaque paragraphe en tant que chaîne.  
  
 Pour récupérer le texte, cet exemple ajoute une requête supplémentaire qui itère au sein de la collection de types anonymes et projette une nouvelle collection d'un type anonyme avec l'ajout d'un nouveau membre, `Text`. Il utilise l'opérateur de requête standard <xref:System.Linq.Enumerable.Aggregate%2A> pour concaténer plusieurs chaînes dans une chaîne.  
  
 Cette technique (qui consiste à projeter vers une collection d'un type anonyme, puis à utiliser cette collection pour projeter vers une nouvelle collection d'un type anonyme) est un idiome commun et utile. Cette requête pourrait avoir été écrite sans projeter vers le premier type anonyme. Toutefois, en raison de l'évaluation différée, procéder ainsi n'utilise pas beaucoup de puissance de traitement supplémentaire. L'idiome crée davantage d'objets à courte durée de vie sur la pile, mais cela ne nuit pas énormément aux performances.  
  
 Bien entendu, il serait possible d'écrire une requête unique contenant la fonctionnalité de récupération des paragraphes, du style de chaque paragraphe et du texte de chaque paragraphe. Toutefois, il est souvent utile de découper une requête compliquée en plusieurs requêtes car le code obtenu sera plus modulable et plus facile à maintenir. En outre, si vous avez besoin de réutiliser une partie de la requête, il est plus facile de refactoriser si les requêtes sont écrites de cette manière.  
  
 Ces requêtes, qui sont chaînées, utilisent le modèle de traitement détaillé dans la rubrique [Tutoriel : Chaînage de requêtes (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md).  
  
## <a name="example"></a>Exemple  
 Cet exemple traite un document WordprocessingML et détermine le nœud d'élément, le nom de style et le texte de chaque paragraphe. Cet exemple se base sur les exemples précédents de ce didacticiel. Dans le code ci-dessous, la nouvelle requête figure dans des commentaires.  
  
 Afin d’obtenir des instructions pour créer le document source utilisé dans cet exemple, consultez [Création du document Office Open XML source (C#)](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).  
  
 Cet exemple utilise des classes de l'assembly WindowsBase. Il utilise des types dans l'espace de noms <xref:System.IO.Packaging?displayProperty=nameWithType>.  
  
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
  
 Quand il est appliqué au document décrit dans [Création du document Office Open XML source (C#)](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md), cet exemple produit la sortie suivante.  
  
```  
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
  
## <a name="next-steps"></a>Étapes suivantes  
 L'exemple suivant montre comment utiliser une méthode d'extension, au lieu de <xref:System.Linq.Enumerable.Aggregate%2A>, pour concaténer plusieurs chaînes en une seule chaîne.  
  
- [Refactorisation à l’aide d’une méthode d’extension (C#)](../../../../csharp/programming-guide/concepts/linq/refactoring-using-an-extension-method.md)  
  
## <a name="see-also"></a>Voir aussi

- [Tutoriel : manipulation de contenu dans un document WordprocessingML (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
- [Exécution et évaluation différées dans LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
