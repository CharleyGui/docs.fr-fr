---
title: 'Procédure : regrouper des fichiers par extension (LINQ)'
ms.date: 07/20/2015
ms.assetid: 904dc6d7-7162-4655-a7f4-5785d669bc5a
ms.openlocfilehash: 67c48cd735b51009835cbc8df3101ea3cb212a87
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396543"
---
# <a name="how-to-group-files-by-extension-linq-visual-basic"></a><span data-ttu-id="8105a-102">Comment : regrouper des fichiers par extension (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8105a-102">How to: Group Files by Extension (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="8105a-103">Cet exemple montre comment utiliser LINQ pour effectuer des opérations de regroupement et de tri avancées sur des listes de fichiers ou de dossiers.</span><span class="sxs-lookup"><span data-stu-id="8105a-103">This example shows how LINQ can be used to perform advanced grouping and sorting operations on lists of files or folders.</span></span> <span data-ttu-id="8105a-104">Il montre également comment parcourir les résultats dans la fenêtre de console à l’aide des méthodes <xref:System.Linq.Enumerable.Skip%2A> et <xref:System.Linq.Enumerable.Take%2A>.</span><span class="sxs-lookup"><span data-stu-id="8105a-104">It also shows how to page output in the console window by using the <xref:System.Linq.Enumerable.Skip%2A> and <xref:System.Linq.Enumerable.Take%2A> methods.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8105a-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="8105a-105">Example</span></span>  
 <span data-ttu-id="8105a-106">La requête suivante montre comment regrouper le contenu d’une arborescence de répertoires spécifiée en fonction de l’extension de nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="8105a-106">The following query shows how to group the contents of a specified directory tree by the file name extension.</span></span>  
  
```vb  
Module GroupByExtension  
    Public Sub Main()  
  
        ' Root folder to query, along with all subfolders.  
        Dim startFolder As String = "C:\program files\Microsoft Visual Studio 9.0\VB\"  
  
        ' Used in WriteLine() to skip over startfolder in output lines.  
        Dim rootLength As Integer = startFolder.Length  
  
        'Take a snapshot of the folder contents  
        Dim dir As New System.IO.DirectoryInfo(startFolder)  
        Dim fileList = dir.GetFiles("*.*", System.IO.SearchOption.AllDirectories)  
  
        ' Create the query.  
        Dim queryGroupByExt = From file In fileList _  
                          Group By file.Extension.ToLower() Into fileGroup = Group _  
                          Order By ToLower _  
                          Select fileGroup  
  
        ' Execute the query. By storing the result we can  
        ' page the display with good performance.  
        Dim groupByExtList = queryGroupByExt.ToList()  
  
        ' Display one group at a time. If the number of
        ' entries is greater than the number of lines  
        ' in the console window, then page the output.  
        Dim trimLength = startFolder.Length  
        PageOutput(groupByExtList, trimLength)  
  
    End Sub  
  
    ' Pages console display for large query results. No more than one group per page.  
    ' This sub specifically works with group queries of FileInfo objects  
    ' but can be modified for any type.  
    Sub PageOutput(ByVal groupQuery, ByVal charsToSkip)  
  
        ' "3" = 1 line for extension key + 1 for "Press any key" + 1 for input cursor.  
        Dim numLines As Integer = Console.WindowHeight - 3  
        ' Flag to indicate whether there are more results to display  
        Dim goAgain As Boolean = True  
  
        For Each fg As IEnumerable(Of System.IO.FileInfo) In groupQuery  
            ' Start a new extension at the top of a page.  
            Dim currentLine As Integer = 0  
  
            Do While (currentLine < fg.Count())  
                Console.Clear()  
                Console.WriteLine(fg(0).Extension)  
  
                ' Get the next page of results  
                ' No more than one filename per page  
                Dim resultPage = From file In fg _  
                                Skip currentLine Take numLines  
  
                ' Execute the query. Trim the display output.  
                For Each line In resultPage  
                    Console.WriteLine(vbTab & line.FullName.Substring(charsToSkip))  
                Next  
  
                ' Advance the current position  
                currentLine = numLines + currentLine  
  
                ' Give the user a chance to break out of the loop  
                Console.WriteLine("Press any key for next page or the 'End' key to exit.")  
                Dim key As ConsoleKey = Console.ReadKey().Key  
                If key = ConsoleKey.End Then  
                    goAgain = False  
                    Exit For  
                End If  
            Loop  
        Next  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="8105a-107">La sortie de ce programme peut être longue, en fonction des détails du système de fichiers local et de la valeur de `startFolder`.</span><span class="sxs-lookup"><span data-stu-id="8105a-107">The output from this program can be long, depending on the details of the local file system and what the `startFolder` is set to.</span></span> <span data-ttu-id="8105a-108">Pour permettre l’affichage de tous les résultats, cet exemple montre comment parcourir les résultats.</span><span class="sxs-lookup"><span data-stu-id="8105a-108">To enable viewing of all results, this example shows how to page through results.</span></span> <span data-ttu-id="8105a-109">Les mêmes techniques sont applicables aux applications Windows et web.</span><span class="sxs-lookup"><span data-stu-id="8105a-109">The same techniques can be applied to Windows and Web applications.</span></span> <span data-ttu-id="8105a-110">Notez qu’étant donné que le code organise les éléments dans un groupe, une boucle `For Each` imbriquée est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="8105a-110">Notice that because the code pages the items in a group, a nested `For Each` loop is required.</span></span> <span data-ttu-id="8105a-111">Il existe également une logique supplémentaire pour calculer la position actuelle dans la liste et pour permettre aux utilisateurs d’arrêter la pagination et de quitter le programme.</span><span class="sxs-lookup"><span data-stu-id="8105a-111">There is also some additional logic to compute the current position in the list, and to enable the user to stop paging and exit the program.</span></span> <span data-ttu-id="8105a-112">Dans ce cas particulier, la requête de pagination est exécutée par rapport aux résultats de la requête d’origine mis en cache.</span><span class="sxs-lookup"><span data-stu-id="8105a-112">In this particular case, the paging query is run against the cached results from the original query.</span></span> <span data-ttu-id="8105a-113">Dans d’autres contextes, tels que LINQ to SQL, ce type de mise en cache n’est pas nécessaire.</span><span class="sxs-lookup"><span data-stu-id="8105a-113">In other contexts, such as LINQ to SQL, such caching is not required.</span></span>  
  
## <a name="compile-the-code"></a><span data-ttu-id="8105a-114">Compiler le code</span><span class="sxs-lookup"><span data-stu-id="8105a-114">Compile the code</span></span>  
<span data-ttu-id="8105a-115">Créez un projet d’application console Visual Basic, avec une `Imports` instruction pour l’espace de noms System. Linq.</span><span class="sxs-lookup"><span data-stu-id="8105a-115">Create a Visual Basic console application project, with an `Imports` statement for the System.Linq namespace.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="8105a-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8105a-116">See also</span></span>

- [<span data-ttu-id="8105a-117">LINQ to Objects (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8105a-117">LINQ to Objects (Visual Basic)</span></span>](linq-to-objects.md)
- [<span data-ttu-id="8105a-118">LINQ et répertoires de fichiers (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8105a-118">LINQ and File Directories (Visual Basic)</span></span>](linq-and-file-directories.md)
