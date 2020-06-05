---
title: 'Procédure : rechercher le nombre total d’octets dans un ensemble de dossiers (LINQ)'
ms.date: 07/20/2015
ms.assetid: bfe85ed2-44dc-4ef1-aac7-241622b80a69
ms.openlocfilehash: c6490c8863b5762b0b487c6f3f3b2809e16d6519
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397932"
---
# <a name="how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq-visual-basic"></a><span data-ttu-id="88b8c-102">Comment : Rechercher le nombre total d’octets dans un ensemble de dossiers (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="88b8c-102">How to: Query for the Total Number of Bytes in a Set of Folders (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="88b8c-103">Cet exemple montre comment récupérer le nombre total d’octets utilisés par tous les fichiers d’un dossier spécifié, ainsi que par tous ses sous-dossiers.</span><span class="sxs-lookup"><span data-stu-id="88b8c-103">This example shows how to retrieve the total number of bytes used by all the files in a specified folder and all its subfolders.</span></span>  
  
## <a name="example"></a><span data-ttu-id="88b8c-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="88b8c-104">Example</span></span>  
 <span data-ttu-id="88b8c-105">La méthode <xref:System.Linq.Enumerable.Sum%2A> ajoute les valeurs de tous les éléments sélectionnés dans la clause `select`.</span><span class="sxs-lookup"><span data-stu-id="88b8c-105">The <xref:System.Linq.Enumerable.Sum%2A> method adds the values of all the items selected in the `select` clause.</span></span> <span data-ttu-id="88b8c-106">Vous pouvez facilement modifier cette requête pour récupérer le fichier le plus grand ou le plus petit de l’arborescence du répertoire spécifié en appelant la méthode <xref:System.Linq.Enumerable.Min%2A> ou <xref:System.Linq.Enumerable.Max%2A> plutôt que <xref:System.Linq.Enumerable.Sum%2A>.</span><span class="sxs-lookup"><span data-stu-id="88b8c-106">You can easily modify this query to retrieve the biggest or smallest file in the specified directory tree by calling the <xref:System.Linq.Enumerable.Min%2A> or <xref:System.Linq.Enumerable.Max%2A> method instead of <xref:System.Linq.Enumerable.Sum%2A>.</span></span>  
  
