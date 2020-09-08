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
# <a name="how-to-perform-streaming-transformations-of-text-to-xml-in-c-linq-to-xml"></a>Comment effectuer des transformations de diffusion en continu de texte en XML en C# (LINQ to XML)

Vous pouvez utiliser une méthode d’extension qui libère une ligne à la fois pour diffuser un fichier texte à des fins de traitement. Cette technique permet de réduire les besoins en mémoire par rapport aux techniques qui chargent le fichier entier, puis le traitent.

La méthode d’extension peut fournir la ligne à l’aide de la `yield return` construction. Une requête LINQ peut traiter le flux de manière différée. Si vous utilisez <xref:System.Xml.Linq.XStreamingElement> pour diffuser la sortie, vous pouvez créer une transformation du fichier texte en XML qui utilise une quantité minimale de mémoire, quelle que soit la taille du fichier texte source.

> [!NOTE]
> La technique est mieux appliquée dans les situations où vous pouvez traiter l’intégralité du fichier une seule fois, en utilisant les lignes dans l’ordre dans le document source. Le traitement du fichier plusieurs fois, ou le tri avant le traitement, réduit les avantages en matière de performances d’une technique de diffusion en continu.

## <a name="example-use-an-extension-method-to-stream-text"></a>Exemple utilise une méthode d’extension pour diffuser du texte en continu

L’exemple utilise le fichier texte suivant, People.txt, comme source :

```text
#This is a comment
1,Tai,Yee,Writer
2,Nikolay,Grachev,Programmer
3,David,Wright,Inventor
```

Dans le code de l’exemple, la méthode d’extension `Lines` fournit le texte une ligne à la fois :

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

L'exemple produit la sortie suivante :

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

## <a name="see-also"></a>Voir aussi

- <xref:System.Xml.Linq.XStreamingElement>
