---
title: Chaîner les opérateurs de requête standard (C#)-LINQ to XML
description: Découvrez comment chaîner des opérateurs de requête.
ms.date: 07/20/2015
dev_langs:
- csharp
ms.assetid: 66f2b0a9-2c23-4735-988e-bbc9dfb55c7b
ms.openlocfilehash: ed3ca44c853ebbeee690cb31232a13e35b383d1b
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552376"
---
# <a name="chain-standard-query-operators-together-c-linq-to-xml"></a><span data-ttu-id="60fe9-103">Chaîner des opérateurs de requête standard (C#) (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="60fe9-103">Chain standard query operators together (C#) (LINQ to XML)</span></span>

<span data-ttu-id="60fe9-104">Les opérateurs de requête standard peuvent être chaînés ensemble.</span><span class="sxs-lookup"><span data-stu-id="60fe9-104">The standard query operators can be chained together.</span></span> <span data-ttu-id="60fe9-105">Par exemple, vous pouvez lancer l' <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> opérateur (appelé par la `where` clause) et il fonctionne de manière différée ; autrement dit, aucun résultat intermédiaire n’est matérialisé par ce dernier.</span><span class="sxs-lookup"><span data-stu-id="60fe9-105">For example, you can interject the <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> operator (invoked by the `where` clause), and it operates in a lazy fashion; that is, no intermediate results are materialized by it.</span></span>

## <a name="example-interject-a-where-clause"></a><span data-ttu-id="60fe9-106">Exemple : lancer une clause WHERE</span><span class="sxs-lookup"><span data-stu-id="60fe9-106">Example: Interject a where clause</span></span>

<span data-ttu-id="60fe9-107">Dans cet exemple, la méthode <xref:System.Linq.Enumerable.Where%2A> est appelée avant `ConvertCollectionToUpperCase`.</span><span class="sxs-lookup"><span data-stu-id="60fe9-107">In this example, the <xref:System.Linq.Enumerable.Where%2A> method is called before calling `ConvertCollectionToUpperCase`.</span></span> <span data-ttu-id="60fe9-108">La méthode <xref:System.Linq.Enumerable.Where%2A> opère presque exactement de la même façon que les méthodes différées utilisées dans les exemples précédents de ce didacticiel, `ConvertCollectionToUpperCase` et `AppendString`.</span><span class="sxs-lookup"><span data-stu-id="60fe9-108">The <xref:System.Linq.Enumerable.Where%2A> method operates in almost exactly the same way as the lazy methods used in previous examples in this tutorial, `ConvertCollectionToUpperCase` and `AppendString`.</span></span>

<span data-ttu-id="60fe9-109">L’une des différences est que dans ce cas, la méthode itère au sein de <xref:System.Linq.Enumerable.Where%2A> sa collection source, détermine que le premier élément ne passe pas le prédicat, puis obtient l’élément suivant qui passe.</span><span class="sxs-lookup"><span data-stu-id="60fe9-109">One difference is that in this case, the <xref:System.Linq.Enumerable.Where%2A> method iterates through its source collection, determines that the first item doesn't pass the predicate, and then gets the next item, which does pass.</span></span> <span data-ttu-id="60fe9-110">Elle génère ensuite le deuxième élément.</span><span class="sxs-lookup"><span data-stu-id="60fe9-110">It then yields the second item.</span></span>

<span data-ttu-id="60fe9-111">Toutefois, l’idée de base est la même : les collections intermédiaires ne sont pas matérialisées, sauf si elles doivent l’être.</span><span class="sxs-lookup"><span data-stu-id="60fe9-111">However, the basic idea is the same: intermediate collections aren't materialized unless they have to be.</span></span>

<span data-ttu-id="60fe9-112">Lorsque des expressions de requête sont utilisées, elles sont converties en appels aux opérateurs de requête standard, et les mêmes principes s’appliquent.</span><span class="sxs-lookup"><span data-stu-id="60fe9-112">When query expressions are used, they're converted to calls to the standard query operators, and the same principles apply.</span></span>

<span data-ttu-id="60fe9-113">Tous les exemples de cette section qui interrogent des documents Office Open XML utilisent le même principe.</span><span class="sxs-lookup"><span data-stu-id="60fe9-113">All of the examples in this section that are querying Office Open XML documents use the same principle.</span></span> <span data-ttu-id="60fe9-114">L’exécution et l’évaluation différées sont des concepts fondamentaux que vous devez comprendre pour utiliser LINQ et LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="60fe9-114">Deferred execution and lazy evaluation are some of the fundamental concepts that you must understand to use LINQ, and LINQ to XML, effectively.</span></span>

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
            where s.CompareTo("D") >= 0
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

<span data-ttu-id="60fe9-115">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="60fe9-115">This example produces the following output:</span></span>

```output
ToUpper: source >abc<
ToUpper: source >def<
AppendString: source >DEF<
Main: str >DEF!!!<

ToUpper: source >ghi<
AppendString: source >GHI<
Main: str >GHI!!!<
```

<span data-ttu-id="60fe9-116">Il s’agit du dernier article du didacticiel [: chaînage de requêtes (C#)](chain-queries-example.md) .</span><span class="sxs-lookup"><span data-stu-id="60fe9-116">This is the final article in the [Tutorial: Chaining Queries Together (C#)](chain-queries-example.md) tutorial.</span></span>
