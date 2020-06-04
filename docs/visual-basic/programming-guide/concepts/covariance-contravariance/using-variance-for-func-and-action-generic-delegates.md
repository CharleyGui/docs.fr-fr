---
title: Utilisation de la variance pour les délégués génériques Func et Action
ms.date: 07/20/2015
ms.assetid: 36c3012f-b39c-493b-b90f-079b5912ac1b
ms.openlocfilehash: f824d2422d67f1395d21a0863ca8c95d9f108989
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84375756"
---
# <a name="using-variance-for-func-and-action-generic-delegates-visual-basic"></a>Utilisation de la variance pour les délégués génériques Func et Action (Visual Basic)

Ces exemples montrent comment utiliser la covariance et la contravariance dans les délégués génériques `Func` et `Action` pour permettre de réutiliser des méthodes et fournir davantage de flexibilité dans votre code.

Pour plus d’informations sur la covariance et la contravariance, consultez [variance dans les délégués (Visual Basic)](variance-in-delegates.md).

## <a name="using-delegates-with-covariant-type-parameters"></a>Utilisation des délégués avec les paramètres de type covariant

L’exemple suivant illustre les avantages de la prise en charge de la covariance dans les délégués génériques `Func`. La méthode `FindByTitle` prend un paramètre de type `String` et retourne un objet de type `Employee`. Toutefois, vous pouvez assigner cette méthode au délégué `Func(Of String, Person)`, car `Employee` hérite de `Person`.

```vb
' Simple hierarchy of classes.
Public Class Person
End Class

Public Class Employee
    Inherits Person
End Class

Class Finder
    Public Shared Function FindByTitle(
        ByVal title As String) As Employee
        ' This is a stub for a method that returns
        ' an employee that has the specified title.
        Return New Employee
    End Function

    Sub Test()
        ' Create an instance of the delegate without using variance.
        Dim findEmployee As Func(Of String, Employee) =
            AddressOf FindByTitle

        ' The delegate expects a method to return Person,
        ' but you can assign it a method that returns Employee.
        Dim findPerson As Func(Of String, Person) =
            AddressOf FindByTitle

        ' You can also assign a delegate
        ' that returns a more derived type to a delegate
        ' that returns a less derived type.
        findPerson = findEmployee
    End Sub
End Class
```

## <a name="using-delegates-with-contravariant-type-parameters"></a>Utilisation des délégués avec les paramètres de type contravariant

L’exemple suivant illustre les avantages de la prise en charge de la contravariance dans les délégués génériques `Action`. La méthode `AddToContacts` prend un paramètre de type `Person`. Toutefois, vous pouvez assigner cette méthode au délégué `Action(Of Employee)`, car `Employee` hérite de `Person`.

```vb
Public Class Person
End Class

Public Class Employee
    Inherits Person
End Class

Class AddressBook
    Shared Sub AddToContacts(ByVal person As Person)
        ' This method adds a Person object
        ' to a contact list.
    End Sub

    Sub Test()
        ' Create an instance of the delegate without using variance.
        Dim addPersonToContacts As Action(Of Person) =
            AddressOf AddToContacts

        ' The Action delegate expects
        ' a method that has an Employee parameter,
        ' but you can assign it a method that has a Person parameter
        ' because Employee derives from Person.
        Dim addEmployeeToContacts As Action(Of Employee) =
            AddressOf AddToContacts

        ' You can also assign a delegate
        ' that accepts a less derived parameter
        ' to a delegate that accepts a more derived parameter.
        addEmployeeToContacts = addPersonToContacts
    End Sub
End Class
```

## <a name="see-also"></a>Voir aussi

- [Covariance et contravariance (Visual Basic)](index.md)
- [Génériques](../../../../standard/generics/index.md)
