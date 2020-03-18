---
title: Comment effectuer des transformations en streaming du texte à XML (C)
ms.date: 07/20/2015
ms.assetid: 9b3bd941-d0ff-4f2d-ae41-7c3b81d8fae6
ms.openlocfilehash: 496535b7f868095a62be2b72b1eea2b082e00a44
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75345798"
---
# <a name="how-to-perform-streaming-transformations-of-text-to-xml-c"></a><span data-ttu-id="a6a19-102">Comment effectuer des transformations en streaming du texte à XML (C)</span><span class="sxs-lookup"><span data-stu-id="a6a19-102">How to perform streaming transformations of text to XML (C#)</span></span>

<span data-ttu-id="a6a19-103">L'une des façons de traiter un fichier texte consiste à écrire une méthode d'extension qui diffuse en continu le fichier texte une ligne à la fois à l'aide de la construction `yield return`.</span><span class="sxs-lookup"><span data-stu-id="a6a19-103">One approach to processing a text file is to write an extension method that streams the text file a line at a time using the `yield return` construct.</span></span> <span data-ttu-id="a6a19-104">Vous pouvez alors écrire une requête LINQ qui traite le fichier texte de manière différée.</span><span class="sxs-lookup"><span data-stu-id="a6a19-104">You then can write a LINQ query that processes the text file in a lazy deferred fashion.</span></span> <span data-ttu-id="a6a19-105">Si vous utilisez ensuite <xref:System.Xml.Linq.XStreamingElement> pour diffuser la sortie en continu, vous pouvez créer une transformation du fichier texte en XML qui utilise une quantité minimale de mémoire, quelle que soit la taille du fichier texte source.</span><span class="sxs-lookup"><span data-stu-id="a6a19-105">If you then use <xref:System.Xml.Linq.XStreamingElement> to stream output, you then can create a transformation from the text file to XML that uses a minimal amount of memory, regardless of the size of the source text file.</span></span>

 <span data-ttu-id="a6a19-106">Il existe certains points à noter concernant les transformations de streaming.</span><span class="sxs-lookup"><span data-stu-id="a6a19-106">There are some caveats regarding streaming transformations.</span></span> <span data-ttu-id="a6a19-107">Il est préférable d'appliquer une transformation de streaming dans les situations où vous pouvez traiter l'intégralité du fichier une seule fois et si vous pouvez traiter les lignes dans l'ordre dans lequel elles apparaissent dans le document source.</span><span class="sxs-lookup"><span data-stu-id="a6a19-107">A streaming transformation is best applied in situations where you can process the entire file once, and if you can process the lines in the order that they occur in the source document.</span></span> <span data-ttu-id="a6a19-108">Si vous devez traiter le fichier à plusieurs reprises, ou si vous devez trier les lignes avant de les traiter, vous perdez une grande partie des avantages offerts par l'utilisation d'une technique de streaming.</span><span class="sxs-lookup"><span data-stu-id="a6a19-108">If you have to process the file more than once, or if you have to sort the lines before you can process them, you will lose many of the benefits of using a streaming technique.</span></span>

## <a name="example"></a><span data-ttu-id="a6a19-109"> Exemple</span><span class="sxs-lookup"><span data-stu-id="a6a19-109">Example</span></span>

 <span data-ttu-id="a6a19-110">Le fichier texte suivant, People.txt, est la source pour cet exemple.</span><span class="sxs-lookup"><span data-stu-id="a6a19-110">The following text file, People.txt, is the source for this example.</span></span>

```text
#This is a comment
1,Tai,Yee,Writer
2,Nikolay,Grachev,Programmer
3,David,Wright,Inventor
```

 <span data-ttu-id="a6a19-111">Le code suivant contient une méthode d'extension qui diffuse en continu les lignes du fichier texte de manière différée.</span><span class="sxs-lookup"><span data-stu-id="a6a19-111">The following code contains an extension method that streams the lines of the text file in a deferred fashion.</span></span>

```csharp
public static class StreamReaderSequence
{
    public static IEnumerable<string> Lines(this StreamReader source)
    {
        if (source == null)
            throw new ArgumentNullException(nameof(source));

        string line;
        while ((line = source.ReadLine()) != null)
        {
            yield return line;
        }
    }
}

class Program
{
    static void Main(string[] args)
    {
        var sr = new StreamReader("People.txt");
        var xmlTree = new XStreamingElement("Root",
            from line in sr.Lines()
            let items = line.Split(',')
            where !line.StartsWith("#")
            select new XElement("Person",
                       new XAttribute("ID", items[0]),
                       new XElement("First", items[1]),
                       new XElement("Last", items[2]),
                       new XElement("Occupation", items[3])
                   )
        );
        Console.WriteLine(xmlTree);
        sr.Close();
    }
}
```

 <span data-ttu-id="a6a19-112">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="a6a19-112">This example produces the following output:</span></span>

```xml
<Root>
  <Person ID="1">
    <First>Tai</First>
    <Last>Yee</Last>
    <Occupation>Writer</Occupation>
  </Person>
  <Person ID="2">
    <First>Nikolay</First>
    <Last>Grachev</Last>
    <Occupation>Programmer</Occupation>
  </Person>
  <Person ID="3">
    <First>David</First>
    <Last>Wright</Last>
    <Occupation>Inventor</Occupation>
  </Person>
</Root>
```

## <a name="see-also"></a><span data-ttu-id="a6a19-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a6a19-113">See also</span></span>

- <xref:System.Xml.Linq.XStreamingElement>
