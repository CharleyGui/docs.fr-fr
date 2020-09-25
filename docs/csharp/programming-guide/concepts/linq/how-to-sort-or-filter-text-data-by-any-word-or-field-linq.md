---
title: Guide pratique pour trier ou filtrer des données texte par mot ou par champ (LINQ) (C#)
description: Découvrez comment trier ou filtrer des données texte par mot ou par champ. Consultez un exemple de tri des lignes de texte structuré par n’importe quel champ de la ligne.
ms.date: 07/20/2015
ms.assetid: 7c04d42f-4a78-42c8-9ec8-57ef18fe13a9
ms.openlocfilehash: 05858cc787d3916b204910df10d3291796cebc02
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203941"
---
# <a name="how-to-sort-or-filter-text-data-by-any-word-or-field-linq-c"></a><span data-ttu-id="508d6-104">Guide pratique pour trier ou filtrer des données texte par mot ou par champ (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="508d6-104">How to sort or filter text data by any word or field (LINQ) (C#)</span></span>

<span data-ttu-id="508d6-105">L’exemple suivant montre comment trier les lignes d’un texte structuré, telles que des valeurs séparées par des virgules, à l’aide d’un champ de la ligne.</span><span class="sxs-lookup"><span data-stu-id="508d6-105">The following example shows how to sort lines of structured text, such as comma-separated values, by any field in the line.</span></span> <span data-ttu-id="508d6-106">Le champ peut être spécifié de manière dynamique lors de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="508d6-106">The field may be dynamically specified at runtime.</span></span> <span data-ttu-id="508d6-107">Supposons que les champs du fichier scores.csv correspondent au numéro d’identification d’un étudiant, suivi d’une série de quatre notes d’examen.</span><span class="sxs-lookup"><span data-stu-id="508d6-107">Assume that the fields in scores.csv represent a student's ID number, followed by a series of four test scores.</span></span>  
  
### <a name="to-create-a-file-that-contains-data"></a><span data-ttu-id="508d6-108">Pour créer un fichier contenant des données</span><span class="sxs-lookup"><span data-stu-id="508d6-108">To create a file that contains data</span></span>  
  
1. <span data-ttu-id="508d6-109">Copiez les données scores.csv à partir de la rubrique [Comment joindre du contenu de fichiers non similaires (LINQ) (C#)](./how-to-join-content-from-dissimilar-files-linq.md) et enregistrez-le dans votre dossier de solution.</span><span class="sxs-lookup"><span data-stu-id="508d6-109">Copy the scores.csv data from the topic [How to join content from dissimilar files (LINQ) (C#)](./how-to-join-content-from-dissimilar-files-linq.md) and save it to your solution folder.</span></span>  
  
## <a name="example"></a><span data-ttu-id="508d6-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="508d6-110">Example</span></span>  
  
```csharp  
public class SortLines  
{  
    static void Main()  
    {  
        // Create an IEnumerable data source  
        string[] scores = System.IO.File.ReadAllLines(@"../../../scores.csv");  
  
        // Change this to any value from 0 to 4.  
        int sortField = 1;  
  
        Console.WriteLine("Sorted highest to lowest by field [{0}]:", sortField);  
  
        // Demonstrates how to return query from a method.  
        // The query is executed here.  
        foreach (string str in RunQuery(scores, sortField))  
        {  
            Console.WriteLine(str);  
        }  
  
        // Keep the console window open in debug mode.  
        Console.WriteLine("Press any key to exit");  
        Console.ReadKey();  
    }  
  
    // Returns the query variable, not query results!  
    static IEnumerable<string> RunQuery(IEnumerable<string> source, int num)  
    {  
        // Split the string and sort on field[num]  
        var scoreQuery = from line in source  
                         let fields = line.Split(',')  
                         orderby fields[num] descending  
                         select line;  
  
        return scoreQuery;  
    }  
}  
/* Output (if sortField == 1):  
   Sorted highest to lowest by field [1]:  
    116, 99, 86, 90, 94  
    120, 99, 82, 81, 79  
    111, 97, 92, 81, 60  
    114, 97, 89, 85, 82  
    121, 96, 85, 91, 60  
    122, 94, 92, 91, 91  
    117, 93, 92, 80, 87  
    118, 92, 90, 83, 78  
    113, 88, 94, 65, 91  
    112, 75, 84, 91, 39  
    119, 68, 79, 88, 92  
    115, 35, 72, 91, 70  
 */  
```  
  
 <span data-ttu-id="508d6-111">Cet exemple montre également comment retourner une variable de requête à partir d’une méthode.</span><span class="sxs-lookup"><span data-stu-id="508d6-111">This example also demonstrates how to return a query variable from a method.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="508d6-112">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="508d6-112">Compiling the Code</span></span>  

<span data-ttu-id="508d6-113">Créez un projet d’application console C# avec des directives `using` pour les espaces de noms System.Linq et System.IO.</span><span class="sxs-lookup"><span data-stu-id="508d6-113">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="508d6-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="508d6-114">See also</span></span>

- [<span data-ttu-id="508d6-115">LINQ et chaînes (C#)</span><span class="sxs-lookup"><span data-stu-id="508d6-115">LINQ and Strings (C#)</span></span>](./linq-and-strings.md)
