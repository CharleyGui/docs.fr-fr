---
title: Comment fractionner un fichier en plusieurs fichiers à l’aide de groupes (LINQ) (C#)
description: Découvrez comment fractionner un fichier en plusieurs fichiers à l’aide de groupes. Consultez un exemple de code et affichez des ressources supplémentaires disponibles.
ms.date: 07/20/2015
ms.assetid: 8179b91c-d778-4e57-884f-77fe5a8e4e40
ms.openlocfilehash: 1db16a48db257069eca83127c0b1fed7e49f19d6
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301058"
---
# <a name="how-to-split-a-file-into-many-files-by-using-groups-linq-c"></a>Comment fractionner un fichier en plusieurs fichiers à l’aide de groupes (LINQ) (C#)
Cet exemple montre comment fusionner le contenu de deux fichiers, puis créer un ensemble de fichiers qui organisent les données d’une nouvelle façon.  
  
### <a name="to-create-the-data-files"></a>Pour créer le fichier de données  
  
1. Copiez ces noms dans un fichier texte nommé names1.txt, puis enregistrez-le dans votre dossier de projet :  
  
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
  
2. Copiez ces noms dans un fichier texte nommé names2.txt, puis enregistrez-le dans votre dossier de projet. Notez que les deux fichiers ont certains noms en commun.  
  
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
  
## <a name="example"></a>Exemple  
  
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
  
 Le programme écrit un fichier distinct pour chaque groupe, dans le même dossier que les fichiers de données.  
  
## <a name="compiling-the-code"></a>Compilation du code

Créez un projet d’application console C# avec des directives `using` pour les espaces de noms System.Linq et System.IO.
  
## <a name="see-also"></a>Voir aussi

- [LINQ et chaînes (C#)](./linq-and-strings.md)
- [LINQ et répertoires de fichiers (C#)](./linq-and-file-directories.md)
