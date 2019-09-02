---
title: Exemple d’exécution différée (C#)
ms.date: 07/20/2015
ms.assetid: 50f4fbac-81fe-4f26-aedf-506e21419b19
ms.openlocfilehash: 0816594ad016f19af4c97198160b4bafb9b4b8b4
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204133"
---
# <a name="deferred-execution-example-c"></a><span data-ttu-id="d3586-102">Exemple d’exécution différée (C#)</span><span class="sxs-lookup"><span data-stu-id="d3586-102">Deferred Execution Example (C#)</span></span>
<span data-ttu-id="d3586-103">Cette rubrique montre comment l'exécution et l'évaluation différées affectent l'exécution de vos requêtes LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="d3586-103">This topic shows how deferred execution and lazy evaluation affect the execution of your LINQ to XML queries.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d3586-104">Exemples</span><span class="sxs-lookup"><span data-stu-id="d3586-104">Example</span></span>  
 <span data-ttu-id="d3586-105">L'exemple suivant illustre l'ordre d'exécution lors de l'utilisation d'une méthode d'extension qui utilise l'exécution différée.</span><span class="sxs-lookup"><span data-stu-id="d3586-105">The following example shows the order of execution when using an extension method that uses deferred execution.</span></span> <span data-ttu-id="d3586-106">L'exemple déclare un tableau de trois chaînes.</span><span class="sxs-lookup"><span data-stu-id="d3586-106">The example declares an array of three strings.</span></span> <span data-ttu-id="d3586-107">Il itère ensuite au sein de la collection retournée par `ConvertCollectionToUpperCase`.</span><span class="sxs-lookup"><span data-stu-id="d3586-107">It then iterates through the collection returned by `ConvertCollectionToUpperCase`.</span></span>  
  
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
  
 <span data-ttu-id="d3586-108">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="d3586-108">This example produces the following output:</span></span>  
  
```output  
ToUpper: source abc  
Main: str ABC  
ToUpper: source def  
Main: str DEF  
ToUpper: source ghi  
Main: str GHI  
```  
  
 <span data-ttu-id="d3586-109">Notez que lors de l'itération de la collection retournée par `ConvertCollectionToUpperCase`, chaque élément est récupéré du tableau de chaînes source et converti en majuscules avant que l'élément suivant ne soit récupéré du tableau de chaînes source.</span><span class="sxs-lookup"><span data-stu-id="d3586-109">Notice that when iterating through the collection returned by `ConvertCollectionToUpperCase`, each item is retrieved from the source string array and converted to uppercase before the next item is retrieved from the source string array.</span></span>  
  
 <span data-ttu-id="d3586-110">Vous pouvez constater que l'intégralité du tableau de chaînes n'est pas convertie en majuscules avant que chaque élément de la collection retournée n'ait été traité dans la boucle `foreach` dans `Main`.</span><span class="sxs-lookup"><span data-stu-id="d3586-110">You can see that the entire array of strings is not converted to uppercase before each item in the returned collection is processed in the `foreach` loop in `Main`.</span></span>  
  
 <span data-ttu-id="d3586-111">La rubrique suivante de ce didacticiel illustre le chaînage de requêtes.</span><span class="sxs-lookup"><span data-stu-id="d3586-111">The next topic in this tutorial illustrates chaining queries together:</span></span>  
  
- [<span data-ttu-id="d3586-112">Exemple de chaînage de requêtes (C#)</span><span class="sxs-lookup"><span data-stu-id="d3586-112">Chaining Queries Example (C#)</span></span>](./chaining-queries-example.md)  
  
## <a name="see-also"></a><span data-ttu-id="d3586-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d3586-113">See also</span></span>

- [<span data-ttu-id="d3586-114">Tutoriel : Chaînage de requêtes (C#)</span><span class="sxs-lookup"><span data-stu-id="d3586-114">Tutorial: Chaining Queries Together (C#)</span></span>](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
