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
# <a name="using-variance-in-delegates-visual-basic"></a><span data-ttu-id="cb3bd-102">Utilisation de la variance dans les délégués (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cb3bd-102">Using Variance in Delegates (Visual Basic)</span></span>

<span data-ttu-id="cb3bd-103">Quand vous assignez une méthode à un délégué, la *covariance* et la *contravariance* offrent une grande flexibilité pour la mise en correspondance d’un type délégué avec une signature de méthode.</span><span class="sxs-lookup"><span data-stu-id="cb3bd-103">When you assign a method to a delegate, *covariance* and *contravariance* provide flexibility for matching a delegate type with a method signature.</span></span> <span data-ttu-id="cb3bd-104">La covariance permet à une méthode d’avoir un type de retour qui est plus dérivé que celui défini dans le délégué.</span><span class="sxs-lookup"><span data-stu-id="cb3bd-104">Covariance permits a method to have return type that is more derived than that defined in the delegate.</span></span> <span data-ttu-id="cb3bd-105">La contravariance autorise une méthode qui a des types de paramètres moins dérivés que ceux du type délégué.</span><span class="sxs-lookup"><span data-stu-id="cb3bd-105">Contravariance permits a method that has parameter types that are less derived than those in the delegate type.</span></span>

## <a name="example-1-covariance"></a><span data-ttu-id="cb3bd-106">Exemple 1 : Covariance</span><span class="sxs-lookup"><span data-stu-id="cb3bd-106">Example 1: Covariance</span></span>

### <a name="description"></a><span data-ttu-id="cb3bd-107">Description</span><span class="sxs-lookup"><span data-stu-id="cb3bd-107">Description</span></span>

<span data-ttu-id="cb3bd-108">Cet exemple montre comment vous pouvez utiliser des délégués avec des méthodes ayant des types de retour dérivés du type de retour dans la signature du délégué.</span><span class="sxs-lookup"><span data-stu-id="cb3bd-108">This example demonstrates how delegates can be used with methods that have return types that are derived from the return type in the delegate signature.</span></span> <span data-ttu-id="cb3bd-109">Le type de données retourné par `DogsHandler` est `Dogs`, qui dérive du type `Mammals` défini dans le délégué.</span><span class="sxs-lookup"><span data-stu-id="cb3bd-109">The data type returned by `DogsHandler` is of type `Dogs`, which derives from the `Mammals` type that is defined in the delegate.</span></span>

### <a name="code"></a><span data-ttu-id="cb3bd-110">Code</span><span class="sxs-lookup"><span data-stu-id="cb3bd-110">Code</span></span>

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

## <a name="example-2-contravariance"></a><span data-ttu-id="cb3bd-111">Exemple 2 : Contravariance</span><span class="sxs-lookup"><span data-stu-id="cb3bd-111">Example 2: Contravariance</span></span>

### <a name="description"></a><span data-ttu-id="cb3bd-112">Description</span><span class="sxs-lookup"><span data-stu-id="cb3bd-112">Description</span></span>

<span data-ttu-id="cb3bd-113">Cet exemple montre comment vous pouvez utiliser des délégués avec des méthodes ayant des paramètres dont les types sont des types de base du type de paramètre de signature de délégué.</span><span class="sxs-lookup"><span data-stu-id="cb3bd-113">This example demonstrates how delegates can be used with methods that have parameters whose types are base types of the delegate signature parameter type.</span></span> <span data-ttu-id="cb3bd-114">Avec la contravariance, vous pouvez maintenant utiliser un gestionnaire d’événements plutôt que des gestionnaires distincts.</span><span class="sxs-lookup"><span data-stu-id="cb3bd-114">With contravariance, you can use one event handler instead of separate handlers.</span></span> <span data-ttu-id="cb3bd-115">L’exemple suivant utilise deux délégués :</span><span class="sxs-lookup"><span data-stu-id="cb3bd-115">The following example makes use of two delegates:</span></span>

- <span data-ttu-id="cb3bd-116">Un délégué <xref:System.Windows.Forms.KeyEventHandler> qui définit la signature de l’événement [Button.KeyDown](xref:System.Windows.Forms.Control.KeyDown).</span><span class="sxs-lookup"><span data-stu-id="cb3bd-116">A <xref:System.Windows.Forms.KeyEventHandler> delegate that defines the signature of the [Button.KeyDown](xref:System.Windows.Forms.Control.KeyDown) event.</span></span> <span data-ttu-id="cb3bd-117">Sa signature est :</span><span class="sxs-lookup"><span data-stu-id="cb3bd-117">Its signature is:</span></span>

   ```vb
   Public Delegate Sub KeyEventHandler(sender As Object, e As KeyEventArgs)
   ```

- <span data-ttu-id="cb3bd-118">Un délégué <xref:System.Windows.Forms.MouseEventHandler> qui définit la signature de l’événement [Button.MouseClick](xref:System.Windows.Forms.Control.MouseDown).</span><span class="sxs-lookup"><span data-stu-id="cb3bd-118">A <xref:System.Windows.Forms.MouseEventHandler> delegate that defines the signature of the [Button.MouseClick](xref:System.Windows.Forms.Control.MouseDown) event.</span></span> <span data-ttu-id="cb3bd-119">Sa signature est :</span><span class="sxs-lookup"><span data-stu-id="cb3bd-119">Its signature is:</span></span>

   ```vb
   Public Delegate Sub MouseEventHandler(sender As Object, e As MouseEventArgs)
   ```

<span data-ttu-id="cb3bd-120">L’exemple définit un gestionnaire d’événements avec un paramètre <xref:System.EventArgs> et s’en sert pour gérer les événements `Button.KeyDown` et `Button.MouseClick`.</span><span class="sxs-lookup"><span data-stu-id="cb3bd-120">The example defines an event handler with an <xref:System.EventArgs> parameter and uses it to handle both the `Button.KeyDown` and `Button.MouseClick` events.</span></span> <span data-ttu-id="cb3bd-121">C’est possible parce que <xref:System.EventArgs> est un type de base de <xref:System.Windows.Forms.KeyEventArgs> et <xref:System.Windows.Forms.MouseEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="cb3bd-121">It can do this because <xref:System.EventArgs> is a base type of both <xref:System.Windows.Forms.KeyEventArgs>  and <xref:System.Windows.Forms.MouseEventArgs>.</span></span>

### <a name="code"></a><span data-ttu-id="cb3bd-122">Code</span><span class="sxs-lookup"><span data-stu-id="cb3bd-122">Code</span></span>

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

## <a name="see-also"></a><span data-ttu-id="cb3bd-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cb3bd-123">See also</span></span>

- [<span data-ttu-id="cb3bd-124">Variance dans les délégués (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cb3bd-124">Variance in Delegates (Visual Basic)</span></span>](variance-in-delegates.md)
- [<span data-ttu-id="cb3bd-125">Utilisation de la variance pour les délégués génériques Func et Action (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cb3bd-125">Using Variance for Func and Action Generic Delegates (Visual Basic)</span></span>](using-variance-for-func-and-action-generic-delegates.md)
