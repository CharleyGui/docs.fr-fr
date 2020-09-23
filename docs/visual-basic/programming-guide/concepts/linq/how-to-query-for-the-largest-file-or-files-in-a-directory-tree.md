---
title: 'Procédure : rechercher les fichiers les plus volumineux dans une arborescence de répertoires (LINQ)'
ms.date: 07/20/2015
ms.assetid: 8c1c9f0c-95dd-4222-9be2-9ec026a13e81
ms.openlocfilehash: 9ae4a1442a0ecbb11d37b56302bec6a387c662aa
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91078266"
---
# <a name="how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq-visual-basic"></a><span data-ttu-id="e43b6-102">Comment : interroger les fichiers les plus volumineux dans une arborescence de répertoires (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e43b6-102">How to: Query for the Largest File or Files in a Directory Tree (LINQ) (Visual Basic)</span></span>

<span data-ttu-id="e43b6-103">Cet exemple montre cinq requêtes liées à la taille des fichiers en octets :</span><span class="sxs-lookup"><span data-stu-id="e43b6-103">This example shows five queries related to file size in bytes:</span></span>  
  
- <span data-ttu-id="e43b6-104">Comment récupérer la taille en octets du plus grand fichier.</span><span class="sxs-lookup"><span data-stu-id="e43b6-104">How to retrieve the size in bytes of the largest file.</span></span>  
  
- <span data-ttu-id="e43b6-105">Comment récupérer la taille en octets du plus petit fichier.</span><span class="sxs-lookup"><span data-stu-id="e43b6-105">How to retrieve the size in bytes of the smallest file.</span></span>  
  
- <span data-ttu-id="e43b6-106">Comment récupérer le plus grand ou le plus petit fichier de l’objet <xref:System.IO.FileInfo> dans un ou plusieurs dossiers situés dans le dossier racine spécifié.</span><span class="sxs-lookup"><span data-stu-id="e43b6-106">How to retrieve the <xref:System.IO.FileInfo> object largest or smallest file from one or more folders under a specified root folder.</span></span>  
  
- <span data-ttu-id="e43b6-107">Comment récupérer une séquence, telle que les 10 fichiers les plus volumineux.</span><span class="sxs-lookup"><span data-stu-id="e43b6-107">How to retrieve a sequence such as the 10 largest files.</span></span>  
  
- <span data-ttu-id="e43b6-108">Comment regrouper des fichiers selon leur taille en octets, en ignorant les fichiers qui sont inférieurs à une taille spécifiée.</span><span class="sxs-lookup"><span data-stu-id="e43b6-108">How to order files into groups based on their file size in bytes, ignoring files that are less than a specified size.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e43b6-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="e43b6-109">Example</span></span>  

 <span data-ttu-id="e43b6-110">L’exemple suivant contient cinq requêtes distinctes qui montrent comment interroger et regrouper des fichiers selon leur taille en octets.</span><span class="sxs-lookup"><span data-stu-id="e43b6-110">The following example contains five separate queries that show how to query and group files, depending on their file size in bytes.</span></span> <span data-ttu-id="e43b6-111">Vous pouvez facilement modifier ces exemples pour baser la requête sur une autre propriété de l’objet <xref:System.IO.FileInfo>.</span><span class="sxs-lookup"><span data-stu-id="e43b6-111">You can easily modify these examples to base the query on some other property of the <xref:System.IO.FileInfo> object.</span></span>  
  
