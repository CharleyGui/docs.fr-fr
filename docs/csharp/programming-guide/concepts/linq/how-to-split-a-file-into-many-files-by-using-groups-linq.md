---
title: Comment fractionner un fichier en plusieurs fichiers à l’aide de groupes (LINQ) (C#)
description: Découvrez comment fractionner un fichier en plusieurs fichiers à l’aide de groupes. Consultez un exemple de code et affichez des ressources supplémentaires disponibles.
ms.date: 07/20/2015
ms.assetid: 8179b91c-d778-4e57-884f-77fe5a8e4e40
ms.openlocfilehash: b7be01be0f1539eb6ed4f4857af2625672319493
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203928"
---
# <a name="how-to-split-a-file-into-many-files-by-using-groups-linq-c"></a><span data-ttu-id="7b931-104">Comment fractionner un fichier en plusieurs fichiers à l’aide de groupes (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="7b931-104">How to split a file into many files by using groups (LINQ) (C#)</span></span>

<span data-ttu-id="7b931-105">Cet exemple montre comment fusionner le contenu de deux fichiers, puis créer un ensemble de fichiers qui organisent les données d’une nouvelle façon.</span><span class="sxs-lookup"><span data-stu-id="7b931-105">This example shows one way to merge the contents of two files and then create a set of new files that organize the data in a new way.</span></span>  
  
### <a name="to-create-the-data-files"></a><span data-ttu-id="7b931-106">Pour créer le fichier de données</span><span class="sxs-lookup"><span data-stu-id="7b931-106">To create the data files</span></span>  
  
1. <span data-ttu-id="7b931-107">Copiez ces noms dans un fichier texte nommé names1.txt, puis enregistrez-le dans votre dossier de projet :</span><span class="sxs-lookup"><span data-stu-id="7b931-107">Copy these names into a text file that is named names1.txt and save it in your project folder:</span></span>  
  
    ```text  
    Bankov, Peter  
    Holm, Michael  
    Garcia, Hugo  
    Potra, Cristina  
    Noriega, Fabricio  
    Aw, Kam Foo  
    Beebe, Ann  
    Toyoshima, Tim  
    Guy, Wey Yuan  
    Garcia, Debra  
    ```  
  
2. <span data-ttu-id="7b931-108">Copiez ces noms dans un fichier texte nommé names2.txt, puis enregistrez-le dans votre dossier de projet. Notez que les deux fichiers ont certains noms en commun.</span><span class="sxs-lookup"><span data-stu-id="7b931-108">Copy these names into a text file that is named names2.txt and save it in your project folder: Note that the two files have some names in common.</span></span>  
  
    ```text  
    Liu, Jinghao  
    Bankov, Peter  
    Holm, Michael  
    Garcia, Hugo  
    Beebe, Ann  
    Gilchrist, Beth  
    Myrcha, Jacek  
    Giakoumakis, Leo  
    McLin, Nkenge  
    El Yassir, Mehdi  
    ```  
  
## <a name="example"></a><span data-ttu-id="7b931-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="7b931-109">Example</span></span>  
  
```csharp  
class SplitWithGroups  
{  
    static void Main()  
    {  
        string[] fileA = System.IO.File.ReadAllLines(@"../../../names1.txt");  
        string[] fileB = System.IO.File.ReadAllLines(@"../../../names2.txt");  
  
        // Concatenate and remove duplicate names based on  
        // default string comparer  
        var mergeQuery = fileA.Union(fileB);  
  
        // Group the names by the first letter in the last name.  
        var groupQuery = from name in mergeQuery  
                         let n = name.Split(',')  
                         group name by n[0][0] into g  
                         orderby g.Key  
                         select g;  
  
        // Create a new file for each group that was created  
        // Note that nested foreach loops are required to access  
        // individual items with each group.  
        foreach (var g in groupQuery)  
        {  
            // Create the new file name.  
            string fileName = @"../../../testFile_" + g.Key + ".txt";  
  
            // Output to display.  
            Console.WriteLine(g.Key);  
  
            // Write file.  
            using (System.IO.StreamWriter sw = new System.IO.StreamWriter(fileName))  
            {  
                foreach (var item in g)  
                {  
                    sw.WriteLine(item);  
                    // Output to console for example purposes.  
                    Console.WriteLine("   {0}", item);  
                }  
            }  
        }  
        // Keep console window open in debug mode.  
        Console.WriteLine("Files have been written. Press any key to exit");  
        Console.ReadKey();  
    }  
}  
/* Output:
    A  
       Aw, Kam Foo  
    B  
       Bankov, Peter  
       Beebe, Ann  
    E  
       El Yassir, Mehdi  
    G  
       Garcia, Hugo  
       Guy, Wey Yuan  
       Garcia, Debra  
       Gilchrist, Beth  
       Giakoumakis, Leo  
    H  
       Holm, Michael  
    L  
       Liu, Jinghao  
    M  
       Myrcha, Jacek  
       McLin, Nkenge  
    N  
       Noriega, Fabricio  
    P  
       Potra, Cristina  
    T  
       Toyoshima, Tim  
 */  
```  
  
 <span data-ttu-id="7b931-110">Le programme écrit un fichier distinct pour chaque groupe, dans le même dossier que les fichiers de données.</span><span class="sxs-lookup"><span data-stu-id="7b931-110">The program writes a separate file for each group in the same folder as the data files.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7b931-111">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="7b931-111">Compiling the Code</span></span>

<span data-ttu-id="7b931-112">Créez un projet d’application console C# avec des directives `using` pour les espaces de noms System.Linq et System.IO.</span><span class="sxs-lookup"><span data-stu-id="7b931-112">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="7b931-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7b931-113">See also</span></span>

- [<span data-ttu-id="7b931-114">LINQ et chaînes (C#)</span><span class="sxs-lookup"><span data-stu-id="7b931-114">LINQ and Strings (C#)</span></span>](./linq-and-strings.md)
- [<span data-ttu-id="7b931-115">LINQ et répertoires de fichiers (C#)</span><span class="sxs-lookup"><span data-stu-id="7b931-115">LINQ and File Directories (C#)</span></span>](./linq-and-file-directories.md)
