---
title: 'Procédure : remplir des collections d’objets issues de plusieurs sources (LINQ)'
ms.date: 06/22/2018
ms.assetid: 63062a22-e6a9-42c0-b357-c7c965f58f33
ms.openlocfilehash: 9c6d8ff5165bf886d8aad87b64305819e65361ab
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396517"
---
# <a name="how-to-populate-object-collections-from-multiple-sources-linq-visual-basic"></a><span data-ttu-id="6fc40-102">Comment : remplir des collections d’objets à partir de plusieurs sources (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6fc40-102">How to: Populate Object Collections from Multiple Sources (LINQ) (Visual Basic)</span></span>

<span data-ttu-id="6fc40-103">Cet exemple montre comment fusionner des données de différentes sources en une séquence de nouveaux types.</span><span class="sxs-lookup"><span data-stu-id="6fc40-103">This example shows how to merge data from different sources into a sequence of new types.</span></span>

> [!NOTE]
> <span data-ttu-id="6fc40-104">N’essayez pas de joindre des données du système de fichiers ou des données en mémoire à des données qui se trouvent encore dans une base de données.</span><span class="sxs-lookup"><span data-stu-id="6fc40-104">Don't try to join in-memory data or data in the file system with data that is still in a database.</span></span> <span data-ttu-id="6fc40-105">Ces jointures interdomaines peuvent générer des résultats indéfinis, en raison des différentes façons par lesquelles les opérations de jointure peuvent être définies pour les requêtes de base de données et autres types de sources.</span><span class="sxs-lookup"><span data-stu-id="6fc40-105">Such cross-domain joins can yield undefined results because of different ways in which join operations might be defined for database queries and other types of sources.</span></span> <span data-ttu-id="6fc40-106">En outre, une telle opération risque de provoquer une exception de mémoire insuffisante si la quantité de données dans la base de données est assez élevée.</span><span class="sxs-lookup"><span data-stu-id="6fc40-106">Additionally, there is a risk that such an operation could cause an out-of-memory exception if the amount of data in the database is large enough.</span></span> <span data-ttu-id="6fc40-107">Pour joindre des données d’une base de données à des données en mémoire, appelez d’abord `ToList` ou `ToArray` sur la requête de base de données, puis effectuez la jointure sur la collection retournée.</span><span class="sxs-lookup"><span data-stu-id="6fc40-107">To join data from a database to in-memory data, first call `ToList` or `ToArray` on the database query, and then perform the join on the returned collection.</span></span>

## <a name="to-create-the-data-file"></a><span data-ttu-id="6fc40-108">Pour créer le fichier de données</span><span class="sxs-lookup"><span data-stu-id="6fc40-108">To create the data file</span></span>

- <span data-ttu-id="6fc40-109">Copiez les fichiers Names. csv et scores. csv dans le dossier de votre projet, comme décrit dans Guide pratique [pour joindre du contenu issu de fichiers différents (LINQ) (Visual Basic)](how-to-join-content-from-dissimilar-files-linq.md).</span><span class="sxs-lookup"><span data-stu-id="6fc40-109">Copy the names.csv and scores.csv files into your project folder, as described in [How to: Join Content from Dissimilar Files (LINQ) (Visual Basic)](how-to-join-content-from-dissimilar-files-linq.md).</span></span>

## <a name="example"></a><span data-ttu-id="6fc40-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="6fc40-110">Example</span></span>

<span data-ttu-id="6fc40-111">L’exemple suivant montre comment utiliser un type nommé `Student` pour stocker des données fusionnées de deux collections en mémoire de chaînes qui simulent des données de feuille de calcul au format .csv.</span><span class="sxs-lookup"><span data-stu-id="6fc40-111">The following example shows how to use a named type `Student` to store merged data from two in-memory collections of strings that simulate spreadsheet data in .csv format.</span></span> <span data-ttu-id="6fc40-112">La première collection de chaînes représente les noms et les ID des étudiants, et la deuxième collection représente l’ID d’étudiant (dans la première colonne) et quatre notes d’examen.</span><span class="sxs-lookup"><span data-stu-id="6fc40-112">The first collection of strings represents the student names and IDs, and the second collection represents the student ID (in the first column) and four exam scores.</span></span> <span data-ttu-id="6fc40-113">L’ID est utilisé comme clé étrangère.</span><span class="sxs-lookup"><span data-stu-id="6fc40-113">The ID is used as the foreign key.</span></span>

