---
title: Comment modifier un document Office Open XML (C#)
description: Découvrez comment ouvrir un document Office Open XML, le modifier et l’enregistrer. Cet exemple C# utilise des classes qui se trouvent dans l’assembly WindowsBase.
ms.date: 07/20/2015
ms.assetid: 467d489c-2b1b-453b-a757-8ac180e82a96
ms.openlocfilehash: 1155851696a0a6ed651c5f84290a3879e73276db
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104831"
---
# <a name="how-to-modify-an-office-open-xml-document-c"></a><span data-ttu-id="859ce-104">Comment modifier un document Office Open XML (C#)</span><span class="sxs-lookup"><span data-stu-id="859ce-104">How to modify an Office Open XML document (C#)</span></span>
<span data-ttu-id="859ce-105">Cette rubrique présente un exemple qui ouvre un document Office Open XML, le modifie et l'enregistre.</span><span class="sxs-lookup"><span data-stu-id="859ce-105">This topic presents an example that opens an Office Open XML document, modifies it, and saves it.</span></span>  
  
 <span data-ttu-id="859ce-106">Pour plus d’informations sur Office Open XML, consultez [Open XML SDK](https://github.com/OfficeDev/Open-XML-SDK) et [www.ericwhite.com](http://ericwhite.com/).</span><span class="sxs-lookup"><span data-stu-id="859ce-106">For more information on Office Open XML, see [Open XML SDK](https://github.com/OfficeDev/Open-XML-SDK) and [www.ericwhite.com](http://ericwhite.com/).</span></span>  
  
## <a name="example"></a><span data-ttu-id="859ce-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="859ce-107">Example</span></span>  
 <span data-ttu-id="859ce-108">Cet exemple recherche le premier élément de paragraphe dans le document.</span><span class="sxs-lookup"><span data-stu-id="859ce-108">This example finds the first paragraph element in the document.</span></span> <span data-ttu-id="859ce-109">Il récupère le texte du paragraphe, puis supprime toutes les exécutions de texte dans le paragraphe.</span><span class="sxs-lookup"><span data-stu-id="859ce-109">It retrieves the text from the paragraph, and then deletes all text runs in the paragraph.</span></span> <span data-ttu-id="859ce-110">Il crée une nouvelle exécution de texte composée du texte du premier paragraphe qui a été converti en majuscules.</span><span class="sxs-lookup"><span data-stu-id="859ce-110">It creates a new text run that consists of the first paragraph text that has been converted to upper case.</span></span> <span data-ttu-id="859ce-111">Il sérialise ensuite le code XML modifié dans le package Open XML et le ferme.</span><span class="sxs-lookup"><span data-stu-id="859ce-111">It then serializes the changed XML into the Open XML package and closes it.</span></span>  
  
 <span data-ttu-id="859ce-112">Cet exemple utilise des classes de l'assembly WindowsBase.</span><span class="sxs-lookup"><span data-stu-id="859ce-112">This example uses classes found in the WindowsBase assembly.</span></span> <span data-ttu-id="859ce-113">Il utilise des types dans l'espace de noms <xref:System.IO.Packaging?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="859ce-113">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
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
  
        using (Package wdPackage = Package.Open(fileName, FileMode.Open, FileAccess.ReadWrite))  
        {  
            PackageRelationship docPackageRelationship =  
              wdPackage.GetRelationshipsByType(documentRelationshipType).FirstOrDefault();  
            if (docPackageRelationship != null)  
            {  
                Uri documentUri = PackUriHelper.ResolvePartUri(new Uri("/", UriKind.Relative),  
                  docPackageRelationship.TargetUri);  
                PackagePart documentPart = wdPackage.GetPart(documentUri);  
  
                //  Load the document XML in the part into an XDocument instance.  
                XDocument xDoc = XDocument.Load(XmlReader.Create(documentPart.GetStream()));  
  
                //  Find the styles part. There will only be one.  
                PackageRelationship styleRelation =  
                  documentPart.GetRelationshipsByType(stylesRelationshipType).FirstOrDefault();  
                PackagePart stylePart = null;  
                XDocument styleDoc = null;  
  
                if (styleRelation != null)  
                {  
                    Uri styleUri = PackUriHelper.ResolvePartUri(documentUri, styleRelation.TargetUri);  
                    stylePart = wdPackage.GetPart(styleUri);  
  
                    //  Load the style XML in the part into an XDocument instance.  
                    styleDoc = XDocument.Load(XmlReader.Create(stylePart.GetStream()));  
                }  
  
                XElement paraNode = xDoc  
                                    .Root  
                                    .Element(w + "body")  
                                    .Descendants(w + "p")  
                                    .FirstOrDefault();  
  
                string paraText = ParagraphText(paraNode);  
  
                // remove all text runs  
                paraNode.Descendants(w + "r").Remove();  
  
                paraNode.Add(  
                    new XElement(w + "r",  
                        new XElement(w + "t", paraText.ToUpper())  
                    )  
                );  
  
                //  Save the XML into the package  
                using (XmlWriter xw =  
                  XmlWriter.Create(documentPart.GetStream(FileMode.Create, FileAccess.Write)))  
                {  
                    xDoc.Save(xw);  
                }  
  
                Console.WriteLine("New first paragraph: >{0}<", paraText.ToUpper());  
            }  
        }  
    }  
}  
```  
  
 <span data-ttu-id="859ce-114">Si vous ouvrez `SampleDoc.docx` après avoir exécuté ce programme, vous constatez que ce programme a converti le premier paragraphe du document en majuscules.</span><span class="sxs-lookup"><span data-stu-id="859ce-114">If you open `SampleDoc.docx` after running this program, you can see that this program converted the first paragraph in the document to upper case.</span></span>  
  
 <span data-ttu-id="859ce-115">Quand il est exécuté avec l’exemple de document Open XML décrit dans [Création du document Office Open XML source (C#)](./creating-the-source-office-open-xml-document.md), cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="859ce-115">When run with the sample Open XML document described in [Creating the Source Office Open XML Document (C#)](./creating-the-source-office-open-xml-document.md), this example produces the following output:</span></span>  
  
```output  
New first paragraph: >PARSING WORDPROCESSINGML WITH LINQ TO XML<  
```  
