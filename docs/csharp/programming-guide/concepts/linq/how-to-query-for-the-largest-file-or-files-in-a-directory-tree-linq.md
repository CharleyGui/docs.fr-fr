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
# <a name="how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq-c"></a>Comment interroger les fichiers les plus volumineux dans une arborescence de répertoires (LINQ) (C#)

Cet exemple montre cinq requêtes liées à la taille des fichiers en octets :  
  
- Comment récupérer la taille en octets du plus grand fichier.  
  
- Comment récupérer la taille en octets du plus petit fichier.  
  
- Comment récupérer le plus grand ou le plus petit fichier de l’objet <xref:System.IO.FileInfo> dans un ou plusieurs dossiers situés dans le dossier racine spécifié.  
  
- Comment récupérer une séquence, telle que les 10 fichiers les plus volumineux.  
  
- Comment regrouper des fichiers selon leur taille en octets, en ignorant les fichiers qui sont inférieurs à une taille spécifiée.  
  
## <a name="example"></a>Exemple  

 L’exemple suivant contient cinq requêtes distinctes qui montrent comment interroger et regrouper des fichiers selon leur taille en octets. Vous pouvez facilement modifier ces exemples pour baser la requête sur une autre propriété de l’objet <xref:System.IO.FileInfo>.  
  
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
  
 Pour retourner un ou plusieurs objets <xref:System.IO.FileInfo> complets, la requête doit d’abord examiner chacun d’eux dans la source de données, puis les trier selon la valeur de leur propriété Length. Elle peut ensuite retourner l’objet ou la séquence d’objets avec les plus grandes valeurs de longueur. Utilisez <xref:System.Linq.Enumerable.First%2A> pour retourner le premier élément d’une liste. Utilisez <xref:System.Linq.Enumerable.Take%2A> pour retourner les n premiers éléments. Spécifiez un ordre de tri décroissant pour placer les plus petits éléments au début de la liste.  
  
 La requête appelle une méthode distincte pour obtenir la taille du fichier en octets et ainsi permettre l’utilisation de l’exception éventuellement levée si un fichier a été supprimé sur un autre thread depuis la création de l’objet <xref:System.IO.FileInfo> dans l’appel à `GetFiles`. Même si l’objet <xref:System.IO.FileInfo> a déjà été créé, l’exception peut être levée, car un objet <xref:System.IO.FileInfo> essaiera d’actualiser sa propriété <xref:System.IO.FileInfo.Length%2A> en utilisant la taille en octets la plus récente lors du premier accès à la propriété. En plaçant cette opération dans un bloc try-catch en dehors de la requête, nous respectons la règle qui consiste à éviter les opérations dans les requêtes qui peuvent avoir des effets secondaires. En règle générale, il faut faire très attention lors de l’utilisation d’exceptions et s’assurer que l’application ne reste pas dans un état inconnu.  
  
## <a name="compiling-the-code"></a>Compilation du code  

Créez un projet d’application console C# avec des directives `using` pour les espaces de noms System.Linq et System.IO.

## <a name="see-also"></a>Voir aussi

- [LINQ to Objects (C#)](./linq-to-objects.md)
- [LINQ et répertoires de fichiers (C#)](./linq-and-file-directories.md)