```vb  
Module QueryBySize  
    Sub Main()  
  
        ' Change the drive\path if necessary  
        Dim root As String = "C:\Program Files\Microsoft Visual Studio 9.0"  
  
        'Take a snapshot of the folder contents  
        Dim dir As New System.IO.DirectoryInfo(root)  
        Dim fileList = dir.GetFiles("*.*", System.IO.SearchOption.AllDirectories)  
  
        ' Return the size of the largest file  
        Dim maxSize = Aggregate aFile In fileList Into Max(GetFileLength(aFile))  
  
        'Dim maxSize = fileLengths.Max  
        Console.WriteLine("The length of the largest file under {0} is {1}", _  
                          root, maxSize)  
  
        ' Return the FileInfo object of the largest file  
        ' by sorting and selecting from the beginning of the list  
        Dim filesByLengDesc = From file In fileList _  
                              Let filelength = GetFileLength(file) _  
                              Where filelength > 0 _  
                              Order By filelength Descending _  
                              Select file  
  
        Dim longestFile = filesByLengDesc.First  
  
        Console.WriteLine("The largest file under {0} is {1} with a length of {2} bytes", _  
                          root, longestFile.FullName, longestFile.Length)  
  
        Dim smallestFile = filesByLengDesc.Last  
  
        Console.WriteLine("The smallest file under {0} is {1} with a length of {2} bytes", _  
                                root, smallestFile.FullName, smallestFile.Length)  
  
        ' Return the FileInfos for the 10 largest files  
        ' Based on a previous query, but nothing is executed  
        ' until the For Each statement below.  
        Dim tenLargest = From file In filesByLengDesc Take 10  
  
        Console.WriteLine("The 10 largest files under {0} are:", root)  
  
        For Each fi As System.IO.FileInfo In tenLargest  
            Console.WriteLine("{0}: {1} bytes", fi.FullName, fi.Length)  
        Next  
  
        ' Group files according to their size,  
        ' leaving out the ones under 200K  
        Dim sizeGroups = From file As System.IO.FileInfo In fileList _  
                         Where file.Length > 0 _  
                         Let groupLength = file.Length / 100000 _  
                         Group file By groupLength Into fileGroup = Group _  
                         Where groupLength >= 2 _  
                         Order By groupLength Descending  
  
        For Each group In sizeGroups  
            Console.WriteLine(group.groupLength + "00000")  
  
            For Each item As System.IO.FileInfo In group.fileGroup  
                Console.WriteLine("   {0}: {1}", item.Name, item.Length)  
            Next  
        Next  
  
        ' Keep the console window open in debug mode  
        Console.WriteLine("Press any key to exit.")  
        Console.ReadKey()  
  
    End Sub  
  
    ' This method is used to catch the possible exception  
    ' that can be raised when accessing the FileInfo.Length property.  
    ' In this particular case, it is safe to ignore the exception.  
    Function GetFileLength(ByVal fi As System.IO.FileInfo) As Long  
        Dim retval As Long  
        Try  
            retval = fi.Length  
        Catch ex As FileNotFoundException  
            ' If a file is no longer present,  
            ' just return zero bytes.
            retval = 0  
        End Try  
  
        Return retval  
    End Function  
End Module  
```  
  
 <span data-ttu-id="e43b6-112">Pour retourner un ou plusieurs objets <xref:System.IO.FileInfo> complets, la requête doit d’abord examiner chacun d’eux dans la source de données, puis les trier selon la valeur de leur propriété Length.</span><span class="sxs-lookup"><span data-stu-id="e43b6-112">To return one or more complete <xref:System.IO.FileInfo> objects, the query first must examine each one in the data source, and then sort them by the value of their Length property.</span></span> <span data-ttu-id="e43b6-113">Elle peut ensuite retourner l’objet ou la séquence d’objets avec les plus grandes valeurs de longueur.</span><span class="sxs-lookup"><span data-stu-id="e43b6-113">Then it can return the single one or the sequence with the greatest lengths.</span></span> <span data-ttu-id="e43b6-114">Utilisez <xref:System.Linq.Enumerable.First%2A> pour retourner le premier élément d’une liste.</span><span class="sxs-lookup"><span data-stu-id="e43b6-114">Use <xref:System.Linq.Enumerable.First%2A> to return the first element in a list.</span></span> <span data-ttu-id="e43b6-115">Utilisez <xref:System.Linq.Enumerable.Take%2A> pour retourner les n premiers éléments.</span><span class="sxs-lookup"><span data-stu-id="e43b6-115">Use <xref:System.Linq.Enumerable.Take%2A> to return the first n number of elements.</span></span> <span data-ttu-id="e43b6-116">Spécifiez un ordre de tri décroissant pour placer les plus petits éléments au début de la liste.</span><span class="sxs-lookup"><span data-stu-id="e43b6-116">Specify a descending sort order to put the smallest elements at the start of the list.</span></span>  
  
 <span data-ttu-id="e43b6-117">La requête appelle une méthode distincte pour obtenir la taille du fichier en octets et ainsi permettre l’utilisation de l’exception éventuellement levée si un fichier a été supprimé sur un autre thread depuis la création de l’objet <xref:System.IO.FileInfo> dans l’appel à `GetFiles`.</span><span class="sxs-lookup"><span data-stu-id="e43b6-117">The query calls out to a separate method to obtain the file size in bytes in order to consume the possible exception that will be raised in the case where a file was deleted on another thread in the time period since the <xref:System.IO.FileInfo> object was created in the call to `GetFiles`.</span></span> <span data-ttu-id="e43b6-118">Même si l’objet <xref:System.IO.FileInfo> a déjà été créé, l’exception peut être levée, car un objet <xref:System.IO.FileInfo> essaiera d’actualiser sa propriété <xref:System.IO.FileInfo.Length%2A> en utilisant la taille en octets la plus récente lors du premier accès à la propriété.</span><span class="sxs-lookup"><span data-stu-id="e43b6-118">Even through the <xref:System.IO.FileInfo> object has already been created, the exception can occur because a <xref:System.IO.FileInfo> object will try to refresh its <xref:System.IO.FileInfo.Length%2A> property by using the most current size in bytes the first time the property is accessed.</span></span> <span data-ttu-id="e43b6-119">En plaçant cette opération dans un bloc try-catch en dehors de la requête, nous respectons la règle qui consiste à éviter les opérations dans les requêtes qui peuvent avoir des effets secondaires.</span><span class="sxs-lookup"><span data-stu-id="e43b6-119">By putting this operation in a try-catch block outside the query, we follow the rule of avoiding operations in queries that can cause side-effects.</span></span> <span data-ttu-id="e43b6-120">En règle générale, il faut faire très attention lors de l’utilisation d’exceptions et s’assurer que l’application ne reste pas dans un état inconnu.</span><span class="sxs-lookup"><span data-stu-id="e43b6-120">In general, great care must be taken when consuming exceptions, to make sure that an application is not left in an unknown state.</span></span>  
  
## <a name="compile-the-code"></a><span data-ttu-id="e43b6-121">Compiler le code</span><span class="sxs-lookup"><span data-stu-id="e43b6-121">Compile the code</span></span>  

<span data-ttu-id="e43b6-122">Créez un projet d’application console Visual Basic, avec une `Imports` instruction pour l’espace de noms System. Linq.</span><span class="sxs-lookup"><span data-stu-id="e43b6-122">Create a Visual Basic console application project, with an `Imports` statement for the System.Linq namespace.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="e43b6-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e43b6-123">See also</span></span>

- [<span data-ttu-id="e43b6-124">LINQ to Objects (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e43b6-124">LINQ to Objects (Visual Basic)</span></span>](linq-to-objects.md)
- [<span data-ttu-id="e43b6-125">LINQ et répertoires de fichiers (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e43b6-125">LINQ and File Directories (Visual Basic)</span></span>](linq-and-file-directories.md)
