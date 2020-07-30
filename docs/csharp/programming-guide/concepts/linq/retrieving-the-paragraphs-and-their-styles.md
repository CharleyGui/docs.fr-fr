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
# <a name="retrieving-the-paragraphs-and-their-styles-c"></a><span data-ttu-id="e77a8-103">Récupération des paragraphes et de leurs styles (C#)</span><span class="sxs-lookup"><span data-stu-id="e77a8-103">Retrieving the Paragraphs and Their Styles (C#)</span></span>
<span data-ttu-id="e77a8-104">Dans cet exemple, nous écrivons une requête qui récupère les nœuds de paragraphe à partir d'un document WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="e77a8-104">In this example, we write a query that retrieves the paragraph nodes from a WordprocessingML document.</span></span> <span data-ttu-id="e77a8-105">Il identifie également le style de chaque paragraphe.</span><span class="sxs-lookup"><span data-stu-id="e77a8-105">It also identifies the style of each paragraph.</span></span>  
  
 <span data-ttu-id="e77a8-106">Cette requête est basée sur celle de l’exemple précédent, [Recherche du style de paragraphe par défaut (C#)](./finding-the-default-paragraph-style.md), qui récupère le style par défaut à partir de la liste de styles.</span><span class="sxs-lookup"><span data-stu-id="e77a8-106">This query builds on the query in the previous example, [Finding the Default Paragraph Style (C#)](./finding-the-default-paragraph-style.md), which retrieves the default style from the list of styles.</span></span> <span data-ttu-id="e77a8-107">Ces informations sont requises de manière que la requête puisse identifier le style des paragraphes pour lesquels aucun style n'est défini de façon explicite.</span><span class="sxs-lookup"><span data-stu-id="e77a8-107">This information is required so that the query can identify the style of paragraphs that do not have a style explicitly set.</span></span> <span data-ttu-id="e77a8-108">Les style de paragraphes sont définis par le biais de l'élément `w:pPr` ; si un paragraphe ne contient pas cet élément, il est mis en forme avec le style par défaut.</span><span class="sxs-lookup"><span data-stu-id="e77a8-108">Paragraph styles are set through the `w:pPr` element; if a paragraph does not contain this element, it is formatted with the default style.</span></span>  
  
 <span data-ttu-id="e77a8-109">Cette rubrique explique l'importance de certaines parties de la requête, puis illustre la requête dans le cadre d'un exemple fonctionnel complet.</span><span class="sxs-lookup"><span data-stu-id="e77a8-109">This topic explains the significance of some pieces of the query, then shows the query as part of a complete, working example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e77a8-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="e77a8-110">Example</span></span>  
 <span data-ttu-id="e77a8-111">La source de la requête permettant de récupérer tous les paragraphes dans un document et leurs styles est la suivante :</span><span class="sxs-lookup"><span data-stu-id="e77a8-111">The source of the query to retrieve all the paragraphs in a document and their styles is as follows:</span></span>  
  
```csharp  
xDoc.Root.Element(w + "body").Descendants(w + "p")  
```  
  
 <span data-ttu-id="e77a8-112">Cette expression est similaire à la source de la requête dans l’exemple précédent, [Recherche du style de paragraphe par défaut (C#)](./finding-the-default-paragraph-style.md).</span><span class="sxs-lookup"><span data-stu-id="e77a8-112">This expression is similar to the source of the query in the previous example, [Finding the Default Paragraph Style (C#)](./finding-the-default-paragraph-style.md).</span></span> <span data-ttu-id="e77a8-113">La différence principale est qu'elle utilise l'axe <xref:System.Xml.Linq.XContainer.Descendants%2A> au lieu de l'axe <xref:System.Xml.Linq.XContainer.Elements%2A>.</span><span class="sxs-lookup"><span data-stu-id="e77a8-113">The main difference is that it uses the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis instead of the <xref:System.Xml.Linq.XContainer.Elements%2A> axis.</span></span> <span data-ttu-id="e77a8-114">La requête utilise l'axe <xref:System.Xml.Linq.XContainer.Descendants%2A> car dans les documents qui ont des sections, les paragraphes ne sont pas les enfants directs de l'élément de corps, mais se trouvent deux niveaux au-dessous dans la hiérarchie.</span><span class="sxs-lookup"><span data-stu-id="e77a8-114">The query uses the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis because in documents that have sections, the paragraphs will not be the direct children of the body element; rather, the paragraphs will be two levels down in the hierarchy.</span></span> <span data-ttu-id="e77a8-115">Grâce à l'utilisation de la méthode <xref:System.Xml.Linq.XContainer.Descendants%2A>, le code fonctionnera, que le document utilise des sections ou non.</span><span class="sxs-lookup"><span data-stu-id="e77a8-115">By using the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis, the code will work of whether or not the document uses sections.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e77a8-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="e77a8-116">Example</span></span>  
 <span data-ttu-id="e77a8-117">La requête utilise une clause `let` afin de déterminer l'élément qui contient le nœud de style.</span><span class="sxs-lookup"><span data-stu-id="e77a8-117">The query uses a `let` clause to determine the element that contains the style node.</span></span> <span data-ttu-id="e77a8-118">S'il n'y a aucun élément, `styleNode` a la valeur `null` :</span><span class="sxs-lookup"><span data-stu-id="e77a8-118">If there is no element, then `styleNode` is set to `null`:</span></span>  
  
```csharp  
let styleNode = para.Elements(w + "pPr").Elements(w + "pStyle").FirstOrDefault()  
```  
  
 <span data-ttu-id="e77a8-119">La clause `let` utilise d'abord l'axe <xref:System.Xml.Linq.XContainer.Elements%2A> pour rechercher tous les éléments nommés `pPr`, puis utilise la méthode d'extension <xref:System.Xml.Linq.Extensions.Elements%2A> pour rechercher tous les éléments enfants nommés `pStyle`, et pour finir utilise l'opérateur de requête standard <xref:System.Linq.Enumerable.FirstOrDefault%2A> pour convertir la collection en singleton.</span><span class="sxs-lookup"><span data-stu-id="e77a8-119">The `let` clause first uses the <xref:System.Xml.Linq.XContainer.Elements%2A> axis to find all elements named `pPr`, then uses the <xref:System.Xml.Linq.Extensions.Elements%2A> extension method to find all child elements named `pStyle`, and finally uses the <xref:System.Linq.Enumerable.FirstOrDefault%2A> standard query operator to convert the collection to a singleton.</span></span> <span data-ttu-id="e77a8-120">Si la collection est vide, `styleNode` a la valeur `null`.</span><span class="sxs-lookup"><span data-stu-id="e77a8-120">If the collection is empty, `styleNode` is set to `null`.</span></span> <span data-ttu-id="e77a8-121">Il s'agit d'un idiome utile pour rechercher le nœud descendant `pStyle`.</span><span class="sxs-lookup"><span data-stu-id="e77a8-121">This is a useful idiom to look for the `pStyle` descendant node.</span></span> <span data-ttu-id="e77a8-122">Notez que si le nœud enfant `pPr` n'existe pas, le code n'échoue pas avec la levée d'une exception ; au lieu de cela, `styleNode` est définie à `null`, ce qui constitue le comportement souhaité de cette clause `let`.</span><span class="sxs-lookup"><span data-stu-id="e77a8-122">Note that if the `pPr` child node does not exist, the code does nor fail by throwing an exception; instead, `styleNode` is set to `null`, which is the desired behavior of this `let` clause.</span></span>  
  
 <span data-ttu-id="e77a8-123">La requête projette une collection d'un type anonyme avec deux membres, `StyleName` et `ParagraphNode`.</span><span class="sxs-lookup"><span data-stu-id="e77a8-123">The query projects a collection of an anonymous type with two members, `StyleName` and `ParagraphNode`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e77a8-124">Exemple</span><span class="sxs-lookup"><span data-stu-id="e77a8-124">Example</span></span>  
 <span data-ttu-id="e77a8-125">Cet exemple traite un document WordprocessingML et récupère les nœuds de paragraphes à partir d'un document WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="e77a8-125">This example processes a WordprocessingML document, retrieving the paragraph nodes from a WordprocessingML document.</span></span> <span data-ttu-id="e77a8-126">Il identifie également le style de chaque paragraphe.</span><span class="sxs-lookup"><span data-stu-id="e77a8-126">It also identifies the style of each paragraph.</span></span> <span data-ttu-id="e77a8-127">Cet exemple se base sur les exemples précédents de ce didacticiel.</span><span class="sxs-lookup"><span data-stu-id="e77a8-127">This example builds on the previous examples in this tutorial.</span></span> <span data-ttu-id="e77a8-128">Dans le code ci-dessous, la nouvelle requête figure dans des commentaires.</span><span class="sxs-lookup"><span data-stu-id="e77a8-128">The new query is called out in comments in the code below.</span></span>  
  
 <span data-ttu-id="e77a8-129">Vous trouverez des instructions pour créer le document source utilisé dans cet exemple dans [Création du document Office Open XML source (C#)](./creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="e77a8-129">You can find instructions for creating the source document for this example in [Creating the Source Office Open XML Document (C#)](./creating-the-source-office-open-xml-document.md).</span></span>  
  
 <span data-ttu-id="e77a8-130">Cet exemple utilise des classes de l'assembly WindowsBase.</span><span class="sxs-lookup"><span data-stu-id="e77a8-130">This example uses classes found in the WindowsBase assembly.</span></span> <span data-ttu-id="e77a8-131">Il utilise des types dans l'espace de noms <xref:System.IO.Packaging?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e77a8-131">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
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
  
 <span data-ttu-id="e77a8-132">Quand il est appliqué au document décrit dans [Création du document Office Open XML source (C#)](./creating-the-source-office-open-xml-document.md), cet exemple produit la sortie suivante.</span><span class="sxs-lookup"><span data-stu-id="e77a8-132">This example produces the following output when applied to the document described in [Creating the Source Office Open XML Document (C#)](./creating-the-source-office-open-xml-document.md).</span></span>  
  
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
  
## <a name="next-steps"></a><span data-ttu-id="e77a8-133">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="e77a8-133">Next Steps</span></span>  
 <span data-ttu-id="e77a8-134">Dans la rubrique suivante, [Récupération du texte des paragraphes (C#)](./retrieving-the-text-of-the-paragraphs.md), vous allez créer une requête pour récupérer le texte des paragraphes.</span><span class="sxs-lookup"><span data-stu-id="e77a8-134">In the next topic, [Retrieving the Text of the Paragraphs (C#)](./retrieving-the-text-of-the-paragraphs.md), you'll create a query to retrieve the text of paragraphs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e77a8-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e77a8-135">See also</span></span>

- [<span data-ttu-id="e77a8-136">Didacticiel : manipulation de contenu dans un document WordprocessingML (C#)</span><span class="sxs-lookup"><span data-stu-id="e77a8-136">Tutorial: Manipulating Content in a WordprocessingML Document (C#)</span></span>](./shape-of-wordprocessingml-documents.md)
