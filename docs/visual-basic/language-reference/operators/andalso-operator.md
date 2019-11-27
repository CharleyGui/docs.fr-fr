---
title: AndAlso, opérateur
ms.date: 07/20/2015
f1_keywords:
- vb.AndAlso
- AndAlso
helpviewer_keywords:
- short-circuiting
- AndAlso operator [Visual Basic]
- operators [Visual Basic], short-circuiting
- operators [Visual Basic], conjunction
- short-circuit evaluation
ms.assetid: bbc15191-b374-495b-9b8f-7b8c2f4388eb
ms.openlocfilehash: b3801c7e05142e1bc793e3c9d49a6f6991756f9d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350237"
---
# <a name="andalso-operator-visual-basic"></a><span data-ttu-id="dc4e1-102">Opérateur AndAlso (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dc4e1-102">AndAlso Operator (Visual Basic)</span></span>
<span data-ttu-id="dc4e1-103">Effectue une conjonction logique de court-circuit sur deux expressions.</span><span class="sxs-lookup"><span data-stu-id="dc4e1-103">Performs short-circuiting logical conjunction on two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc4e1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dc4e1-104">Syntax</span></span>  
  
```vb
result = expression1 AndAlso expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="dc4e1-105">Composants</span><span class="sxs-lookup"><span data-stu-id="dc4e1-105">Parts</span></span>  
  
|<span data-ttu-id="dc4e1-106">Terme</span><span class="sxs-lookup"><span data-stu-id="dc4e1-106">Term</span></span>|<span data-ttu-id="dc4e1-107">Définition</span><span class="sxs-lookup"><span data-stu-id="dc4e1-107">Definition</span></span>|  
|---|---|  
|`result`|<span data-ttu-id="dc4e1-108">Requis.</span><span class="sxs-lookup"><span data-stu-id="dc4e1-108">Required.</span></span> <span data-ttu-id="dc4e1-109">Toute expression `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="dc4e1-109">Any `Boolean` expression.</span></span> <span data-ttu-id="dc4e1-110">Le résultat est le résultat `Boolean` de la comparaison des deux expressions.</span><span class="sxs-lookup"><span data-stu-id="dc4e1-110">The result is the `Boolean` result of comparison of the two expressions.</span></span>|  
|`expression1`|<span data-ttu-id="dc4e1-111">Requis.</span><span class="sxs-lookup"><span data-stu-id="dc4e1-111">Required.</span></span> <span data-ttu-id="dc4e1-112">Toute expression `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="dc4e1-112">Any `Boolean` expression.</span></span>|  
|`expression2`|<span data-ttu-id="dc4e1-113">Requis.</span><span class="sxs-lookup"><span data-stu-id="dc4e1-113">Required.</span></span> <span data-ttu-id="dc4e1-114">Toute expression `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="dc4e1-114">Any `Boolean` expression.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dc4e1-115">Notes</span><span class="sxs-lookup"><span data-stu-id="dc4e1-115">Remarks</span></span>  
 <span data-ttu-id="dc4e1-116">Une opération logique est dite *court-circuit* si le code compilé peut contourner l’évaluation d’une expression en fonction du résultat d’une autre expression.</span><span class="sxs-lookup"><span data-stu-id="dc4e1-116">A logical operation is said to be *short-circuiting* if the compiled code can bypass the evaluation of one expression depending on the result of another expression.</span></span> <span data-ttu-id="dc4e1-117">Si le résultat de la première expression évaluée détermine le résultat final de l’opération, il n’est pas nécessaire d’évaluer la deuxième expression, car elle ne peut pas modifier le résultat final.</span><span class="sxs-lookup"><span data-stu-id="dc4e1-117">If the result of the first expression evaluated determines the final result of the operation, there is no need to evaluate the second expression, because it cannot change the final result.</span></span> <span data-ttu-id="dc4e1-118">Le court-circuit peut améliorer les performances si l’expression ignorée est complexe ou si elle implique des appels de procédure.</span><span class="sxs-lookup"><span data-stu-id="dc4e1-118">Short-circuiting can improve performance if the bypassed expression is complex, or if it involves procedure calls.</span></span>  
  
 <span data-ttu-id="dc4e1-119">Si les deux expressions ont la valeur `True`, `result` est `True`.</span><span class="sxs-lookup"><span data-stu-id="dc4e1-119">If both expressions evaluate to `True`, `result` is `True`.</span></span> <span data-ttu-id="dc4e1-120">Le tableau suivant illustre la façon dont `result` est déterminé.</span><span class="sxs-lookup"><span data-stu-id="dc4e1-120">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="dc4e1-121">Si `expression1` est</span><span class="sxs-lookup"><span data-stu-id="dc4e1-121">If `expression1` is</span></span>|<span data-ttu-id="dc4e1-122">Et `expression2` est</span><span class="sxs-lookup"><span data-stu-id="dc4e1-122">And `expression2` is</span></span>|<span data-ttu-id="dc4e1-123">La valeur de `result` est</span><span class="sxs-lookup"><span data-stu-id="dc4e1-123">The value of `result` is</span></span>|  
