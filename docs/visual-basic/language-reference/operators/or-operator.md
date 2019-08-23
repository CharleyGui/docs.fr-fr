---
title: Or, opérateur (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Or
helpviewer_keywords:
- Or operator [Visual Basic]
- operators [Visual Basic], bitwise
- inclusive Or operator [Visual Basic]
- bitwise operators [Visual Basic], OR operator
- Or keyword [Visual Basic]
- operators [Visual Basic], inclusive or
- operators [Visual Basic], disjunction
- bitwise comparison [Visual Basic]
- logical disjunction
- disjunction operator [Visual Basic]
ms.assetid: 41ed6905-bf3d-468a-9e3b-03c10d461891
ms.openlocfilehash: 1d11a6d009f6ecfea9fb1a86b00c67b87d5555dc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955840"
---
# <a name="or-operator-visual-basic"></a><span data-ttu-id="6d6ff-102">Or, opérateur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6d6ff-102">Or Operator (Visual Basic)</span></span>
<span data-ttu-id="6d6ff-103">Effectue une disjonction logique sur deux `Boolean` expressions, ou une disjonction d’opérations de bits sur deux expressions numériques.</span><span class="sxs-lookup"><span data-stu-id="6d6ff-103">Performs a logical disjunction on two `Boolean` expressions, or a bitwise disjunction on two numeric expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d6ff-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6d6ff-104">Syntax</span></span>  
  
```  
result = expression1 Or expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="6d6ff-105">Composants</span><span class="sxs-lookup"><span data-stu-id="6d6ff-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="6d6ff-106">Requis.</span><span class="sxs-lookup"><span data-stu-id="6d6ff-106">Required.</span></span> <span data-ttu-id="6d6ff-107">Toute `Boolean` expression ou numérique.</span><span class="sxs-lookup"><span data-stu-id="6d6ff-107">Any `Boolean` or numeric expression.</span></span> <span data-ttu-id="6d6ff-108">À `Boolean` des fins `result` de comparaison, est la disjonction logique `Boolean` inclusive de deux valeurs.</span><span class="sxs-lookup"><span data-stu-id="6d6ff-108">For `Boolean` comparison, `result` is the inclusive logical disjunction of two `Boolean` values.</span></span> <span data-ttu-id="6d6ff-109">Pour les opérations au `result` niveau du bit, est une valeur numérique représentant la disjonction de bits inclusive de deux modèles binaires numériques.</span><span class="sxs-lookup"><span data-stu-id="6d6ff-109">For bitwise operations, `result` is a numeric value representing the inclusive bitwise disjunction of two numeric bit patterns.</span></span>  
  
 `expression1`  
 <span data-ttu-id="6d6ff-110">Requis.</span><span class="sxs-lookup"><span data-stu-id="6d6ff-110">Required.</span></span> <span data-ttu-id="6d6ff-111">Toute `Boolean` expression ou numérique.</span><span class="sxs-lookup"><span data-stu-id="6d6ff-111">Any `Boolean` or numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="6d6ff-112">Requis.</span><span class="sxs-lookup"><span data-stu-id="6d6ff-112">Required.</span></span> <span data-ttu-id="6d6ff-113">Toute `Boolean` expression ou numérique.</span><span class="sxs-lookup"><span data-stu-id="6d6ff-113">Any `Boolean` or numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6d6ff-114">Notes</span><span class="sxs-lookup"><span data-stu-id="6d6ff-114">Remarks</span></span>  
 <span data-ttu-id="6d6ff-115">À `Boolean` des fins `result` de `False` comparaison, `expression1` est siet`expression2` seulement si et sont tous deux et ont la valeur. `False`</span><span class="sxs-lookup"><span data-stu-id="6d6ff-115">For `Boolean` comparison, `result` is `False` if and only if both `expression1` and `expression2` evaluate to `False`.</span></span> <span data-ttu-id="6d6ff-116">Le tableau suivant illustre la façon `result` dont est déterminé.</span><span class="sxs-lookup"><span data-stu-id="6d6ff-116">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="6d6ff-117">Si `expression1` est</span><span class="sxs-lookup"><span data-stu-id="6d6ff-117">If `expression1` is</span></span>|<span data-ttu-id="6d6ff-118">Et `expression2` est</span><span class="sxs-lookup"><span data-stu-id="6d6ff-118">And `expression2` is</span></span>|<span data-ttu-id="6d6ff-119">La valeur de `result` est</span><span class="sxs-lookup"><span data-stu-id="6d6ff-119">The value of `result` is</span></span>|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
> <span data-ttu-id="6d6ff-120">Dans une `Boolean` comparaison, l' `Or` opérateur évalue toujours les deux expressions, ce qui peut inclure des appels de procédure.</span><span class="sxs-lookup"><span data-stu-id="6d6ff-120">In a `Boolean` comparison, the `Or` operator always evaluates both expressions, which could include making procedure calls.</span></span> <span data-ttu-id="6d6ff-121">L' [opérateur OrElse](../../../visual-basic/language-reference/operators/orelse-operator.md) effectue *un court-circuit*, ce qui signifie que `expression1` si `True`est, `expression2` n’est pas évalué.</span><span class="sxs-lookup"><span data-stu-id="6d6ff-121">The [OrElse Operator](../../../visual-basic/language-reference/operators/orelse-operator.md) performs *short-circuiting*, which means that if `expression1` is `True`, then `expression2` is not evaluated.</span></span>  
  
 <span data-ttu-id="6d6ff-122">Pour les opérations au niveau `Or` du bit, l’opérateur effectue une comparaison au niveau du bit des bits positionnés de manière identique dans `result` deux expressions numériques et définit le bit correspondant dans selon le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="6d6ff-122">For bitwise operations, the `Or` operator performs a bitwise comparison of identically positioned bits in two numeric expressions and sets the corresponding bit in `result` according to the following table.</span></span>  
  
|<span data-ttu-id="6d6ff-123">Si le bit `expression1` dans est</span><span class="sxs-lookup"><span data-stu-id="6d6ff-123">If bit in `expression1` is</span></span>|<span data-ttu-id="6d6ff-124">Et le bit `expression2` dans est</span><span class="sxs-lookup"><span data-stu-id="6d6ff-124">And bit in `expression2` is</span></span>|<span data-ttu-id="6d6ff-125">Le bit dans `result` est</span><span class="sxs-lookup"><span data-stu-id="6d6ff-125">The bit in `result` is</span></span>|  
|--------------------------------|---------------------------------|----------------------------|  
|<span data-ttu-id="6d6ff-126">1</span><span class="sxs-lookup"><span data-stu-id="6d6ff-126">1</span></span>|<span data-ttu-id="6d6ff-127">1</span><span class="sxs-lookup"><span data-stu-id="6d6ff-127">1</span></span>|<span data-ttu-id="6d6ff-128">1</span><span class="sxs-lookup"><span data-stu-id="6d6ff-128">1</span></span>|  
|<span data-ttu-id="6d6ff-129">1</span><span class="sxs-lookup"><span data-stu-id="6d6ff-129">1</span></span>|<span data-ttu-id="6d6ff-130">0</span><span class="sxs-lookup"><span data-stu-id="6d6ff-130">0</span></span>|<span data-ttu-id="6d6ff-131">1</span><span class="sxs-lookup"><span data-stu-id="6d6ff-131">1</span></span>|  
|<span data-ttu-id="6d6ff-132">0</span><span class="sxs-lookup"><span data-stu-id="6d6ff-132">0</span></span>|<span data-ttu-id="6d6ff-133">1</span><span class="sxs-lookup"><span data-stu-id="6d6ff-133">1</span></span>|<span data-ttu-id="6d6ff-134">1</span><span class="sxs-lookup"><span data-stu-id="6d6ff-134">1</span></span>|  
|<span data-ttu-id="6d6ff-135">0</span><span class="sxs-lookup"><span data-stu-id="6d6ff-135">0</span></span>|<span data-ttu-id="6d6ff-136">0</span><span class="sxs-lookup"><span data-stu-id="6d6ff-136">0</span></span>|<span data-ttu-id="6d6ff-137">0</span><span class="sxs-lookup"><span data-stu-id="6d6ff-137">0</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="6d6ff-138">Étant donné que les opérateurs logiques et au niveau du bit ont une priorité inférieure à celle des autres opérateurs arithmétiques et relationnels, toutes les opérations au niveau du bit doivent être mises entre parenthèses pour garantir une exécution précise.</span><span class="sxs-lookup"><span data-stu-id="6d6ff-138">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate execution.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="6d6ff-139">Types de données</span><span class="sxs-lookup"><span data-stu-id="6d6ff-139">Data Types</span></span>  
 <span data-ttu-id="6d6ff-140">Si `Boolean` les opérandes se composent d’une expression et d’une expression numérique, Visual Basic convertit l’expression en une valeur numérique (– 1 pour `True` et 0 pour `False`) et effectue une opération au niveau du `Boolean` bit.</span><span class="sxs-lookup"><span data-stu-id="6d6ff-140">If the operands consist of one `Boolean` expression and one numeric expression, Visual Basic converts the `Boolean` expression to a numeric value (–1 for `True` and 0 for `False`) and performs a bitwise operation.</span></span>  
  
 <span data-ttu-id="6d6ff-141">Pour une `Boolean` comparaison, le type de données du résultat est `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="6d6ff-141">For a `Boolean` comparison, the data type of the result is `Boolean`.</span></span> <span data-ttu-id="6d6ff-142">Pour une comparaison au niveau du bit, le type de données de résultat est un type numérique approprié `expression1` pour `expression2`les types de données de et.</span><span class="sxs-lookup"><span data-stu-id="6d6ff-142">For a bitwise comparison, the result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="6d6ff-143">Consultez la table «comparaisons et comparaisons au niveau du bit» dans [types de données des résultats d’opérateur](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span><span class="sxs-lookup"><span data-stu-id="6d6ff-143">See the "Relational and Bitwise Comparisons" table in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="6d6ff-144">Surcharge</span><span class="sxs-lookup"><span data-stu-id="6d6ff-144">Overloading</span></span>  
 <span data-ttu-id="6d6ff-145">L' `Or` opérateur peut être *surchargé*, ce qui signifie qu’une classe ou une structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou de cette structure.</span><span class="sxs-lookup"><span data-stu-id="6d6ff-145">The `Or` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="6d6ff-146">Si votre code utilise cet opérateur sur une classe ou une structure de ce type, veillez à bien comprendre son comportement redéfini.</span><span class="sxs-lookup"><span data-stu-id="6d6ff-146">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="6d6ff-147">Pour plus d'informations, consultez [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="6d6ff-147">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6d6ff-148">Exemple</span><span class="sxs-lookup"><span data-stu-id="6d6ff-148">Example</span></span>  
 <span data-ttu-id="6d6ff-149">L’exemple suivant utilise l' `Or` opérateur pour effectuer une disjonction logique inclusive sur deux expressions.</span><span class="sxs-lookup"><span data-stu-id="6d6ff-149">The following example uses the `Or` operator to perform an inclusive logical disjunction on two expressions.</span></span> <span data-ttu-id="6d6ff-150">Le résultat est une `Boolean` valeur qui indique si l’une ou l’autre des `True`deux expressions est.</span><span class="sxs-lookup"><span data-stu-id="6d6ff-150">The result is a `Boolean` value that represents whether either of the two expressions is `True`.</span></span>  
  
 [!code-vb[VbVbalrOperators#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#35)]  
  
 <span data-ttu-id="6d6ff-151">L’exemple précédent produit les résultats `True`de `True`, et `False`, respectivement.</span><span class="sxs-lookup"><span data-stu-id="6d6ff-151">The preceding example produces results of `True`, `True`, and `False`, respectively.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6d6ff-152">Exemple</span><span class="sxs-lookup"><span data-stu-id="6d6ff-152">Example</span></span>  
 <span data-ttu-id="6d6ff-153">L’exemple suivant utilise l' `Or` opérateur pour effectuer une disjonction logique inclusive sur les bits individuels de deux expressions numériques.</span><span class="sxs-lookup"><span data-stu-id="6d6ff-153">The following example uses the `Or` operator to perform inclusive logical disjunction on the individual bits of two numeric expressions.</span></span> <span data-ttu-id="6d6ff-154">Le bit dans le modèle de résultat est défini si l’un des bits correspondants dans les opérandes a la valeur 1.</span><span class="sxs-lookup"><span data-stu-id="6d6ff-154">The bit in the result pattern is set if either of the corresponding bits in the operands is set to 1.</span></span>  
  
 [!code-vb[VbVbalrOperators#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#36)]  
  
 <span data-ttu-id="6d6ff-155">L’exemple précédent produit respectivement les résultats 10, 14 et 14.</span><span class="sxs-lookup"><span data-stu-id="6d6ff-155">The preceding example produces results of 10, 14, and 14, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d6ff-156">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6d6ff-156">See also</span></span>

- [<span data-ttu-id="6d6ff-157">Opérateurs logiques/de bits (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6d6ff-157">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [<span data-ttu-id="6d6ff-158">Priorité des opérateurs en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6d6ff-158">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="6d6ff-159">Opérateurs répertoriés par fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="6d6ff-159">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="6d6ff-160">OrElse (opérateur)</span><span class="sxs-lookup"><span data-stu-id="6d6ff-160">OrElse Operator</span></span>](../../../visual-basic/language-reference/operators/orelse-operator.md)
- [<span data-ttu-id="6d6ff-161">Opérateurs logiques et au niveau du bit dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6d6ff-161">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
