---
title: Comment interroger les fichiers les plus volumineux dans une arborescence de répertoires (LINQ) (C#)
description: Cet exemple C# montre cinq requêtes LINQ relatives à la taille de fichier en octets. Vous pouvez les modifier pour effectuer une requête sur une autre propriété de l’objet FileInfo.
ms.date: 07/20/2015
ms.assetid: 20c8a917-0552-4514-b489-0b8b6a4c3b4c
ms.openlocfilehash: 049db9bf104af1593ba9807c307008e8e760da32
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91176251"
---
# <a name="how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq-c"></a><span data-ttu-id="9b507-104">Comment interroger les fichiers les plus volumineux dans une arborescence de répertoires (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="9b507-104">How to query for the largest file or files in a directory tree (LINQ) (C#)</span></span>

<span data-ttu-id="9b507-105">Cet exemple montre cinq requêtes liées à la taille des fichiers en octets :</span><span class="sxs-lookup"><span data-stu-id="9b507-105">This example shows five queries related to file size in bytes:</span></span>  
  
- <span data-ttu-id="9b507-106">Comment récupérer la taille en octets du plus grand fichier.</span><span class="sxs-lookup"><span data-stu-id="9b507-106">How to retrieve the size in bytes of the largest file.</span></span>  
  
- <span data-ttu-id="9b507-107">Comment récupérer la taille en octets du plus petit fichier.</span><span class="sxs-lookup"><span data-stu-id="9b507-107">How to retrieve the size in bytes of the smallest file.</span></span>  
  
- <span data-ttu-id="9b507-108">Comment récupérer le plus grand ou le plus petit fichier de l’objet <xref:System.IO.FileInfo> dans un ou plusieurs dossiers situés dans le dossier racine spécifié.</span><span class="sxs-lookup"><span data-stu-id="9b507-108">How to retrieve the <xref:System.IO.FileInfo> object largest or smallest file from one or more folders under a specified root folder.</span></span>  
  
- <span data-ttu-id="9b507-109">Comment récupérer une séquence, telle que les 10 fichiers les plus volumineux.</span><span class="sxs-lookup"><span data-stu-id="9b507-109">How to retrieve a sequence such as the 10 largest files.</span></span>  
  
- <span data-ttu-id="9b507-110">Comment regrouper des fichiers selon leur taille en octets, en ignorant les fichiers qui sont inférieurs à une taille spécifiée.</span><span class="sxs-lookup"><span data-stu-id="9b507-110">How to order files into groups based on their file size in bytes, ignoring files that are less than a specified size.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9b507-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="9b507-111">Example</span></span>  

 <span data-ttu-id="9b507-112">L’exemple suivant contient cinq requêtes distinctes qui montrent comment interroger et regrouper des fichiers selon leur taille en octets.</span><span class="sxs-lookup"><span data-stu-id="9b507-112">The following example contains five separate queries that show how to query and group files, depending on their file size in bytes.</span></span> <span data-ttu-id="9b507-113">Vous pouvez facilement modifier ces exemples pour baser la requête sur une autre propriété de l’objet <xref:System.IO.FileInfo>.</span><span class="sxs-lookup"><span data-stu-id="9b507-113">You can easily modify these examples to base the query on some other property of the <xref:System.IO.FileInfo> object.</span></span>  
  
```csharp  
class QueryBySize  
{  
    static void Main(string[] args)  
    {  
        QueryFilesBySize();  
        Console.WriteLine("Press any key to exit");  
        Console.ReadKey();  
    }  
  
    private static void QueryFilesBySize()  
    {  
        string startFolder = @"c:\program files\Microsoft Visual Studio 9.0\";  
  
        // Take a snapshot of the file system.  
        System.IO.DirectoryInfo dir = new System.IO.DirectoryInfo(startFolder);  
  
        // This method assumes that the application has discovery permissions  
        // for all folders under the specified path.  
        IEnumerable<System.IO.FileInfo> fileList = dir.GetFiles("*.*", System.IO.SearchOption.AllDirectories);  
  
        //Return the size of the largest file  
        long maxSize =  
            (from file in fileList  
             let len = GetFileLength(file)  
             select len)  
             .Max();  
  
        Console.WriteLine("The length of the largest file under {0} is {1}",  
            startFolder, maxSize);  
  
        // Return the FileInfo object for the largest file  
        // by sorting and selecting from beginning of list  
        System.IO.FileInfo longestFile =  
            (from file in fileList  
             let len = GetFileLength(file)  
             where len > 0  
             orderby len descending  
             select file)  
            .First();  
  
        Console.WriteLine("The largest file under {0} is {1} with a length of {2} bytes",  
                            startFolder, longestFile.FullName, longestFile.Length);  
  
        //Return the FileInfo of the smallest file  
        System.IO.FileInfo smallestFile =  
            (from file in fileList  
             let len = GetFileLength(file)  
             where len > 0  
             orderby len ascending  
             select file).First();  
  
        Console.WriteLine("The smallest file under {0} is {1} with a length of {2} bytes",  
                            startFolder, smallestFile.FullName, smallestFile.Length);  
  
        //Return the FileInfos for the 10 largest files  
        // queryTenLargest is an IEnumerable<System.IO.FileInfo>  
        var queryTenLargest =  
            (from file in fileList  
             let len = GetFileLength(file)  
             orderby len descending  
             select file).Take(10);  
  
        Console.WriteLine("The 10 largest files under {0} are:", startFolder);  
  
        foreach (var v in queryTenLargest)  
        {  
            Console.WriteLine("{0}: {1} bytes", v.FullName, v.Length);  
        }  
  
        // Group the files according to their size, leaving out  
        // files that are less than 200000 bytes.
        var querySizeGroups =  
            from file in fileList  
            let len = GetFileLength(file)  
            where len > 0  
            group file by (len / 100000) into fileGroup  
            where fileGroup.Key >= 2  
            orderby fileGroup.Key descending  
            select fileGroup;  
  
        foreach (var filegroup in querySizeGroups)  
        {  
            Console.WriteLine(filegroup.Key.ToString() + "00000");  
            foreach (var item in filegroup)  
            {  
                Console.WriteLine("\t{0}: {1}", item.Name, item.Length);  
            }  
        }  
    }  
  
    // This method is used to swallow the possible exception  
    // that can be raised when accessing the FileInfo.Length property.  
    // In this particular case, it is safe to swallow the exception.  
    static long GetFileLength(System.IO.FileInfo fi)  
    {  
        long retval;  
        try  
        {  
            retval = fi.Length;  
        }  
        catch (System.IO.FileNotFoundException)  
        {  
            // If a file is no longer present,  
            // just add zero bytes to the total.  
            retval = 0;  
        }  
        return retval;  
    }  
  
}  
```  
  
 <span data-ttu-id="9b507-114">Pour retourner un ou plusieurs objets <xref:System.IO.FileInfo> complets, la requête doit d’abord examiner chacun d’eux dans la source de données, puis les trier selon la valeur de leur propriété Length.</span><span class="sxs-lookup"><span data-stu-id="9b507-114">To return one or more complete <xref:System.IO.FileInfo> objects, the query first must examine each one in the data source, and then sort them by the value of their Length property.</span></span> <span data-ttu-id="9b507-115">Elle peut ensuite retourner l’objet ou la séquence d’objets avec les plus grandes valeurs de longueur.</span><span class="sxs-lookup"><span data-stu-id="9b507-115">Then it can return the single one or the sequence with the greatest lengths.</span></span> <span data-ttu-id="9b507-116">Utilisez <xref:System.Linq.Enumerable.First%2A> pour retourner le premier élément d’une liste.</span><span class="sxs-lookup"><span data-stu-id="9b507-116">Use <xref:System.Linq.Enumerable.First%2A> to return the first element in a list.</span></span> <span data-ttu-id="9b507-117">Utilisez <xref:System.Linq.Enumerable.Take%2A> pour retourner les n premiers éléments.</span><span class="sxs-lookup"><span data-stu-id="9b507-117">Use <xref:System.Linq.Enumerable.Take%2A> to return the first n number of elements.</span></span> <span data-ttu-id="9b507-118">Spécifiez un ordre de tri décroissant pour placer les plus petits éléments au début de la liste.</span><span class="sxs-lookup"><span data-stu-id="9b507-118">Specify a descending sort order to put the smallest elements at the start of the list.</span></span>  
  
 <span data-ttu-id="9b507-119">La requête appelle une méthode distincte pour obtenir la taille du fichier en octets et ainsi permettre l’utilisation de l’exception éventuellement levée si un fichier a été supprimé sur un autre thread depuis la création de l’objet <xref:System.IO.FileInfo> dans l’appel à `GetFiles`.</span><span class="sxs-lookup"><span data-stu-id="9b507-119">The query calls out to a separate method to obtain the file size in bytes in order to consume the possible exception that will be raised in the case where a file was deleted on another thread in the time period since the <xref:System.IO.FileInfo> object was created in the call to `GetFiles`.</span></span> <span data-ttu-id="9b507-120">Même si l’objet <xref:System.IO.FileInfo> a déjà été créé, l’exception peut être levée, car un objet <xref:System.IO.FileInfo> essaiera d’actualiser sa propriété <xref:System.IO.FileInfo.Length%2A> en utilisant la taille en octets la plus récente lors du premier accès à la propriété.</span><span class="sxs-lookup"><span data-stu-id="9b507-120">Even through the <xref:System.IO.FileInfo> object has already been created, the exception can occur because a <xref:System.IO.FileInfo> object will try to refresh its <xref:System.IO.FileInfo.Length%2A> property by using the most current size in bytes the first time the property is accessed.</span></span> <span data-ttu-id="9b507-121">En plaçant cette opération dans un bloc try-catch en dehors de la requête, nous respectons la règle qui consiste à éviter les opérations dans les requêtes qui peuvent avoir des effets secondaires.</span><span class="sxs-lookup"><span data-stu-id="9b507-121">By putting this operation in a try-catch block outside the query, we follow the rule of avoiding operations in queries that can cause side-effects.</span></span> <span data-ttu-id="9b507-122">En règle générale, il faut faire très attention lors de l’utilisation d’exceptions et s’assurer que l’application ne reste pas dans un état inconnu.</span><span class="sxs-lookup"><span data-stu-id="9b507-122">In general, great care must be taken when consuming exceptions, to make sure that an application is not left in an unknown state.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9b507-123">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="9b507-123">Compiling the Code</span></span>  

<span data-ttu-id="9b507-124">Créez un projet d’application console C# avec des directives `using` pour les espaces de noms System.Linq et System.IO.</span><span class="sxs-lookup"><span data-stu-id="9b507-124">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>

## <a name="see-also"></a><span data-ttu-id="9b507-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9b507-125">See also</span></span>

- [<span data-ttu-id="9b507-126">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="9b507-126">LINQ to Objects (C#)</span></span>](./linq-to-objects.md)
- [<span data-ttu-id="9b507-127">LINQ et répertoires de fichiers (C#)</span><span class="sxs-lookup"><span data-stu-id="9b507-127">LINQ and File Directories (C#)</span></span>](./linq-and-file-directories.md)
