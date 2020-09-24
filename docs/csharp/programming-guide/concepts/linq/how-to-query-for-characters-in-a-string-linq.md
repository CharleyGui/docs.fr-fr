---
title: Comment interroger des caractères dans une chaîne (LINQ) (C#)
description: Vous pouvez interroger une chaîne sous la forme d’une séquence de caractères dans LINQ. Cet exemple C# interroge une chaîne pour déterminer le nombre de chiffres numériques qu’elle contient.
ms.date: 07/20/2015
ms.assetid: 727a1be7-dbec-4ab8-b414-bc2d56feb6ff
ms.openlocfilehash: 73288924d057e720a744b853998a52437b9db481
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91153935"
---
# <a name="how-to-query-for-characters-in-a-string-linq-c"></a><span data-ttu-id="d702d-104">Comment interroger des caractères dans une chaîne (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="d702d-104">How to query for characters in a string (LINQ) (C#)</span></span>

<span data-ttu-id="d702d-105">La classe <xref:System.String> implémente l’interface <xref:System.Collections.Generic.IEnumerable%601> générique. De ce fait, il est possible d’interroger n’importe quelle chaîne comme une séquence de caractères.</span><span class="sxs-lookup"><span data-stu-id="d702d-105">Because the <xref:System.String> class implements the generic <xref:System.Collections.Generic.IEnumerable%601> interface, any string can be queried as a sequence of characters.</span></span> <span data-ttu-id="d702d-106">Toutefois, ceci n’est pas une utilisation courante de LINQ.</span><span class="sxs-lookup"><span data-stu-id="d702d-106">However, this is not a common use of LINQ.</span></span> <span data-ttu-id="d702d-107">Pour les opérations de critères spéciaux complexes, utilisez la classe <xref:System.Text.RegularExpressions.Regex>.</span><span class="sxs-lookup"><span data-stu-id="d702d-107">For complex pattern matching operations, use the <xref:System.Text.RegularExpressions.Regex> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d702d-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="d702d-108">Example</span></span>  

 <span data-ttu-id="d702d-109">L’exemple suivant interroge une chaîne pour déterminer le nombre de chiffres qu’elle contient.</span><span class="sxs-lookup"><span data-stu-id="d702d-109">The following example queries a string to determine the number of numeric digits it contains.</span></span> <span data-ttu-id="d702d-110">Notez que la requête est « réutilisée » après sa première exécution.</span><span class="sxs-lookup"><span data-stu-id="d702d-110">Note that the query is "reused" after it is executed the first time.</span></span> <span data-ttu-id="d702d-111">Ceci est possible car la requête proprement dite ne stocke pas de résultats réels.</span><span class="sxs-lookup"><span data-stu-id="d702d-111">This is possible because the query itself does not store any actual results.</span></span>  
  
```csharp  
class QueryAString  
{  
    static void Main()  
    {  
        string aString = "ABCDE99F-J74-12-89A";  
  
        // Select only those characters that are numbers  
        IEnumerable<char> stringQuery =  
          from ch in aString  
          where Char.IsDigit(ch)  
          select ch;  
  
        // Execute the query  
        foreach (char c in stringQuery)  
            Console.Write(c + " ");  
  
        // Call the Count method on the existing query.  
        int count = stringQuery.Count();  
        Console.WriteLine("Count = {0}", count);  
  
        // Select all characters before the first '-'  
        IEnumerable<char> stringQuery2 = aString.TakeWhile(c => c != '-');  
  
        // Execute the second query  
        foreach (char c in stringQuery2)  
            Console.Write(c);  
  
        Console.WriteLine(System.Environment.NewLine + "Press any key to exit");  
        Console.ReadKey();  
    }  
}  
/* Output:  
  Output: 9 9 7 4 1 2 8 9  
  Count = 8  
  ABCDE99F  
*/  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d702d-112">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="d702d-112">Compiling the Code</span></span>  

 <span data-ttu-id="d702d-113">Créez un projet d’application console C# avec des directives `using` pour les espaces de noms System.Linq et System.IO.</span><span class="sxs-lookup"><span data-stu-id="d702d-113">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d702d-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d702d-114">See also</span></span>

- [<span data-ttu-id="d702d-115">LINQ et chaînes (C#)</span><span class="sxs-lookup"><span data-stu-id="d702d-115">LINQ and Strings (C#)</span></span>](./linq-and-strings.md)
- [<span data-ttu-id="d702d-116">Comment combiner des requêtes LINQ avec des expressions régulières (C#)</span><span class="sxs-lookup"><span data-stu-id="d702d-116">How to combine LINQ queries with regular expressions (C#)</span></span>](./how-to-combine-linq-queries-with-regular-expressions.md)
