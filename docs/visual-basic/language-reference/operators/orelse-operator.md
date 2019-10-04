---
title: Opérateur OrElse (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- OrElse
- vb.OrElse
helpviewer_keywords:
- short-circuiting
- operators [Visual Basic], short-circuiting
- operators [Visual Basic], disjunction
- short-circuit evaluation
- OrElse operator [Visual Basic]
ms.assetid: 253803d8-05b0-47d7-b213-abd222847779
ms.openlocfilehash: 8290e642db3ec76a931bdd2febe427309457bc86
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71835242"
---
# <a name="orelse-operator-visual-basic"></a><span data-ttu-id="4e6eb-102">Opérateur OrElse (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4e6eb-102">OrElse Operator (Visual Basic)</span></span>
<span data-ttu-id="4e6eb-103">Effectue une disjonction logique inclusive de court-circuit sur deux expressions.</span><span class="sxs-lookup"><span data-stu-id="4e6eb-103">Performs short-circuiting inclusive logical disjunction on two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e6eb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4e6eb-104">Syntax</span></span>  
  
```vb
result = expression1 OrElse expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="4e6eb-105">Composants</span><span class="sxs-lookup"><span data-stu-id="4e6eb-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="4e6eb-106">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="4e6eb-106">Required.</span></span> <span data-ttu-id="4e6eb-107">Toute expression `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="4e6eb-107">Any `Boolean` expression.</span></span>  
  
 `expression1`  
 <span data-ttu-id="4e6eb-108">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="4e6eb-108">Required.</span></span> <span data-ttu-id="4e6eb-109">Toute expression `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="4e6eb-109">Any `Boolean` expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="4e6eb-110">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="4e6eb-110">Required.</span></span> <span data-ttu-id="4e6eb-111">Toute expression `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="4e6eb-111">Any `Boolean` expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4e6eb-112">Notes</span><span class="sxs-lookup"><span data-stu-id="4e6eb-112">Remarks</span></span>  
 <span data-ttu-id="4e6eb-113">Une opération logique est dite *court-circuit* si le code compilé peut contourner l’évaluation d’une expression en fonction du résultat d’une autre expression.</span><span class="sxs-lookup"><span data-stu-id="4e6eb-113">A logical operation is said to be *short-circuiting* if the compiled code can bypass the evaluation of one expression depending on the result of another expression.</span></span> <span data-ttu-id="4e6eb-114">Si le résultat de la première expression évaluée détermine le résultat final de l’opération, il n’est pas nécessaire d’évaluer la deuxième expression, car elle ne peut pas modifier le résultat final.</span><span class="sxs-lookup"><span data-stu-id="4e6eb-114">If the result of the first expression evaluated determines the final result of the operation, there is no need to evaluate the second expression, because it cannot change the final result.</span></span> <span data-ttu-id="4e6eb-115">Le court-circuit peut améliorer les performances si l’expression ignorée est complexe ou si elle implique des appels de procédure.</span><span class="sxs-lookup"><span data-stu-id="4e6eb-115">Short-circuiting can improve performance if the bypassed expression is complex, or if it involves procedure calls.</span></span>  
  
 <span data-ttu-id="4e6eb-116">Si l’une ou les deux expressions ont la valeur `True`, `result` est `True`.</span><span class="sxs-lookup"><span data-stu-id="4e6eb-116">If either or both expressions evaluate to `True`, `result` is `True`.</span></span> <span data-ttu-id="4e6eb-117">Le tableau suivant illustre la façon dont `result` est déterminé.</span><span class="sxs-lookup"><span data-stu-id="4e6eb-117">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="4e6eb-118">Si `expression1` est</span><span class="sxs-lookup"><span data-stu-id="4e6eb-118">If `expression1` is</span></span>|<span data-ttu-id="4e6eb-119">Et `expression2` est</span><span class="sxs-lookup"><span data-stu-id="4e6eb-119">And `expression2` is</span></span>|<span data-ttu-id="4e6eb-120">La valeur de `result` est</span><span class="sxs-lookup"><span data-stu-id="4e6eb-120">The value of `result` is</span></span>|  
|-------------------------|--------------------------|------------------------------|  
|`True`|<span data-ttu-id="4e6eb-121">(non évalué)</span><span class="sxs-lookup"><span data-stu-id="4e6eb-121">(not evaluated)</span></span>|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
## <a name="data-types"></a><span data-ttu-id="4e6eb-122">Types de données</span><span class="sxs-lookup"><span data-stu-id="4e6eb-122">Data Types</span></span>  
 <span data-ttu-id="4e6eb-123">L’opérateur `OrElse` est défini uniquement pour le [type de données booléen](../../../visual-basic/language-reference/data-types/boolean-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="4e6eb-123">The `OrElse` operator is defined only for the [Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md).</span></span> <span data-ttu-id="4e6eb-124">Visual Basic convertit chaque opérande si nécessaire pour `Boolean` avant d’évaluer l’expression.</span><span class="sxs-lookup"><span data-stu-id="4e6eb-124">Visual Basic converts each operand as necessary to `Boolean` before evaluating the expression.</span></span> <span data-ttu-id="4e6eb-125">Si vous assignez le résultat à un type numérique, Visual Basic le convertit de `Boolean` en ce type de sorte que `False` devient `0` et `True` devient `-1`.</span><span class="sxs-lookup"><span data-stu-id="4e6eb-125">If you assign the result to a numeric type, Visual Basic converts it from `Boolean` to that type such that `False` becomes `0` and `True` becomes `-1`.</span></span>
<span data-ttu-id="4e6eb-126">Pour plus d’informations, consultez [conversions de types booléens](../data-types/boolean-data-type.md#type-conversions).</span><span class="sxs-lookup"><span data-stu-id="4e6eb-126">For more information, see [Boolean Type Conversions](../data-types/boolean-data-type.md#type-conversions).</span></span>
  
## <a name="overloading"></a><span data-ttu-id="4e6eb-127">Surcharge</span><span class="sxs-lookup"><span data-stu-id="4e6eb-127">Overloading</span></span>  
 <span data-ttu-id="4e6eb-128">L' [opérateur or](../../../visual-basic/language-reference/operators/or-operator.md) et l' [opérateur IsTrue](../../../visual-basic/language-reference/operators/istrue-operator.md) peuvent être *surchargés*, ce qui signifie qu’une classe ou une structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou structure.</span><span class="sxs-lookup"><span data-stu-id="4e6eb-128">The [Or Operator](../../../visual-basic/language-reference/operators/or-operator.md) and the [IsTrue Operator](../../../visual-basic/language-reference/operators/istrue-operator.md) can be *overloaded*, which means that a class or structure can redefine their behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="4e6eb-129">La surcharge des opérateurs `Or` et `IsTrue` affecte le comportement de l’opérateur `OrElse`.</span><span class="sxs-lookup"><span data-stu-id="4e6eb-129">Overloading the `Or` and `IsTrue` operators affects the behavior of the `OrElse` operator.</span></span> <span data-ttu-id="4e6eb-130">Si votre code utilise `OrElse` sur une classe ou une structure qui surcharge `Or` et `IsTrue`, assurez-vous que vous comprenez le comportement redéfini.</span><span class="sxs-lookup"><span data-stu-id="4e6eb-130">If your code uses `OrElse` on a class or structure that overloads `Or` and `IsTrue`, be sure you understand their redefined behavior.</span></span> <span data-ttu-id="4e6eb-131">Pour plus d'informations, consultez [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="4e6eb-131">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4e6eb-132">Exemple</span><span class="sxs-lookup"><span data-stu-id="4e6eb-132">Example</span></span>  
 <span data-ttu-id="4e6eb-133">L’exemple suivant utilise l’opérateur `OrElse` pour effectuer une disjonction logique sur deux expressions.</span><span class="sxs-lookup"><span data-stu-id="4e6eb-133">The following example uses the `OrElse` operator to perform logical disjunction on two expressions.</span></span> <span data-ttu-id="4e6eb-134">Le résultat est une valeur `Boolean` qui indique si l’une ou l’autre des deux expressions a la valeur true.</span><span class="sxs-lookup"><span data-stu-id="4e6eb-134">The result is a `Boolean` value that represents whether either of the two expressions is true.</span></span> <span data-ttu-id="4e6eb-135">Si la première expression est `True`, la seconde n’est pas évaluée.</span><span class="sxs-lookup"><span data-stu-id="4e6eb-135">If the first expression is `True`, the second is not evaluated.</span></span>  
  
 [!code-vb[VbVbalrOperators#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#37)]  
  
 <span data-ttu-id="4e6eb-136">L’exemple précédent produit les résultats de `True`, `True` et `False`, respectivement.</span><span class="sxs-lookup"><span data-stu-id="4e6eb-136">The preceding example produces results of `True`, `True`, and `False` respectively.</span></span> <span data-ttu-id="4e6eb-137">Dans le calcul de `firstCheck`, la deuxième expression n’est pas évaluée, car la première est déjà `True`.</span><span class="sxs-lookup"><span data-stu-id="4e6eb-137">In the calculation of `firstCheck`, the second expression is not evaluated because the first is already `True`.</span></span> <span data-ttu-id="4e6eb-138">Toutefois, la deuxième expression est évaluée dans le calcul de `secondCheck`.</span><span class="sxs-lookup"><span data-stu-id="4e6eb-138">However, the second expression is evaluated in the calculation of `secondCheck`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4e6eb-139">Exemple</span><span class="sxs-lookup"><span data-stu-id="4e6eb-139">Example</span></span>  
 <span data-ttu-id="4e6eb-140">L’exemple suivant montre une instruction `If`... `Then` contenant deux appels de procédure.</span><span class="sxs-lookup"><span data-stu-id="4e6eb-140">The following example shows an `If`...`Then` statement containing two procedure calls.</span></span> <span data-ttu-id="4e6eb-141">Si le premier appel retourne `True`, la deuxième procédure n’est pas appelée.</span><span class="sxs-lookup"><span data-stu-id="4e6eb-141">If the first call returns `True`, the second procedure is not called.</span></span> <span data-ttu-id="4e6eb-142">Cela peut produire des résultats inattendus si la deuxième procédure exécute des tâches importantes qui doivent toujours être exécutées lorsque cette section du code s’exécute.</span><span class="sxs-lookup"><span data-stu-id="4e6eb-142">This could produce unexpected results if the second procedure performs important tasks that should always be performed when this section of the code runs.</span></span>  
  
 [!code-vb[VbVbalrOperators#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#38)]  
  
## <a name="see-also"></a><span data-ttu-id="4e6eb-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4e6eb-143">See also</span></span>

- [<span data-ttu-id="4e6eb-144">Opérateurs logiques/de bits (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4e6eb-144">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [<span data-ttu-id="4e6eb-145">Priorité des opérateurs en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4e6eb-145">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="4e6eb-146">Opérateurs répertoriés par fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="4e6eb-146">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="4e6eb-147">Or (opérateur)</span><span class="sxs-lookup"><span data-stu-id="4e6eb-147">Or Operator</span></span>](../../../visual-basic/language-reference/operators/or-operator.md)
- [<span data-ttu-id="4e6eb-148">IsTrue (opérateur)</span><span class="sxs-lookup"><span data-stu-id="4e6eb-148">IsTrue Operator</span></span>](../../../visual-basic/language-reference/operators/istrue-operator.md)
- [<span data-ttu-id="4e6eb-149">Opérateurs logiques et au niveau du bit dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4e6eb-149">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
