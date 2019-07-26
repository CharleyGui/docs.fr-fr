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
# <a name="handles-clause-requires-a-withevents-variable-defined-in-the-containing-type-or-one-of-its-base-types"></a>La clause Handles requiert une variable WithEvents définie dans le type conteneur ou l'un de ses types de base
Vous n’avez pas fourni `WithEvents` de variable dans `Handles` votre clause. Le `Handles` mot clé à la fin d’une déclaration de procédure l’amène à gérer des événements déclenchés par une variable `WithEvents` objet déclarée à l’aide du mot clé.
  
 **ID d’erreur:** BC30506

## <a name="to-correct-this-error"></a>Pour corriger cette erreur
  
- Fournissez la `WithEvents` variable nécessaire.
  
## <a name="example"></a>Exemples

Dans l’exemple suivant, Visual Basic génère une erreur `BC30506` du compilateur, car le mot clé [WithEvents](../modifiers/withevents.md) n’est pas utilisé <xref:System.Timers.Timer?displayProperty=nameWithType> dans la définition de l’instance.

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

L’exemple suivant compile correctement, car la `_timer1` variable est définie avec le `WithEvents` mot clé:

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

## <a name="see-also"></a>Voir aussi

- [Handles](../../../visual-basic/language-reference/statements/handles-clause.md)
