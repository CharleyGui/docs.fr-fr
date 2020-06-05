---
title: OrElse, opérateur
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
ms.openlocfilehash: 3095a11523eeb8ec531c7f312fca74d2a070c92f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401405"
---
# <a name="orelse-operator-visual-basic"></a><span data-ttu-id="3c768-102">Opérateur OrElse (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3c768-102">OrElse Operator (Visual Basic)</span></span>
<span data-ttu-id="3c768-103">Effectue une disjonction logique inclusive de court-circuit sur deux expressions.</span><span class="sxs-lookup"><span data-stu-id="3c768-103">Performs short-circuiting inclusive logical disjunction on two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c768-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3c768-104">Syntax</span></span>  
  
```vb
result = expression1 OrElse expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="3c768-105">Éléments</span><span class="sxs-lookup"><span data-stu-id="3c768-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="3c768-106">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="3c768-106">Required.</span></span> <span data-ttu-id="3c768-107">Toute expression `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="3c768-107">Any `Boolean` expression.</span></span>  
  
 `expression1`  
 <span data-ttu-id="3c768-108">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="3c768-108">Required.</span></span> <span data-ttu-id="3c768-109">Toute expression `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="3c768-109">Any `Boolean` expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="3c768-110">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="3c768-110">Required.</span></span> <span data-ttu-id="3c768-111">Toute expression `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="3c768-111">Any `Boolean` expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3c768-112">Notes</span><span class="sxs-lookup"><span data-stu-id="3c768-112">Remarks</span></span>  
 <span data-ttu-id="3c768-113">Une opération logique est dite *court-circuit* si le code compilé peut contourner l’évaluation d’une expression en fonction du résultat d’une autre expression.</span><span class="sxs-lookup"><span data-stu-id="3c768-113">A logical operation is said to be *short-circuiting* if the compiled code can bypass the evaluation of one expression depending on the result of another expression.</span></span> <span data-ttu-id="3c768-114">Si le résultat de la première expression évaluée détermine le résultat final de l’opération, il n’est pas nécessaire d’évaluer la deuxième expression, car elle ne peut pas modifier le résultat final.</span><span class="sxs-lookup"><span data-stu-id="3c768-114">If the result of the first expression evaluated determines the final result of the operation, there is no need to evaluate the second expression, because it cannot change the final result.</span></span> <span data-ttu-id="3c768-115">Le court-circuit peut améliorer les performances si l’expression ignorée est complexe ou si elle implique des appels de procédure.</span><span class="sxs-lookup"><span data-stu-id="3c768-115">Short-circuiting can improve performance if the bypassed expression is complex, or if it involves procedure calls.</span></span>  
  
 <span data-ttu-id="3c768-116">Si l’une ou l’autre ou les deux expressions ont la valeur `True` , `result` est `True` .</span><span class="sxs-lookup"><span data-stu-id="3c768-116">If either or both expressions evaluate to `True`, `result` is `True`.</span></span> <span data-ttu-id="3c768-117">Le tableau suivant illustre la façon dont `result` est déterminé.</span><span class="sxs-lookup"><span data-stu-id="3c768-117">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="3c768-118">Si `expression1` est </span><span class="sxs-lookup"><span data-stu-id="3c768-118">If `expression1` is</span></span>|<span data-ttu-id="3c768-119">Et `expression2` est</span><span class="sxs-lookup"><span data-stu-id="3c768-119">And `expression2` is</span></span>|<span data-ttu-id="3c768-120">La valeur de `result` est</span><span class="sxs-lookup"><span data-stu-id="3c768-120">The value of `result` is</span></span>|  
|-------------------------|--------------------------|------------------------------|  
|`True`|<span data-ttu-id="3c768-121">(non évalué)</span><span class="sxs-lookup"><span data-stu-id="3c768-121">(not evaluated)</span></span>|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
## <a name="data-types"></a><span data-ttu-id="3c768-122">Types de données</span><span class="sxs-lookup"><span data-stu-id="3c768-122">Data Types</span></span>  
 <span data-ttu-id="3c768-123">L' `OrElse` opérateur est défini uniquement pour le [type de données booléen](../data-types/boolean-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="3c768-123">The `OrElse` operator is defined only for the [Boolean Data Type](../data-types/boolean-data-type.md).</span></span> <span data-ttu-id="3c768-124">Visual Basic convertit chaque opérande si nécessaire en `Boolean` avant d’évaluer l’expression.</span><span class="sxs-lookup"><span data-stu-id="3c768-124">Visual Basic converts each operand as necessary to `Boolean` before evaluating the expression.</span></span> <span data-ttu-id="3c768-125">Si vous assignez le résultat à un type numérique, Visual Basic le convertit de `Boolean` en ce type qui `False` devient `0` et `True` devient `-1` .</span><span class="sxs-lookup"><span data-stu-id="3c768-125">If you assign the result to a numeric type, Visual Basic converts it from `Boolean` to that type such that `False` becomes `0` and `True` becomes `-1`.</span></span>
