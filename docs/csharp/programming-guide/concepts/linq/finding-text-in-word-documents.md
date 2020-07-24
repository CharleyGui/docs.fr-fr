---
title: Recherche de texte dans des documents Word (C#)
description: Découvrez comment traiter un document WordprocessingML avec LINQ en C#. Cet exemple recherche toutes les occurrences d’une chaîne dans le document.
ms.date: 07/20/2015
ms.assetid: 82f86677-560b-49dc-a089-610409939b2a
ms.openlocfilehash: 1efcbef6185b718287f1222ecc086f4c675f02ab
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105393"
---
# <a name="finding-text-in-word-documents-c"></a><span data-ttu-id="fb6b2-104">Recherche de texte dans des documents Word (C#)</span><span class="sxs-lookup"><span data-stu-id="fb6b2-104">Finding Text in Word Documents (C#)</span></span>
<span data-ttu-id="fb6b2-105">Cette rubrique étend les requêtes précédentes afin d'effectuer une opération utile : rechercher toutes les occurrences d'une chaîne dans le document.</span><span class="sxs-lookup"><span data-stu-id="fb6b2-105">This topic extends the previous queries to do something useful: find all occurrences of a string in the document.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fb6b2-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="fb6b2-106">Example</span></span>  
 <span data-ttu-id="fb6b2-107">Cet exemple traite un document WordprocessingML afin de rechercher toutes les occurrences d'un segment de texte spécifique dans le document.</span><span class="sxs-lookup"><span data-stu-id="fb6b2-107">This example processes a WordprocessingML document, to find all the occurrences of a specific piece of text in the document.</span></span> <span data-ttu-id="fb6b2-108">Pour cela, nous utilisons une requête qui recherche la chaîne « Hello ».</span><span class="sxs-lookup"><span data-stu-id="fb6b2-108">To do this, we use a query that finds the string "Hello".</span></span> <span data-ttu-id="fb6b2-109">Cet exemple se base sur les exemples précédents de ce didacticiel.</span><span class="sxs-lookup"><span data-stu-id="fb6b2-109">This example builds on the previous examples in this tutorial.</span></span> <span data-ttu-id="fb6b2-110">Dans le code ci-dessous, la nouvelle requête figure dans des commentaires.</span><span class="sxs-lookup"><span data-stu-id="fb6b2-110">The new query is called out in comments in the code below.</span></span>  
  
 <span data-ttu-id="fb6b2-111">Pour obtenir des instructions pour créer le document source utilisé dans cet exemple, consultez [Création du document Office Open XML source (C#)](./creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="fb6b2-111">For instructions for creating the source document for this example, see [Creating the Source Office Open XML Document (C#)](./creating-the-source-office-open-xml-document.md).</span></span>  
  
 <span data-ttu-id="fb6b2-112">Cet exemple utilise des classes de l'assembly WindowsBase.</span><span class="sxs-lookup"><span data-stu-id="fb6b2-112">This example uses classes found in the WindowsBase assembly.</span></span> <span data-ttu-id="fb6b2-113">Il utilise des types dans l'espace de noms <xref:System.IO.Packaging?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fb6b2-113">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
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
    public static string ParagraphText(XElement e)  
    {  
        XNamespace w = e.Name.Namespace;  
        return e  
               .Elements(w + "r")  
               .Elements(w + "t")  
               .StringConcatenate(element => (string)element);  
    }  
  
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
                Text = ParagraphText(para.ParagraphNode)  
            };  
  
        // Following is the new query that retrieves all paragraphs  
        // that have specific text in them.  
        var helloParagraphs =  
            from para in paraWithText  
            where para.Text.Contains("Hello")  
            select new  
            {  
                ParagraphNode = para.ParagraphNode,  
                StyleName = para.StyleName,  
                Text = para.Text  
            };  
  
        foreach (var p in helloParagraphs)  
            Console.WriteLine("StyleName:{0} >{1}<", p.StyleName, p.Text);  
    }  
}  
```  
  
 <span data-ttu-id="fb6b2-114">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="fb6b2-114">This example produces the following output:</span></span>  
  
```output  
StyleName:Code >        Console.WriteLine("Hello World");<  
StyleName:Code >Hello World<  
```  
  
 <span data-ttu-id="fb6b2-115">Vous pouvez bien entendu modifier la recherche afin de rechercher les lignes avec un style spécifique.</span><span class="sxs-lookup"><span data-stu-id="fb6b2-115">You can, of course, modify the search so that it searches for lines with a specific style.</span></span> <span data-ttu-id="fb6b2-116">La requête suivante recherche toutes les lignes vides qui possèdent le style Code :</span><span class="sxs-lookup"><span data-stu-id="fb6b2-116">The following query finds all blank lines that have the Code style:</span></span>  
  
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
    public static string ParagraphText(XElement e)  
    {  
        XNamespace w = e.Name.Namespace;  
        return e  
               .Elements(w + "r")  
               .Elements(w + "t")  
               .StringConcatenate(element => (string)element);  
    }  
  
    static void Main(string[] args)  
    {  
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
                Text = ParagraphText(para.ParagraphNode)  
            };  
  
        // Retrieve all paragraphs that have no text and are styled Code.  
        var blankCodeParagraphs =  
            from para in paraWithText  
            where para.Text == "" && para.StyleName == "Code"  
            select new  
            {  
                ParagraphNode = para.ParagraphNode,  
                StyleName = para.StyleName,  
                Text = para.Text  
            };  
  
        foreach (var p in blankCodeParagraphs)  
            Console.WriteLine("StyleName:{0} >{1}<", p.StyleName, p.Text);  
    }  
}  
```  
  
 <span data-ttu-id="fb6b2-117">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="fb6b2-117">This example produces the following output:</span></span>  
  
