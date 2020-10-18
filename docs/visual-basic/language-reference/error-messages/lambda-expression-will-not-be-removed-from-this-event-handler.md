---
title: L’expression lambda ne sera pas supprimée de ce gestionnaire d’événements
ms.date: 07/20/2015
f1_keywords:
- bc42326
- vbc42326
helpviewer_keywords:
- BC42326
ms.assetid: 63214dc6-0112-4245-8ebf-7c9e8f5a5782
ms.openlocfilehash: 5a30e63044b51f8176dfeebdcc9eb8fd517739ae
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163114"
---
# <a name="bc42326-lambda-expression-will-not-be-removed-from-this-event-handler"></a>BC42326 : l’expression lambda ne sera pas supprimée de ce gestionnaire d’événements

L’expression lambda ne sera pas supprimée de ce gestionnaire d’événements. Assignez l’expression lambda à une variable et utilisez la variable pour ajouter et supprimer l’événement.

Lorsque des expressions lambda sont utilisées avec des gestionnaires d’événements, vous ne verrez peut-être pas le comportement que vous attendez. Le compilateur génère une nouvelle méthode pour chaque définition d’expression lambda, même si elles sont identiques. Par conséquent, le code suivant s’affiche `False` .

```vb
Module Module1

    Sub Main()
        Dim fun1 As ChangeInteger = Function(p As Integer) p + 1
        Dim fun2 As ChangeInteger = Function(p As Integer) p + 1
        Console.WriteLine(fun1 = fun2)
    End Sub

    Delegate Function ChangeInteger(ByVal x As Integer) As Integer

End Module
```

Lorsque des expressions lambda sont utilisées avec des gestionnaires d’événements, cela peut entraîner des résultats inattendus. Dans l’exemple suivant, l’expression lambda ajoutée par `AddHandler` n’est pas supprimée par l' `RemoveHandler` instruction.

```vb
Module Module1

    Event ProcessInteger(ByVal x As Integer)

    Sub Main()

        ' The following line adds one listener to the event.
        AddHandler ProcessInteger, Function(m As Integer) m

        ' The following statement searches the current listeners
        ' for a match to remove. However, this lambda is not the same
        ' as the previous one, so nothing is removed.
        RemoveHandler ProcessInteger, Function(m As Integer) m

    End Sub
End Module
```

Par défaut, ce message est un avertissement. Pour plus d’informations sur le masquage des avertissements ou le traitement des avertissements en tant qu’erreurs, consultez [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).

**ID d’erreur :** BC42326

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

Pour éviter l’avertissement et supprimer l’expression lambda, assignez l’expression lambda à une variable et utilisez la variable dans les deux `AddHandler` `RemoveHandler` instructions et, comme indiqué dans l’exemple suivant.

```vb
Module Module1

    Event ProcessInteger(ByVal x As Integer)

    Dim PrintHandler As ProcessIntegerEventHandler

    Sub Main()

        ' Assign the lambda expression to a variable.
        PrintHandler = Function(m As Integer) m

        ' Use the variable to add the listener.
        AddHandler ProcessInteger, PrintHandler

        ' Use the variable again when you want to remove the listener.
        RemoveHandler ProcessInteger, PrintHandler

    End Sub
End Module
```

## <a name="see-also"></a>Voir aussi

- [Expressions lambda](../../programming-guide/language-features/procedures/lambda-expressions.md)
- [Conversion simplifiée des délégués](../../programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
- [Événements](../../programming-guide/language-features/events/index.md)
