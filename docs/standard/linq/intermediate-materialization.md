---
title: Matérialisation intermédiaire (C#)
description: Découvrez comment l’utilisation de certains opérateurs de requête standard peut entraîner la matérialisation des collections dans une requête et modifier radicalement la mémoire et le profil de performances de votre application.
ms.date: 07/20/2015
ms.assetid: 7922d38f-5044-41cf-8e17-7173d6553a5e
ms.openlocfilehash: 8dca4bb29886973762351049d06bcf5d3ba352db
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552413"
---
# <a name="intermediate-materialization-c"></a><span data-ttu-id="34808-103">Matérialisation intermédiaire (C#)</span><span class="sxs-lookup"><span data-stu-id="34808-103">Intermediate materialization (C#)</span></span>

<span data-ttu-id="34808-104">Si vous n’êtes pas prudent, vous pouvez, dans certains cas, modifier radicalement le profil de mémoire et de performances de votre application en provoquant la matérialisation prématurée de collections dans vos requêtes.</span><span class="sxs-lookup"><span data-stu-id="34808-104">If you're not careful you can, in some situations, drastically alter the memory and performance profile of your application by causing premature materialization of collections in your queries.</span></span> <span data-ttu-id="34808-105">Certains opérateurs de requête standard provoquent la matérialisation de leur collection source avant de générer un seul élément.</span><span class="sxs-lookup"><span data-stu-id="34808-105">Some standard query operators cause materialization of their source collection before yielding a single element.</span></span> <span data-ttu-id="34808-106">Par exemple, <xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType> itère au sein de l'ensemble de sa collection source, trie tous les éléments, puis génère le premier élément.</span><span class="sxs-lookup"><span data-stu-id="34808-106">For example, <xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType> first iterates through its entire source collection, then sorts all items, and then finally yields the first item.</span></span> <span data-ttu-id="34808-107">Cela signifie qu’il est coûteux d’avoir le premier élément d’une collection ordonnée ; chaque élément par la suite n’est pas onéreux.</span><span class="sxs-lookup"><span data-stu-id="34808-107">This means that it's expensive to get the first item of an ordered collection; each item thereafter isn't expensive.</span></span> <span data-ttu-id="34808-108">Tout cela est logique : il serait impossible pour cet opérateur de requête de faire autrement.</span><span class="sxs-lookup"><span data-stu-id="34808-108">This makes sense: It would be impossible for that query operator to do otherwise.</span></span>

## <a name="example-add-a-method-that-calls-tolist-causing-materialization"></a><span data-ttu-id="34808-109">Exemple : ajouter une méthode qui appelle `ToList` , provoquant la matérialisation</span><span class="sxs-lookup"><span data-stu-id="34808-109">Example: Add a method that calls `ToList`, causing materialization</span></span>

<span data-ttu-id="34808-110">Cet exemple modifie l’exemple dans [exemples de requêtes de chaîne (C#)](chain-queries-example.md): la `AppendString` méthode est modifiée pour appeler <xref:System.Linq.Enumerable.ToList%2A> avant d’itérer au sein de la source, ce qui provoque la matérialisation.</span><span class="sxs-lookup"><span data-stu-id="34808-110">This example alters the example in [Chain queries example (C#)](chain-queries-example.md): the `AppendString` method is changed to call <xref:System.Linq.Enumerable.ToList%2A> before iterating through the source, which causes materialization.</span></span>

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
        // the following statement materializes the source collection in a List<T>
        // before iterating through it
        foreach (string str in source.ToList())
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

 <span data-ttu-id="34808-111">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="34808-111">This example produces the following output:</span></span>

```output
ToUpper: source >abc<
ToUpper: source >def<
ToUpper: source >ghi<
AppendString: source >ABC<
Main: str >ABC!!!<

AppendString: source >DEF<
Main: str >DEF!!!<

AppendString: source >GHI<
Main: str >GHI!!!<
```

<span data-ttu-id="34808-112">Dans cet exemple, on observe que l'appel de <xref:System.Linq.Enumerable.ToList%2A> force `AppendString` à parcourir l'ensemble de sa source avant de générer le premier élément.</span><span class="sxs-lookup"><span data-stu-id="34808-112">In this example, you can see that the call to <xref:System.Linq.Enumerable.ToList%2A> causes `AppendString` to enumerate its entire source before yielding the first item.</span></span> <span data-ttu-id="34808-113">Si la source est un grand tableau, cela modifie considérablement le profil de mémoire de l'application.</span><span class="sxs-lookup"><span data-stu-id="34808-113">If the source were a large array, this would significantly alter the memory profile of the application.</span></span>

<span data-ttu-id="34808-114">Les opérateurs de requête standard peuvent également être chaînés, comme indiqué dans le dernier article de ce didacticiel :</span><span class="sxs-lookup"><span data-stu-id="34808-114">Standard query operators can also be chained together as shown in the final article in this tutorial:</span></span>

- [<span data-ttu-id="34808-115">Chaîner des opérateurs de requête standard (C#)</span><span class="sxs-lookup"><span data-stu-id="34808-115">Chain standard query operators together (C#)</span></span>](chain-standard-query-operators-together.md)

## <a name="see-also"></a><span data-ttu-id="34808-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="34808-116">See also</span></span>

- [<span data-ttu-id="34808-117">Exécution différée et évaluation différée</span><span class="sxs-lookup"><span data-stu-id="34808-117">Deferred execution and lazy evaluation</span></span>](deferred-execution-lazy-evaluation.md)
