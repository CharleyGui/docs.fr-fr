---
title: Projection de code XML en une autre forme (C#)
description: Découvrez comment projeter du code XML dans une autre forme que le XML source. Passez en revue un exemple de code qui utilise des classes de l’assembly WindowsBase.
ms.date: 07/20/2015
ms.assetid: 4cb6b14a-32dc-4a2a-813e-bf9368fa8d86
ms.openlocfilehash: 492c0671b6a81f7e6b8d5f93698f84b88b14bd23
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87299095"
---
# <a name="projecting-xml-in-a-different-shape-c"></a>Projection de code XML en une autre forme (C#)
Cette rubrique illustre un exemple de projection de code XML dont la forme est différente du code XML source.  
  
 De nombreuses transformations XML courantes sont composées de requêtes chaînées, comme dans cet exemple. Il est courant de commencer avec une certaine forme de code XML, de projeter des résultats intermédiaires en tant que collections de types anonymes ou nommés, puis de projeter les résultats dans du code XML sous une forme complètement différente du code XML source.  
  
## <a name="example"></a>Exemple  
 Cet exemple traite un document WordprocessingML et récupère les nœuds de paragraphes à partir d'un document WordprocessingML. Il identifie également le style et le texte de chaque paragraphe. Pour finir, l'exemple projette le code XML sous une forme différente. Cet exemple se base sur les exemples précédents de ce didacticiel. Dans le code ci-dessous, la nouvelle instruction qui effectue la projection figure dans des commentaires.  
  
 Pour obtenir des instructions pour créer le document source utilisé dans cet exemple, consultez [Création du document Office Open XML source (C#)](./creating-the-source-office-open-xml-document.md).  
  
 Cet exemple utilise des classes de l'assembly WindowsBase. Il utilise des types dans l'espace de noms <xref:System.IO.Packaging?displayProperty=nameWithType>.  
  
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
  
        // The following is the new code that projects XML in a new shape.  
        XElement root = new XElement("Root",  
            from p in paraWithText  
            select new XElement("Paragraph",  
                new XElement("StyleName", p.StyleName),  
                new XElement("Text", p.Text)  
            )  
        );  
  
        Console.WriteLine(root);  
    }  
}  
```  
  
 Cet exemple produit la sortie suivante :  
  
```xml  
<Root>  
  <Paragraph>  
    <StyleName>Heading1</StyleName>  
    <Text>Parsing WordprocessingML with LINQ to XML</Text>  
  </Paragraph>  
  <Paragraph>  
    <StyleName>Normal</StyleName>  
    <Text></Text>  
  </Paragraph>  
  <Paragraph>  
    <StyleName>Normal</StyleName>  
    <Text>The following example prints to the console.</Text>  
  </Paragraph>  
  <Paragraph>  
    <StyleName>Normal</StyleName>  
    <Text></Text>  
  </Paragraph>  
  <Paragraph>  
    <StyleName>Code</StyleName>  
    <Text>using System;</Text>  
  </Paragraph>  
  <Paragraph>  
    <StyleName>Code</StyleName>  
    <Text></Text>  
  </Paragraph>  
  <Paragraph>  
    <StyleName>Code</StyleName>  
    <Text>class Program {</Text>  
  </Paragraph>  
  <Paragraph>  
    <StyleName>Code</StyleName>  
    <Text>    public static void (string[] args) {</Text>  
  </Paragraph>  
  <Paragraph>  
    <StyleName>Code</StyleName>  
    <Text>        Console.WriteLine("Hello World");</Text>  
  </Paragraph>  
  <Paragraph>  
    <StyleName>Code</StyleName>  
    <Text>    }</Text>  
  </Paragraph>  
  <Paragraph>  
    <StyleName>Code</StyleName>  
    <Text>}</Text>  
  </Paragraph>  
  <Paragraph>  
    <StyleName>Normal</StyleName>  
    <Text></Text>  
  </Paragraph>  
  <Paragraph>  
    <StyleName>Normal</StyleName>  
    <Text>This example produces the following output:</Text>  
  </Paragraph>  
  <Paragraph>  
    <StyleName>Normal</StyleName>  
    <Text></Text>  
  </Paragraph>  
  <Paragraph>  
    <StyleName>Code</StyleName>  
    <Text>Hello World</Text>  
  </Paragraph>  
</Root>  
```  
  
## <a name="next-steps"></a>Étapes suivantes  
 Dans l’exemple suivant, vous allez effectuer une requête pour rechercher toutes les occurrences d’un texte dans un document Word :  
  
- [Recherche de texte dans des documents Word (C#)](./finding-text-in-word-documents.md)  
  