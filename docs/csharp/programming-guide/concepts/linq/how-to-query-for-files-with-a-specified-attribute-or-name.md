---
title: Comment rechercher des fichiers avec un attribut ou un nom spécifié (C#)
description: Découvrez comment utiliser LINQ en C# pour rechercher des fichiers qui ont une extension de nom de fichier spécifiée dans une arborescence de répertoires et comment retourner le fichier le plus récent ou le plus ancien.
ms.date: 07/20/2015
ms.assetid: 560e3879-b0b3-4549-ad02-0a53aff2f83c
ms.openlocfilehash: 01a3482d8ea4c95b60dd9434320f175f0498c3e8
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91165310"
---
# <a name="how-to-query-for-files-with-a-specified-attribute-or-name-c"></a><span data-ttu-id="76f07-103">Comment rechercher des fichiers avec un attribut ou un nom spécifié (C#)</span><span class="sxs-lookup"><span data-stu-id="76f07-103">How to query for files with a specified attribute or name (C#)</span></span>

<span data-ttu-id="76f07-104">Cet exemple montre comment rechercher tous les fichiers ayant une extension de nom de fichier spécifiée (par exemple « .txt ») dans une arborescence de répertoires spécifiée.</span><span class="sxs-lookup"><span data-stu-id="76f07-104">This example shows how to find all files that have a specified file name extension (for example ".txt") in a specified directory tree.</span></span> <span data-ttu-id="76f07-105">Il montre également comment retourner le fichier le plus récent ou le plus ancien dans l’arborescence en fonction de l’heure de création.</span><span class="sxs-lookup"><span data-stu-id="76f07-105">It also shows how to return either the newest or oldest file in the tree based on the creation time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="76f07-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="76f07-106">Example</span></span>  
  
```csharp  
class FindFileByExtension  
{  
    // This query will produce the full path for all .txt files  
    // under the specified folder including subfolders.  
    // It orders the list according to the file name.  
    static void Main()  
    {  
        string startFolder = @"c:\program files\Microsoft Visual Studio 9.0\";  
  
        // Take a snapshot of the file system.  
        System.IO.DirectoryInfo dir = new System.IO.DirectoryInfo(startFolder);  
  
        // This method assumes that the application has discovery permissions  
        // for all folders under the specified path.  
        IEnumerable<System.IO.FileInfo> fileList = dir.GetFiles("*.*", System.IO.SearchOption.AllDirectories);  
  
        //Create the query  
        IEnumerable<System.IO.FileInfo> fileQuery =  
            from file in fileList  
            where file.Extension == ".txt"  
            orderby file.Name  
            select file;  
  
        //Execute the query. This might write out a lot of files!  
        foreach (System.IO.FileInfo fi in fileQuery)  
        {  
            Console.WriteLine(fi.FullName);  
        }  
  
        // Create and execute a new query by using the previous
        // query as a starting point. fileQuery is not
        // executed again until the call to Last()  
        var newestFile =  
            (from file in fileQuery  
             orderby file.CreationTime  
             select new { file.FullName, file.CreationTime })  
            .Last();  
  
        Console.WriteLine("\r\nThe newest .txt file is {0}. Creation time: {1}",  
            newestFile.FullName, newestFile.CreationTime);  
  
        // Keep the console window open in debug mode.  
        Console.WriteLine("Press any key to exit");  
        Console.ReadKey();  
    }  
}  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="76f07-107">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="76f07-107">Compiling the Code</span></span>  

  <span data-ttu-id="76f07-108">Créez un projet d’application console C# avec des directives `using` pour les espaces de noms System.Linq et System.IO.</span><span class="sxs-lookup"><span data-stu-id="76f07-108">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="76f07-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="76f07-109">See also</span></span>

- [<span data-ttu-id="76f07-110">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="76f07-110">LINQ to Objects (C#)</span></span>](./linq-to-objects.md)
- [<span data-ttu-id="76f07-111">LINQ et répertoires de fichiers (C#)</span><span class="sxs-lookup"><span data-stu-id="76f07-111">LINQ and File Directories (C#)</span></span>](./linq-and-file-directories.md)
