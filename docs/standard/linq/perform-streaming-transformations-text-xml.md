---
title: Comment effectuer des transformations de diffusion en continu de texte en XML en C#-LINQ to XML
description: Vous pouvez utiliser une méthode d’extension qui libère une ligne à la fois pour diffuser un fichier texte à des fins de traitement. Cette technique permet de réduire les besoins en mémoire par rapport aux techniques qui chargent le fichier entier, puis le traitent.
ms.date: 07/20/2015
dev_langs:
- csharp
ms.assetid: 9b3bd941-d0ff-4f2d-ae41-7c3b81d8fae6
ms.openlocfilehash: 8e0d710d7cbc6de8cc60721c211376a82b6c29fc
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553784"
---
# <a name="how-to-perform-streaming-transformations-of-text-to-xml-in-c-linq-to-xml"></a><span data-ttu-id="a5075-104">Comment effectuer des transformations de diffusion en continu de texte en XML en C# (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="a5075-104">How to perform streaming transformations of text to XML in C# (LINQ to XML)</span></span>

<span data-ttu-id="a5075-105">Vous pouvez utiliser une méthode d’extension qui libère une ligne à la fois pour diffuser un fichier texte à des fins de traitement.</span><span class="sxs-lookup"><span data-stu-id="a5075-105">You can use an extension method that releases a line at a time to stream a text file for processing.</span></span> <span data-ttu-id="a5075-106">Cette technique permet de réduire les besoins en mémoire par rapport aux techniques qui chargent le fichier entier, puis le traitent.</span><span class="sxs-lookup"><span data-stu-id="a5075-106">This technique reduces memory requirements compared to techniques which load the entire file and then process it.</span></span>

<span data-ttu-id="a5075-107">La méthode d’extension peut fournir la ligne à l’aide de la `yield return` construction.</span><span class="sxs-lookup"><span data-stu-id="a5075-107">The extension method can provide the line using the `yield return` construct.</span></span> <span data-ttu-id="a5075-108">Une requête LINQ peut traiter le flux de manière différée.</span><span class="sxs-lookup"><span data-stu-id="a5075-108">A LINQ query can process the stream in a lazy deferred fashion.</span></span> <span data-ttu-id="a5075-109">Si vous utilisez <xref:System.Xml.Linq.XStreamingElement> pour diffuser la sortie, vous pouvez créer une transformation du fichier texte en XML qui utilise une quantité minimale de mémoire, quelle que soit la taille du fichier texte source.</span><span class="sxs-lookup"><span data-stu-id="a5075-109">If you use <xref:System.Xml.Linq.XStreamingElement> to stream output, you can create a transformation from the text file to XML that uses a minimal amount of memory, regardless of the size of the source text file.</span></span>

> [!NOTE]
> <span data-ttu-id="a5075-110">La technique est mieux appliquée dans les situations où vous pouvez traiter l’intégralité du fichier une seule fois, en utilisant les lignes dans l’ordre dans le document source.</span><span class="sxs-lookup"><span data-stu-id="a5075-110">The technique is best applied in situations in which you can process the entire file once, taking the lines in order from the source document.</span></span> <span data-ttu-id="a5075-111">Le traitement du fichier plusieurs fois, ou le tri avant le traitement, réduit les avantages en matière de performances d’une technique de diffusion en continu.</span><span class="sxs-lookup"><span data-stu-id="a5075-111">Processing the file more than once, or sorting before processing, reduces the performance benefits of a streaming technique.</span></span>

## <a name="example-use-an-extension-method-to-stream-text"></a><span data-ttu-id="a5075-112">Exemple utilise une méthode d’extension pour diffuser du texte en continu</span><span class="sxs-lookup"><span data-stu-id="a5075-112">Example Use an extension method to stream text</span></span>

<span data-ttu-id="a5075-113">L’exemple utilise le fichier texte suivant, People.txt, comme source :</span><span class="sxs-lookup"><span data-stu-id="a5075-113">The example uses the following text file, People.txt, as its source:</span></span>

```text
#This is a comment
1,Tai,Yee,Writer
2,Nikolay,Grachev,Programmer
3,David,Wright,Inventor
```

<span data-ttu-id="a5075-114">Dans le code de l’exemple, la méthode d’extension `Lines` fournit le texte une ligne à la fois :</span><span class="sxs-lookup"><span data-stu-id="a5075-114">In the code for the example, extension method `Lines` provides the text a line at a time:</span></span>

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

<span data-ttu-id="a5075-115">L'exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="a5075-115">The example produces the following output:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="a5075-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a5075-116">See also</span></span>

- <xref:System.Xml.Linq.XStreamingElement>
