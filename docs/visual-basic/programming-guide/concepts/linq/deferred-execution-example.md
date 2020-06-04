---
title: Exemple d'exécution différée
ms.date: 07/20/2015
ms.assetid: 9a22bea1-c755-4aac-800a-fcd9e5107ace
ms.openlocfilehash: 863b018b6047d61f6fb4a5c1ac68151ed69d24a1
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410797"
---
# <a name="deferred-execution-example-visual-basic"></a><span data-ttu-id="936a8-102">Exemple d’exécution différée (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="936a8-102">Deferred Execution Example (Visual Basic)</span></span>

<span data-ttu-id="936a8-103">Cette rubrique montre comment l'exécution et l'évaluation différées affectent l'exécution de vos requêtes LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="936a8-103">This topic shows how deferred execution and lazy evaluation affect the execution of your LINQ to XML queries.</span></span>

## <a name="example"></a><span data-ttu-id="936a8-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="936a8-104">Example</span></span>

<span data-ttu-id="936a8-105">L'exemple suivant illustre l'ordre d'exécution lors de l'utilisation d'une méthode d'extension qui utilise l'exécution différée.</span><span class="sxs-lookup"><span data-stu-id="936a8-105">The following example shows the order of execution when using an extension method that uses deferred execution.</span></span> <span data-ttu-id="936a8-106">L'exemple déclare un tableau de trois chaînes.</span><span class="sxs-lookup"><span data-stu-id="936a8-106">The example declares an array of three strings.</span></span> <span data-ttu-id="936a8-107">Il itère ensuite au sein de la collection retournée par `ConvertCollectionToUpperCase`.</span><span class="sxs-lookup"><span data-stu-id="936a8-107">It then iterates through the collection returned by `ConvertCollectionToUpperCase`.</span></span>

```vb
Imports System.Runtime.CompilerServices

Module Module1

    <Extension()>
    Private Iterator Function ConvertCollectionToUpperCase(
    ByVal source As IEnumerable(Of String)) _
    As IEnumerable(Of String)
        For Each str As String In source
            Console.WriteLine("ToUpper: source {0}", str)
            Yield str.ToUpper()
        Next
    End Function

    Sub Main()
        Dim stringArray = New String() {"abc", "def", "ghi"}

        Dim q = From str In stringArray.ConvertCollectionToUpperCase()
                Select str

        For Each Str As String In q
            Console.WriteLine("Main: str {0}", Str)
        Next
    End Sub

End Module
```

<span data-ttu-id="936a8-108">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="936a8-108">This example produces the following output:</span></span>

```console
ToUpper: source abc
Main: str ABC
ToUpper: source def
Main: str DEF
ToUpper: source ghi
Main: str GHI
```

<span data-ttu-id="936a8-109">Notez que lors de l'itération de la collection retournée par `ConvertCollectionToUpperCase`, chaque élément est récupéré du tableau de chaînes source et converti en majuscules avant que l'élément suivant ne soit récupéré du tableau de chaînes source.</span><span class="sxs-lookup"><span data-stu-id="936a8-109">Notice that when iterating through the collection returned by `ConvertCollectionToUpperCase`, each item is retrieved from the source string array and converted to uppercase before the next item is retrieved from the source string array.</span></span>

<span data-ttu-id="936a8-110">Vous pouvez constater que l'intégralité du tableau de chaînes n'est pas convertie en majuscules avant que chaque élément de la collection retournée n'ait été traité dans la boucle `foreach` dans `Main`.</span><span class="sxs-lookup"><span data-stu-id="936a8-110">You can see that the entire array of strings is not converted to uppercase before each item in the returned collection is processed in the `foreach` loop in `Main`.</span></span>

## <a name="see-also"></a><span data-ttu-id="936a8-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="936a8-111">See also</span></span>

- [<span data-ttu-id="936a8-112">Didacticiel : exécution différée (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="936a8-112">Tutorial: Deferred Execution (Visual Basic)</span></span>](tutorial-deferred-execution.md)
