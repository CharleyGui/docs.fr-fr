---
title: Comment rechercher la différence définie entre deux listes (LINQ) (C#)
ms.date: 07/20/2015
ms.assetid: 8e8945f0-4aba-439d-8d5d-c8d1eeef4e71
ms.openlocfilehash: 227405428a1b418cbe6ceb3d0e3274595307e5ef
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345936"
---
# <a name="how-to-find-the-set-difference-between-two-lists-linq-c"></a>Comment rechercher la différence définie entre deux listes (LINQ) (C#)
Cet exemple montre comment utiliser LINQ pour comparer deux listes de chaînes et sortir les lignes qui sont présentes dans names1.txt, mais pas dans names2.txt.  
  
### <a name="to-create-the-data-files"></a>Pour créer le fichier de données  
  
1. Copiez names1. txt et names2. txt dans votre dossier de solution, comme indiqué dans [Comment combiner et comparer des collections de chaînesC#(LINQ) ()](./how-to-combine-and-compare-string-collections-linq.md).  
  
## <a name="example"></a>Exemple  
  
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
  
 Certains types d’opérations de requête en C#, tels que <xref:System.Linq.Enumerable.Except%2A>, <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Union%2A> et <xref:System.Linq.Enumerable.Concat%2A>, peuvent uniquement être exprimés dans une syntaxe basée sur une méthode.  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Créez un projet d’application console C# avec des directives `using` pour les espaces de noms System.Linq et System.IO.  
  
## <a name="see-also"></a>Voir aussi

- [LINQ et chaînes (C#)](./linq-and-strings.md)
