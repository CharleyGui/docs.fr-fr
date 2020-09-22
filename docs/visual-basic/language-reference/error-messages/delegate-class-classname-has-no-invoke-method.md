---
title: La classe déléguée '<classname>' n'a pas de méthode Invoke, c'est pourquoi une expression de ce type ne peut pas être la cible d'un appel de méthode
ms.date: 07/20/2015
f1_keywords:
- vbc30220
- bc30220
helpviewer_keywords:
- BC30220
ms.assetid: 6be0d61c-f2f9-4f9b-ab90-8871a0d7206d
ms.openlocfilehash: e6ad06262806088347c94b3040b743618a3b3695
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874495"
---
# <a name="delegate-class-classname-has-no-invoke-method-so-an-expression-of-this-type-cannot-be-the-target-of-a-method-call"></a><span data-ttu-id="32ec6-102">La classe déléguée '\<classname>' n'a pas de méthode Invoke, c'est pourquoi une expression de ce type ne peut pas être la cible d'un appel de méthode</span><span class="sxs-lookup"><span data-stu-id="32ec6-102">Delegate class '\<classname>' has no Invoke method, so an expression of this type cannot be the target of a method call</span></span>

<span data-ttu-id="32ec6-103">Un appel à `Invoke` via un délégué a échoué, car `Invoke` n’est pas implémenté sur la classe déléguée.</span><span class="sxs-lookup"><span data-stu-id="32ec6-103">A call to `Invoke` through a delegate has failed because `Invoke` is not implemented on the delegate class.</span></span>  
  
 <span data-ttu-id="32ec6-104">**ID d’erreur :** BC30220</span><span class="sxs-lookup"><span data-stu-id="32ec6-104">**Error ID:** BC30220</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="32ec6-105">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="32ec6-105">To correct this error</span></span>  
  
1. <span data-ttu-id="32ec6-106">Assurez-vous qu’une instance de la classe déléguée a été créée avec une `Dim` instruction et qu’une procédure a été assignée à l’instance de délégué avec l' `AddressOf` opérateur.</span><span class="sxs-lookup"><span data-stu-id="32ec6-106">Ensure that an instance of the delegate class has been created with a `Dim` statement and that a procedure has been assigned to the delegate instance with the `AddressOf` operator.</span></span>  
  
2. <span data-ttu-id="32ec6-107">Recherchez le code qui implémente la classe déléguée et assurez-vous qu’il implémente la `Invoke` procédure.</span><span class="sxs-lookup"><span data-stu-id="32ec6-107">Locate the code that implements the delegate class and make sure it implements the `Invoke` procedure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32ec6-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="32ec6-108">See also</span></span>

- [<span data-ttu-id="32ec6-109">Délégués</span><span class="sxs-lookup"><span data-stu-id="32ec6-109">Delegates</span></span>](../../programming-guide/language-features/delegates/index.md)
- [<span data-ttu-id="32ec6-110">Delegate, instruction</span><span class="sxs-lookup"><span data-stu-id="32ec6-110">Delegate Statement</span></span>](../statements/delegate-statement.md)
- [<span data-ttu-id="32ec6-111">AddressOf, opérateur</span><span class="sxs-lookup"><span data-stu-id="32ec6-111">AddressOf Operator</span></span>](../operators/addressof-operator.md)
- [<span data-ttu-id="32ec6-112">Dim (instruction)</span><span class="sxs-lookup"><span data-stu-id="32ec6-112">Dim Statement</span></span>](../statements/dim-statement.md)
