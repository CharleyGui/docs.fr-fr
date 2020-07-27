---
title: Matérialisation intermédiaire (C#)
description: Cet exemple C# illustre la matérialisation intermédiaire, où une requête amène AppendString à énumérer la totalité de sa source avant de générer le premier élément.
ms.date: 07/20/2015
ms.assetid: 7922d38f-5044-41cf-8e17-7173d6553a5e
ms.openlocfilehash: 30951aaeea261efbd414205bcc54b63106324344
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165715"
---
# <a name="intermediate-materialization-c"></a><span data-ttu-id="19d53-103">Matérialisation intermédiaire (C#)</span><span class="sxs-lookup"><span data-stu-id="19d53-103">Intermediate Materialization (C#)</span></span>
<span data-ttu-id="19d53-104">Si vous n’y prenez pas garde, dans certaines situations vous risquez de modifier de manière significative le profil de mémoire et de performances de votre application en provoquant la matérialisation prématurée de collections dans vos requêtes.</span><span class="sxs-lookup"><span data-stu-id="19d53-104">If you are not careful, in some situations you can drastically alter the memory and performance profile of your application by causing premature materialization of collections in your queries.</span></span> <span data-ttu-id="19d53-105">Certains opérateurs de requête standard provoquent la matérialisation de leur collection source avant de générer un seul élément.</span><span class="sxs-lookup"><span data-stu-id="19d53-105">Some standard query operators cause materialization of their source collection before yielding a single element.</span></span> <span data-ttu-id="19d53-106">Par exemple, <xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType> itère au sein de l'ensemble de sa collection source, trie tous les éléments, puis génère le premier élément.</span><span class="sxs-lookup"><span data-stu-id="19d53-106">For example, <xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType> first iterates through its entire source collection, then sorts all items, and then finally yields the first item.</span></span> <span data-ttu-id="19d53-107">Cela signifie qu'il est coûteux d'obtenir le premier élément d'une collection ordonnée ; chaque élément ultérieur a un faible coût.</span><span class="sxs-lookup"><span data-stu-id="19d53-107">This means that it is expensive to get the first item of an ordered collection; each item thereafter is not expensive.</span></span> <span data-ttu-id="19d53-108">Tout cela est logique : il serait impossible pour cet opérateur de requête de faire autrement.</span><span class="sxs-lookup"><span data-stu-id="19d53-108">This makes sense: It would be impossible for that query operator to do otherwise.</span></span>  
  
## <a name="example"></a><span data-ttu-id="19d53-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="19d53-109">Example</span></span>  
 <span data-ttu-id="19d53-110">Cet exemple modifie l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="19d53-110">This example alters the previous example.</span></span> <span data-ttu-id="19d53-111">La méthode `AppendString` appelle <xref:System.Linq.Enumerable.ToList%2A> avant d'itérer la source.</span><span class="sxs-lookup"><span data-stu-id="19d53-111">The `AppendString` method calls <xref:System.Linq.Enumerable.ToList%2A> before iterating through the source.</span></span> <span data-ttu-id="19d53-112">Cela provoque la matérialisation.</span><span class="sxs-lookup"><span data-stu-id="19d53-112">This causes materialization.</span></span>  
  
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
  
 <span data-ttu-id="19d53-113">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="19d53-113">This example produces the following output:</span></span>  
  
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
  
 <span data-ttu-id="19d53-114">Dans cet exemple, on observe que l'appel de <xref:System.Linq.Enumerable.ToList%2A> force `AppendString` à parcourir l'ensemble de sa source avant de générer le premier élément.</span><span class="sxs-lookup"><span data-stu-id="19d53-114">In this example, you can see that the call to <xref:System.Linq.Enumerable.ToList%2A> causes `AppendString` to enumerate its entire source before yielding the first item.</span></span> <span data-ttu-id="19d53-115">Si la source est un grand tableau, cela modifie considérablement le profil de mémoire de l'application.</span><span class="sxs-lookup"><span data-stu-id="19d53-115">If the source were a large array, this would significantly alter the memory profile of the application.</span></span>  
  
 <span data-ttu-id="19d53-116">Les opérateurs de requête standard peuvent également être chaînés ensemble.</span><span class="sxs-lookup"><span data-stu-id="19d53-116">Standard query operators can also be chained together.</span></span> <span data-ttu-id="19d53-117">La dernière rubrique de ce didacticiel illustre cela.</span><span class="sxs-lookup"><span data-stu-id="19d53-117">The final topic in this tutorial illustrates this.</span></span>  
  
- [<span data-ttu-id="19d53-118">Chaînage d’opérateurs de requête standard (C#)</span><span class="sxs-lookup"><span data-stu-id="19d53-118">Chaining Standard Query Operators Together (C#)</span></span>](./chaining-standard-query-operators-together.md)  
  
## <a name="see-also"></a><span data-ttu-id="19d53-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="19d53-119">See also</span></span>

- [<span data-ttu-id="19d53-120">Didacticiel : chaînage de requêtes (C#)</span><span class="sxs-lookup"><span data-stu-id="19d53-120">Tutorial: Chaining Queries Together (C#)</span></span>](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
