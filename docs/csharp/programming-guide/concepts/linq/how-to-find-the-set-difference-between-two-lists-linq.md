---
title: 'Procédure : Rechercher la différence ensembliste entre deux listes (LINQ) (C#)'
ms.date: 07/20/2015
ms.assetid: 8e8945f0-4aba-439d-8d5d-c8d1eeef4e71
ms.openlocfilehash: c8f01cb53665d01d4c7861bab758ecc9e0dcc3c8
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65585709"
---
# <a name="how-to-find-the-set-difference-between-two-lists-linq-c"></a><span data-ttu-id="ede45-102">Procédure : Rechercher la différence ensembliste entre deux listes (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="ede45-102">How to: Find the Set Difference Between Two Lists (LINQ) (C#)</span></span>
<span data-ttu-id="ede45-103">Cet exemple montre comment utiliser LINQ pour comparer deux listes de chaînes et sortir les lignes qui sont présentes dans names1.txt, mais pas dans names2.txt.</span><span class="sxs-lookup"><span data-stu-id="ede45-103">This example shows how to use LINQ to compare two lists of strings and output those lines that are in names1.txt but not in names2.txt.</span></span>  
  
### <a name="to-create-the-data-files"></a><span data-ttu-id="ede45-104">Pour créer les fichiers de données</span><span class="sxs-lookup"><span data-stu-id="ede45-104">To create the data files</span></span>  
  
1. <span data-ttu-id="ede45-105">Copiez names1.txt et names2.txt dans votre dossier de solution comme indiqué dans le [Guide pratique pour combiner et comparer des collections de chaînes (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-combine-and-compare-string-collections-linq.md).</span><span class="sxs-lookup"><span data-stu-id="ede45-105">Copy names1.txt and names2.txt to your solution folder as shown in [How to: Combine and Compare String Collections (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-combine-and-compare-string-collections-linq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ede45-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="ede45-106">Example</span></span>  
  
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
  
 <span data-ttu-id="ede45-107">Certains types d’opérations de requête en C#, tels que <xref:System.Linq.Enumerable.Except%2A>, <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Union%2A> et <xref:System.Linq.Enumerable.Concat%2A>, peuvent uniquement être exprimés dans une syntaxe basée sur une méthode.</span><span class="sxs-lookup"><span data-stu-id="ede45-107">Some types of query operations in C#, such as <xref:System.Linq.Enumerable.Except%2A>, <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Union%2A>, and <xref:System.Linq.Enumerable.Concat%2A>, can only be expressed in method-based syntax.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ede45-108">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="ede45-108">Compiling the Code</span></span>  
 <span data-ttu-id="ede45-109">Créez un projet d’application console C# avec des directives `using` pour les espaces de noms System.Linq et System.IO.</span><span class="sxs-lookup"><span data-stu-id="ede45-109">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ede45-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ede45-110">See also</span></span>

- [<span data-ttu-id="ede45-111">LINQ et chaînes (C#)</span><span class="sxs-lookup"><span data-stu-id="ede45-111">LINQ and Strings (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-and-strings.md)
