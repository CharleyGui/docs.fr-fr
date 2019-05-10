---
title: 'Procédure : Comparer le contenu de deux dossiers (LINQ) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 903c7e9a-f48d-4a07-a8a8-5450d2646efa
ms.openlocfilehash: 63027e892fe8404001c6869be33af8cff1bc014a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64643994"
---
# <a name="how-to-compare-the-contents-of-two-folders-linq-visual-basic"></a><span data-ttu-id="565ba-102">Procédure : Comparer le contenu de deux dossiers (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="565ba-102">How to: Compare the Contents of Two Folders (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="565ba-103">Cet exemple montre trois façons de comparer deux listes de fichiers :</span><span class="sxs-lookup"><span data-stu-id="565ba-103">This example demonstrates three ways to compare two file listings:</span></span>  
  
- <span data-ttu-id="565ba-104">En recherchant une valeur booléenne qui spécifie si les deux listes sont identiques</span><span class="sxs-lookup"><span data-stu-id="565ba-104">By querying for a Boolean value that specifies whether the two file lists are identical.</span></span>  
  
- <span data-ttu-id="565ba-105">En recherchant l’intersection pour récupérer les fichiers qui se trouvent dans les deux dossiers</span><span class="sxs-lookup"><span data-stu-id="565ba-105">By querying for the intersection to retrieve the files that are in both folders.</span></span>  
  
- <span data-ttu-id="565ba-106">En recherchant la différence ensembliste pour récupérer les fichiers qui se trouvent dans un dossier, mais pas dans l’autre</span><span class="sxs-lookup"><span data-stu-id="565ba-106">By querying for the set difference to retrieve the files that are in one folder but not the other.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="565ba-107">Les techniques présentées ici peuvent être adaptées pour comparer des séquences d’objets de tout type.</span><span class="sxs-lookup"><span data-stu-id="565ba-107">The techniques shown here can be adapted to compare sequences of objects of any type.</span></span>  
  
 <span data-ttu-id="565ba-108">La classe `FileComparer` présentée ici montre comment utiliser une classe de comparateur personnalisée avec les opérateurs de requête standard.</span><span class="sxs-lookup"><span data-stu-id="565ba-108">The `FileComparer` class shown here demonstrates how to use a custom comparer class together with the Standard Query Operators.</span></span> <span data-ttu-id="565ba-109">La classe n’est pas destinée à être utilisée dans des scénarios réels.</span><span class="sxs-lookup"><span data-stu-id="565ba-109">The class is not intended for use in real-world scenarios.</span></span> <span data-ttu-id="565ba-110">Elle utilise simplement le nom et la longueur en octets de chaque fichier pour déterminer si les dossiers ont un contenu identique.</span><span class="sxs-lookup"><span data-stu-id="565ba-110">It just uses the name and length in bytes of each file to determine whether the contents of each folder are identical or not.</span></span> <span data-ttu-id="565ba-111">Dans un scénario réel, vous devriez modifier ce comparateur pour effectuer une vérification d’égalité plus rigoureuse.</span><span class="sxs-lookup"><span data-stu-id="565ba-111">In a real-world scenario, you should modify this comparer to perform a more rigorous equality check.</span></span>  
  
## <a name="example"></a><span data-ttu-id="565ba-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="565ba-112">Example</span></span>  
  
