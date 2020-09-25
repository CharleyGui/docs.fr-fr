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
# <a name="how-to-sort-or-filter-text-data-by-any-word-or-field-linq-c"></a>Guide pratique pour trier ou filtrer des données texte par mot ou par champ (LINQ) (C#)

L’exemple suivant montre comment trier les lignes d’un texte structuré, telles que des valeurs séparées par des virgules, à l’aide d’un champ de la ligne. Le champ peut être spécifié de manière dynamique lors de l’exécution. Supposons que les champs du fichier scores.csv correspondent au numéro d’identification d’un étudiant, suivi d’une série de quatre notes d’examen.  
  
### <a name="to-create-a-file-that-contains-data"></a>Pour créer un fichier contenant des données  
  
1. Copiez les données scores.csv à partir de la rubrique [Comment joindre du contenu de fichiers non similaires (LINQ) (C#)](./how-to-join-content-from-dissimilar-files-linq.md) et enregistrez-le dans votre dossier de solution.  
  
## <a name="example"></a>Exemple  
  
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
  
 Cet exemple montre également comment retourner une variable de requête à partir d’une méthode.  
  
## <a name="compiling-the-code"></a>Compilation du code  

Créez un projet d’application console C# avec des directives `using` pour les espaces de noms System.Linq et System.IO.
  
## <a name="see-also"></a>Voir aussi

- [LINQ et chaînes (C#)](./linq-and-strings.md)
