---
title: Comment joindre du contenu issu de fichiers différents (LINQ) (C#)
description: Découvrez comment joindre des données de deux fichiers délimités par des virgules à l’aide de LINQ en C#. Les données partagent une valeur commune utilisée comme clé correspondante.
ms.date: 06/27/2018
ms.assetid: aa2d12a6-70a9-492f-a6db-b2b850d46811
ms.openlocfilehash: 136d10ff5c0bf5f4f18998b50eb7bbee218b00a9
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104983"
---
# <a name="how-to-join-content-from-dissimilar-files-linq-c"></a><span data-ttu-id="7d5c8-104">Comment joindre du contenu issu de fichiers différents (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="7d5c8-104">How to join content from dissimilar files (LINQ) (C#)</span></span>

<span data-ttu-id="7d5c8-105">Cet exemple montre comment joindre des données de deux fichiers CSV qui partagent une valeur commune utilisée comme clé correspondante.</span><span class="sxs-lookup"><span data-stu-id="7d5c8-105">This example shows how to join data from two comma-delimited files that share a common value that is used as a matching key.</span></span> <span data-ttu-id="7d5c8-106">Cette technique peut être utile si vous devez combiner les données de deux feuilles de calcul, ou d’une feuille de calcul et d’un fichier qui a un autre format, dans un nouveau fichier.</span><span class="sxs-lookup"><span data-stu-id="7d5c8-106">This technique can be useful if you have to combine data from two spreadsheets, or from a spreadsheet and from a file that has another format, into a new file.</span></span> <span data-ttu-id="7d5c8-107">Vous pouvez modifier l’exemple pour qu’il fonctionne avec tout type de texte structuré.</span><span class="sxs-lookup"><span data-stu-id="7d5c8-107">You can modify the example to work with any kind of structured text.</span></span>  
  
## <a name="to-create-the-data-files"></a><span data-ttu-id="7d5c8-108">Pour créer le fichier de données</span><span class="sxs-lookup"><span data-stu-id="7d5c8-108">To create the data files</span></span>
  
1. <span data-ttu-id="7d5c8-109">Copiez les lignes suivantes dans un fichier nommé *scores.csv*, puis enregistrez-le dans votre dossier de projet.</span><span class="sxs-lookup"><span data-stu-id="7d5c8-109">Copy the following lines into a file that is named *scores.csv* and save it to your project folder.</span></span> <span data-ttu-id="7d5c8-110">Le fichier représente les données de feuille de calcul.</span><span class="sxs-lookup"><span data-stu-id="7d5c8-110">The file represents spreadsheet data.</span></span> <span data-ttu-id="7d5c8-111">La colonne 1 est l’ID de l’étudiant et les colonnes 2 à 5 correspondent à des résultats d’examens.</span><span class="sxs-lookup"><span data-stu-id="7d5c8-111">Column 1 is the student's ID, and columns 2 through 5 are test scores.</span></span>  
  
    ```csv  
    111, 97, 92, 81, 60  
    112, 75, 84, 91, 39  
    113, 88, 94, 65, 91  
    114, 97, 89, 85, 82  
    115, 35, 72, 91, 70  
    116, 99, 86, 90, 94  
    117, 93, 92, 80, 87  
    118, 92, 90, 83, 78  
    119, 68, 79, 88, 92  
    120, 99, 82, 81, 79  
    121, 96, 85, 91, 60  
    122, 94, 92, 91, 91  
    ```  
  
2. <span data-ttu-id="7d5c8-112">Copiez les lignes suivantes dans un fichier nommé *names.csv*, puis enregistrez-le dans votre dossier de projet.</span><span class="sxs-lookup"><span data-stu-id="7d5c8-112">Copy the following lines into a file that is named *names.csv* and save it to your project folder.</span></span> <span data-ttu-id="7d5c8-113">Le fichier représente une feuille de calcul qui contient le nom, le prénom et l’ID de l’étudiant.</span><span class="sxs-lookup"><span data-stu-id="7d5c8-113">The file represents a spreadsheet that contains the student's last name, first name, and student ID.</span></span>  
  
    ```csv  
    Omelchenko,Svetlana,111  
    O'Donnell,Claire,112  
    Mortensen,Sven,113  
    Garcia,Cesar,114  
    Garcia,Debra,115  
    Fakhouri,Fadi,116  
    Feng,Hanying,117  
    Garcia,Hugo,118  
    Tucker,Lance,119  
    Adams,Terry,120  
    Zabokritski,Eugene,121  
    Tucker,Michael,122  
    ```  
  
## <a name="example"></a><span data-ttu-id="7d5c8-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="7d5c8-114">Example</span></span>  

```csharp
using System;
using System.Collections.Generic;
using System.Linq;

class JoinStrings  
{  
    static void Main()  
    {  
        // Join content from dissimilar files that contain  
        // related information. File names.csv contains the student  
        // name plus an ID number. File scores.csv contains the ID
        // and a set of four test scores. The following query joins  
        // the scores to the student names by using ID as a  
        // matching key.  
  
        string[] names = System.IO.File.ReadAllLines(@"../../../names.csv");  
        string[] scores = System.IO.File.ReadAllLines(@"../../../scores.csv");  
  
        // Name:    Last[0],       First[1],  ID[2]  
        //          Omelchenko,    Svetlana,  11  
        // Score:   StudentID[0],  Exam1[1]   Exam2[2],  Exam3[3],  Exam4[4]  
        //          111,           97,        92,        81,        60  
  
        // This query joins two dissimilar spreadsheets based on common ID value.  
        // Multiple from clauses are used instead of a join clause  
        // in order to store results of id.Split.  
        IEnumerable<string> scoreQuery1 =  
            from name in names  
            let nameFields = name.Split(',')  
            from id in scores  
            let scoreFields = id.Split(',')  
            where Convert.ToInt32(nameFields[2]) == Convert.ToInt32(scoreFields[0])
            select nameFields[0] + "," + scoreFields[1] + "," + scoreFields[2]
                   + "," + scoreFields[3] + "," + scoreFields[4];  
  
        // Pass a query variable to a method and execute it  
        // in the method. The query itself is unchanged.  
        OutputQueryResults(scoreQuery1, "Merge two spreadsheets:");  
  
        // Keep console window open in debug mode.  
        Console.WriteLine("Press any key to exit");  
        Console.ReadKey();  
    }  
  
    static void OutputQueryResults(IEnumerable<string> query, string message)  
    {  
        Console.WriteLine(System.Environment.NewLine + message);  
        foreach (string item in query)  
        {  
            Console.WriteLine(item);  
        }  
        Console.WriteLine("{0} total names in list", query.Count());  
    }  
}  
/* Output:  
Merge two spreadsheets:
Omelchenko, 97, 92, 81, 60
O'Donnell, 75, 84, 91, 39
Mortensen, 88, 94, 65, 91
Garcia, 97, 89, 85, 82
Garcia, 35, 72, 91, 70
Fakhouri, 99, 86, 90, 94
Feng, 93, 92, 80, 87
Garcia, 92, 90, 83, 78
Tucker, 68, 79, 88, 92
Adams, 99, 82, 81, 79
Zabokritski, 96, 85, 91, 60
Tucker, 94, 92, 91, 91
12 total names in list
 */  
```

## <a name="see-also"></a><span data-ttu-id="7d5c8-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7d5c8-115">See also</span></span>

- [<span data-ttu-id="7d5c8-116">LINQ et chaînes (C#)</span><span class="sxs-lookup"><span data-stu-id="7d5c8-116">LINQ and Strings (C#)</span></span>](./linq-and-strings.md)
- [<span data-ttu-id="7d5c8-117">LINQ et répertoires de fichiers (C#)</span><span class="sxs-lookup"><span data-stu-id="7d5c8-117">LINQ and File Directories (C#)</span></span>](./linq-and-file-directories.md)
