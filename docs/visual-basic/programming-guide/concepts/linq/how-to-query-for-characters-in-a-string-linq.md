---
title: 'Comment : interroger des caractères dans une chaîne (LINQ) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 499ebbe0-746c-4235-9dba-ce722c12b50e
ms.openlocfilehash: f2102a8cb149fa9c7886826e509bf254fad5eb95
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582723"
---
# <a name="how-to-query-for-characters-in-a-string-linq-visual-basic"></a><span data-ttu-id="5bd9a-102">Comment : interroger des caractères dans une chaîne (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5bd9a-102">How to: Query for Characters in a String (LINQ) (Visual Basic)</span></span>

<span data-ttu-id="5bd9a-103">La classe <xref:System.String> implémente l’interface <xref:System.Collections.Generic.IEnumerable%601> générique. De ce fait, il est possible d’interroger n’importe quelle chaîne comme une séquence de caractères.</span><span class="sxs-lookup"><span data-stu-id="5bd9a-103">Because the <xref:System.String> class implements the generic <xref:System.Collections.Generic.IEnumerable%601> interface, any string can be queried as a sequence of characters.</span></span> <span data-ttu-id="5bd9a-104">Toutefois, ceci n’est pas une utilisation courante de LINQ.</span><span class="sxs-lookup"><span data-stu-id="5bd9a-104">However, this is not a common use of LINQ.</span></span> <span data-ttu-id="5bd9a-105">Pour les opérations de critères spéciaux complexes, utilisez la classe <xref:System.Text.RegularExpressions.Regex>.</span><span class="sxs-lookup"><span data-stu-id="5bd9a-105">For complex pattern matching operations, use the <xref:System.Text.RegularExpressions.Regex> class.</span></span>

## <a name="example"></a><span data-ttu-id="5bd9a-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="5bd9a-106">Example</span></span>

<span data-ttu-id="5bd9a-107">L’exemple suivant interroge une chaîne pour déterminer le nombre de chiffres qu’elle contient.</span><span class="sxs-lookup"><span data-stu-id="5bd9a-107">The following example queries a string to determine the number of numeric digits it contains.</span></span> <span data-ttu-id="5bd9a-108">Notez que la requête est « réutilisée » après sa première exécution.</span><span class="sxs-lookup"><span data-stu-id="5bd9a-108">Note that the query is "reused" after it is executed the first time.</span></span> <span data-ttu-id="5bd9a-109">Ceci est possible car la requête proprement dite ne stocke pas de résultats réels.</span><span class="sxs-lookup"><span data-stu-id="5bd9a-109">This is possible because the query itself does not store any actual results.</span></span>

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

## <a name="compiling-the-code"></a><span data-ttu-id="5bd9a-110">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="5bd9a-110">Compiling the Code</span></span>

<span data-ttu-id="5bd9a-111">Créez un projet d’application console VB.NET, avec une instruction `Imports` pour l’espace de noms System. Linq.</span><span class="sxs-lookup"><span data-stu-id="5bd9a-111">Create a VB.NET console application project, with an `Imports` statement for the System.Linq namespace.</span></span>

## <a name="see-also"></a><span data-ttu-id="5bd9a-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5bd9a-112">See also</span></span>

- [<span data-ttu-id="5bd9a-113">LINQ et Strings (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5bd9a-113">LINQ and Strings (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
- [<span data-ttu-id="5bd9a-114">Comment : combiner des requêtes LINQ avec des expressions régulières (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5bd9a-114">How to: Combine LINQ Queries with Regular Expressions (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-combine-linq-queries-with-regular-expressions.md)
