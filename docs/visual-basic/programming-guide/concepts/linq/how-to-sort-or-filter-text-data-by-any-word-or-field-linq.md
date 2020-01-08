---
title: 'Comment : trier ou filtrer des données texte par mot ou par champ (LINQ)'
ms.date: 07/20/2015
ms.assetid: 9df137fe-335b-46e0-aecf-ea8a9eddd4e3
ms.openlocfilehash: f0eeda77a721d482ec7a2b8562c0a71f34c5a3ae
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75348046"
---
# <a name="how-to-sort-or-filter-text-data-by-any-word-or-field-linq-visual-basic"></a><span data-ttu-id="d1ccd-102">Comment : trier ou filtrer des données texte par mot ou par champ (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d1ccd-102">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (Visual Basic)</span></span>

<span data-ttu-id="d1ccd-103">L’exemple suivant montre comment trier les lignes d’un texte structuré, telles que des valeurs séparées par des virgules, à l’aide d’un champ de la ligne.</span><span class="sxs-lookup"><span data-stu-id="d1ccd-103">The following example shows how to sort lines of structured text, such as comma-separated values, by any field in the line.</span></span> <span data-ttu-id="d1ccd-104">Le champ peut être spécifié de manière dynamique lors de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="d1ccd-104">The field may be dynamically specified at runtime.</span></span> <span data-ttu-id="d1ccd-105">Supposons que les champs du fichier scores.csv correspondent au numéro d’identification d’un étudiant, suivi d’une série de quatre notes d’examen.</span><span class="sxs-lookup"><span data-stu-id="d1ccd-105">Assume that the fields in scores.csv represent a student's ID number, followed by a series of four test scores.</span></span>

### <a name="to-create-a-file-that-contains-data"></a><span data-ttu-id="d1ccd-106">Pour créer un fichier contenant des données</span><span class="sxs-lookup"><span data-stu-id="d1ccd-106">To create a file that contains data</span></span>

<span data-ttu-id="d1ccd-107">Copiez les données scores. csv de la rubrique [procédure : joindre du contenu de fichiers non similaires (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md) et enregistrez-le dans votre dossier de solution.</span><span class="sxs-lookup"><span data-stu-id="d1ccd-107">Copy the scores.csv data from the topic [How to: Join Content from Dissimilar Files (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md) and save it to your solution folder.</span></span>

## <a name="example"></a><span data-ttu-id="d1ccd-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="d1ccd-108">Example</span></span>

```vb
Class SortLines

    Shared Sub Main()
        Dim scores As String() = System.IO.File.ReadAllLines("../../../scores.csv")

        ' Change this to any value from 0 to 4
        Dim sortField As Integer = 1

        Console.WriteLine("Sorted highest to lowest by field " & sortField)

        ' Demonstrates how to return query from a method.
        ' The query is executed here.
        For Each str As String In SortQuery(scores, sortField)
            Console.WriteLine(str)
        Next

        ' Keep console window open in debug mode.
        Console.WriteLine("Press any key to exit.")
        Console.ReadKey()

    End Sub

    Shared Function SortQuery(
        ByVal source As IEnumerable(Of String),
        ByVal num As Integer) As IEnumerable(Of String)

        Dim scoreQuery = From line In source
                         Let fields = line.Split(New Char() {","})
                         Order By fields(num) Descending
                         Select line

        Return scoreQuery
    End Function
End Class
' Output:
' Sorted highest to lowest by field 1
' 116, 99, 86, 90, 94
' 120, 99, 82, 81, 79
' 111, 97, 92, 81, 60
' 114, 97, 89, 85, 82
' 121, 96, 85, 91, 60
' 122, 94, 92, 91, 91
' 117, 93, 92, 80, 87
' 118, 92, 90, 83, 78
' 113, 88, 94, 65, 91
' 112, 75, 84, 91, 39
' 119, 68, 79, 88, 92
' 115, 35, 72, 91, 70
```

<span data-ttu-id="d1ccd-109">Cet exemple montre également comment retourner une variable de requête à partir d’une fonction.</span><span class="sxs-lookup"><span data-stu-id="d1ccd-109">This example also demonstrates how to return a query variable from a Function.</span></span>

## <a name="compile-the-code"></a><span data-ttu-id="d1ccd-110">Compiler le code</span><span class="sxs-lookup"><span data-stu-id="d1ccd-110">Compile the code</span></span>

<span data-ttu-id="d1ccd-111">Créez un projet d’application console Visual Basic, avec une instruction `Imports` pour l’espace de noms System. Linq.</span><span class="sxs-lookup"><span data-stu-id="d1ccd-111">Create a Visual Basic console application project, with an `Imports` statement for the System.Linq namespace.</span></span>

## <a name="see-also"></a><span data-ttu-id="d1ccd-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d1ccd-112">See also</span></span>

- [<span data-ttu-id="d1ccd-113">LINQ et Strings (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d1ccd-113">LINQ and Strings (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
