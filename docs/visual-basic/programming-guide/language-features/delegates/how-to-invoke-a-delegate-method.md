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
# <a name="how-to-invoke-a-delegate-method-visual-basic"></a><span data-ttu-id="fa44f-102">Comment : appeler une méthode déléguée (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fa44f-102">How to: Invoke a Delegate Method (Visual Basic)</span></span>

<span data-ttu-id="fa44f-103">Cet exemple montre comment associer une méthode à un délégué, puis comment appeler cette méthode via le délégué.</span><span class="sxs-lookup"><span data-stu-id="fa44f-103">This example shows how to associate a method with a delegate and then invoke that method through the delegate.</span></span>

### <a name="create-the-delegate-and-matching-procedures"></a><span data-ttu-id="fa44f-104">Créer le délégué et les procédures de correspondance</span><span class="sxs-lookup"><span data-stu-id="fa44f-104">Create the delegate and matching procedures</span></span>

1. <span data-ttu-id="fa44f-105">Créez un délégué nommé `MySubDelegate` .</span><span class="sxs-lookup"><span data-stu-id="fa44f-105">Create a delegate named `MySubDelegate`.</span></span>

    ```vb
    Delegate Sub MySubDelegate(ByVal x As Integer)
    ```

2. <span data-ttu-id="fa44f-106">Déclarez une classe qui contient une méthode avec la même signature que le délégué.</span><span class="sxs-lookup"><span data-stu-id="fa44f-106">Declare a class that contains a method with the same signature as the delegate.</span></span>

    ```vb
    Class class1
        Sub Sub1(ByVal x As Integer)
            MsgBox("The value of x is: " & CStr(x))
        End Sub
    End Class
    ```

3. <span data-ttu-id="fa44f-107">Définissez une méthode qui crée une instance du délégué et appelle la méthode associée au délégué en appelant la `Invoke` méthode intégrée.</span><span class="sxs-lookup"><span data-stu-id="fa44f-107">Define a method that creates an instance of the delegate and invokes the method associated with the delegate by calling the built-in `Invoke` method.</span></span>

    ```vb
    Protected Sub DelegateTest()
        Dim c1 As New class1
        ' Create an instance of the delegate.
        Dim msd As MySubDelegate = AddressOf c1.Sub1
        ' Call the method.
        msd.Invoke(10)
    End Sub
    ```

## <a name="see-also"></a><span data-ttu-id="fa44f-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fa44f-108">See also</span></span>

- [<span data-ttu-id="fa44f-109">Delegate, instruction</span><span class="sxs-lookup"><span data-stu-id="fa44f-109">Delegate Statement</span></span>](../../../language-reference/statements/delegate-statement.md)
- [<span data-ttu-id="fa44f-110">Délégués</span><span class="sxs-lookup"><span data-stu-id="fa44f-110">Delegates</span></span>](index.md)
- [<span data-ttu-id="fa44f-111">Événements</span><span class="sxs-lookup"><span data-stu-id="fa44f-111">Events</span></span>](../events/index.md)
- [<span data-ttu-id="fa44f-112">Applications multithread</span><span class="sxs-lookup"><span data-stu-id="fa44f-112">Multithreaded Applications</span></span>](../../../../standard/threading/using-threads-and-threading.md)
