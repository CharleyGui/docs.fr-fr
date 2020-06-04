---
title: 'Comment : appeler une méthode déléguée'
ms.date: 07/20/2015
ms.assetid: b56866ae-abf9-4a5a-a855-486359455e9c
ms.openlocfilehash: f319727c007b93c7b334af0598f1b9f7c034144d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410719"
---
# <a name="how-to-invoke-a-delegate-method-visual-basic"></a>Comment : appeler une méthode déléguée (Visual Basic)

Cet exemple montre comment associer une méthode à un délégué, puis comment appeler cette méthode via le délégué.

### <a name="create-the-delegate-and-matching-procedures"></a>Créer le délégué et les procédures de correspondance

1. Créez un délégué nommé `MySubDelegate` .

    ```vb
    Delegate Sub MySubDelegate(ByVal x As Integer)
    ```

2. Déclarez une classe qui contient une méthode avec la même signature que le délégué.

    ```vb
    Class class1
        Sub Sub1(ByVal x As Integer)
            MsgBox("The value of x is: " & CStr(x))
        End Sub
    End Class
    ```

3. Définissez une méthode qui crée une instance du délégué et appelle la méthode associée au délégué en appelant la `Invoke` méthode intégrée.

    ```vb
    Protected Sub DelegateTest()
        Dim c1 As New class1
        ' Create an instance of the delegate.
        Dim msd As MySubDelegate = AddressOf c1.Sub1
        ' Call the method.
        msd.Invoke(10)
    End Sub
    ```

## <a name="see-also"></a>Voir aussi

- [Delegate, instruction](../../../language-reference/statements/delegate-statement.md)
- [Délégués](index.md)
- [Événements](../events/index.md)
- [Applications multithread](../../../../standard/threading/using-threads-and-threading.md)
