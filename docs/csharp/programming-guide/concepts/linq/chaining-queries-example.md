---
title: Exemple de chaînage de requêtes (C#)
description: Cet exemple montre ce qui se passe lorsque vous chaînez deux requêtes qui utilisent toutes deux l’exécution différée et l’évaluation paresseuse en C#.
ms.date: 07/20/2015
ms.assetid: abbca162-d95e-43af-b92c-e46e6aa2540e
ms.openlocfilehash: 0cfcfe1c8f537778fd1ef909277d95d83991af51
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105545"
---
# <a name="chaining-queries-example-c"></a><span data-ttu-id="77b84-103">Exemple de chaînage de requêtes (C#)</span><span class="sxs-lookup"><span data-stu-id="77b84-103">Chaining Queries Example (C#)</span></span>
<span data-ttu-id="77b84-104">Cet exemple est basé sur l’exemple précédent et illustre ce qui se produit quand vous chaînez deux requêtes qui utilisent toutes deux l’exécution et l’évaluation différées.</span><span class="sxs-lookup"><span data-stu-id="77b84-104">This example builds on the previous example and shows what happens when you chain together two queries that both use deferred execution and lazy evaluation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="77b84-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="77b84-105">Example</span></span>  
 <span data-ttu-id="77b84-106">Dans cet exemple, une autre méthode d'extension est introduite : `AppendString`. Elle ajoute une chaîne spécifiée à chaque chaîne de la collection source, puis génère les nouvelles chaînes.</span><span class="sxs-lookup"><span data-stu-id="77b84-106">In this example, another extension method is introduced, `AppendString`, which appends a specified string onto every string in the source collection, and then yields the new strings.</span></span>  
  
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
  
 <span data-ttu-id="77b84-107">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="77b84-107">This example produces the following output:</span></span>  
  
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
  
 <span data-ttu-id="77b84-108">Dans cet exemple, vous pouvez constater que chaque méthode d'extension opère l'une après l'autre pour chaque élément de la collection source.</span><span class="sxs-lookup"><span data-stu-id="77b84-108">In this example, you can see that each extension method operates one at a time for each item in the source collection.</span></span>  
  
 <span data-ttu-id="77b84-109">Il doit être clair, au vu de cet exemple, que bien que nous ayons chaîné des requêtes qui produisent des collections, aucune collection intermédiaire n'est matérialisée.</span><span class="sxs-lookup"><span data-stu-id="77b84-109">What should be clear from this example is that even though we have chained together queries that yield collections, no intermediate collections are materialized.</span></span> <span data-ttu-id="77b84-110">Au lieu de cela, chaque élément est passé d'une méthode différée à la suivante.</span><span class="sxs-lookup"><span data-stu-id="77b84-110">Instead, each item is passed from one lazy method to the next.</span></span> <span data-ttu-id="77b84-111">L'encombrement mémoire est par conséquent beaucoup plus faible par rapport à une approche qui consisterait à prendre d'abord un tableau de chaînes, à créer un deuxième tableau de chaînes converties en majuscules, puis à créer un troisième tableau de chaînes où des points d'exclamations sont ajoutés à chaque chaîne.</span><span class="sxs-lookup"><span data-stu-id="77b84-111">This results in a much smaller memory footprint than an approach that would first take one array of strings, then create a second array of strings that have been converted to uppercase, and finally create a third array of strings where each string has the exclamation points appended to it.</span></span>  
  
 <span data-ttu-id="77b84-112">La rubrique suivante de ce didacticiel illustre la matérialisation intermédiaire :</span><span class="sxs-lookup"><span data-stu-id="77b84-112">The next topic in this tutorial illustrates intermediate materialization:</span></span>  
  
- [<span data-ttu-id="77b84-113">Matérialisation intermédiaire (C#)</span><span class="sxs-lookup"><span data-stu-id="77b84-113">Intermediate Materialization (C#)</span></span>](./intermediate-materialization.md)  
  
## <a name="see-also"></a><span data-ttu-id="77b84-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="77b84-114">See also</span></span>

- [<span data-ttu-id="77b84-115">Didacticiel : chaînage de requêtes (C#)</span><span class="sxs-lookup"><span data-stu-id="77b84-115">Tutorial: Chaining Queries Together (C#)</span></span>](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
