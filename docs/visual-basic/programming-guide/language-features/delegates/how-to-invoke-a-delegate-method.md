---
title: 'Comment : appeler une méthode déléguée'
ms.date: 07/20/2015
ms.assetid: b56866ae-abf9-4a5a-a855-486359455e9c
ms.openlocfilehash: 520bacfbe6103490e0459cd5af149c1d55a8fce4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345262"
---
# <a name="how-to-invoke-a-delegate-method-visual-basic"></a>Comment : appeler une méthode déléguée (Visual Basic)

Cet exemple montre comment associer une méthode à un délégué, puis comment appeler cette méthode via le délégué.

### <a name="create-the-delegate-and-matching-procedures"></a>Créer le délégué et les procédures de correspondance

1. Créez un délégué nommé `MySubDelegate`.

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

3. Définissez une méthode qui crée une instance du délégué et appelle la méthode associée au délégué en appelant la méthode `Invoke` intégrée.

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

- [Delegate (instruction)](../../../../visual-basic/language-reference/statements/delegate-statement.md)
- [Délégués](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [Événements](../../../../visual-basic/programming-guide/language-features/events/index.md)
- [Applications multithread](../../../../standard/threading/using-threads-and-threading.md)