<span data-ttu-id="3c768-126">Pour plus d’informations, consultez [conversions de types booléens](../data-types/boolean-data-type.md#type-conversions).</span><span class="sxs-lookup"><span data-stu-id="3c768-126">For more information, see [Boolean Type Conversions](../data-types/boolean-data-type.md#type-conversions).</span></span>
  
## <a name="overloading"></a><span data-ttu-id="3c768-127">Surcharge</span><span class="sxs-lookup"><span data-stu-id="3c768-127">Overloading</span></span>  
 <span data-ttu-id="3c768-128">L' [opérateur or](or-operator.md) et l' [opérateur IsTrue](istrue-operator.md) peuvent être *surchargés*, ce qui signifie qu’une classe ou une structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou structure.</span><span class="sxs-lookup"><span data-stu-id="3c768-128">The [Or Operator](or-operator.md) and the [IsTrue Operator](istrue-operator.md) can be *overloaded*, which means that a class or structure can redefine their behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="3c768-129">La surcharge `Or` `IsTrue` des opérateurs et affecte le comportement de l' `OrElse` opérateur.</span><span class="sxs-lookup"><span data-stu-id="3c768-129">Overloading the `Or` and `IsTrue` operators affects the behavior of the `OrElse` operator.</span></span> <span data-ttu-id="3c768-130">Si votre code utilise `OrElse` sur une classe ou une structure qui surcharge `Or` et `IsTrue` , veillez à bien comprendre son comportement redéfini.</span><span class="sxs-lookup"><span data-stu-id="3c768-130">If your code uses `OrElse` on a class or structure that overloads `Or` and `IsTrue`, be sure you understand their redefined behavior.</span></span> <span data-ttu-id="3c768-131">Pour plus d'informations, consultez [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="3c768-131">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3c768-132">Exemple</span><span class="sxs-lookup"><span data-stu-id="3c768-132">Example</span></span>  
 <span data-ttu-id="3c768-133">L’exemple suivant utilise l' `OrElse` opérateur pour effectuer une disjonction logique sur deux expressions.</span><span class="sxs-lookup"><span data-stu-id="3c768-133">The following example uses the `OrElse` operator to perform logical disjunction on two expressions.</span></span> <span data-ttu-id="3c768-134">Le résultat est une `Boolean` valeur qui indique si l’une ou l’autre des deux expressions a la valeur true.</span><span class="sxs-lookup"><span data-stu-id="3c768-134">The result is a `Boolean` value that represents whether either of the two expressions is true.</span></span> <span data-ttu-id="3c768-135">Si la première expression est `True` , la seconde n’est pas évaluée.</span><span class="sxs-lookup"><span data-stu-id="3c768-135">If the first expression is `True`, the second is not evaluated.</span></span>  
  
 [!code-vb[VbVbalrOperators#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#37)]  
  
 <span data-ttu-id="3c768-136">L’exemple précédent produit les résultats de `True` , `True` et `False` respectivement.</span><span class="sxs-lookup"><span data-stu-id="3c768-136">The preceding example produces results of `True`, `True`, and `False` respectively.</span></span> <span data-ttu-id="3c768-137">Dans le calcul de `firstCheck` , la deuxième expression n’est pas évaluée, car la première est déjà `True` .</span><span class="sxs-lookup"><span data-stu-id="3c768-137">In the calculation of `firstCheck`, the second expression is not evaluated because the first is already `True`.</span></span> <span data-ttu-id="3c768-138">Toutefois, la deuxième expression est évaluée dans le calcul de `secondCheck` .</span><span class="sxs-lookup"><span data-stu-id="3c768-138">However, the second expression is evaluated in the calculation of `secondCheck`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3c768-139">Exemple</span><span class="sxs-lookup"><span data-stu-id="3c768-139">Example</span></span>  
 <span data-ttu-id="3c768-140">L’exemple suivant montre une `If` instruction... `Then` contenant deux appels de procédure.</span><span class="sxs-lookup"><span data-stu-id="3c768-140">The following example shows an `If`...`Then` statement containing two procedure calls.</span></span> <span data-ttu-id="3c768-141">Si le premier appel retourne `True` , la deuxième procédure n’est pas appelée.</span><span class="sxs-lookup"><span data-stu-id="3c768-141">If the first call returns `True`, the second procedure is not called.</span></span> <span data-ttu-id="3c768-142">Cela peut produire des résultats inattendus si la deuxième procédure exécute des tâches importantes qui doivent toujours être exécutées lorsque cette section du code s’exécute.</span><span class="sxs-lookup"><span data-stu-id="3c768-142">This could produce unexpected results if the second procedure performs important tasks that should always be performed when this section of the code runs.</span></span>  
  
 [!code-vb[VbVbalrOperators#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#38)]  
  
## <a name="see-also"></a><span data-ttu-id="3c768-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3c768-143">See also</span></span>

- [<span data-ttu-id="3c768-144">Opérateurs logiques/de bits (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3c768-144">Logical/Bitwise Operators (Visual Basic)</span></span>](logical-bitwise-operators.md)
- [<span data-ttu-id="3c768-145">Priorité des opérateurs en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3c768-145">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="3c768-146">Opérateurs listés par fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="3c768-146">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="3c768-147">Or, opérateur</span><span class="sxs-lookup"><span data-stu-id="3c768-147">Or Operator</span></span>](or-operator.md)
- [<span data-ttu-id="3c768-148">IsTrue, opérateur</span><span class="sxs-lookup"><span data-stu-id="3c768-148">IsTrue Operator</span></span>](istrue-operator.md)
- [<span data-ttu-id="3c768-149">Opérateurs de bits et opérateurs logiques en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3c768-149">Logical and Bitwise Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
