---
title: 'Comment : déterminer si deux objets sont identiques'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], reference
- Is operator [Visual Basic], comparing objects
- reference variables [Visual Basic]
- variables [Visual Basic], referring to same object
- objects [Visual Basic], variables referring to same
- Visual Basic code, operators
ms.assetid: f760e828-8704-4256-bc2d-c22a4c93b524
ms.openlocfilehash: b215225dbc2d8c0d2bdfe2206e5d4a4f1faa6d0c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403419"
---
# <a name="how-to-test-whether-two-objects-are-the-same-visual-basic"></a><span data-ttu-id="eaa2e-102">Comment : déterminer si deux objets sont identiques (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eaa2e-102">How to: Test Whether Two Objects Are the Same (Visual Basic)</span></span>
<span data-ttu-id="eaa2e-103">Si vous avez deux variables qui font référence à des objets, vous pouvez utiliser `Is` l' `IsNot` opérateur ou, ou les deux, pour déterminer s’ils font référence à la même instance.</span><span class="sxs-lookup"><span data-stu-id="eaa2e-103">If you have two variables that refer to objects, you can use either the `Is` or `IsNot` operator, or both, to determine whether they refer to the same instance.</span></span>  
  
### <a name="to-test-whether-two-objects-are-the-same"></a><span data-ttu-id="eaa2e-104">Pour tester si deux objets sont identiques</span><span class="sxs-lookup"><span data-stu-id="eaa2e-104">To test whether two objects are the same</span></span>  
  
- <span data-ttu-id="eaa2e-105">Utilisez l' [opérateur is](../../../language-reference/operators/is-operator.md) ou l' [opérateur IsNot](../../../language-reference/operators/isnot-operator.md) avec les deux variables comme opérandes.</span><span class="sxs-lookup"><span data-stu-id="eaa2e-105">Use the [Is Operator](../../../language-reference/operators/is-operator.md) or the [IsNot Operator](../../../language-reference/operators/isnot-operator.md) with the two variables as operands.</span></span>  
  
     [!code-vb[VbVbalrOperators#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#69)]  
  
 <span data-ttu-id="eaa2e-106">Vous souhaiterez peut-être effectuer une certaine action selon que deux objets font référence à la même instance.</span><span class="sxs-lookup"><span data-stu-id="eaa2e-106">You might want to take a certain action depending on whether two objects refer to the same instance.</span></span> <span data-ttu-id="eaa2e-107">L’exemple précédent compare `c` le contrôle par rapport au contrôle actif sur le formulaire `f` .</span><span class="sxs-lookup"><span data-stu-id="eaa2e-107">The preceding example compares control `c` against the active control on form `f`.</span></span> <span data-ttu-id="eaa2e-108">S’il n’y a aucun contrôle actif, ou s’il en existe un mais qu’il ne s’agit pas de la même instance de contrôle que `c` , l' `If` instruction échoue et la procédure est retournée sans traitement supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="eaa2e-108">If there is no active control, or if there is one but it is not the same control instance as `c`, then the `If` statement fails and the procedure returns without further processing.</span></span>  
  
 <span data-ttu-id="eaa2e-109">Que vous utilisiez ou que vous soyez `Is` `IsNot` une question de commodité personnelle.</span><span class="sxs-lookup"><span data-stu-id="eaa2e-109">Whether you use `Is` or `IsNot` is a matter of personal convenience to you.</span></span> <span data-ttu-id="eaa2e-110">Il peut être plus facile à lire que l’autre dans une expression donnée.</span><span class="sxs-lookup"><span data-stu-id="eaa2e-110">One might be easier to read than the other in a given expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eaa2e-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eaa2e-111">See also</span></span>

- [<span data-ttu-id="eaa2e-112">Comparison Operators in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="eaa2e-112">Comparison Operators in Visual Basic</span></span>](comparison-operators.md)
