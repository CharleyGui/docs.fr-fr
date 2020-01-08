---
title: 'Comment : interroger des caractères dans une chaîne (LINQ)'
ms.date: 07/20/2015
ms.assetid: 499ebbe0-746c-4235-9dba-ce722c12b50e
ms.openlocfilehash: 2f306a488610aaa5775210eba3d7312b092545a7
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345523"
---
# <a name="how-to-query-for-characters-in-a-string-linq-visual-basic"></a><span data-ttu-id="ef5f8-102">Comment : interroger des caractères dans une chaîne (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ef5f8-102">How to: Query for Characters in a String (LINQ) (Visual Basic)</span></span>

<span data-ttu-id="ef5f8-103">La classe <xref:System.String> implémente l’interface <xref:System.Collections.Generic.IEnumerable%601> générique. De ce fait, il est possible d’interroger n’importe quelle chaîne comme une séquence de caractères.</span><span class="sxs-lookup"><span data-stu-id="ef5f8-103">Because the <xref:System.String> class implements the generic <xref:System.Collections.Generic.IEnumerable%601> interface, any string can be queried as a sequence of characters.</span></span> <span data-ttu-id="ef5f8-104">Toutefois, ceci n’est pas une utilisation courante de LINQ.</span><span class="sxs-lookup"><span data-stu-id="ef5f8-104">However, this is not a common use of LINQ.</span></span> <span data-ttu-id="ef5f8-105">Pour les opérations de critères spéciaux complexes, utilisez la classe <xref:System.Text.RegularExpressions.Regex>.</span><span class="sxs-lookup"><span data-stu-id="ef5f8-105">For complex pattern matching operations, use the <xref:System.Text.RegularExpressions.Regex> class.</span></span>

## <a name="example"></a><span data-ttu-id="ef5f8-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="ef5f8-106">Example</span></span>

<span data-ttu-id="ef5f8-107">L’exemple suivant interroge une chaîne pour déterminer le nombre de chiffres qu’elle contient.</span><span class="sxs-lookup"><span data-stu-id="ef5f8-107">The following example queries a string to determine the number of numeric digits it contains.</span></span> <span data-ttu-id="ef5f8-108">Notez que la requête est « réutilisée » après sa première exécution.</span><span class="sxs-lookup"><span data-stu-id="ef5f8-108">Note that the query is "reused" after it is executed the first time.</span></span> <span data-ttu-id="ef5f8-109">Ceci est possible car la requête proprement dite ne stocke pas de résultats réels.</span><span class="sxs-lookup"><span data-stu-id="ef5f8-109">This is possible because the query itself does not store any actual results.</span></span>

```vb
Class QueryAString

    Shared Sub Main()

        ' A string is an IEnumerable data source.
        Dim aString As String = "ABCDE99F-J74-12-89A"

        ' Select only those characters that are numbers
        Dim stringQuery = From ch In aString
                          Where Char.IsDigit(ch)
                          Select ch
        ' Execute the query
        For Each c As Char In stringQuery
            Console.Write(c & " ")
        Next

        ' Call the Count method on the existing query.
        Dim count As Integer = stringQuery.Count()
        Console.WriteLine(System.Environment.NewLine & "Count = " & count)

        ' Select all characters before the first '-'
        Dim stringQuery2 = aString.TakeWhile(Function(c) c <> "-")

        ' Execute the second query
        For Each ch In stringQuery2
            Console.Write(ch)
        Next

        Console.WriteLine(System.Environment.NewLine & "Press any key to exit")
        Console.ReadKey()
    End Sub
End Class
' Output:
' 9 9 7 4 1 2 8 9
' Count = 8
' ABCDE99F
```

## <a name="compile-the-code"></a><span data-ttu-id="ef5f8-110">Compiler le code</span><span class="sxs-lookup"><span data-stu-id="ef5f8-110">Compile the code</span></span>

<span data-ttu-id="ef5f8-111">Créez un projet d’application console Visual Basic, avec une instruction `Imports` pour l’espace de noms System. Linq.</span><span class="sxs-lookup"><span data-stu-id="ef5f8-111">Create a Visual Basic console application project, with an `Imports` statement for the System.Linq namespace.</span></span>

## <a name="see-also"></a><span data-ttu-id="ef5f8-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ef5f8-112">See also</span></span>

- [<span data-ttu-id="ef5f8-113">LINQ et Strings (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ef5f8-113">LINQ and Strings (Visual Basic)</span></span>](linq-and-strings.md)
- [<span data-ttu-id="ef5f8-114">Comment combiner des requêtes LINQ avec des expressions régulières (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ef5f8-114">How to combine LINQ queries with regular expressions (Visual Basic)</span></span>](how-to-combine-linq-queries-with-regular-expressions.md)
