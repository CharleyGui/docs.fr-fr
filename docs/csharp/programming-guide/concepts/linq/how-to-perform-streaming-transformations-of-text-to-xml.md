---
title: Comment effectuer des transformations de diffusion en continu de texte au format XML (C#)
description: Découvrez comment effectuer une transformation de streaming de texte en XML en C#, où vous diffusez le fichier texte une ligne à la fois et utilisez une requête LINQ pour traiter le fichier texte.
ms.date: 07/20/2015
ms.assetid: 9b3bd941-d0ff-4f2d-ae41-7c3b81d8fae6
ms.openlocfilehash: f933064be70d39b59cf7dbe51b4ee92e5226647a
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104748"
---
# <a name="how-to-perform-streaming-transformations-of-text-to-xml-c"></a><span data-ttu-id="2f28d-103">Comment effectuer des transformations de diffusion en continu de texte au format XML (C#)</span><span class="sxs-lookup"><span data-stu-id="2f28d-103">How to perform streaming transformations of text to XML (C#)</span></span>

<span data-ttu-id="2f28d-104">L'une des façons de traiter un fichier texte consiste à écrire une méthode d'extension qui diffuse en continu le fichier texte une ligne à la fois à l'aide de la construction `yield return`.</span><span class="sxs-lookup"><span data-stu-id="2f28d-104">One approach to processing a text file is to write an extension method that streams the text file a line at a time using the `yield return` construct.</span></span> <span data-ttu-id="2f28d-105">Vous pouvez alors écrire une requête LINQ qui traite le fichier texte de manière différée.</span><span class="sxs-lookup"><span data-stu-id="2f28d-105">You then can write a LINQ query that processes the text file in a lazy deferred fashion.</span></span> <span data-ttu-id="2f28d-106">Si vous utilisez ensuite <xref:System.Xml.Linq.XStreamingElement> pour diffuser la sortie en continu, vous pouvez créer une transformation du fichier texte en XML qui utilise une quantité minimale de mémoire, quelle que soit la taille du fichier texte source.</span><span class="sxs-lookup"><span data-stu-id="2f28d-106">If you then use <xref:System.Xml.Linq.XStreamingElement> to stream output, you then can create a transformation from the text file to XML that uses a minimal amount of memory, regardless of the size of the source text file.</span></span>

 <span data-ttu-id="2f28d-107">Il existe certains points à noter concernant les transformations de streaming.</span><span class="sxs-lookup"><span data-stu-id="2f28d-107">There are some caveats regarding streaming transformations.</span></span> <span data-ttu-id="2f28d-108">Il est préférable d'appliquer une transformation de streaming dans les situations où vous pouvez traiter l'intégralité du fichier une seule fois et si vous pouvez traiter les lignes dans l'ordre dans lequel elles apparaissent dans le document source.</span><span class="sxs-lookup"><span data-stu-id="2f28d-108">A streaming transformation is best applied in situations where you can process the entire file once, and if you can process the lines in the order that they occur in the source document.</span></span> <span data-ttu-id="2f28d-109">Si vous devez traiter le fichier à plusieurs reprises, ou si vous devez trier les lignes avant de les traiter, vous perdez une grande partie des avantages offerts par l'utilisation d'une technique de streaming.</span><span class="sxs-lookup"><span data-stu-id="2f28d-109">If you have to process the file more than once, or if you have to sort the lines before you can process them, you will lose many of the benefits of using a streaming technique.</span></span>

## <a name="example"></a><span data-ttu-id="2f28d-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="2f28d-110">Example</span></span>

 <span data-ttu-id="2f28d-111">Le fichier texte suivant, People.txt, est la source pour cet exemple.</span><span class="sxs-lookup"><span data-stu-id="2f28d-111">The following text file, People.txt, is the source for this example.</span></span>

```text
#This is a comment
1,Tai,Yee,Writer
2,Nikolay,Grachev,Programmer
3,David,Wright,Inventor
```

 <span data-ttu-id="2f28d-112">Le code suivant contient une méthode d'extension qui diffuse en continu les lignes du fichier texte de manière différée.</span><span class="sxs-lookup"><span data-stu-id="2f28d-112">The following code contains an extension method that streams the lines of the text file in a deferred fashion.</span></span>

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

 <span data-ttu-id="2f28d-113">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="2f28d-113">This example produces the following output:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="2f28d-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2f28d-114">See also</span></span>

- <xref:System.Xml.Linq.XStreamingElement>
