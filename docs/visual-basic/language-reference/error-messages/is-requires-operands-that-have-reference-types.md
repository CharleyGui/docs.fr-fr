---
title: "'Is' requiert des opérandes ayant des types référence, mais cet opérande a le type valeur '<typename>'"
ms.date: 07/20/2015
f1_keywords:
- bc30020
- vbc30020
helpviewer_keywords:
- BC30020
ms.assetid: 228afebd-1203-4bd3-8d7a-c5c56f3cedc4
ms.openlocfilehash: daf9724fef81b4d7adb4f571ee950723aec09d8d
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873912"
---
# <a name="is-requires-operands-that-have-reference-types-but-this-operand-has-the-value-type-typename"></a><span data-ttu-id="246a9-102">'Is' requiert des opérandes ayant des types référence, mais cet opérande a le type valeur '\<typename>'</span><span class="sxs-lookup"><span data-stu-id="246a9-102">'Is' requires operands that have reference types, but this operand has the value type '\<typename>'</span></span>

<span data-ttu-id="246a9-103">L' `Is` opérateur de comparaison détermine si deux variables objets font référence à la même instance.</span><span class="sxs-lookup"><span data-stu-id="246a9-103">The `Is` comparison operator determines whether two object variables refer to the same instance.</span></span> <span data-ttu-id="246a9-104">Cette comparaison n’est pas définie pour les types valeur.</span><span class="sxs-lookup"><span data-stu-id="246a9-104">This comparison is not defined for value types.</span></span>  
  
 <span data-ttu-id="246a9-105">**ID d’erreur :** BC30020</span><span class="sxs-lookup"><span data-stu-id="246a9-105">**Error ID:** BC30020</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="246a9-106">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="246a9-106">To correct this error</span></span>  
  
- <span data-ttu-id="246a9-107">Utilisez l’opérateur de comparaison arithmétique approprié ou l' `Like` opérateur pour comparer deux types valeur.</span><span class="sxs-lookup"><span data-stu-id="246a9-107">Use the appropriate arithmetic comparison operator or the `Like` operator to compare two value types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="246a9-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="246a9-108">See also</span></span>

- [<span data-ttu-id="246a9-109">Is, opérateur</span><span class="sxs-lookup"><span data-stu-id="246a9-109">Is Operator</span></span>](../operators/is-operator.md)
- [<span data-ttu-id="246a9-110">Like, opérateur</span><span class="sxs-lookup"><span data-stu-id="246a9-110">Like Operator</span></span>](../operators/like-operator.md)
- [<span data-ttu-id="246a9-111">Opérateurs de comparaison</span><span class="sxs-lookup"><span data-stu-id="246a9-111">Comparison Operators</span></span>](../operators/comparison-operators.md)