```vb
Imports System.Collections.Generic
Imports System.Linq

Class Student
    Public FirstName As String
    Public LastName As String
    Public ID As Integer
    Public ExamScores As List(Of Integer)
End Class

Class PopulateCollection

    Shared Sub Main()

        ' Merge content from spreadsheets into a list of Student objects.

        ' These data files are defined in How to: Join Content from
        ' Dissimilar Files (LINQ).

        ' Each line of names.csv consists of a last name, a first name, and an
        ' ID number, separated by commas. For example, Omelchenko,Svetlana,111
        Dim names As String() = System.IO.File.ReadAllLines("../../../names.csv")

        ' Each line of scores.csv consists of an ID number and four test
        ' scores, separated by commas. For example, 111, 97, 92, 81, 60
        Dim scores As String() = System.IO.File.ReadAllLines("../../../scores.csv")

        ' The following query merges the content of two dissimilar spreadsheets
        ' based on common ID values.
        ' Multiple From clauses are used instead of a Join clause
        ' in order to store the results of scoreLine.Split.
        ' Note the dynamic creation of a list of integers for the
        ' ExamScores member. The first item is skipped in the split string
        ' because it is the student ID, not an exam score.
        Dim queryNamesScores = From nameLine In names
                          Let splitName = nameLine.Split(New Char() {","})
                          From scoreLine In scores
                          Let splitScoreLine = scoreLine.Split(New Char() {","})
                          Where Convert.ToInt32(splitName(2)) = Convert.ToInt32(splitScoreLine(0))
                          Select New Student() With {
                               .FirstName = splitName(1), .LastName = splitName(0), .ID = splitName(2),
                               .ExamScores = (From scoreAsText In splitScoreLine Skip 1
                                             Select Convert.ToInt32(scoreAsText)).ToList()}

        ' Optional. Store the query results for faster access in future
        ' queries. This could be useful with very large data files.
        Dim students As List(Of Student) = queryNamesScores.ToList()

        ' Display each student's name and exam score average.
        For Each s In students
            Console.WriteLine("The average score of " & s.FirstName & " " &
                              s.LastName & " is " & s.ExamScores.Average())
        Next

        ' Keep console window open in debug mode.
        Console.WriteLine("Press any key to exit.")
        Console.ReadKey()
    End Sub
End Class

' Output:
' The average score of Svetlana Omelchenko is 82.5
' The average score of Claire O'Donnell is 72.25
' The average score of Sven Mortensen is 84.5
' The average score of Cesar Garcia is 88.25
' The average score of Debra Garcia is 67
' The average score of Fadi Fakhouri is 92.25
' The average score of Hanying Feng is 88
' The average score of Hugo Garcia is 85.75
' The average score of Lance Tucker is 81.75
' The average score of Terry Adams is 85.25
' The average score of Eugene Zabokritski is 83
' The average score of Michael Tucker is 92
```

<span data-ttu-id="6fc40-114">Dans la clause [Select](../../../language-reference/queries/select-clause.md) , un initialiseur d’objet est utilisé pour instancier chaque nouvel objet à l' `Student` aide des données des deux sources.</span><span class="sxs-lookup"><span data-stu-id="6fc40-114">In the [Select Clause](../../../language-reference/queries/select-clause.md) clause, an object initializer is used to instantiate each new `Student` object by using the data from the two sources.</span></span>

<span data-ttu-id="6fc40-115">Si vous n’êtes pas obligé de stocker les résultats d’une requête, les types anonymes peuvent être plus pratiques que les types nommés.</span><span class="sxs-lookup"><span data-stu-id="6fc40-115">If you don't have to store the results of a query, anonymous types can be more convenient than named types.</span></span> <span data-ttu-id="6fc40-116">Les types nommés sont nécessaires si vous passez les résultats de requête en dehors de la méthode dans laquelle la requête est exécutée.</span><span class="sxs-lookup"><span data-stu-id="6fc40-116">Named types are required if you pass the query results outside the method in which the query is executed.</span></span> <span data-ttu-id="6fc40-117">L’exemple suivant effectue la même tâche que l’exemple précédent, mais il utilise des types anonymes plutôt que des types nommés :</span><span class="sxs-lookup"><span data-stu-id="6fc40-117">The following example performs the same task as the previous example, but uses anonymous types instead of named types:</span></span>

```vb
' Merge the data by using an anonymous type.
' Note the dynamic creation of a list of integers for the
' ExamScores member. We skip 1 because the first string
' in the array is the student ID, not an exam score.
Dim queryNamesScores2 =
    From nameLine In names
    Let splitName = nameLine.Split(New Char() {","})
    From scoreLine In scores
    Let splitScoreLine = scoreLine.Split(New Char() {","})
    Where Convert.ToInt32(splitName(2)) = Convert.ToInt32(splitScoreLine(0))
    Select New With
           {.Last = splitName(0),
            .First = splitName(1),
            .ExamScores = (From scoreAsText In splitScoreLine Skip 1
                           Select Convert.ToInt32(scoreAsText)).ToList()}

' Display each student's name and exam score average.
For Each s In queryNamesScores2
    Console.WriteLine("The average score of " & s.First & " " &
                      s.Last & " is " & s.ExamScores.Average())
Next
```

## <a name="see-also"></a><span data-ttu-id="6fc40-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6fc40-118">See also</span></span>

- [<span data-ttu-id="6fc40-119">LINQ et chaînes (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6fc40-119">LINQ and Strings (Visual Basic)</span></span>](linq-and-strings.md)
