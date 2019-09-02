---
title: Chaînage d’opérateurs de requête standard (C#)
ms.date: 07/20/2015
ms.assetid: 66f2b0a9-2c23-4735-988e-bbc9dfb55c7b
ms.openlocfilehash: 37df654b2bfdcc135460e5ded2ceec1eca33b35a
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204207"
---
# <a name="chaining-standard-query-operators-together-c"></a><span data-ttu-id="55d93-102">Chaînage d’opérateurs de requête standard (C#)</span><span class="sxs-lookup"><span data-stu-id="55d93-102">Chaining Standard Query Operators Together (C#)</span></span>
<span data-ttu-id="55d93-103">C’est la dernière rubrique du [Tutoriel : Chaînage de requêtes (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="55d93-103">This is the final topic in the [Tutorial: Chaining Queries Together (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md) tutorial.</span></span>  
  
 <span data-ttu-id="55d93-104">Les opérateurs de requête standard peuvent également être chaînés ensemble.</span><span class="sxs-lookup"><span data-stu-id="55d93-104">The standard query operators can also be chained together.</span></span> <span data-ttu-id="55d93-105">Par exemple, vous pouvez lancer l'opérateur <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> et il fonctionne également de manière différée.</span><span class="sxs-lookup"><span data-stu-id="55d93-105">For example, you can interject the <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> operator, and it also operates in a lazy fashion.</span></span> <span data-ttu-id="55d93-106">Aucun résultat intermédiaire n'est matérialisé par l'opérateur.</span><span class="sxs-lookup"><span data-stu-id="55d93-106">No intermediate results are materialized by it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="55d93-107">Exemples</span><span class="sxs-lookup"><span data-stu-id="55d93-107">Example</span></span>  
 <span data-ttu-id="55d93-108">Dans cet exemple, la méthode <xref:System.Linq.Enumerable.Where%2A> est appelée avant `ConvertCollectionToUpperCase`.</span><span class="sxs-lookup"><span data-stu-id="55d93-108">In this example, the <xref:System.Linq.Enumerable.Where%2A> method is called before calling `ConvertCollectionToUpperCase`.</span></span> <span data-ttu-id="55d93-109">La méthode <xref:System.Linq.Enumerable.Where%2A> opère presque exactement de la même façon que les méthodes différées utilisées dans les exemples précédents de ce didacticiel, `ConvertCollectionToUpperCase` et `AppendString`.</span><span class="sxs-lookup"><span data-stu-id="55d93-109">The <xref:System.Linq.Enumerable.Where%2A> method operates in almost exactly the same way as the lazy methods used in previous examples in this tutorial, `ConvertCollectionToUpperCase` and `AppendString`.</span></span>  
  
 <span data-ttu-id="55d93-110">Il existe toutefois une différence : dans le cas présent, la méthode <xref:System.Linq.Enumerable.Where%2A> itère au sein de sa collection source, détermine que le premier élément ne passe pas le prédicat et obtient l'élément suivant qui, lui, passe.</span><span class="sxs-lookup"><span data-stu-id="55d93-110">One difference is that in this case, the <xref:System.Linq.Enumerable.Where%2A> method iterates through its source collection, determines that the first item does not pass the predicate, and then gets the next item, which does pass.</span></span> <span data-ttu-id="55d93-111">Elle génère ensuite le deuxième élément.</span><span class="sxs-lookup"><span data-stu-id="55d93-111">It then yields the second item.</span></span>  
  
 <span data-ttu-id="55d93-112">L’idée de base est néanmoins la même : les collections intermédiaires sont matérialisées uniquement si cela est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="55d93-112">However, the basic idea is the same: Intermediate collections are not materialized unless they have to be.</span></span>  
  
 <span data-ttu-id="55d93-113">Lorsque des expressions de requêtes sont utilisées, elles sont converties en appels aux opérateurs de requête standard et les mêmes principes sont applicables.</span><span class="sxs-lookup"><span data-stu-id="55d93-113">When query expressions are used, they are converted to calls to the standard query operators, and the same principles apply.</span></span>  
  
 <span data-ttu-id="55d93-114">Tous les exemples de cette section qui interrogent des documents Office Open XML utilisent le même principe.</span><span class="sxs-lookup"><span data-stu-id="55d93-114">All of the examples in this section that are querying Office Open XML documents use the same principle.</span></span> <span data-ttu-id="55d93-115">L'exécution et l'évaluation différées sont deux concepts fondamentaux que vous devez comprendre pour utiliser LINQ (et LINQ to XML) de manière optimale.</span><span class="sxs-lookup"><span data-stu-id="55d93-115">Deferred execution and lazy evaluation are some of the fundamental concepts that you must understand  to use LINQ (and LINQ to XML) effectively.</span></span>  
  
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
  
 <span data-ttu-id="55d93-116">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="55d93-116">This example produces the following output:</span></span>  
  
```output  
ToUpper: source >abc<  
ToUpper: source >def<  
AppendString: source >DEF<  
Main: str >DEF!!!<  
  
ToUpper: source >ghi<  
AppendString: source >GHI<  
Main: str >GHI!!!<  
```  
