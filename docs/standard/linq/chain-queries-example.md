---
title: Exemples de requêtes de chaîne (C#)-LINQ to XML
description: Découvrez ce qui se passe lorsque vous chaînez deux requêtes qui utilisent toutes deux l’exécution et l’évaluation différées.
ms.date: 07/20/2015
ms.assetid: abbca162-d95e-43af-b92c-e46e6aa2540e
ms.openlocfilehash: c0bbab9061b98eda15523f8a8e64e997bde8b307
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553492"
---
# <a name="chain-queries-example-c-linq-to-xml"></a><span data-ttu-id="f2ebc-103">Exemples de requêtes de chaîne (C#) (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="f2ebc-103">Chain queries example (C#) (LINQ to XML)</span></span>

<span data-ttu-id="f2ebc-104">Cet exemple s’appuie sur l’exemple dans l' [exemple d’exécution différée](deferred-execution-example.md) et montre ce qui se passe lorsque vous chaînez deux requêtes qui utilisent toutes deux l’exécution différée et l’évaluation différée.</span><span class="sxs-lookup"><span data-stu-id="f2ebc-104">This example builds on the example in [Deferred execution example](deferred-execution-example.md) and shows what happens when you chain together two queries that both use deferred execution and lazy evaluation.</span></span>

## <a name="example-add-a-second-extension-method-that-uses-yield-return-to-defer-execution"></a><span data-ttu-id="f2ebc-105">Exemple : ajouter une deuxième méthode d’extension qui utilise `yield return` pour différer l’exécution</span><span class="sxs-lookup"><span data-stu-id="f2ebc-105">Example: Add a second extension method that uses `yield return` to defer execution</span></span>

<span data-ttu-id="f2ebc-106">Dans cet exemple, une autre méthode d’extension est introduite, `AppendString` , qui ajoute une chaîne spécifiée à chaque chaîne de la collection source, puis génère la chaîne modifiée.</span><span class="sxs-lookup"><span data-stu-id="f2ebc-106">In this example, another extension method is introduced, `AppendString`, which appends a specified string onto every string in the source collection, and then yields the changed string.</span></span>

```csharp
public static class LocalExtensions
{
    public static IEnumerable<string>
      ConvertCollectionToUpperCase(this IEnumerable<string> source)
    {
        foreach (string str in source)
        {
            Console.WriteLine("ToUpper: source >{0}<", str);
            yield return str.ToUpper();
        }
    }

    public static IEnumerable<string>
      AppendString(this IEnumerable<string> source, string stringToAppend)
    {
        foreach (string str in source)
        {
            Console.WriteLine("AppendString: source >{0}<", str);
            yield return str + stringToAppend;
        }
    }
}

class Program
{
    static void Main(string[] args)
    {
        string[] stringArray = { "abc", "def", "ghi" };

        IEnumerable<string> q1 =
            from s in stringArray.ConvertCollectionToUpperCase()
            select s;

        IEnumerable<string> q2 =
            from s in q1.AppendString("!!!")
            select s;

        foreach (string str in q2)
        {
            Console.WriteLine("Main: str >{0}<", str);
            Console.WriteLine();
        }
    }
}
```

 <span data-ttu-id="f2ebc-107">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="f2ebc-107">This example produces the following output:</span></span>

```output
ToUpper: source >abc<
AppendString: source >ABC<
Main: str >ABC!!!<

ToUpper: source >def<
AppendString: source >DEF<
Main: str >DEF!!!<

ToUpper: source >ghi<
AppendString: source >GHI<
Main: str >GHI!!!<
```

<span data-ttu-id="f2ebc-108">Dans cet exemple, vous pouvez constater que chaque méthode d'extension opère l'une après l'autre pour chaque élément de la collection source.</span><span class="sxs-lookup"><span data-stu-id="f2ebc-108">In this example, you can see that each extension method operates one at a time for each item in the source collection.</span></span>

<span data-ttu-id="f2ebc-109">Il doit être clair, au vu de cet exemple, que bien que nous ayons chaîné des requêtes qui produisent des collections, aucune collection intermédiaire n'est matérialisée.</span><span class="sxs-lookup"><span data-stu-id="f2ebc-109">What should be clear from this example is that even though we have chained together queries that yield collections, no intermediate collections are materialized.</span></span> <span data-ttu-id="f2ebc-110">Au lieu de cela, chaque élément est passé d'une méthode différée à la suivante.</span><span class="sxs-lookup"><span data-stu-id="f2ebc-110">Instead, each item is passed from one lazy method to the next.</span></span> <span data-ttu-id="f2ebc-111">L'encombrement mémoire est par conséquent beaucoup plus faible par rapport à une approche qui consisterait à prendre d'abord un tableau de chaînes, à créer un deuxième tableau de chaînes converties en majuscules, puis à créer un troisième tableau de chaînes où des points d'exclamations sont ajoutés à chaque chaîne.</span><span class="sxs-lookup"><span data-stu-id="f2ebc-111">This results in a much smaller memory footprint than an approach that would first take one array of strings, then create a second array of strings that have been converted to uppercase, and finally create a third array of strings where each string has the exclamation points appended to it.</span></span>

<span data-ttu-id="f2ebc-112">L’article suivant de ce didacticiel illustre la matérialisation intermédiaire :</span><span class="sxs-lookup"><span data-stu-id="f2ebc-112">The next article in this tutorial illustrates intermediate materialization:</span></span>

- [<span data-ttu-id="f2ebc-113">Matérialisation intermédiaire (C#)</span><span class="sxs-lookup"><span data-stu-id="f2ebc-113">Intermediate materialization (C#)</span></span>](intermediate-materialization.md)

## <a name="see-also"></a><span data-ttu-id="f2ebc-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f2ebc-114">See also</span></span>

- [<span data-ttu-id="f2ebc-115">Exécution différée et évaluation différée</span><span class="sxs-lookup"><span data-stu-id="f2ebc-115">Deferred execution and lazy evaluation</span></span>](deferred-execution-lazy-evaluation.md)
