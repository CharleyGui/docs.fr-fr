---
title: Guide pratique pour rechercher la différence définie entre deux listes (LINQ) (C#)
description: Découvrez comment utiliser LINQ en C# pour comparer deux listes de chaînes et sortir les lignes qui se trouvent dans une liste, mais pas dans l’autre.
ms.date: 07/20/2015
ms.assetid: 8e8945f0-4aba-439d-8d5d-c8d1eeef4e71
ms.openlocfilehash: 24509488d91f9861ee9bf84277238bea7031e5f6
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105081"
---
# <a name="how-to-find-the-set-difference-between-two-lists-linq-c"></a><span data-ttu-id="f2a95-103">Guide pratique pour rechercher la différence définie entre deux listes (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="f2a95-103">How to find the set difference between two lists (LINQ) (C#)</span></span>
<span data-ttu-id="f2a95-104">Cet exemple montre comment utiliser LINQ pour comparer deux listes de chaînes et sortir les lignes qui sont présentes dans names1.txt, mais pas dans names2.txt.</span><span class="sxs-lookup"><span data-stu-id="f2a95-104">This example shows how to use LINQ to compare two lists of strings and output those lines that are in names1.txt but not in names2.txt.</span></span>  
  
### <a name="to-create-the-data-files"></a><span data-ttu-id="f2a95-105">Pour créer le fichier de données</span><span class="sxs-lookup"><span data-stu-id="f2a95-105">To create the data files</span></span>  
  
1. <span data-ttu-id="f2a95-106">Copiez names1.txt et names2.txt vers votre dossier de solution, comme indiqué dans [Comment combiner et comparer des collections de chaînes (LINQ) (C#)](./how-to-combine-and-compare-string-collections-linq.md).</span><span class="sxs-lookup"><span data-stu-id="f2a95-106">Copy names1.txt and names2.txt to your solution folder as shown in [How to combine and compare string collections (LINQ) (C#)](./how-to-combine-and-compare-string-collections-linq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f2a95-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="f2a95-107">Example</span></span>  
  
```csharp  
class CompareLists  
{
    static void Main()  
    {  
        // Create the IEnumerable data sources.  
        string[] names1 = System.IO.File.ReadAllLines(@"../../../names1.txt");  
        string[] names2 = System.IO.File.ReadAllLines(@"../../../names2.txt");  
  
        // Create the query. Note that method syntax must be used here.  
        IEnumerable<string> differenceQuery =  
          names1.Except(names2);  
  
        // Execute the query.  
        Console.WriteLine("The following lines are in names1.txt but not names2.txt");  
        foreach (string s in differenceQuery)  
            Console.WriteLine(s);  
  
        // Keep the console window open in debug mode.  
        Console.WriteLine("Press any key to exit");  
        Console.ReadKey();  
    }  
}  
/* Output:  
     The following lines are in names1.txt but not names2.txt  
    Potra, Cristina  
    Noriega, Fabricio  
    Aw, Kam Foo  
    Toyoshima, Tim  
    Guy, Wey Yuan  
    Garcia, Debra  
     */  
```  
  
 <span data-ttu-id="f2a95-108">Certains types d’opérations de requête en C#, tels que <xref:System.Linq.Enumerable.Except%2A>, <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Union%2A> et <xref:System.Linq.Enumerable.Concat%2A>, peuvent uniquement être exprimés dans une syntaxe basée sur une méthode.</span><span class="sxs-lookup"><span data-stu-id="f2a95-108">Some types of query operations in C#, such as <xref:System.Linq.Enumerable.Except%2A>, <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Union%2A>, and <xref:System.Linq.Enumerable.Concat%2A>, can only be expressed in method-based syntax.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f2a95-109">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="f2a95-109">Compiling the Code</span></span>  
 <span data-ttu-id="f2a95-110">Créez un projet d’application console C# avec des directives `using` pour les espaces de noms System.Linq et System.IO.</span><span class="sxs-lookup"><span data-stu-id="f2a95-110">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2a95-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f2a95-111">See also</span></span>

- [<span data-ttu-id="f2a95-112">LINQ et chaînes (C#)</span><span class="sxs-lookup"><span data-stu-id="f2a95-112">LINQ and Strings (C#)</span></span>](./linq-and-strings.md)
