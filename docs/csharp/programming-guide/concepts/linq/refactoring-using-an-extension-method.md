---
title: Refactorisation à l’aide d’une méthode d’extension (C#)
description: Découvrez comment refactoriser du code à l’aide d’une méthode d’extension. Consultez des exemples de code et affichez des ressources disponibles supplémentaires.
ms.date: 07/20/2015
ms.assetid: c5fc123d-af10-4a2f-b8e4-db921efb2639
ms.openlocfilehash: e786f0e1514156535fd6a6033e37ed8879e99709
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381942"
---
# <a name="refactoring-using-an-extension-method-c"></a><span data-ttu-id="38ad9-104">Refactorisation à l’aide d’une méthode d’extension (C#)</span><span class="sxs-lookup"><span data-stu-id="38ad9-104">Refactoring Using an Extension Method (C#)</span></span>
<span data-ttu-id="38ad9-105">Cet exemple se base sur l’exemple précédent, [Récupération du texte des paragraphes (C#)](./retrieving-the-text-of-the-paragraphs.md), en refactorisant la concaténation de chaînes à l’aide d’une fonction pure implémentée en tant que méthode d’extension.</span><span class="sxs-lookup"><span data-stu-id="38ad9-105">This example builds on the previous example, [Retrieving the Text of the Paragraphs (C#)](./retrieving-the-text-of-the-paragraphs.md), by refactoring the concatenation of strings using a pure function that is implemented as an extension method.</span></span>  
  
 <span data-ttu-id="38ad9-106">L'exemple précédent utilisait l'opérateur de requête standard <xref:System.Linq.Enumerable.Aggregate%2A> pour concaténer plusieurs chaînes dans une chaîne.</span><span class="sxs-lookup"><span data-stu-id="38ad9-106">The previous example used the <xref:System.Linq.Enumerable.Aggregate%2A> standard query operator to concatenate multiple strings into one string.</span></span> <span data-ttu-id="38ad9-107">Toutefois, il est plus commode d'écrire une méthode d'extension pour cela, car la requête résultante est plus petite et plus simple.</span><span class="sxs-lookup"><span data-stu-id="38ad9-107">However, it is more convenient to write an extension method to do this, because the resulting query smaller and more simple.</span></span>  
  
## <a name="example"></a><span data-ttu-id="38ad9-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="38ad9-108">Example</span></span>  
 <span data-ttu-id="38ad9-109">Cet exemple traite un document WordprocessingML, récupère les paragraphes, le style de chaque paragraphe et le texte de chaque paragraphe.</span><span class="sxs-lookup"><span data-stu-id="38ad9-109">This example processes a WordprocessingML document, retrieving the paragraphs, the style of each paragraph, and the text of each paragraph.</span></span> <span data-ttu-id="38ad9-110">Cet exemple se base sur les exemples précédents de ce didacticiel.</span><span class="sxs-lookup"><span data-stu-id="38ad9-110">This example builds on the previous examples in this tutorial.</span></span>  
  
 <span data-ttu-id="38ad9-111">L'exemple contient plusieurs surcharges de la méthode `StringConcatenate`.</span><span class="sxs-lookup"><span data-stu-id="38ad9-111">The example contains multiple overloads of the `StringConcatenate` method.</span></span>  
  
 <span data-ttu-id="38ad9-112">Vous trouverez des instructions pour créer le document source utilisé dans cet exemple dans [Création du document Office Open XML source (C#)](./creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="38ad9-112">You can find instructions for creating the source document for this example in [Creating the Source Office Open XML Document (C#)](./creating-the-source-office-open-xml-document.md).</span></span>  
  
 <span data-ttu-id="38ad9-113">Cet exemple utilise des classes de l'assembly WindowsBase.</span><span class="sxs-lookup"><span data-stu-id="38ad9-113">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="38ad9-114">Il utilise des types dans l'espace de noms <xref:System.IO.Packaging?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="38ad9-114">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
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
```  
  
## <a name="example"></a><span data-ttu-id="38ad9-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="38ad9-115">Example</span></span>  
 <span data-ttu-id="38ad9-116">Il existe quatre surcharges de la méthode `StringConcatenate`.</span><span class="sxs-lookup"><span data-stu-id="38ad9-116">There are four overloads of the `StringConcatenate` method.</span></span> <span data-ttu-id="38ad9-117">Une surcharge prend simplement une collection de chaînes et retourne une seule chaîne.</span><span class="sxs-lookup"><span data-stu-id="38ad9-117">One overload simply takes a collection of strings and returns a single string.</span></span> <span data-ttu-id="38ad9-118">Une autre surcharge prend une collection d'un type quelconque et un délégué qui projette depuis un singleton de la collection vers une chaîne.</span><span class="sxs-lookup"><span data-stu-id="38ad9-118">Another overload can take a collection of any type, and a delegate that projects from a singleton of the collection to a string.</span></span> <span data-ttu-id="38ad9-119">Il existe deux surcharges supplémentaires qui vous permettent de spécifier une chaîne de séparation.</span><span class="sxs-lookup"><span data-stu-id="38ad9-119">There are two more overloads that allow you to specify a separator string.</span></span>  
  
 <span data-ttu-id="38ad9-120">Le code suivant utilise les quatre surcharges.</span><span class="sxs-lookup"><span data-stu-id="38ad9-120">The following code uses all four overloads.</span></span>  
  
```csharp  
string[] numbers = { "one", "two", "three" };  
  
Console.WriteLine("{0}", numbers.StringConcatenate());  
Console.WriteLine("{0}", numbers.StringConcatenate(":"));  
  
int[] intNumbers = { 1, 2, 3 };  
Console.WriteLine("{0}", intNumbers.StringConcatenate(i => i.ToString()));  
Console.WriteLine("{0}", intNumbers.StringConcatenate(i => i.ToString(), ":"));  
```  
  
 <span data-ttu-id="38ad9-121">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="38ad9-121">This example produces the following output:</span></span>  
  
```output  
onetwothree  
one:two:three:  
123  
1:2:3:  
```  
  
## <a name="example"></a><span data-ttu-id="38ad9-122">Exemple</span><span class="sxs-lookup"><span data-stu-id="38ad9-122">Example</span></span>  
 <span data-ttu-id="38ad9-123">À présent, l’exemple peut être modifié pour tirer parti de la nouvelle méthode d’extension :</span><span class="sxs-lookup"><span data-stu-id="38ad9-123">Now, the example can be modified to take advantage of the new extension method:</span></span>  
  
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
                    Uri styleUri =  
                      PackUriHelper.ResolvePartUri(documentUri, styleRelation.TargetUri);  
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
                Text = para  
                       .ParagraphNode  
                       .Elements(w + "r")  
                       .Elements(w + "t")  
                       .StringConcatenate(e => (string)e)  
            };  
  
        foreach (var p in paraWithText)  
            Console.WriteLine("StyleName:{0} >{1}<", p.StyleName, p.Text);  
    }  
}  
```  
  
 <span data-ttu-id="38ad9-124">Quand il est appliqué au document décrit dans [Création du document Office Open XML source (C#)](./creating-the-source-office-open-xml-document.md), cet exemple produit la sortie suivante.</span><span class="sxs-lookup"><span data-stu-id="38ad9-124">This example produces the following output when applied to the document described in [Creating the Source Office Open XML Document (C#)](./creating-the-source-office-open-xml-document.md).</span></span>  
  
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
  
 <span data-ttu-id="38ad9-125">Notez que cette refactorisation est une variante de la refactorisation dans une fonction pure.</span><span class="sxs-lookup"><span data-stu-id="38ad9-125">Note that this refactoring is a variant of refactoring into a pure function.</span></span> <span data-ttu-id="38ad9-126">La rubrique suivante présente le concept de factorisation dans des fonctions pures de manière plus détaillée.</span><span class="sxs-lookup"><span data-stu-id="38ad9-126">The next topic will introduce the idea of factoring into pure functions in more detail.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="38ad9-127">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="38ad9-127">Next Steps</span></span>  
 <span data-ttu-id="38ad9-128">L'exemple suivant montre comment refactoriser ce code d'une autre manière, à l'aide de fonctions pures :</span><span class="sxs-lookup"><span data-stu-id="38ad9-128">The next example shows how to refactor this code in another way, by using pure functions:</span></span>  
  
- [<span data-ttu-id="38ad9-129">Refactorisation à l’aide d’une fonction pure (C#)</span><span class="sxs-lookup"><span data-stu-id="38ad9-129">Refactoring Using a Pure Function (C#)</span></span>](./refactoring-using-a-pure-function.md)
  
## <a name="see-also"></a><span data-ttu-id="38ad9-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="38ad9-130">See also</span></span>

- [<span data-ttu-id="38ad9-131">Didacticiel : manipulation de contenu dans un document WordprocessingML (C#)</span><span class="sxs-lookup"><span data-stu-id="38ad9-131">Tutorial: Manipulating Content in a WordprocessingML Document (C#)</span></span>](./shape-of-wordprocessingml-documents.md)
- [<span data-ttu-id="38ad9-132">Refactorisation dans des fonctions pures (C#)</span><span class="sxs-lookup"><span data-stu-id="38ad9-132">Refactoring Into Pure Functions (C#)</span></span>](./refactoring-into-pure-functions.md)
