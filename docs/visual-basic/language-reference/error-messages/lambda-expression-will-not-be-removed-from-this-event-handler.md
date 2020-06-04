---
title: L’expression lambda ne sera pas supprimée de ce gestionnaire d’événements
ms.date: 07/20/2015
f1_keywords:
- bc42326
- vbc42326
helpviewer_keywords:
- BC42326
ms.assetid: 63214dc6-0112-4245-8ebf-7c9e8f5a5782
ms.openlocfilehash: 07ace3f1b9c5e512227dc1f718ef768b631c8303
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397374"
---
# <a name="lambda-expression-will-not-be-removed-from-this-event-handler"></a><span data-ttu-id="6de65-102">L’expression lambda ne sera pas supprimée de ce gestionnaire d’événements</span><span class="sxs-lookup"><span data-stu-id="6de65-102">Lambda expression will not be removed from this event handler</span></span>

<span data-ttu-id="6de65-103">L’expression lambda ne sera pas supprimée de ce gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="6de65-103">Lambda expression will not be removed from this event handler.</span></span> <span data-ttu-id="6de65-104">Assignez l’expression lambda à une variable et utilisez la variable pour ajouter et supprimer l’événement.</span><span class="sxs-lookup"><span data-stu-id="6de65-104">Assign the lambda expression to a variable and use the variable to add and remove the event.</span></span>

<span data-ttu-id="6de65-105">Lorsque des expressions lambda sont utilisées avec des gestionnaires d’événements, vous ne verrez peut-être pas le comportement que vous attendez.</span><span class="sxs-lookup"><span data-stu-id="6de65-105">When lambda expressions are used with event handlers, you may not see the behavior you expect.</span></span> <span data-ttu-id="6de65-106">Le compilateur génère une nouvelle méthode pour chaque définition d’expression lambda, même si elles sont identiques.</span><span class="sxs-lookup"><span data-stu-id="6de65-106">The compiler generates a new method for each lambda expression definition, even if they are identical.</span></span> <span data-ttu-id="6de65-107">Par conséquent, le code suivant s’affiche `False` .</span><span class="sxs-lookup"><span data-stu-id="6de65-107">Therefore, the following code displays `False`.</span></span>

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

<span data-ttu-id="6de65-108">Lorsque des expressions lambda sont utilisées avec des gestionnaires d’événements, cela peut entraîner des résultats inattendus.</span><span class="sxs-lookup"><span data-stu-id="6de65-108">When lambda expressions are used with event handlers, this may cause unexpected results.</span></span> <span data-ttu-id="6de65-109">Dans l’exemple suivant, l’expression lambda ajoutée par `AddHandler` n’est pas supprimée par l' `RemoveHandler` instruction.</span><span class="sxs-lookup"><span data-stu-id="6de65-109">In the following example, the lambda expression added by `AddHandler` is not removed by the `RemoveHandler` statement.</span></span>

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

<span data-ttu-id="6de65-110">Par défaut, ce message est un avertissement.</span><span class="sxs-lookup"><span data-stu-id="6de65-110">By default, this message is a warning.</span></span> <span data-ttu-id="6de65-111">Pour plus d’informations sur le masquage des avertissements ou le traitement des avertissements en tant qu’erreurs, consultez [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="6de65-111">For more information about how to hide warnings or treat warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>

<span data-ttu-id="6de65-112">**ID d’erreur :** BC42326</span><span class="sxs-lookup"><span data-stu-id="6de65-112">**Error ID:** BC42326</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="6de65-113">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="6de65-113">To correct this error</span></span>

<span data-ttu-id="6de65-114">Pour éviter l’avertissement et supprimer l’expression lambda, assignez l’expression lambda à une variable et utilisez la variable dans les deux `AddHandler` `RemoveHandler` instructions et, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="6de65-114">To avoid the warning and remove the lambda expression, assign the lambda expression to a variable and use the variable in both the `AddHandler` and `RemoveHandler` statements, as shown in the following example.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="6de65-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6de65-115">See also</span></span>

- [<span data-ttu-id="6de65-116">Expressions lambda</span><span class="sxs-lookup"><span data-stu-id="6de65-116">Lambda Expressions</span></span>](../../programming-guide/language-features/procedures/lambda-expressions.md)
- [<span data-ttu-id="6de65-117">Conversion simplifiée des délégués</span><span class="sxs-lookup"><span data-stu-id="6de65-117">Relaxed Delegate Conversion</span></span>](../../programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
- [<span data-ttu-id="6de65-118">Événements</span><span class="sxs-lookup"><span data-stu-id="6de65-118">Events</span></span>](../../programming-guide/language-features/events/index.md)
