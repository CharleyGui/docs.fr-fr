---
title: 'Procédure : rechercher des fichiers ayant un attribut ou un nom donné'
ms.date: 07/20/2015
ms.assetid: b26026a3-3f43-448f-a582-259997af6be0
ms.openlocfilehash: eeacd94fb303a439e8034b84d285ab11b2333581
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91059312"
---
# <a name="how-to-query-for-files-with-a-specified-attribute-or-name-visual-basic"></a><span data-ttu-id="56593-102">Comment : interroger des fichiers ayant un attribut ou un nom spécifié (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="56593-102">How to: Query for Files with a Specified Attribute or Name (Visual Basic)</span></span>

<span data-ttu-id="56593-103">Cet exemple montre comment rechercher tous les fichiers ayant une extension de nom de fichier spécifiée (par exemple « .txt ») dans une arborescence de répertoires spécifiée.</span><span class="sxs-lookup"><span data-stu-id="56593-103">This example shows how to find all files that have a specified file name extension (for example ".txt") in a specified directory tree.</span></span> <span data-ttu-id="56593-104">Il montre également comment retourner le fichier le plus récent ou le plus ancien dans l’arborescence en fonction de l’heure de création.</span><span class="sxs-lookup"><span data-stu-id="56593-104">It also shows how to return either the newest or oldest file in the tree based on the creation time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="56593-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="56593-105">Example</span></span>  
  
```vb  
Module FindFileByExtension  
    Sub Main()  
  
        ' Change the drive\path if necessary  
        Dim root As String = "C:\Program Files\Microsoft Visual Studio 9.0"  
  
        'Take a snapshot of the folder contents  
        Dim dir As New System.IO.DirectoryInfo(root)  
  
        Dim fileList = dir.GetFiles("*.*", System.IO.SearchOption.AllDirectories)  
  
        ' This query will produce the full path for all .txt files  
        ' under the specified folder including subfolders.  
        ' It orders the list according to the file name.  
        Dim fileQuery = From file In fileList _  
                        Where file.Extension = ".txt" _  
                        Order By file.Name _  
                        Select file  
  
        For Each file In fileQuery  
            Console.WriteLine(file.FullName)  
        Next  
  
        ' Create and execute a new query by using  
        ' the previous query as a starting point.  
        ' fileQuery is not executed again until the  
        ' call to Last  
        Dim fileQuery2 = From file In fileQuery _  
                         Order By file.CreationTime _  
                         Select file.Name, file.CreationTime  
  
        ' Execute the query  
        Dim newestFile = fileQuery2.Last  
  
        Console.WriteLine("\r\nThe newest .txt file is {0}. Creation time: {1}", _  
                newestFile.Name, newestFile.CreationTime)  
  
        ' Keep the console window open in debug mode  
        Console.WriteLine("Press any key to exit.")  
        Console.ReadKey()  
  
    End Sub  
End Module  
```  
  
## <a name="compile-the-code"></a><span data-ttu-id="56593-106">Compiler le code</span><span class="sxs-lookup"><span data-stu-id="56593-106">Compile the code</span></span>  

<span data-ttu-id="56593-107">Créez un projet d’application console Visual Basic, avec une `Imports` instruction pour l’espace de noms System. Linq.</span><span class="sxs-lookup"><span data-stu-id="56593-107">Create a Visual Basic console application project, with an `Imports` statement for the System.Linq namespace.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="56593-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="56593-108">See also</span></span>

- [<span data-ttu-id="56593-109">LINQ to Objects (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="56593-109">LINQ to Objects (Visual Basic)</span></span>](linq-to-objects.md)
- [<span data-ttu-id="56593-110">LINQ et répertoires de fichiers (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="56593-110">LINQ and File Directories (Visual Basic)</span></span>](linq-and-file-directories.md)
