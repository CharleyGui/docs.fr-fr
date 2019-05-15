---
title: Matérialisation intermédiaire (C#)
ms.date: 07/20/2015
ms.assetid: 7922d38f-5044-41cf-8e17-7173d6553a5e
ms.openlocfilehash: fa1e11c6b4cacff3b5a5a7ca1cc311f5fabda6c7
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64596617"
---
# <a name="intermediate-materialization-c"></a><span data-ttu-id="19f4c-102">Matérialisation intermédiaire (C#)</span><span class="sxs-lookup"><span data-stu-id="19f4c-102">Intermediate Materialization (C#)</span></span>
<span data-ttu-id="19f4c-103">Si vous n’y prenez pas garde, dans certaines situations vous risquez de modifier de manière significative le profil de mémoire et de performances de votre application en provoquant la matérialisation prématurée de collections dans vos requêtes.</span><span class="sxs-lookup"><span data-stu-id="19f4c-103">If you are not careful, in some situations you can drastically alter the memory and performance profile of your application by causing premature materialization of collections in your queries.</span></span> <span data-ttu-id="19f4c-104">Certains opérateurs de requête standard provoquent la matérialisation de leur collection source avant de générer un seul élément.</span><span class="sxs-lookup"><span data-stu-id="19f4c-104">Some standard query operators cause materialization of their source collection before yielding a single element.</span></span> <span data-ttu-id="19f4c-105">Par exemple, <xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType> itère au sein de l'ensemble de sa collection source, trie tous les éléments, puis génère le premier élément.</span><span class="sxs-lookup"><span data-stu-id="19f4c-105">For example, <xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType> first iterates through its entire source collection, then sorts all items, and then finally yields the first item.</span></span> <span data-ttu-id="19f4c-106">Cela signifie qu'il est coûteux d'obtenir le premier élément d'une collection ordonnée ; chaque élément ultérieur a un faible coût.</span><span class="sxs-lookup"><span data-stu-id="19f4c-106">This means that it is expensive to get the first item of an ordered collection; each item thereafter is not expensive.</span></span> <span data-ttu-id="19f4c-107">Tout cela est logique : il serait impossible pour cet opérateur de requête de faire autrement.</span><span class="sxs-lookup"><span data-stu-id="19f4c-107">This makes sense: It would be impossible for that query operator to do otherwise.</span></span>  
  
## <a name="example"></a><span data-ttu-id="19f4c-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="19f4c-108">Example</span></span>  
 <span data-ttu-id="19f4c-109">Cet exemple modifie l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="19f4c-109">This example alters the previous example.</span></span> <span data-ttu-id="19f4c-110">La méthode `AppendString` appelle <xref:System.Linq.Enumerable.ToList%2A> avant d'itérer la source.</span><span class="sxs-lookup"><span data-stu-id="19f4c-110">The `AppendString` method calls <xref:System.Linq.Enumerable.ToList%2A> before iterating through the source.</span></span> <span data-ttu-id="19f4c-111">Cela provoque la matérialisation.</span><span class="sxs-lookup"><span data-stu-id="19f4c-111">This causes materialization.</span></span>  
  
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
  
 <span data-ttu-id="19f4c-112">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="19f4c-112">This example produces the following output:</span></span>  
  
```  
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
  
 <span data-ttu-id="19f4c-113">Dans cet exemple, on observe que l'appel de <xref:System.Linq.Enumerable.ToList%2A> force `AppendString` à parcourir l'ensemble de sa source avant de générer le premier élément.</span><span class="sxs-lookup"><span data-stu-id="19f4c-113">In this example, you can see that the call to <xref:System.Linq.Enumerable.ToList%2A> causes `AppendString` to enumerate its entire source before yielding the first item.</span></span> <span data-ttu-id="19f4c-114">Si la source est un grand tableau, cela modifie considérablement le profil de mémoire de l'application.</span><span class="sxs-lookup"><span data-stu-id="19f4c-114">If the source were a large array, this would significantly alter the memory profile of the application.</span></span>  
  
 <span data-ttu-id="19f4c-115">Les opérateurs de requête standard peuvent également être chaînés ensemble.</span><span class="sxs-lookup"><span data-stu-id="19f4c-115">Standard query operators can also be chained together.</span></span> <span data-ttu-id="19f4c-116">La dernière rubrique de ce didacticiel illustre cela.</span><span class="sxs-lookup"><span data-stu-id="19f4c-116">The final topic in this tutorial illustrates this.</span></span>  
  
- [<span data-ttu-id="19f4c-117">Chaînage d’opérateurs de requête standard (C#)</span><span class="sxs-lookup"><span data-stu-id="19f4c-117">Chaining Standard Query Operators Together (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/chaining-standard-query-operators-together.md)  
  
## <a name="see-also"></a><span data-ttu-id="19f4c-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="19f4c-118">See also</span></span>

- [<span data-ttu-id="19f4c-119">Tutoriel : Chaînage de requêtes (C#)</span><span class="sxs-lookup"><span data-stu-id="19f4c-119">Tutorial: Chaining Queries Together (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md)
