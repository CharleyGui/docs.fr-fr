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
# <a name="retrieving-the-text-of-the-paragraphs-c"></a><span data-ttu-id="c3da2-102">Récupération du texte des paragraphes (C#)</span><span class="sxs-lookup"><span data-stu-id="c3da2-102">Retrieving the Text of the Paragraphs (C#)</span></span>
<span data-ttu-id="c3da2-103">Cet exemple s’appuie sur l’exemple précédent, [Récupération des paragraphes et de leurs styles (C#)](../../../../csharp/programming-guide/concepts/linq/retrieving-the-paragraphs-and-their-styles.md).</span><span class="sxs-lookup"><span data-stu-id="c3da2-103">This example builds on the previous example, [Retrieving the Paragraphs and Their Styles (C#)](../../../../csharp/programming-guide/concepts/linq/retrieving-the-paragraphs-and-their-styles.md).</span></span> <span data-ttu-id="c3da2-104">Ce nouvel exemple récupère le texte de chaque paragraphe en tant que chaîne.</span><span class="sxs-lookup"><span data-stu-id="c3da2-104">This new example retrieves the text of each paragraph as a string.</span></span>  
  
 <span data-ttu-id="c3da2-105">Pour récupérer le texte, cet exemple ajoute une requête supplémentaire qui itère au sein de la collection de types anonymes et projette une nouvelle collection d'un type anonyme avec l'ajout d'un nouveau membre, `Text`.</span><span class="sxs-lookup"><span data-stu-id="c3da2-105">To retrieve the text, this example adds an additional query that iterates through the collection of anonymous types and projects a new collection of an anonymous type with the addition of a new member, `Text`.</span></span> <span data-ttu-id="c3da2-106">Il utilise l'opérateur de requête standard <xref:System.Linq.Enumerable.Aggregate%2A> pour concaténer plusieurs chaînes dans une chaîne.</span><span class="sxs-lookup"><span data-stu-id="c3da2-106">It uses the <xref:System.Linq.Enumerable.Aggregate%2A> standard query operator to concatenate multiple strings into one string.</span></span>  
  
 <span data-ttu-id="c3da2-107">Cette technique (qui consiste à projeter vers une collection d'un type anonyme, puis à utiliser cette collection pour projeter vers une nouvelle collection d'un type anonyme) est un idiome commun et utile.</span><span class="sxs-lookup"><span data-stu-id="c3da2-107">This technique (that is, first projecting to a collection of an anonymous type, then using this collection to project to a new collection of an anonymous type) is a common and useful idiom.</span></span> <span data-ttu-id="c3da2-108">Cette requête pourrait avoir été écrite sans projeter vers le premier type anonyme.</span><span class="sxs-lookup"><span data-stu-id="c3da2-108">This query could have been written without projecting to the first anonymous type.</span></span> <span data-ttu-id="c3da2-109">Toutefois, en raison de l'évaluation différée, procéder ainsi n'utilise pas beaucoup de puissance de traitement supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="c3da2-109">However, because of lazy evaluation, doing so does not use much additional processing power.</span></span> <span data-ttu-id="c3da2-110">L'idiome crée davantage d'objets à courte durée de vie sur la pile, mais cela ne nuit pas énormément aux performances.</span><span class="sxs-lookup"><span data-stu-id="c3da2-110">The idiom creates more short lived objects on the heap, but this does not substantially degrade performance.</span></span>  
  
 <span data-ttu-id="c3da2-111">Bien entendu, il serait possible d'écrire une requête unique contenant la fonctionnalité de récupération des paragraphes, du style de chaque paragraphe et du texte de chaque paragraphe.</span><span class="sxs-lookup"><span data-stu-id="c3da2-111">Of course, it would be possible to write a single query that contains the functionality to retrieve the paragraphs, the style of each paragraph, and the text of each paragraph.</span></span> <span data-ttu-id="c3da2-112">Toutefois, il est souvent utile de découper une requête compliquée en plusieurs requêtes car le code obtenu sera plus modulable et plus facile à maintenir.</span><span class="sxs-lookup"><span data-stu-id="c3da2-112">However, it often is useful to break up a more complicated query into multiple queries because the resulting code is more modular and easier to maintain.</span></span> <span data-ttu-id="c3da2-113">En outre, si vous avez besoin de réutiliser une partie de la requête, il est plus facile de refactoriser si les requêtes sont écrites de cette manière.</span><span class="sxs-lookup"><span data-stu-id="c3da2-113">Furthermore, if you need to reuse a portion of the query, it is easier to refactor if the queries are written in this manner.</span></span>  
  
 <span data-ttu-id="c3da2-114">Ces requêtes, qui sont chaînées, utilisent le modèle de traitement détaillé dans la rubrique [Tutoriel : Chaînage de requêtes (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md).</span><span class="sxs-lookup"><span data-stu-id="c3da2-114">These queries, which are chained together, use the processing model that is examined in detail in the topic [Tutorial: Chaining Queries Together (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c3da2-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="c3da2-115">Example</span></span>  
 <span data-ttu-id="c3da2-116">Cet exemple traite un document WordprocessingML et détermine le nœud d'élément, le nom de style et le texte de chaque paragraphe.</span><span class="sxs-lookup"><span data-stu-id="c3da2-116">This example processes a WordprocessingML document, determining the element node, the style name, and the text of each paragraph.</span></span> <span data-ttu-id="c3da2-117">Cet exemple se base sur les exemples précédents de ce didacticiel.</span><span class="sxs-lookup"><span data-stu-id="c3da2-117">This example builds on the previous examples in this tutorial.</span></span> <span data-ttu-id="c3da2-118">Dans le code ci-dessous, la nouvelle requête figure dans des commentaires.</span><span class="sxs-lookup"><span data-stu-id="c3da2-118">The new query is called out in comments in the code below.</span></span>  
  
 <span data-ttu-id="c3da2-119">Afin d’obtenir des instructions pour créer le document source utilisé dans cet exemple, consultez [Création du document Office Open XML source (C#)](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="c3da2-119">For instructions for creating the source document for this example, see [Creating the Source Office Open XML Document (C#)](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span></span>  
  
 <span data-ttu-id="c3da2-120">Cet exemple utilise des classes de l'assembly WindowsBase.</span><span class="sxs-lookup"><span data-stu-id="c3da2-120">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="c3da2-121">Il utilise des types dans l'espace de noms <xref:System.IO.Packaging?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c3da2-121">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
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
  
 <span data-ttu-id="c3da2-122">Quand il est appliqué au document décrit dans [Création du document Office Open XML source (C#)](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md), cet exemple produit la sortie suivante.</span><span class="sxs-lookup"><span data-stu-id="c3da2-122">This example produces the following output when applied to the document described in [Creating the Source Office Open XML Document (C#)](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span></span>  
  
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
  
## <a name="next-steps"></a><span data-ttu-id="c3da2-123">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="c3da2-123">Next Steps</span></span>  
 <span data-ttu-id="c3da2-124">L'exemple suivant montre comment utiliser une méthode d'extension, au lieu de <xref:System.Linq.Enumerable.Aggregate%2A>, pour concaténer plusieurs chaînes en une seule chaîne.</span><span class="sxs-lookup"><span data-stu-id="c3da2-124">The next example shows how to use an extension method, instead of <xref:System.Linq.Enumerable.Aggregate%2A>, to concatenate multiple strings into a single string.</span></span>  
  
- [<span data-ttu-id="c3da2-125">Refactorisation à l’aide d’une méthode d’extension (C#)</span><span class="sxs-lookup"><span data-stu-id="c3da2-125">Refactoring Using an Extension Method (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/refactoring-using-an-extension-method.md)  
  
## <a name="see-also"></a><span data-ttu-id="c3da2-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c3da2-126">See also</span></span>

- [<span data-ttu-id="c3da2-127">Tutoriel : manipulation de contenu dans un document WordprocessingML (C#)</span><span class="sxs-lookup"><span data-stu-id="c3da2-127">Tutorial: Manipulating Content in a WordprocessingML Document (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
- [<span data-ttu-id="c3da2-128">Exécution et évaluation différées dans LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="c3da2-128">Deferred Execution and Lazy Evaluation in LINQ to XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