```vb  
Module QueryTotalBytes  
    Sub Main()  
  
        ' Change the drive\path if necessary.  
        Dim root As String = "C:\Program Files\Microsoft Visual Studio 9.0\VB"  
  
        'Take a snapshot of the folder contents.  
        ' This method assumes that the application has discovery permissions  
        ' for all folders under the specified path.  
        Dim fileList = My.Computer.FileSystem.GetFiles _  
                  (root, FileIO.SearchOption.SearchAllSubDirectories, "*.*")  
  
        Dim fileQuery = From file In fileList _  
                        Select GetFileLength(file)  
  
        ' Force execution and cache the results to avoid multiple trips to the file system.  
        Dim fileLengths = fileQuery.ToArray()  
  
        ' Find the largest file  
        Dim maxSize = Aggregate aFile In fileLengths Into Max()  
  
        ' Find the total number of bytes  
        Dim totalBytes = Aggregate aFile In fileLengths Into Sum()  
  
        Console.WriteLine("The largest file is " & maxSize & " bytes")  
        Console.WriteLine("There are " & totalBytes & " total bytes in " & _  
                          fileList.Count & " files under " & root)  
  
        ' Keep the console window open in debug mode  
        Console.WriteLine("Press any key to exit.")  
        Console.ReadKey()  
    End Sub  
  
    ' This method is used to catch the possible exception  
    ' that can be raised when accessing the FileInfo.Length property.  
    Function GetFileLength(ByVal filename As String) As Long  
        Dim retval As Long  
        Try  
            Dim fi As New System.IO.FileInfo(filename)  
            retval = fi.Length  
        Catch ex As System.IO.FileNotFoundException  
            ' If a file is no longer present,  
            ' just return zero bytes.
            retval = 0  
        End Try  
  
        Return retval  
    End Function  
End Module  
```  
  
 <span data-ttu-id="88b8c-107">Si vous devez seulement compter le nombre d’octets dans une arborescence de répertoires spécifiée, pour être plus efficace, ne créez pas de requête LINQ, car cela induit la surcharge liée à la création de la collection de listes comme source de données.</span><span class="sxs-lookup"><span data-stu-id="88b8c-107">If you only have to count the number of bytes in a specified directory tree, you can do this more efficiently without creating a LINQ query, which incurs the overhead of creating the list collection as a data source.</span></span> <span data-ttu-id="88b8c-108">Plus la requête est complexe, plus l’approche LINQ devient utile. C’est également valable lorsque vous devez exécuter plusieurs requêtes sur une même source de données.</span><span class="sxs-lookup"><span data-stu-id="88b8c-108">The usefulness of the LINQ approach increases as the query becomes more complex, or when you have to run multiple queries against the same data source.</span></span>  
  
 <span data-ttu-id="88b8c-109">La requête appelle une méthode distincte pour obtenir la longueur du fichier.</span><span class="sxs-lookup"><span data-stu-id="88b8c-109">The query calls out to a separate method to obtain the file length.</span></span> <span data-ttu-id="88b8c-110">Elle procède ainsi pour utiliser l’exception qui sera éventuellement levée si le fichier a été supprimé sur un autre thread après la création de l’objet <xref:System.IO.FileInfo> dans l’appel à `GetFiles`.</span><span class="sxs-lookup"><span data-stu-id="88b8c-110">It does this in order to consume the possible exception that will be raised if the file was deleted on another thread after the <xref:System.IO.FileInfo> object was created in the call to `GetFiles`.</span></span> <span data-ttu-id="88b8c-111">Même si l’objet <xref:System.IO.FileInfo> a déjà été créé, l’exception peut être levée, car un objet <xref:System.IO.FileInfo> essaiera d’actualiser sa propriété <xref:System.IO.FileInfo.Length%2A> avec la longueur la plus récente lors du premier accès à la propriété.</span><span class="sxs-lookup"><span data-stu-id="88b8c-111">Even though the <xref:System.IO.FileInfo> object has already been created, the exception can occur because a <xref:System.IO.FileInfo> object will try to refresh its <xref:System.IO.FileInfo.Length%2A> property with the most current length the first time the property is accessed.</span></span> <span data-ttu-id="88b8c-112">En plaçant cette opération dans un bloc try-catch en dehors de la requête, le code respecte la règle qui consiste à éviter les opérations dans les requêtes qui peuvent avoir des effets secondaires.</span><span class="sxs-lookup"><span data-stu-id="88b8c-112">By putting this operation in a try-catch block outside the query, the code follows the rule of avoiding operations in queries that can cause side-effects.</span></span> <span data-ttu-id="88b8c-113">En règle générale, il faut faire très attention lors de l’utilisation d’exceptions et s’assurer que l’application ne reste pas dans un état inconnu.</span><span class="sxs-lookup"><span data-stu-id="88b8c-113">In general, great care must be taken when you consume exceptions to make sure that an application is not left in an unknown state.</span></span>  
  
## <a name="compile-the-code"></a><span data-ttu-id="88b8c-114">Compiler le code</span><span class="sxs-lookup"><span data-stu-id="88b8c-114">Compile the code</span></span>  
<span data-ttu-id="88b8c-115">Créez un projet d’application console Visual Basic, avec une `Imports` instruction pour l’espace de noms System. Linq.</span><span class="sxs-lookup"><span data-stu-id="88b8c-115">Create a Visual Basic console application project, with an `Imports` statement for the System.Linq namespace.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="88b8c-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="88b8c-116">See also</span></span>

- [<span data-ttu-id="88b8c-117">LINQ to Objects (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="88b8c-117">LINQ to Objects (Visual Basic)</span></span>](linq-to-objects.md)
- [<span data-ttu-id="88b8c-118">LINQ et répertoires de fichiers (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="88b8c-118">LINQ and File Directories (Visual Basic)</span></span>](linq-and-file-directories.md)
