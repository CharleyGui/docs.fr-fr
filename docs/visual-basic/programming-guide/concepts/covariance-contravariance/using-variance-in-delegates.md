---
title: Utilisation de la variance dans les délégués
ms.date: 07/20/2015
ms.assetid: 7b5c20f1-6416-46a3-94b6-f109c31c842c
ms.openlocfilehash: 842392a1342f7d3689d4d1f2a2adb7470eeda05e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84375782"
---
# <a name="using-variance-in-delegates-visual-basic"></a>Utilisation de la variance dans les délégués (Visual Basic)

Quand vous assignez une méthode à un délégué, la *covariance* et la *contravariance* offrent une grande flexibilité pour la mise en correspondance d’un type délégué avec une signature de méthode. La covariance permet à une méthode d’avoir un type de retour qui est plus dérivé que celui défini dans le délégué. La contravariance autorise une méthode qui a des types de paramètres moins dérivés que ceux du type délégué.

## <a name="example-1-covariance"></a>Exemple 1 : Covariance

### <a name="description"></a>Description

Cet exemple montre comment vous pouvez utiliser des délégués avec des méthodes ayant des types de retour dérivés du type de retour dans la signature du délégué. Le type de données retourné par `DogsHandler` est `Dogs`, qui dérive du type `Mammals` défini dans le délégué.

### <a name="code"></a>Code

```vb
Class Mammals
End Class

Class Dogs
    Inherits Mammals
End Class
Class Test
    Public Delegate Function HandlerMethod() As Mammals
    Public Shared Function MammalsHandler() As Mammals
        Return Nothing
    End Function
    Public Shared Function DogsHandler() As Dogs
        Return Nothing
    End Function
    Sub Test()
        Dim handlerMammals As HandlerMethod = AddressOf MammalsHandler
        ' Covariance enables this assignment.
        Dim handlerDogs As HandlerMethod = AddressOf DogsHandler
    End Sub
End Class
```

## <a name="example-2-contravariance"></a>Exemple 2 : Contravariance

### <a name="description"></a>Description

Cet exemple montre comment vous pouvez utiliser des délégués avec des méthodes ayant des paramètres dont les types sont des types de base du type de paramètre de signature de délégué. Avec la contravariance, vous pouvez maintenant utiliser un gestionnaire d’événements plutôt que des gestionnaires distincts. L’exemple suivant utilise deux délégués :

- Un délégué <xref:System.Windows.Forms.KeyEventHandler> qui définit la signature de l’événement [Button.KeyDown](xref:System.Windows.Forms.Control.KeyDown). Sa signature est :

   ```vb
   Public Delegate Sub KeyEventHandler(sender As Object, e As KeyEventArgs)
   ```

- Un délégué <xref:System.Windows.Forms.MouseEventHandler> qui définit la signature de l’événement [Button.MouseClick](xref:System.Windows.Forms.Control.MouseDown). Sa signature est :

   ```vb
   Public Delegate Sub MouseEventHandler(sender As Object, e As MouseEventArgs)
   ```

L’exemple définit un gestionnaire d’événements avec un paramètre <xref:System.EventArgs> et s’en sert pour gérer les événements `Button.KeyDown` et `Button.MouseClick`. C’est possible parce que <xref:System.EventArgs> est un type de base de <xref:System.Windows.Forms.KeyEventArgs> et <xref:System.Windows.Forms.MouseEventArgs>.

### <a name="code"></a>Code

```vb
' Event handler that accepts a parameter of the EventArgs type.
Private Sub MultiHandler(ByVal sender As Object,
                         ByVal e As System.EventArgs)
    Label1.Text = DateTime.Now
End Sub

Private Sub Form1_Load(ByVal sender As System.Object,
    ByVal e As System.EventArgs) Handles MyBase.Load

    ' You can use a method that has an EventArgs parameter,
    ' although the event expects the KeyEventArgs parameter.
    AddHandler Button1.KeyDown, AddressOf MultiHandler

    ' You can use the same method
    ' for the event that expects the MouseEventArgs parameter.
    AddHandler Button1.MouseClick, AddressOf MultiHandler
End Sub
```

## <a name="see-also"></a>Voir aussi

- [Variance dans les délégués (Visual Basic)](variance-in-delegates.md)
- [Utilisation de la variance pour les délégués génériques Func et Action (Visual Basic)](using-variance-for-func-and-action-generic-delegates.md)
