---
title: La clause Handles requiert une variable WithEvents définie dans le type conteneur ou l'un de ses types de base
ms.date: 07/20/2015
f1_keywords:
- vbc30506
- bc30506
helpviewer_keywords:
- BC30506
ms.assetid: 5b66f6a8-f050-4e03-a57f-a64e85f80cb5
ms.openlocfilehash: 191415408f607d0ff768e50c41fa9b3c4405a688
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582825"
---
# <a name="handles-clause-requires-a-withevents-variable-defined-in-the-containing-type-or-one-of-its-base-types"></a><span data-ttu-id="039bc-102">La clause Handles requiert une variable WithEvents définie dans le type conteneur ou l'un de ses types de base</span><span class="sxs-lookup"><span data-stu-id="039bc-102">Handles clause requires a WithEvents variable defined in the containing type or one of its base types</span></span>

<span data-ttu-id="039bc-103">Vous n’avez pas fourni de variable `WithEvents` dans votre clause `Handles`.</span><span class="sxs-lookup"><span data-stu-id="039bc-103">You did not supply a `WithEvents` variable in your `Handles` clause.</span></span> <span data-ttu-id="039bc-104">Le mot clé `Handles` à la fin d’une déclaration de procédure, il gère les événements déclenchés par une variable objet déclarée à l’aide du mot clé `WithEvents`.</span><span class="sxs-lookup"><span data-stu-id="039bc-104">The `Handles` keyword at the end of a procedure declaration causes it to handle events raised by an object variable declared using the `WithEvents` keyword.</span></span>

<span data-ttu-id="039bc-105">**ID d’erreur :** BC30506</span><span class="sxs-lookup"><span data-stu-id="039bc-105">**Error ID:** BC30506</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="039bc-106">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="039bc-106">To correct this error</span></span>

<span data-ttu-id="039bc-107">Fournissez la variable `WithEvents` nécessaire.</span><span class="sxs-lookup"><span data-stu-id="039bc-107">Supply the necessary `WithEvents` variable.</span></span>

## <a name="example"></a><span data-ttu-id="039bc-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="039bc-108">Example</span></span>

<span data-ttu-id="039bc-109">Dans l’exemple suivant, Visual Basic génère une erreur du compilateur `BC30506` car le mot clé [WithEvents](../modifiers/withevents.md) n’est pas utilisé dans la définition de l’instance <xref:System.Timers.Timer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="039bc-109">In the following example, Visual Basic generates compiler error `BC30506` because the [WithEvents](../modifiers/withevents.md) keyword is not used in the definition of the <xref:System.Timers.Timer?displayProperty=nameWithType> instance.</span></span>

```vb
Imports System.Timers

Module Module1
    Private _timer1 As New Timer() With {.Interval = 1000, .Enabled = True}

    Sub Main()
        Console.WriteLine("Press any key to start the timer...")
        Console.ReadKey()
        _timer1.Start()
        Console.ReadKey()
    End Sub

    Private Sub Timer1_Tick(sender As Object, args As EventArgs) Handles _timer1.Elapsed
        Console.WriteLine("Press any key to terminate...")
    End Sub
End Module
```

<span data-ttu-id="039bc-110">L’exemple suivant compile correctement, car la variable `_timer1` est définie avec le mot clé `WithEvents` :</span><span class="sxs-lookup"><span data-stu-id="039bc-110">The following example compiles successfully because the `_timer1` variable is defined with the `WithEvents` keyword:</span></span>

```vb
Imports System.Timers

Module Module1
    Private WithEvents _timer1 As New Timer() With {.Interval = 1000}

    Sub Main()
        Console.WriteLine("Press any key to start the timer...")
        Console.ReadKey()
        _timer1.Start()
        Console.ReadKey()
    End Sub

    Private Sub Timer1_Tick(sender As Object, args As EventArgs) Handles _timer1.Elapsed
        Console.WriteLine("Press any key to terminate...")
    End Sub

End Module
```

## <a name="see-also"></a><span data-ttu-id="039bc-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="039bc-111">See also</span></span>

- [<span data-ttu-id="039bc-112">Handles</span><span class="sxs-lookup"><span data-stu-id="039bc-112">Handles</span></span>](../../../visual-basic/language-reference/statements/handles-clause.md)
