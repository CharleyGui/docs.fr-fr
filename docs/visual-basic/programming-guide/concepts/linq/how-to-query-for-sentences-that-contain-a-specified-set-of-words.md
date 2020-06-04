---
title: 'Procédure : rechercher des phrases qui contiennent un groupe de mots spécifié (LINQ)'
ms.date: 07/20/2015
ms.assetid: a5ae8ced-61fe-4c10-bb8a-95630e50f603
ms.openlocfilehash: ce88bf001346f90eb9b08ca1ff14afc7dcb04fa0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397958"
---
# <a name="how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq-visual-basic"></a>Comment : rechercher des phrases qui contiennent un groupe de mots spécifié (LINQ) (Visual Basic)

Cet exemple montre comment rechercher dans un fichier texte les phrases qui contiennent des correspondances pour chaque ensemble de mots spécifié. Même si le tableau des termes de recherche est codé en dur dans cet exemple, il pourrait aussi être rempli dynamiquement lors de l’exécution. Dans cet exemple, la requête retourne les phrases qui contiennent les mots « Historically », « data » et « integrated ».

## <a name="example"></a>Exemple

```vb
Class FindSentences

    Shared Sub Main()
        Dim text As String = "Historically, the world of data and the world of objects " &
        "have not been well integrated. Programmers work in C# or Visual Basic " &
        "and also in SQL or XQuery. On the one side are concepts such as classes, " &
        "objects, fields, inheritance, and .NET Framework APIs. On the other side " &
        "are tables, columns, rows, nodes, and separate languages for dealing with " &
        "them. Data types often require translation between the two worlds; there are " &
        "different standard functions. Because the object world has no notion of query, a " &
        "query can only be represented as a string without compile-time type checking or " &
        "IntelliSense support in the IDE. Transferring data from SQL tables or XML trees to " &
        "objects in memory is often tedious and error-prone."

        ' Split the text block into an array of sentences.
        Dim sentences As String() = text.Split(New Char() {".", "?", "!"})

        ' Define the search terms. This list could also be dynamically populated at runtime
        Dim wordsToMatch As String() = {"Historically", "data", "integrated"}

        ' Find sentences that contain all the terms in the wordsToMatch array
        ' Note that the number of terms to match is not specified at compile time
        Dim sentenceQuery = From sentence In sentences
                            Let w = sentence.Split(New Char() {" ", ",", ".", ";", ":"},
                                                   StringSplitOptions.RemoveEmptyEntries)
                            Where w.Distinct().Intersect(wordsToMatch).Count = wordsToMatch.Count()
                            Select sentence

        ' Execute the query
        For Each str As String In sentenceQuery
            Console.WriteLine(str)
        Next

        ' Keep console window open in debug mode.
        Console.WriteLine("Press any key to exit.")
        Console.ReadKey()
    End Sub

End Class
' Output:
' Historically, the world of data and the world of objects have not been well integrated
```

La requête fractionne d’abord le texte en phrases, puis fractionne les phrases en tableaux de chaînes contenant chacun des mots. Pour chacun de ces tableaux, la méthode <xref:System.Linq.Enumerable.Distinct%2A> supprime tous les mots en double, puis la requête effectue une opération <xref:System.Linq.Enumerable.Intersect%2A> sur le tableau de mots et le tableau `wordsToMatch`. Si le nombre de l’intersection est identique à celui du tableau `wordsToMatch`, cela signifie que tous les mots ont été trouvés et la phrase d’origine est donc retournée.

Dans l’appel à <xref:System.String.Split%2A>, les signes de ponctuation sont utilisés comme séparateurs pour être supprimés de la chaîne. Si vous ne l’avez pas fait, vous pourriez avoir, par exemple, la chaîne « Historically, », qui ne correspondrait pas au mot « Historically » du tableau `wordsToMatch`. Vous devrez peut-être utiliser des séparateurs supplémentaires, selon le type des signes de ponctuation qui se trouvent dans le texte source.

## <a name="compile-the-code"></a>Compiler le code

Créez un projet d’application console Visual Basic, avec une `Imports` instruction pour l’espace de noms System. Linq.

## <a name="see-also"></a>Voir aussi

- [LINQ et chaînes (Visual Basic)](linq-and-strings.md)
