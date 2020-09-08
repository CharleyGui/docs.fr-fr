---
title: Exemple d’exécution différée-LINQ to XML
description: Découvrez comment l’exécution et l’évaluation différées affectent l’exécution de vos requêtes LINQ to XML.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 50f4fbac-81fe-4f26-aedf-506e21419b19
ms.openlocfilehash: 59784db895211aecbd263b5ee050734ecd16fa4b
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553471"
---
# <a name="deferred-execution-example-linq-to-xml"></a><span data-ttu-id="2ac77-103">Exemple d’exécution différée (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="2ac77-103">Deferred execution example (LINQ to XML)</span></span>

<span data-ttu-id="2ac77-104">Cet article montre comment l’exécution et l’évaluation différées affectent l’exécution de vos requêtes LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="2ac77-104">This article shows how deferred execution and lazy evaluation affect the execution of your LINQ to XML queries.</span></span>

## <a name="example-use-the-yield-return-construct-in-an-extension-method-to-defer-execution"></a><span data-ttu-id="2ac77-105">Exemple : utiliser la `yield return` construction dans une méthode d’extension pour différer l’exécution</span><span class="sxs-lookup"><span data-stu-id="2ac77-105">Example: Use the `yield return` construct in an extension method to defer execution</span></span>

<span data-ttu-id="2ac77-106">L'exemple suivant illustre l'ordre d'exécution lors de l'utilisation d'une méthode d'extension qui utilise l'exécution différée.</span><span class="sxs-lookup"><span data-stu-id="2ac77-106">The following example shows the order of execution when using an extension method that uses deferred execution.</span></span> <span data-ttu-id="2ac77-107">L'exemple déclare un tableau de trois chaînes.</span><span class="sxs-lookup"><span data-stu-id="2ac77-107">The example declares an array of three strings.</span></span> <span data-ttu-id="2ac77-108">Il itère ensuite au sein de la collection retournée par `ConvertCollectionToUpperCase`.</span><span class="sxs-lookup"><span data-stu-id="2ac77-108">It then iterates through the collection returned by `ConvertCollectionToUpperCase`.</span></span>

```csharp
public static class LocalExtensions
{
    public static IEnumerable<string>
      ConvertCollectionToUpperCase(this IEnumerable<string> source)
    {
        foreach (string str in source)
        {
            Console.WriteLine("ToUpper: source {0}", str);
            yield return str.ToUpper();
        }
    }
}

class Program
{
    static void Main(string[] args)
    {
        string[] stringArray = { "abc", "def", "ghi" };

        var q = from str in stringArray.ConvertCollectionToUpperCase()
                select str;

        foreach (string str in q)
            Console.WriteLine("Main: str {0}", str);
    }
}
```

```vb
Imports System.Runtime.CompilerServices

Module Module1

    <Extension()>
    Private Iterator Function ConvertCollectionToUpperCase(
    ByVal source As IEnumerable(Of String)) _
    As IEnumerable(Of String)
        For Each str As String In source
            Console.WriteLine("ToUpper: source {0}", str)
            Yield str.ToUpper()
        Next
    End Function

    Sub Main()
        Dim stringArray = New String() {"abc", "def", "ghi"}

        Dim q = From str In stringArray.ConvertCollectionToUpperCase()
                Select str

        For Each Str As String In q
            Console.WriteLine("Main: str {0}", Str)
        Next
    End Sub

End Module
```

<span data-ttu-id="2ac77-109">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="2ac77-109">This example produces the following output:</span></span>

```output
ToUpper: source abc
Main: str ABC
ToUpper: source def
Main: str DEF
ToUpper: source ghi
Main: str GHI
```

<span data-ttu-id="2ac77-110">Notez que lors de l'itération de la collection retournée par `ConvertCollectionToUpperCase`, chaque élément est récupéré du tableau de chaînes source et converti en majuscules avant que l'élément suivant ne soit récupéré du tableau de chaînes source.</span><span class="sxs-lookup"><span data-stu-id="2ac77-110">Notice that when iterating through the collection returned by `ConvertCollectionToUpperCase`, each item is retrieved from the source string array and converted to uppercase before the next item is retrieved from the source string array.</span></span>

<span data-ttu-id="2ac77-111">Vous pouvez voir que l’intégralité du tableau de chaînes n’est pas convertie en majuscules avant que chaque élément de la collection retournée soit traité dans la `foreach` boucle de `Main` .</span><span class="sxs-lookup"><span data-stu-id="2ac77-111">You can see that the entire array of strings isn't converted to uppercase before each item in the returned collection is processed in the `foreach` loop in `Main`.</span></span>

## <a name="see-also"></a><span data-ttu-id="2ac77-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2ac77-112">See also</span></span>

- [<span data-ttu-id="2ac77-113">Exécution différée et évaluation différée</span><span class="sxs-lookup"><span data-stu-id="2ac77-113">Deferred execution and lazy evaluation</span></span>](deferred-execution-lazy-evaluation.md)
- [<span data-ttu-id="2ac77-114">Didacticiel : chaînes de requêtes (C#)</span><span class="sxs-lookup"><span data-stu-id="2ac77-114">Tutorial: Chain queries together (C#)</span></span>](chain-queries-example.md)
