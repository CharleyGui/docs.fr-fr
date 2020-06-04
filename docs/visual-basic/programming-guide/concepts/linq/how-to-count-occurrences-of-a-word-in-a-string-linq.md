---
title: 'Procédure : compter les occurrences d’un mot dans une chaîne (LINQ)'
ms.date: 07/20/2015
ms.assetid: bc367e46-f7cc-45f9-936f-754e661b7bb9
ms.openlocfilehash: c6894359e5785419ccf8f283f976c0a897288a5d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84405324"
---
# <a name="how-to-count-occurrences-of-a-word-in-a-string-linq-visual-basic"></a><span data-ttu-id="a4aa9-102">Comment : compter les occurrences d’un mot dans une chaîne (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a4aa9-102">How to: Count Occurrences of a Word in a String (LINQ) (Visual Basic)</span></span>

<span data-ttu-id="a4aa9-103">Cet exemple montre comment utiliser une requête LINQ pour compter les occurrences d’un mot spécifié dans une chaîne.</span><span class="sxs-lookup"><span data-stu-id="a4aa9-103">This example shows how to use a LINQ query to count the occurrences of a specified word in a string.</span></span> <span data-ttu-id="a4aa9-104">Notez que, pour effectuer le décompte, la méthode <xref:System.String.Split%2A> est d’abord appelée pour créer un tableau de mots.</span><span class="sxs-lookup"><span data-stu-id="a4aa9-104">Note that to perform the count, first the <xref:System.String.Split%2A> method is called to create an array of words.</span></span> <span data-ttu-id="a4aa9-105">La méthode <xref:System.String.Split%2A> a un coût en matière de performances.</span><span class="sxs-lookup"><span data-stu-id="a4aa9-105">There is a performance cost to the <xref:System.String.Split%2A> method.</span></span> <span data-ttu-id="a4aa9-106">Si la seule opération sur la chaîne consiste à compter les mots, il est préférable d’utiliser les méthodes <xref:System.Text.RegularExpressions.Regex.Matches%2A> ou <xref:System.String.IndexOf%2A>.</span><span class="sxs-lookup"><span data-stu-id="a4aa9-106">If the only operation on the string is to count the words, you should consider using the <xref:System.Text.RegularExpressions.Regex.Matches%2A> or <xref:System.String.IndexOf%2A> methods instead.</span></span> <span data-ttu-id="a4aa9-107">Toutefois, si les performances ne sont pas un facteur critique, ou si vous avez déjà fractionné la phrase pour effectuer d’autres types de requêtes sur elle, il est judicieux d’utiliser LINQ pour compter les mots ou les expressions.</span><span class="sxs-lookup"><span data-stu-id="a4aa9-107">However, if performance is not a critical issue, or you have already split the sentence in order to perform other types of queries over it, then it makes sense to use LINQ to count the words or phrases as well.</span></span>

## <a name="example"></a><span data-ttu-id="a4aa9-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="a4aa9-108">Example</span></span>

```vb
Class CountWords

    Shared Sub Main()

        Dim text As String = "Historically, the world of data and the world of objects" &
                  " have not been well integrated. Programmers work in C# or Visual Basic" &
                  " and also in SQL or XQuery. On the one side are concepts such as classes," &
                  " objects, fields, inheritance, and .NET Framework APIs. On the other side" &
                  " are tables, columns, rows, nodes, and separate languages for dealing with" &
                  " them. Data types often require translation between the two worlds; there are" &
                  " different standard functions. Because the object world has no notion of query, a" &
                  " query can only be represented as a string without compile-time type checking or" &
                  " IntelliSense support in the IDE. Transferring data from SQL tables or XML trees to" &
                  " objects in memory is often tedious and error-prone."

        Dim searchTerm As String = "data"

        ' Convert the string into an array of words.
        Dim dataSource As String() = text.Split(New Char() {" ", ",", ".", ";", ":"},
                                                 StringSplitOptions.RemoveEmptyEntries)

        ' Create and execute the query. It executes immediately
        ' because a singleton value is produced.
        ' Use ToLower to match "data" and "Data"
        Dim matchQuery = From word In dataSource
                      Where word.ToLowerInvariant() = searchTerm.ToLowerInvariant()
                      Select word

        ' Count the matches.
        Dim count As Integer = matchQuery.Count()
        Console.WriteLine(count & " occurrence(s) of the search term """ &
                          searchTerm & """ were found.")

        ' Keep console window open in debug mode.
        Console.WriteLine("Press any key to exit.")
        Console.ReadKey()
    End Sub
End Class
' Output:
' 3 occurrence(s) of the search term "data" were found.
```

## <a name="compile-the-code"></a><span data-ttu-id="a4aa9-109">Compiler le code</span><span class="sxs-lookup"><span data-stu-id="a4aa9-109">Compile the code</span></span>

<span data-ttu-id="a4aa9-110">Créez un projet d’application console Visual Basic, avec une `Imports` instruction pour l’espace de noms System. Linq.</span><span class="sxs-lookup"><span data-stu-id="a4aa9-110">Create a Visual Basic console application project, with an `Imports` statement for the System.Linq namespace.</span></span>

## <a name="see-also"></a><span data-ttu-id="a4aa9-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a4aa9-111">See also</span></span>

- [<span data-ttu-id="a4aa9-112">LINQ et chaînes (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a4aa9-112">LINQ and Strings (Visual Basic)</span></span>](linq-and-strings.md)
