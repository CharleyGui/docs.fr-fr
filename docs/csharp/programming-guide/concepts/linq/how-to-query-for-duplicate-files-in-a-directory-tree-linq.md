---
title: 'Procédure : Rechercher les fichiers dupliqués dans une arborescence de répertoires (LINQ) (C#)'
ms.date: 07/20/2015
ms.assetid: 1ff5562b-0d30-46d1-b426-a04e8f78c840
ms.openlocfilehash: a4d7ece3c69db294437ac0ca41ed5b1a3307e524
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65584340"
---
# <a name="how-to-query-for-duplicate-files-in-a-directory-tree-linq-c"></a><span data-ttu-id="73047-102">Procédure : Rechercher les fichiers dupliqués dans une arborescence de répertoires (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="73047-102">How to: Query for Duplicate Files in a Directory Tree (LINQ) (C#)</span></span>
<span data-ttu-id="73047-103">Parfois, plusieurs dossiers peuvent contenir des fichiers ayant le même nom.</span><span class="sxs-lookup"><span data-stu-id="73047-103">Sometimes files that have the same name may be located in more than one folder.</span></span> <span data-ttu-id="73047-104">Par exemple, sous le dossier d’installation de Visual Studio, plusieurs dossiers ont un fichier readme.htm.</span><span class="sxs-lookup"><span data-stu-id="73047-104">For example, under the Visual Studio installation folder, several folders have a readme.htm file.</span></span> <span data-ttu-id="73047-105">Cet exemple montre comment rechercher ces noms de fichiers dupliqués sous un dossier racine spécifié.</span><span class="sxs-lookup"><span data-stu-id="73047-105">This example shows how to query for such duplicate file names under a specified root folder.</span></span> <span data-ttu-id="73047-106">Le deuxième exemple montre comment rechercher des fichiers dont la taille et l’heure de création correspondent également.</span><span class="sxs-lookup"><span data-stu-id="73047-106">The second example shows how to query for files whose size and creation times also match.</span></span>  
  
## <a name="example"></a><span data-ttu-id="73047-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="73047-107">Example</span></span>  
  
