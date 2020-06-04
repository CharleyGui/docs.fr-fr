---
title: La fonction imbriquée n'a pas une signature compatible avec le délégué '<delegatename>'.
ms.date: 07/20/2015
f1_keywords:
- vbc36532
- bc36532
helpviewer_keywords:
- BC36532
ms.assetid: 493f292c-d81e-40ef-8b47-61f020571829
ms.openlocfilehash: 28d07f01c0fd467cb68d73749988273eee95edf4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409424"
---
# <a name="nested-function-does-not-have-a-signature-that-is-compatible-with-delegate-delegatename"></a><span data-ttu-id="1587c-102">La fonction imbriquée n'a pas une signature compatible avec le délégué '\<delegatename>'.</span><span class="sxs-lookup"><span data-stu-id="1587c-102">Nested function does not have a signature that is compatible with delegate '\<delegatename>'</span></span>

<span data-ttu-id="1587c-103">Une expression lambda a été assignée à un délégué qui a une signature incompatible.</span><span class="sxs-lookup"><span data-stu-id="1587c-103">A lambda expression has been assigned to a delegate that has an incompatible signature.</span></span> <span data-ttu-id="1587c-104">Par exemple, dans le code suivant, le délégué `Del` a deux paramètres entiers.</span><span class="sxs-lookup"><span data-stu-id="1587c-104">For example, in the following code, delegate `Del` has two integer parameters.</span></span>

```vb
Delegate Function Del(ByVal p As Integer, ByVal q As Integer) As Integer
```

<span data-ttu-id="1587c-105">L’erreur est déclenchée si une expression lambda avec un argument est déclarée en tant que type `Del` :</span><span class="sxs-lookup"><span data-stu-id="1587c-105">The error is raised if a lambda expression with one argument is declared as type `Del`:</span></span>

```vb
' Neither of these is valid.
' Dim lambda1 As Del = Function(n As Integer) n + 1
' Dim lambda2 As Del = Function(n) n + 1
```

<span data-ttu-id="1587c-106">**ID d’erreur :** BC36532</span><span class="sxs-lookup"><span data-stu-id="1587c-106">**Error ID:** BC36532</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="1587c-107">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="1587c-107">To correct this error</span></span>

<span data-ttu-id="1587c-108">Ajustez la définition du délégué ou l’expression lambda assignée afin que les signatures soient compatibles.</span><span class="sxs-lookup"><span data-stu-id="1587c-108">Adjust either the delegate definition or the assigned lambda expression so that the signatures are compatible.</span></span>

## <a name="see-also"></a><span data-ttu-id="1587c-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1587c-109">See also</span></span>

- [<span data-ttu-id="1587c-110">Conversion simplifiée des délégués</span><span class="sxs-lookup"><span data-stu-id="1587c-110">Relaxed Delegate Conversion</span></span>](../../programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
- [<span data-ttu-id="1587c-111">Expressions lambda</span><span class="sxs-lookup"><span data-stu-id="1587c-111">Lambda Expressions</span></span>](../../programming-guide/language-features/procedures/lambda-expressions.md)
