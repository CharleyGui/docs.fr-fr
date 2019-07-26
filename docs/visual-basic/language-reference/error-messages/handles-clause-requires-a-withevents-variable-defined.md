---
title: La clause Handles requiert une variable WithEvents définie dans le type conteneur ou l'un de ses types de base
ms.date: 07/20/2015
f1_keywords:
- vbc30506
- bc30506
helpviewer_keywords:
- BC30506
ms.assetid: 5b66f6a8-f050-4e03-a57f-a64e85f80cb5
ms.openlocfilehash: 04c94d3d32660d1a186a9bb377c49a53e1451be6
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/26/2019
ms.locfileid: "68512735"
---
# <a name="handles-clause-requires-a-withevents-variable-defined-in-the-containing-type-or-one-of-its-base-types"></a><span data-ttu-id="16e0b-102">La clause Handles requiert une variable WithEvents définie dans le type conteneur ou l'un de ses types de base</span><span class="sxs-lookup"><span data-stu-id="16e0b-102">Handles clause requires a WithEvents variable defined in the containing type or one of its base types</span></span>
<span data-ttu-id="16e0b-103">Vous n’avez pas fourni `WithEvents` de variable dans `Handles` votre clause.</span><span class="sxs-lookup"><span data-stu-id="16e0b-103">You did not supply a `WithEvents` variable in your `Handles` clause.</span></span> <span data-ttu-id="16e0b-104">Le `Handles` mot clé à la fin d’une déclaration de procédure l’amène à gérer des événements déclenchés par une variable `WithEvents` objet déclarée à l’aide du mot clé.</span><span class="sxs-lookup"><span data-stu-id="16e0b-104">The `Handles` keyword at the end of a procedure declaration causes it to handle events raised by an object variable declared using the `WithEvents` keyword.</span></span>
  
 <span data-ttu-id="16e0b-105">**ID d’erreur:** BC30506</span><span class="sxs-lookup"><span data-stu-id="16e0b-105">**Error ID:** BC30506</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="16e0b-106">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="16e0b-106">To correct this error</span></span>
  
- <span data-ttu-id="16e0b-107">Fournissez la `WithEvents` variable nécessaire.</span><span class="sxs-lookup"><span data-stu-id="16e0b-107">Supply the necessary `WithEvents` variable.</span></span>
  
## <a name="example"></a><span data-ttu-id="16e0b-108">Exemples</span><span class="sxs-lookup"><span data-stu-id="16e0b-108">Example</span></span>

<span data-ttu-id="16e0b-109">Dans l’exemple suivant, Visual Basic génère une erreur `BC30506` du compilateur, car le mot clé [WithEvents](../modifiers/withevents.md) n’est pas utilisé <xref:System.Timers.Timer?displayProperty=nameWithType> dans la définition de l’instance.</span><span class="sxs-lookup"><span data-stu-id="16e0b-109">In the following example, Visual Basic generates compiler error `BC30506` because the [WithEvents](../modifiers/withevents.md) keyword is not used in the definition of the <xref:System.Timers.Timer?displayProperty=nameWithType> instance.</span></span>

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

<span data-ttu-id="16e0b-110">L’exemple suivant compile correctement, car la `_timer1` variable est définie avec le `WithEvents` mot clé:</span><span class="sxs-lookup"><span data-stu-id="16e0b-110">The following example compiles successfully because the `_timer1` variable is defined with the `WithEvents` keyword:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="16e0b-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="16e0b-111">See also</span></span>

- [<span data-ttu-id="16e0b-112">Handles</span><span class="sxs-lookup"><span data-stu-id="16e0b-112">Handles</span></span>](../../../visual-basic/language-reference/statements/handles-clause.md)