```csharp  
class QueryDuplicateFileNames  
{  
    static void Main(string[] args)  
    {  
        // Uncomment QueryDuplicates2 to run that query.  
        QueryDuplicates();  
        // QueryDuplicates2();  
  
        // Keep the console window open in debug mode.  
        Console.WriteLine("Press any key to exit.");  
        Console.ReadKey();  
    }  
  
    static void QueryDuplicates()  
    {  
        // Change the root drive or folder if necessary  
        string startFolder = @"c:\program files\Microsoft Visual Studio 9.0\";  
  
        // Take a snapshot of the file system.  
        System.IO.DirectoryInfo dir = new System.IO.DirectoryInfo(startFolder);  
  
        // This method assumes that the application has discovery permissions  
        // for all folders under the specified path.  
        IEnumerable<System.IO.FileInfo> fileList = dir.GetFiles("*.*", System.IO.SearchOption.AllDirectories);  
  
        // used in WriteLine to keep the lines shorter  
        int charsToSkip = startFolder.Length;  
  
        // var can be used for convenience with groups.  
        var queryDupNames =  
            from file in fileList  
            group file.FullName.Substring(charsToSkip) by file.Name into fileGroup  
            where fileGroup.Count() > 1  
            select fileGroup;  
  
        // Pass the query to a method that will  
        // output one page at a time.  
        PageOutput<string, string>(queryDupNames);  
    }  
  
    // A Group key that can be passed to a separate method.  
    // Override Equals and GetHashCode to define equality for the key.  
    // Override ToString to provide a friendly name for Key.ToString()  
    class PortableKey  
    {  
        public string Name { get; set; }  
        public DateTime CreationTime { get; set; }  
        public long Length { get; set; }  
  
        public override bool Equals(object obj)  
        {  
            PortableKey other = (PortableKey)obj;  
            return other.CreationTime == this.CreationTime &&  
                   other.Length == this.Length &&  
                   other.Name == this.Name;  
        }  
  
        public override int GetHashCode()  
        {  
            string str = $"{this.CreationTime}{this.Length}{this.Name}";
            return str.GetHashCode();  
        }  
        public override string ToString()  
        {  
            return $"{this.Name} {this.Length} {this.CreationTime}";
        }  
    }  
    static void QueryDuplicates2()  
    {  
        // Change the root drive or folder if necessary.  
        string startFolder = @"c:\program files\Microsoft Visual Studio 9.0\Common7";  
  
        // Make the lines shorter for the console display  
        int charsToSkip = startFolder.Length;  
  
        // Take a snapshot of the file system.  
        System.IO.DirectoryInfo dir = new System.IO.DirectoryInfo(startFolder);  
        IEnumerable<System.IO.FileInfo> fileList = dir.GetFiles("*.*", System.IO.SearchOption.AllDirectories);  
  
        // Note the use of a compound key. Files that match  
        // all three properties belong to the same group.  
        // A named type is used to enable the query to be  
        // passed to another method. Anonymous types can also be used  
        // for composite keys but cannot be passed across method boundaries  
        //   
        var queryDupFiles =  
            from file in fileList  
            group file.FullName.Substring(charsToSkip) by  
                new PortableKey { Name = file.Name, CreationTime = file.CreationTime, Length = file.Length } into fileGroup  
            where fileGroup.Count() > 1  
            select fileGroup;  
  
        var list = queryDupFiles.ToList();  
  
        int i = queryDupFiles.Count();  
  
        PageOutput<PortableKey, string>(queryDupFiles);  
    }  
  
    // A generic method to page the output of the QueryDuplications methods  
    // Here the type of the group must be specified explicitly. "var" cannot  
    // be used in method signatures. This method does not display more than one  
    // group per page.  
    private static void PageOutput<K, V>(IEnumerable<System.Linq.IGrouping<K, V>> groupByExtList)  
    {  
        // Flag to break out of paging loop.  
        bool goAgain = true;  
  
        // "3" = 1 line for extension + 1 for "Press any key" + 1 for input cursor.  
        int numLines = Console.WindowHeight - 3;  
  
        // Iterate through the outer collection of groups.  
        foreach (var filegroup in groupByExtList)  
        {  
            // Start a new extension at the top of a page.  
            int currentLine = 0;  
  
            // Output only as many lines of the current group as will fit in the window.  
            do  
            {  
                Console.Clear();  
                Console.WriteLine("Filename = {0}", filegroup.Key.ToString() == String.Empty ? "[none]" : filegroup.Key.ToString());  
  
                // Get 'numLines' number of items starting at number 'currentLine'.  
                var resultPage = filegroup.Skip(currentLine).Take(numLines);  
  
                //Execute the resultPage query  
                foreach (var fileName in resultPage)  
                {  
                    Console.WriteLine("\t{0}", fileName);  
                }  
  
                // Increment the line counter.  
                currentLine += numLines;  
  
                // Give the user a chance to escape.  
                Console.WriteLine("Press any key to continue or the 'End' key to break...");  
                ConsoleKey key = Console.ReadKey().Key;  
                if (key == ConsoleKey.End)  
                {  
                    goAgain = false;  
                    break;  
                }  
            } while (currentLine < filegroup.Count());  
  
            if (goAgain == false)  
                break;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="73047-108">La première requête utilise une clé simple pour déterminer une correspondance ; elle trouve les fichiers qui ont le même nom mais dont le contenu peut être différent.</span><span class="sxs-lookup"><span data-stu-id="73047-108">The first query uses a simple key to determine a match; this finds files that have the same name but whose contents might be different.</span></span> <span data-ttu-id="73047-109">La deuxième requête utilise une clé composée à comparer à trois propriétés de l’objet <xref:System.IO.FileInfo>.</span><span class="sxs-lookup"><span data-stu-id="73047-109">The second query uses a compound key to match against three properties of the <xref:System.IO.FileInfo> object.</span></span> <span data-ttu-id="73047-110">Cette requête est beaucoup plus susceptible de trouver les fichiers ayant le même nom et un contenu similaire ou identique.</span><span class="sxs-lookup"><span data-stu-id="73047-110">This query is much more likely to find files that have the same name and similar or identical content.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="73047-111">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="73047-111">Compiling the Code</span></span>  
 <span data-ttu-id="73047-112">Créez un projet d’application console C#, avec des directives `using` pour les espaces de noms System.Linq et System.IO.</span><span class="sxs-lookup"><span data-stu-id="73047-112">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73047-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="73047-113">See also</span></span>

- [<span data-ttu-id="73047-114">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="73047-114">LINQ to Objects (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)
- [<span data-ttu-id="73047-115">LINQ et répertoires de fichiers (C#)</span><span class="sxs-lookup"><span data-stu-id="73047-115">LINQ and File Directories (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-and-file-directories.md)
