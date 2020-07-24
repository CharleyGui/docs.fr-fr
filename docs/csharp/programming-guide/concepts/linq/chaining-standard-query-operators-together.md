---
title: Chaînage d’opérateurs de requête standard (C#)
description: Cet exemple montre comment les opérateurs de requête standard peuvent également être chaînés en C#. La requête ne matérialise pas les résultats intermédiaires.
ms.date: 07/20/2015
ms.assetid: 66f2b0a9-2c23-4735-988e-bbc9dfb55c7b
ms.openlocfilehash: 41a7e4c7910c783d07181fe16254b0cac6902794
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104071"
---
# <a name="chaining-standard-query-operators-together-c"></a><span data-ttu-id="ec996-104">Chaînage d’opérateurs de requête standard (C#)</span><span class="sxs-lookup"><span data-stu-id="ec996-104">Chaining Standard Query Operators Together (C#)</span></span>
<span data-ttu-id="ec996-105">Il s’agit de la dernière rubrique du [Didacticiel : chaînage de requêtes (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="ec996-105">This is the final topic in the [Tutorial: Chaining Queries Together (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md) tutorial.</span></span>  
  
 <span data-ttu-id="ec996-106">Les opérateurs de requête standard peuvent également être chaînés ensemble.</span><span class="sxs-lookup"><span data-stu-id="ec996-106">The standard query operators can also be chained together.</span></span> <span data-ttu-id="ec996-107">Par exemple, vous pouvez lancer l'opérateur <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> et il fonctionne également de manière différée.</span><span class="sxs-lookup"><span data-stu-id="ec996-107">For example, you can interject the <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> operator, and it also operates in a lazy fashion.</span></span> <span data-ttu-id="ec996-108">Aucun résultat intermédiaire n'est matérialisé par l'opérateur.</span><span class="sxs-lookup"><span data-stu-id="ec996-108">No intermediate results are materialized by it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ec996-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="ec996-109">Example</span></span>  
 <span data-ttu-id="ec996-110">Dans cet exemple, la méthode <xref:System.Linq.Enumerable.Where%2A> est appelée avant `ConvertCollectionToUpperCase`.</span><span class="sxs-lookup"><span data-stu-id="ec996-110">In this example, the <xref:System.Linq.Enumerable.Where%2A> method is called before calling `ConvertCollectionToUpperCase`.</span></span> <span data-ttu-id="ec996-111">La méthode <xref:System.Linq.Enumerable.Where%2A> opère presque exactement de la même façon que les méthodes différées utilisées dans les exemples précédents de ce didacticiel, `ConvertCollectionToUpperCase` et `AppendString`.</span><span class="sxs-lookup"><span data-stu-id="ec996-111">The <xref:System.Linq.Enumerable.Where%2A> method operates in almost exactly the same way as the lazy methods used in previous examples in this tutorial, `ConvertCollectionToUpperCase` and `AppendString`.</span></span>  
  
 <span data-ttu-id="ec996-112">Il existe toutefois une différence : dans le cas présent, la méthode <xref:System.Linq.Enumerable.Where%2A> itère au sein de sa collection source, détermine que le premier élément ne passe pas le prédicat et obtient l'élément suivant qui, lui, passe.</span><span class="sxs-lookup"><span data-stu-id="ec996-112">One difference is that in this case, the <xref:System.Linq.Enumerable.Where%2A> method iterates through its source collection, determines that the first item does not pass the predicate, and then gets the next item, which does pass.</span></span> <span data-ttu-id="ec996-113">Elle génère ensuite le deuxième élément.</span><span class="sxs-lookup"><span data-stu-id="ec996-113">It then yields the second item.</span></span>  
  
 <span data-ttu-id="ec996-114">L'idée de base est néanmoins identique : les collections intermédiaires ne sont matérialisées que si elles doivent l'être.</span><span class="sxs-lookup"><span data-stu-id="ec996-114">However, the basic idea is the same: Intermediate collections are not materialized unless they have to be.</span></span>  
  
 <span data-ttu-id="ec996-115">Lorsque des expressions de requêtes sont utilisées, elles sont converties en appels aux opérateurs de requête standard et les mêmes principes sont applicables.</span><span class="sxs-lookup"><span data-stu-id="ec996-115">When query expressions are used, they are converted to calls to the standard query operators, and the same principles apply.</span></span>  
  
 <span data-ttu-id="ec996-116">Tous les exemples de cette section qui interrogent des documents Office Open XML utilisent le même principe.</span><span class="sxs-lookup"><span data-stu-id="ec996-116">All of the examples in this section that are querying Office Open XML documents use the same principle.</span></span> <span data-ttu-id="ec996-117">L'exécution et l'évaluation différées sont deux concepts fondamentaux que vous devez comprendre pour utiliser LINQ (et LINQ to XML) de manière optimale.</span><span class="sxs-lookup"><span data-stu-id="ec996-117">Deferred execution and lazy evaluation are some of the fundamental concepts that you must understand  to use LINQ (and LINQ to XML) effectively.</span></span>  
  
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
  
 <span data-ttu-id="ec996-118">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="ec996-118">This example produces the following output:</span></span>  
  
```output  
ToUpper: source >abc<  
ToUpper: source >def<  
AppendString: source >DEF<  
Main: str >DEF!!!<  
  
ToUpper: source >ghi<  
AppendString: source >GHI<  
Main: str >GHI!!!<  
```  