|---|---|---|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|<span data-ttu-id="dc4e1-124">(non évalué)</span><span class="sxs-lookup"><span data-stu-id="dc4e1-124">(not evaluated)</span></span>|`False`|  
  
## <a name="data-types"></a><span data-ttu-id="dc4e1-125">Types de données</span><span class="sxs-lookup"><span data-stu-id="dc4e1-125">Data Types</span></span>  
 <span data-ttu-id="dc4e1-126">L’opérateur `AndAlso` est défini uniquement pour le [type de données booléen](../../../visual-basic/language-reference/data-types/boolean-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="dc4e1-126">The `AndAlso` operator is defined only for the [Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md).</span></span> <span data-ttu-id="dc4e1-127">Visual Basic convertit chaque opérande si nécessaire pour `Boolean` avant l’évaluation de l’expression.</span><span class="sxs-lookup"><span data-stu-id="dc4e1-127">Visual Basic converts each operand as necessary to `Boolean` before evaluating the expression.</span></span> <span data-ttu-id="dc4e1-128">Si vous assignez le résultat à un type numérique, Visual Basic le convertit de `Boolean` en ce type de sorte que `False` devienne `0` et `True` devient `-1`.</span><span class="sxs-lookup"><span data-stu-id="dc4e1-128">If you assign the result to a numeric type, Visual Basic converts it from `Boolean` to that type such that `False` becomes `0` and `True` becomes `-1`.</span></span>
<span data-ttu-id="dc4e1-129">Pour plus d’informations, consultez [conversions de types booléens](../data-types/boolean-data-type.md#type-conversions).</span><span class="sxs-lookup"><span data-stu-id="dc4e1-129">For more information, see [Boolean Type Conversions](../data-types/boolean-data-type.md#type-conversions).</span></span>
  
## <a name="overloading"></a><span data-ttu-id="dc4e1-130">Surcharge</span><span class="sxs-lookup"><span data-stu-id="dc4e1-130">Overloading</span></span>  
 <span data-ttu-id="dc4e1-131">L' [opérateur and](../../../visual-basic/language-reference/operators/and-operator.md) et l' [opérateur IsFalse](../../../visual-basic/language-reference/operators/isfalse-operator.md) peuvent être *surchargés*, ce qui signifie qu’une classe ou une structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou structure.</span><span class="sxs-lookup"><span data-stu-id="dc4e1-131">The [And Operator](../../../visual-basic/language-reference/operators/and-operator.md) and the [IsFalse Operator](../../../visual-basic/language-reference/operators/isfalse-operator.md) can be *overloaded*, which means that a class or structure can redefine their behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="dc4e1-132">La surcharge des opérateurs `And` et `IsFalse` affecte le comportement de l’opérateur `AndAlso`.</span><span class="sxs-lookup"><span data-stu-id="dc4e1-132">Overloading the `And` and `IsFalse` operators affects the behavior of the `AndAlso` operator.</span></span> <span data-ttu-id="dc4e1-133">Si votre code utilise `AndAlso` sur une classe ou une structure qui surcharge `And` et `IsFalse`, veillez à bien comprendre leur comportement redéfini.</span><span class="sxs-lookup"><span data-stu-id="dc4e1-133">If your code uses `AndAlso` on a class or structure that overloads `And` and `IsFalse`, be sure you understand their redefined behavior.</span></span> <span data-ttu-id="dc4e1-134">Pour plus d'informations, consultez [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="dc4e1-134">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="dc4e1-135">Exemple</span><span class="sxs-lookup"><span data-stu-id="dc4e1-135">Example</span></span>  
 <span data-ttu-id="dc4e1-136">L’exemple suivant utilise l’opérateur `AndAlso` pour effectuer une conjonction logique sur deux expressions.</span><span class="sxs-lookup"><span data-stu-id="dc4e1-136">The following example uses the `AndAlso` operator to perform a logical conjunction on two expressions.</span></span> <span data-ttu-id="dc4e1-137">Le résultat est une valeur `Boolean` qui indique si l’intégralité de l’expression conjointe a la valeur true.</span><span class="sxs-lookup"><span data-stu-id="dc4e1-137">The result is a `Boolean` value that represents whether the entire conjoined expression is true.</span></span> <span data-ttu-id="dc4e1-138">Si la première expression est `False`, la seconde n’est pas évaluée.</span><span class="sxs-lookup"><span data-stu-id="dc4e1-138">If the first expression is `False`, the second is not evaluated.</span></span>  
  
 [!code-vb[VbVbalrOperators#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#24)]  
  
 <span data-ttu-id="dc4e1-139">L’exemple précédent produit respectivement les résultats de `True`, `False`et `False`.</span><span class="sxs-lookup"><span data-stu-id="dc4e1-139">The preceding example produces results of `True`, `False`, and `False`, respectively.</span></span> <span data-ttu-id="dc4e1-140">Dans le calcul de `secondCheck`, la deuxième expression n’est pas évaluée, car la première est déjà `False`.</span><span class="sxs-lookup"><span data-stu-id="dc4e1-140">In the calculation of `secondCheck`, the second expression is not evaluated because the first is already `False`.</span></span> <span data-ttu-id="dc4e1-141">Toutefois, la deuxième expression est évaluée dans le calcul de `thirdCheck`.</span><span class="sxs-lookup"><span data-stu-id="dc4e1-141">However, the second expression is evaluated in the calculation of `thirdCheck`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dc4e1-142">Exemple</span><span class="sxs-lookup"><span data-stu-id="dc4e1-142">Example</span></span>  
 <span data-ttu-id="dc4e1-143">L’exemple suivant montre une procédure `Function` qui recherche une valeur donnée parmi les éléments d’un tableau.</span><span class="sxs-lookup"><span data-stu-id="dc4e1-143">The following example shows a `Function` procedure that searches for a given value among the elements of an array.</span></span> <span data-ttu-id="dc4e1-144">Si le tableau est vide ou si la longueur du tableau a été dépassée, l’instruction `While` ne teste pas l’élément de tableau par rapport à la valeur de recherche.</span><span class="sxs-lookup"><span data-stu-id="dc4e1-144">If the array is empty, or if the array length has been exceeded, the `While` statement does not test the array element against the search value.</span></span>  
  
 [!code-vb[VbVbalrOperators#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#25)]  
  
## <a name="see-also"></a><span data-ttu-id="dc4e1-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dc4e1-145">See also</span></span>

- [<span data-ttu-id="dc4e1-146">Opérateurs logiques/de bits (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dc4e1-146">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [<span data-ttu-id="dc4e1-147">Priorité des opérateurs en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="dc4e1-147">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="dc4e1-148">Opérateurs répertoriés par fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="dc4e1-148">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="dc4e1-149">And (opérateur)</span><span class="sxs-lookup"><span data-stu-id="dc4e1-149">And Operator</span></span>](../../../visual-basic/language-reference/operators/and-operator.md)
- [<span data-ttu-id="dc4e1-150">IsFalse (opérateur)</span><span class="sxs-lookup"><span data-stu-id="dc4e1-150">IsFalse Operator</span></span>](../../../visual-basic/language-reference/operators/isfalse-operator.md)
- [<span data-ttu-id="dc4e1-151">Opérateurs logiques et au niveau du bit dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="dc4e1-151">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
