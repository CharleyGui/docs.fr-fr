---
title: Comment interroger le contenu des fichiers texte dans un dossier (LINQ) (C)
ms.date: 07/20/2015
ms.assetid: f5b4dce7-1a34-4eb4-9bf1-60d5bdda264c
ms.openlocfilehash: 998fddd3f59ee64df9adcee1acc720d82861c3d9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79168737"
---
# <a name="how-to-query-the-contents-of-text-files-in-a-folder-linq-c"></a><span data-ttu-id="ca838-102">Comment interroger le contenu des fichiers texte dans un dossier (LINQ) (C)</span><span class="sxs-lookup"><span data-stu-id="ca838-102">How to query the contents of text files in a folder (LINQ) (C#)</span></span>
<span data-ttu-id="ca838-103">Cet exemple montre comment interroger tous les fichiers d’une arborescence de répertoires spécifiée, comment ouvrir chaque fichier et comment inspecter son contenu.</span><span class="sxs-lookup"><span data-stu-id="ca838-103">This example shows how to query over all the files in a specified directory tree, open each file, and inspect its contents.</span></span> <span data-ttu-id="ca838-104">Ce type de technique peut être utilisé pour créer des index ou des index inversés à partir du contenu d’une arborescence de répertoires.</span><span class="sxs-lookup"><span data-stu-id="ca838-104">This type of technique could be used to create indexes or reverse indexes of the contents of a directory tree.</span></span> <span data-ttu-id="ca838-105">Dans cet exemple, une recherche de chaîne simple est effectuée.</span><span class="sxs-lookup"><span data-stu-id="ca838-105">A simple string search is performed in this example.</span></span> <span data-ttu-id="ca838-106">Toutefois, il est possible d’effectuer une recherche avec des critères spéciaux plus complexes à l’aide d’une expression régulière.</span><span class="sxs-lookup"><span data-stu-id="ca838-106">However, more complex types of pattern matching can be performed with a regular expression.</span></span> <span data-ttu-id="ca838-107">Pour plus d’informations, voir [Comment combiner les requêtes LINQ avec des expressions régulières ( CMD)](./how-to-combine-linq-queries-with-regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="ca838-107">For more information, see [How to combine LINQ queries with regular expressions (C#)](./how-to-combine-linq-queries-with-regular-expressions.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ca838-108"> Exemple</span><span class="sxs-lookup"><span data-stu-id="ca838-108">Example</span></span>  
  
```csharp  
class QueryContents  
{  
    public static void Main()  
    {  
        // Modify this path as necessary.  
        string startFolder = @"c:\program files\Microsoft Visual Studio 9.0\";  
  
        // Take a snapshot of the file system.  
        System.IO.DirectoryInfo dir = new System.IO.DirectoryInfo(startFolder);  
  
        // This method assumes that the application has discovery permissions  
        // for all folders under the specified path.  
        IEnumerable<System.IO.FileInfo> fileList = dir.GetFiles("*.*", System.IO.SearchOption.AllDirectories);  
  
        string searchTerm = @"Visual Studio";  
  
        // Search the contents of each file.  
        // A regular expression created with the RegEx class  
        // could be used instead of the Contains method.  
        // queryMatchingFiles is an IEnumerable<string>.  
        var queryMatchingFiles =  
            from file in fileList  
            where file.Extension == ".htm"  
            let fileText = GetFileText(file.FullName)  
            where fileText.Contains(searchTerm)  
            select file.FullName;  
  
        // Execute the query.  
        Console.WriteLine("The term \"{0}\" was found in:", searchTerm);  
        foreach (string filename in queryMatchingFiles)  
        {  
            Console.WriteLine(filename);  
        }  
  
        // Keep the console window open in debug mode.  
        Console.WriteLine("Press any key to exit");  
        Console.ReadKey();  
    }  
  
    // Read the contents of the file.  
    static string GetFileText(string name)  
    {  
        string fileContents = String.Empty;  
  
        // If the file has been deleted since we took
        // the snapshot, ignore it and return the empty string.  
        if (System.IO.File.Exists(name))  
        {  
            fileContents = System.IO.File.ReadAllText(name);  
        }  
        return fileContents;  
    }  
}  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ca838-109">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="ca838-109">Compiling the Code</span></span>  
<span data-ttu-id="ca838-110">Créez un projet d’application console C# avec des directives `using` pour les espaces de noms System.Linq et System.IO.</span><span class="sxs-lookup"><span data-stu-id="ca838-110">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="ca838-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ca838-111">See also</span></span>

- [<span data-ttu-id="ca838-112">LINQ et répertoires de fichiers (C#)</span><span class="sxs-lookup"><span data-stu-id="ca838-112">LINQ and File Directories (C#)</span></span>](./linq-and-file-directories.md)
- [<span data-ttu-id="ca838-113">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="ca838-113">LINQ to Objects (C#)</span></span>](./linq-to-objects.md)