```vb  
Module CompareDirs  
    Public Sub Main()  
  
        ' Create two identical or different temporary folders   
        ' on a local drive and add files to them.  
        ' Then set these file paths accordingly.  
        Dim pathA As String = "C:\TestDir"  
        Dim pathB As String = "C:\TestDir2"  
  
        ' Take a snapshot of the file system.   
        Dim dir1 As New System.IO.DirectoryInfo(pathA)  
        Dim dir2 As New System.IO.DirectoryInfo(pathB)  
  
        Dim list1 = dir1.GetFiles("*.*", System.IO.SearchOption.AllDirectories)  
        Dim list2 = dir2.GetFiles("*.*", System.IO.SearchOption.AllDirectories)  
  
        ' Create the FileCompare object we'll use in each query  
        Dim myFileCompare As New FileCompare  
  
        ' This query determines whether the two folders contain  
        ' identical file lists, based on the custom file comparer  
        ' that is defined in the FileCompare class.  
        ' The query executes immediately because it returns a bool.  
        Dim areIdentical As Boolean = list1.SequenceEqual(list2, myFileCompare)  
        If areIdentical = True Then  
            Console.WriteLine("The two folders are the same.")  
        Else  
            Console.WriteLine("The two folders are not the same.")  
        End If  
  
        ' Find common files in both folders. It produces a sequence and doesn't execute  
        ' until the foreach statement.  
        Dim queryCommonFiles = list1.Intersect(list2, myFileCompare)  
  
        If queryCommonFiles.Count() > 0 Then  
  
            Console.WriteLine("The following files are in both folders:")  
            For Each fi As System.IO.FileInfo In queryCommonFiles  
                Console.WriteLine(fi.FullName)  
            Next  
        Else  
            Console.WriteLine("There are no common files in the two folders.")  
        End If  
  
        ' Find the set difference between the two folders.  
        ' For this example we only check one way.  
        Dim queryDirAOnly = list1.Except(list2, myFileCompare)  
        Console.WriteLine("The following files are in dirA but not dirB:")  
        For Each fi As System.IO.FileInfo In queryDirAOnly  
            Console.WriteLine(fi.FullName)  
        Next  
  
        ' Keep the console window open in debug mode  
        Console.WriteLine("Press any key to exit.")  
        Console.ReadKey()  
    End Sub  
  
    ' This implementation defines a very simple comparison  
    ' between two FileInfo objects. It only compares the name  
    ' of the files being compared and their length in bytes.  
    Public Class FileCompare  
        Implements System.Collections.Generic.IEqualityComparer(Of System.IO.FileInfo)  
  
        Public Function Equals1(ByVal x As System.IO.FileInfo, ByVal y As System.IO.FileInfo) _  
            As Boolean Implements System.Collections.Generic.IEqualityComparer(Of System.IO.FileInfo).Equals  
  
            If (x.Name = y.Name) And (x.Length = y.Length) Then  
                Return True  
            Else  
                Return False  
            End If  
        End Function  
  
        ' Return a hash that reflects the comparison criteria. According to the   
        ' rules for IEqualityComparer(Of T), if Equals is true, then the hash codes must  
        ' also be equal. Because equality as defined here is a simple value equality, not  
        ' reference identity, it is possible that two or more objects will produce the same  
        ' hash code.  
        Public Function GetHashCode1(ByVal fi As System.IO.FileInfo) _  
            As Integer Implements System.Collections.Generic.IEqualityComparer(Of System.IO.FileInfo).GetHashCode  
            Dim s As String = fi.Name & fi.Length  
            Return s.GetHashCode()  
        End Function  
    End Class  
End Module  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="565ba-113">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="565ba-113">Compiling the Code</span></span>  
 <span data-ttu-id="565ba-114">Créez un projet qui cible le .NET Framework version 3.5 ou ultérieure, avec une référence à System.Core.dll et une déclaration `Imports` pour l’espace de noms System.Linq.</span><span class="sxs-lookup"><span data-stu-id="565ba-114">Create a project that targets the .NET Framework version 3.5 or higher with a reference to System.Core.dll and a `Imports` statement for the System.Linq namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="565ba-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="565ba-115">See also</span></span>

- [<span data-ttu-id="565ba-116">LINQ to Objects (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="565ba-116">LINQ to Objects (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
- [<span data-ttu-id="565ba-117">LINQ et répertoires de fichiers (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="565ba-117">LINQ and File Directories (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)
