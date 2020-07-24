---
title: Comment interroger le contenu de fichiers texte dans un dossier (LINQ) (C#)
description: Découvrez comment utiliser LINQ en C# pour interroger tous les fichiers d’une arborescence de répertoires, ouvrir chaque fichier et inspecter son contenu.
ms.date: 07/20/2015
ms.assetid: f5b4dce7-1a34-4eb4-9bf1-60d5bdda264c
ms.openlocfilehash: 216edc2ee6fc43fd06a3c89b1b6b73f693f752f8
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104269"
---
# <a name="how-to-query-the-contents-of-text-files-in-a-folder-linq-c"></a><span data-ttu-id="7bd80-103">Comment interroger le contenu de fichiers texte dans un dossier (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="7bd80-103">How to query the contents of text files in a folder (LINQ) (C#)</span></span>
<span data-ttu-id="7bd80-104">Cet exemple montre comment interroger tous les fichiers d’une arborescence de répertoires spécifiée, comment ouvrir chaque fichier et comment inspecter son contenu.</span><span class="sxs-lookup"><span data-stu-id="7bd80-104">This example shows how to query over all the files in a specified directory tree, open each file, and inspect its contents.</span></span> <span data-ttu-id="7bd80-105">Ce type de technique peut être utilisé pour créer des index ou des index inversés à partir du contenu d’une arborescence de répertoires.</span><span class="sxs-lookup"><span data-stu-id="7bd80-105">This type of technique could be used to create indexes or reverse indexes of the contents of a directory tree.</span></span> <span data-ttu-id="7bd80-106">Dans cet exemple, une recherche de chaîne simple est effectuée.</span><span class="sxs-lookup"><span data-stu-id="7bd80-106">A simple string search is performed in this example.</span></span> <span data-ttu-id="7bd80-107">Toutefois, il est possible d’effectuer une recherche avec des critères spéciaux plus complexes à l’aide d’une expression régulière.</span><span class="sxs-lookup"><span data-stu-id="7bd80-107">However, more complex types of pattern matching can be performed with a regular expression.</span></span> <span data-ttu-id="7bd80-108">Pour plus d’informations, consultez Guide pratique [pour combiner des requêtes LINQ avec des expressions régulières (C#)](./how-to-combine-linq-queries-with-regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="7bd80-108">For more information, see [How to combine LINQ queries with regular expressions (C#)](./how-to-combine-linq-queries-with-regular-expressions.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7bd80-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="7bd80-109">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="7bd80-110">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="7bd80-110">Compiling the Code</span></span>  
<span data-ttu-id="7bd80-111">Créez un projet d’application console C# avec des directives `using` pour les espaces de noms System.Linq et System.IO.</span><span class="sxs-lookup"><span data-stu-id="7bd80-111">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="7bd80-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7bd80-112">See also</span></span>

- [<span data-ttu-id="7bd80-113">LINQ et répertoires de fichiers (C#)</span><span class="sxs-lookup"><span data-stu-id="7bd80-113">LINQ and File Directories (C#)</span></span>](./linq-and-file-directories.md)
- [<span data-ttu-id="7bd80-114">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="7bd80-114">LINQ to Objects (C#)</span></span>](./linq-to-objects.md)