```output  
StyleName:Code ><  
```  
  
 <span data-ttu-id="fb6b2-118">Bien entendu, cet exemple pourrait être amélioré de diverses manières.</span><span class="sxs-lookup"><span data-stu-id="fb6b2-118">Of course, this example could be enhanced in a number of ways.</span></span> <span data-ttu-id="fb6b2-119">Par exemple, nous pourrions utiliser des expressions régulières pour rechercher du texte, nous pourrions itérer au sein de tous les fichiers Word dans un répertoire donné, et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="fb6b2-119">For example, we could use regular expressions to search for text, we could iterate through all the Word files in a particular directory, and so on.</span></span>  
  
 <span data-ttu-id="fb6b2-120">Notez que si cet exemple était écrit comme une seule requête, ses performances seraient à peu près les mêmes.</span><span class="sxs-lookup"><span data-stu-id="fb6b2-120">Note that this example performs approximately as well as if it were written as a single query.</span></span> <span data-ttu-id="fb6b2-121">Chaque requête étant implémentée d'une manière différée, elle ne produit ses résultats qu'une fois qu'elle a été itérée.</span><span class="sxs-lookup"><span data-stu-id="fb6b2-121">Because each query is implemented in a lazy, deferred fashion, each query does not yield its results until the query is iterated.</span></span> <span data-ttu-id="fb6b2-122">Pour plus d’informations sur l’exécution et l’évaluation différée, consultez [Exécution et évaluation différées dans LINQ to XML (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="fb6b2-122">For more information about execution and lazy evaluation, see [Deferred Execution and Lazy Evaluation in LINQ to XML (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="fb6b2-123">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="fb6b2-123">Next Steps</span></span>  
 <span data-ttu-id="fb6b2-124">La section suivante fournit plus d'informations sur les documents WordprocessingML :</span><span class="sxs-lookup"><span data-stu-id="fb6b2-124">The next section provides more information about WordprocessingML documents:</span></span>  
  
- [<span data-ttu-id="fb6b2-125">Détails des documents WordprocessingML Office Open XML (C#)</span><span class="sxs-lookup"><span data-stu-id="fb6b2-125">Details of Office Open XML WordprocessingML Documents (C#)</span></span>](./wordprocessingml-document-with-styles.md)  
  
## <a name="see-also"></a><span data-ttu-id="fb6b2-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fb6b2-126">See also</span></span>

- [<span data-ttu-id="fb6b2-127">Didacticiel : manipulation de contenu dans un document WordprocessingML (C#)</span><span class="sxs-lookup"><span data-stu-id="fb6b2-127">Tutorial: Manipulating Content in a WordprocessingML Document (C#)</span></span>](./shape-of-wordprocessingml-documents.md)
- [<span data-ttu-id="fb6b2-128">Refactorisation à l’aide d’une fonction pure (C#)</span><span class="sxs-lookup"><span data-stu-id="fb6b2-128">Refactoring Using a Pure Function (C#)</span></span>](./refactoring-using-a-pure-function.md)
- [<span data-ttu-id="fb6b2-129">Exécution et évaluation différées dans LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="fb6b2-129">Deferred Execution and Lazy Evaluation in LINQ to XML (C#)</span></span>](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
