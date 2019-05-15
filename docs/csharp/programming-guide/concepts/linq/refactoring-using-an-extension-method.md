---
title: Refactorisation à l’aide d’une méthode d’extension (C#)
ms.date: 07/20/2015
ms.assetid: c5fc123d-af10-4a2f-b8e4-db921efb2639
ms.openlocfilehash: 0f41c4b4357125b6c92b17d8c818a0cfcf9822e7
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64596179"
---
# <a name="refactoring-using-an-extension-method-c"></a><span data-ttu-id="512b7-102">Refactorisation à l’aide d’une méthode d’extension (C#)</span><span class="sxs-lookup"><span data-stu-id="512b7-102">Refactoring Using an Extension Method (C#)</span></span>
<span data-ttu-id="512b7-103">Cet exemple se base sur l’exemple précédent, [Récupération du texte des paragraphes (C#)](../../../../csharp/programming-guide/concepts/linq/retrieving-the-text-of-the-paragraphs.md), en refactorisant la concaténation de chaînes à l’aide d’une fonction pure implémentée en tant que méthode d’extension.</span><span class="sxs-lookup"><span data-stu-id="512b7-103">This example builds on the previous example, [Retrieving the Text of the Paragraphs (C#)](../../../../csharp/programming-guide/concepts/linq/retrieving-the-text-of-the-paragraphs.md), by refactoring the concatenation of strings using a pure function that is implemented as an extension method.</span></span>  
  
 <span data-ttu-id="512b7-104">L'exemple précédent utilisait l'opérateur de requête standard <xref:System.Linq.Enumerable.Aggregate%2A> pour concaténer plusieurs chaînes dans une chaîne.</span><span class="sxs-lookup"><span data-stu-id="512b7-104">The previous example used the <xref:System.Linq.Enumerable.Aggregate%2A> standard query operator to concatenate multiple strings into one string.</span></span> <span data-ttu-id="512b7-105">Toutefois, il est plus commode d'écrire une méthode d'extension pour cela, car la requête résultante est plus petite et plus simple.</span><span class="sxs-lookup"><span data-stu-id="512b7-105">However, it is more convenient to write an extension method to do this, because the resulting query smaller and more simple.</span></span>  
  
## <a name="example"></a><span data-ttu-id="512b7-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="512b7-106">Example</span></span>  
 <span data-ttu-id="512b7-107">Cet exemple traite un document WordprocessingML, récupère les paragraphes, le style de chaque paragraphe et le texte de chaque paragraphe.</span><span class="sxs-lookup"><span data-stu-id="512b7-107">This example processes a WordprocessingML document, retrieving the paragraphs, the style of each paragraph, and the text of each paragraph.</span></span> <span data-ttu-id="512b7-108">Cet exemple se base sur les exemples précédents de ce didacticiel.</span><span class="sxs-lookup"><span data-stu-id="512b7-108">This example builds on the previous examples in this tutorial.</span></span>  
  
 <span data-ttu-id="512b7-109">L'exemple contient plusieurs surcharges de la méthode `StringConcatenate`.</span><span class="sxs-lookup"><span data-stu-id="512b7-109">The example contains multiple overloads of the `StringConcatenate` method.</span></span>  
  
 <span data-ttu-id="512b7-110">Vous trouverez des instructions pour créer le document source utilisé dans cet exemple dans [Création du document Office Open XML source (C#)](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="512b7-110">You can find instructions for creating the source document for this example in [Creating the Source Office Open XML Document (C#)](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span></span>  
  
 <span data-ttu-id="512b7-111">Cet exemple utilise des classes de l'assembly WindowsBase.</span><span class="sxs-lookup"><span data-stu-id="512b7-111">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="512b7-112">Il utilise des types dans l'espace de noms <xref:System.IO.Packaging?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="512b7-112">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="512b7-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="512b7-113">Example</span></span>  
 <span data-ttu-id="512b7-114">Il existe quatre surcharges de la méthode `StringConcatenate`.</span><span class="sxs-lookup"><span data-stu-id="512b7-114">There are four overloads of the `StringConcatenate` method.</span></span> <span data-ttu-id="512b7-115">Une surcharge prend simplement une collection de chaînes et retourne une seule chaîne.</span><span class="sxs-lookup"><span data-stu-id="512b7-115">One overload simply takes a collection of strings and returns a single string.</span></span> <span data-ttu-id="512b7-116">Une autre surcharge prend une collection d'un type quelconque et un délégué qui projette depuis un singleton de la collection vers une chaîne.</span><span class="sxs-lookup"><span data-stu-id="512b7-116">Another overload can take a collection of any type, and a delegate that projects from a singleton of the collection to a string.</span></span> <span data-ttu-id="512b7-117">Il existe deux surcharges supplémentaires qui vous permettent de spécifier une chaîne de séparation.</span><span class="sxs-lookup"><span data-stu-id="512b7-117">There are two more overloads that allow you to specify a separator string.</span></span>  
  
 <span data-ttu-id="512b7-118">Le code suivant utilise les quatre surcharges.</span><span class="sxs-lookup"><span data-stu-id="512b7-118">The following code uses all four overloads.</span></span>  
  
```csharp  
string[] numbers = { "one", "two", "three" };  
  
Console.WriteLine("{0}", numbers.StringConcatenate());  
Console.WriteLine("{0}", numbers.StringConcatenate(":"));  
  
int[] intNumbers = { 1, 2, 3 };  
Console.WriteLine("{0}", intNumbers.StringConcatenate(i => i.ToString()));  
Console.WriteLine("{0}", intNumbers.StringConcatenate(i => i.ToString(), ":"));  
```  
  
 <span data-ttu-id="512b7-119">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="512b7-119">This example produces the following output:</span></span>  
  
```  
onetwothree  
one:two:three:  
123  
1:2:3:  
```  
  
## <a name="example"></a><span data-ttu-id="512b7-120">Exemple</span><span class="sxs-lookup"><span data-stu-id="512b7-120">Example</span></span>  
 <span data-ttu-id="512b7-121">À présent, l’exemple peut être modifié pour tirer parti de la nouvelle méthode d’extension :</span><span class="sxs-lookup"><span data-stu-id="512b7-121">Now, the example can be modified to take advantage of the new extension method:</span></span>  
  
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
  
 <span data-ttu-id="512b7-122">Quand il est appliqué au document décrit dans [Création du document Office Open XML source (C#)](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md), cet exemple produit la sortie suivante.</span><span class="sxs-lookup"><span data-stu-id="512b7-122">This example produces the following output when applied to the document described in [Creating the Source Office Open XML Document (C#)](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span></span>  
  
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
  
 <span data-ttu-id="512b7-123">Notez que cette refactorisation est une variante de la refactorisation dans une fonction pure.</span><span class="sxs-lookup"><span data-stu-id="512b7-123">Note that this refactoring is a variant of refactoring into a pure function.</span></span> <span data-ttu-id="512b7-124">La rubrique suivante présente le concept de factorisation dans des fonctions pures de manière plus détaillée.</span><span class="sxs-lookup"><span data-stu-id="512b7-124">The next topic will introduce the idea of factoring into pure functions in more detail.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="512b7-125">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="512b7-125">Next Steps</span></span>  
 <span data-ttu-id="512b7-126">L'exemple suivant montre comment refactoriser ce code d'une autre manière, à l'aide de fonctions pures :</span><span class="sxs-lookup"><span data-stu-id="512b7-126">The next example shows how to refactor this code in another way, by using pure functions:</span></span>  
  
- [<span data-ttu-id="512b7-127">Refactorisation à l’aide d’une fonction pure (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="512b7-127">Refactoring Using a Pure Function (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/refactoring-using-a-pure-function.md)  
  
## <a name="see-also"></a><span data-ttu-id="512b7-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="512b7-128">See also</span></span>

- [<span data-ttu-id="512b7-129">Tutoriel : manipulation de contenu dans un document WordprocessingML (C#)</span><span class="sxs-lookup"><span data-stu-id="512b7-129">Tutorial: Manipulating Content in a WordprocessingML Document (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
- [<span data-ttu-id="512b7-130">Refactorisation dans des fonctions pures (C#)</span><span class="sxs-lookup"><span data-stu-id="512b7-130">Refactoring Into Pure Functions (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/refactoring-into-pure-functions.md)
