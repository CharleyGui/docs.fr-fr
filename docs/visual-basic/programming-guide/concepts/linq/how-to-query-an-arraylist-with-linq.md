---
title: 'Procédure : interroger un ArrayList avec LINQ'
ms.date: 07/20/2015
ms.assetid: 176358a9-d765-4b57-9557-7feb4428138d
ms.openlocfilehash: b7b75e017fb314b5e5998b743dbf922f34fd9b7c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396465"
---
# <a name="how-to-query-an-arraylist-with-linq-visual-basic"></a><span data-ttu-id="518fc-102">Comment : interroger un ArrayList avec LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="518fc-102">How to: Query an ArrayList with LINQ (Visual Basic)</span></span>

<span data-ttu-id="518fc-103">Quand vous utilisez LINQ pour interroger des collections <xref:System.Collections.IEnumerable> non génériques telles que <xref:System.Collections.ArrayList>, vous devez déclarer explicitement le type de la variable de portée pour qu’il reflète le type spécifique des objets de la collection.</span><span class="sxs-lookup"><span data-stu-id="518fc-103">When using LINQ to query non-generic <xref:System.Collections.IEnumerable> collections such as <xref:System.Collections.ArrayList>, you must explicitly declare the type of the range variable to reflect the specific type of the objects in the collection.</span></span> <span data-ttu-id="518fc-104">Par exemple, si vous avez un <xref:System.Collections.ArrayList> d' `Student` objets, votre [clause from](../../../language-reference/queries/from-clause.md) doit ressembler à ceci :</span><span class="sxs-lookup"><span data-stu-id="518fc-104">For example, if you have an <xref:System.Collections.ArrayList> of `Student` objects, your [From Clause](../../../language-reference/queries/from-clause.md) should look like this:</span></span>

```vb
Dim query = From student As Student In arrList
'...
```

<span data-ttu-id="518fc-105">En spécifiant le type de la variable de portée, vous effectuez un cast de chaque élément du `Student` en <xref:System.Collections.ArrayList>.</span><span class="sxs-lookup"><span data-stu-id="518fc-105">By specifying the type of the range variable, you are casting each item in the <xref:System.Collections.ArrayList> to a `Student`.</span></span>

<span data-ttu-id="518fc-106">L’utilisation d’une variable de portée explicitement typée dans une expression de requête équivaut à appeler la méthode <xref:System.Linq.Enumerable.Cast%2A>.</span><span class="sxs-lookup"><span data-stu-id="518fc-106">The use of an explicitly typed range variable in a query expression is equivalent to calling the <xref:System.Linq.Enumerable.Cast%2A> method.</span></span> <span data-ttu-id="518fc-107"><xref:System.Linq.Enumerable.Cast%2A> lève une exception si le cast spécifié ne peut pas être effectué.</span><span class="sxs-lookup"><span data-stu-id="518fc-107"><xref:System.Linq.Enumerable.Cast%2A> throws an exception if the specified cast cannot be performed.</span></span> <span data-ttu-id="518fc-108"><xref:System.Linq.Enumerable.Cast%2A> et <xref:System.Linq.Enumerable.OfType%2A> sont les deux méthodes d’opérateur de requête standard qui fonctionnent sur les types <xref:System.Collections.IEnumerable> non génériques.</span><span class="sxs-lookup"><span data-stu-id="518fc-108"><xref:System.Linq.Enumerable.Cast%2A> and <xref:System.Linq.Enumerable.OfType%2A> are the two Standard Query Operator methods that operate on non-generic <xref:System.Collections.IEnumerable> types.</span></span> <span data-ttu-id="518fc-109">Dans Visual Basic, vous devez appeler explicitement la <xref:System.Linq.Enumerable.Cast%2A> méthode sur la source de données pour garantir un type de variable de portée spécifique.</span><span class="sxs-lookup"><span data-stu-id="518fc-109">In Visual Basic, you must explicitly call the <xref:System.Linq.Enumerable.Cast%2A> method on the data source to ensure a specific range variable type.</span></span> <span data-ttu-id="518fc-110">Pour plus d’informations, consultez [relations de types dans les opérations de requête (Visual Basic)](type-relationships-in-query-operations.md).</span><span class="sxs-lookup"><span data-stu-id="518fc-110">For more information, see [Type Relationships in Query Operations (Visual Basic)](type-relationships-in-query-operations.md).</span></span>

## <a name="example"></a><span data-ttu-id="518fc-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="518fc-111">Example</span></span>

<span data-ttu-id="518fc-112">L’exemple suivant montre une requête simple sur un <xref:System.Collections.ArrayList>.</span><span class="sxs-lookup"><span data-stu-id="518fc-112">The following example shows a simple query over an <xref:System.Collections.ArrayList>.</span></span> <span data-ttu-id="518fc-113">Notez que cet exemple utilise des initialiseurs d’objets quand le code appelle la méthode <xref:System.Collections.ArrayList.Add%2A>, mais cela n’est pas une obligation.</span><span class="sxs-lookup"><span data-stu-id="518fc-113">Note that this example uses object initializers when the code calls the <xref:System.Collections.ArrayList.Add%2A> method, but this is not a requirement.</span></span>

```vb
Imports System.Collections
Imports System.Linq

Module Module1

    Public Class Student
        Public Property FirstName As String
        Public Property LastName As String
        Public Property Scores As Integer()
    End Class

    Sub Main()

        Dim student1 As New Student With {.FirstName = "Svetlana",
                                     .LastName = "Omelchenko",
                                     .Scores = New Integer() {98, 92, 81, 60}}
        Dim student2 As New Student With {.FirstName = "Claire",
                                    .LastName = "O'Donnell",
                                    .Scores = New Integer() {75, 84, 91, 39}}
        Dim student3 As New Student With {.FirstName = "Cesar",
                                    .LastName = "Garcia",
                                    .Scores = New Integer() {97, 89, 85, 82}}
        Dim student4 As New Student With {.FirstName = "Sven",
                                    .LastName = "Mortensen",
                                    .Scores = New Integer() {88, 94, 65, 91}}

        Dim arrList As New ArrayList()
        arrList.Add(student1)
        arrList.Add(student2)
        arrList.Add(student3)
        arrList.Add(student4)

        ' Use an explicit type for non-generic collections
        Dim query = From student As Student In arrList
                    Where student.Scores(0) > 95
                    Select student

        For Each student As Student In query
            Console.WriteLine(student.LastName & ": " & student.Scores(0))
        Next
        ' Keep the console window open in debug mode.
        Console.WriteLine("Press any key to exit.")
        Console.ReadKey()
    End Sub

End Module
' Output:
'   Omelchenko: 98
'   Garcia: 97
```

## <a name="see-also"></a><span data-ttu-id="518fc-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="518fc-114">See also</span></span>

- [<span data-ttu-id="518fc-115">LINQ to Objects (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="518fc-115">LINQ to Objects (Visual Basic)</span></span>](linq-to-objects.md)
