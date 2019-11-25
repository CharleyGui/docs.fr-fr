---
title: Comment combiner des requêtes LINQ avec des expressions régulières (C#)
ms.date: 07/20/2015
ms.assetid: 6b003b65-20a4-4ca2-929e-2ee3f215aecc
ms.openlocfilehash: 97551f7d9d8cf13f05449c2f825ed4d29eb3d86e
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141411"
---
# <a name="how-to-combine-linq-queries-with-regular-expressions-c"></a><span data-ttu-id="3ccad-102">Comment combiner des requêtes LINQ avec des expressions régulières (C#)</span><span class="sxs-lookup"><span data-stu-id="3ccad-102">How to combine LINQ queries with regular expressions (C#)</span></span>
<span data-ttu-id="3ccad-103">Cet exemple montre comment utiliser la classe <xref:System.Text.RegularExpressions.Regex> afin de créer une expression régulière pour les correspondances plus complexes des chaînes de texte.</span><span class="sxs-lookup"><span data-stu-id="3ccad-103">This example shows how to use the <xref:System.Text.RegularExpressions.Regex> class to create a regular expression for more complex matching in text strings.</span></span> <span data-ttu-id="3ccad-104">La requête LINQ facilite le filtrage des fichiers à parcourir à l’aide de l’expression régulière, et facilite également la personnalisation des résultats.</span><span class="sxs-lookup"><span data-stu-id="3ccad-104">The LINQ query makes it easy to filter on exactly the files that you want to search with the regular expression, and to shape the results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3ccad-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="3ccad-105">Example</span></span>  
  
```csharp  
class QueryWithRegEx  
{  
    public static void Main()  
    {  
        // Modify this path as necessary so that it accesses your version of Visual Studio.  
        string startFolder = @"C:\Program Files (x86)\Microsoft Visual Studio 14.0\";  
        // One of the following paths may be more appropriate on your computer.  
        //string startFolder = @"C:\Program Files (x86)\Microsoft Visual Studio\2017\";  
  
        // Take a snapshot of the file system.  
        IEnumerable<System.IO.FileInfo> fileList = GetFiles(startFolder);  
  
        // Create the regular expression to find all things "Visual".  
        System.Text.RegularExpressions.Regex searchTerm =  
            new System.Text.RegularExpressions.Regex(@"Visual (Basic|C#|C\+\+|Studio)");  
  
        // Search the contents of each .htm file.  
        // Remove the where clause to find even more matchedValues!  
        // This query produces a list of files where a match  
        // was found, and a list of the matchedValues in that file.  
        // Note: Explicit typing of "Match" in select clause.  
        // This is required because MatchCollection is not a   
        // generic IEnumerable collection.  
        var queryMatchingFiles =  
            from file in fileList  
            where file.Extension == ".htm"  
            let fileText = System.IO.File.ReadAllText(file.FullName)  
            let matches = searchTerm.Matches(fileText)  
            where matches.Count > 0  
            select new  
            {  
                name = file.FullName,  
                matchedValues = from System.Text.RegularExpressions.Match match in matches  
                                select match.Value  
            };  
  
        // Execute the query.  
        Console.WriteLine("The term \"{0}\" was found in:", searchTerm.ToString());  
  
        foreach (var v in queryMatchingFiles)  
        {  
            // Trim the path a bit, then write   
            // the file name in which a match was found.  
            string s = v.name.Substring(startFolder.Length - 1);  
            Console.WriteLine(s);  
  
            // For this file, write out all the matching strings  
            foreach (var v2 in v.matchedValues)  
            {  
                Console.WriteLine("  " + v2);  
            }  
        }  
  
        // Keep the console window open in debug mode  
        Console.WriteLine("Press any key to exit");  
        Console.ReadKey();  
    }  
  
    // This method assumes that the application has discovery   
    // permissions for all folders under the specified path.  
    static IEnumerable<System.IO.FileInfo> GetFiles(string path)  
    {  
        if (!System.IO.Directory.Exists(path))  
            throw new System.IO.DirectoryNotFoundException();  
  
        string[] fileNames = null;  
        List<System.IO.FileInfo> files = new List<System.IO.FileInfo>();  
  
        fileNames = System.IO.Directory.GetFiles(path, "*.*", System.IO.SearchOption.AllDirectories);  
        foreach (string name in fileNames)  
        {  
            files.Add(new System.IO.FileInfo(name));  
        }  
        return files;  
    }  
}  
```  
  
 <span data-ttu-id="3ccad-106">Notez que vous pouvez également interroger l’objet <xref:System.Text.RegularExpressions.MatchCollection> qui est retourné par une recherche `RegEx`.</span><span class="sxs-lookup"><span data-stu-id="3ccad-106">Note that you can also query the <xref:System.Text.RegularExpressions.MatchCollection> object that is returned by a `RegEx` search.</span></span> <span data-ttu-id="3ccad-107">Dans cet exemple, seule la valeur de chaque correspondance est générée dans les résultats.</span><span class="sxs-lookup"><span data-stu-id="3ccad-107">In this example only the value of each match is produced in the results.</span></span> <span data-ttu-id="3ccad-108">Toutefois, il est également possible d’utiliser LINQ pour effectuer toutes sortes de filtrage, de tri et de regroupement au sein de cette collection.</span><span class="sxs-lookup"><span data-stu-id="3ccad-108">However, it is also possible to use LINQ to perform all kinds of filtering, sorting, and grouping on that collection.</span></span> <span data-ttu-id="3ccad-109">Étant donné que <xref:System.Text.RegularExpressions.MatchCollection> est une collection <xref:System.Collections.IEnumerable> non générique, vous devez déclarer explicitement le type de la variable de portée dans la requête.</span><span class="sxs-lookup"><span data-stu-id="3ccad-109">Because <xref:System.Text.RegularExpressions.MatchCollection> is a non-generic <xref:System.Collections.IEnumerable> collection, you have to explicitly state the type of the range variable in the query.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="3ccad-110">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="3ccad-110">Compiling the Code</span></span>  
 <span data-ttu-id="3ccad-111">Créez un projet d’application console C# avec des directives `using` pour les espaces de noms System.Linq et System.IO.</span><span class="sxs-lookup"><span data-stu-id="3ccad-111">Create a C# console application project with `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ccad-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3ccad-112">See also</span></span>

- [<span data-ttu-id="3ccad-113">LINQ et chaînes (C#)</span><span class="sxs-lookup"><span data-stu-id="3ccad-113">LINQ and Strings (C#)</span></span>](./linq-and-strings.md)
- [<span data-ttu-id="3ccad-114">LINQ et répertoires de fichiers (C#)</span><span class="sxs-lookup"><span data-stu-id="3ccad-114">LINQ and File Directories (C#)</span></span>](./linq-and-file-directories.md)
