---
title: And, opérateur (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.And
helpviewer_keywords:
- operators [Visual Basic], bitwise
- logical conjunction
- bitwise AND operator [Visual Basic]
- conjunction operator [Visual Basic]
- And operator [Visual Basic]
- bitwise operators [Visual Basic], AND operator
- operators [Visual Basic], conjunction
- bitwise comparison [Visual Basic]
ms.assetid: 2ea711f3-439a-4c7c-9e3a-1ffe3b0d6046
ms.openlocfilehash: a1802d3a7018b1b6190ff5601eba055e16e62371
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913167"
---
# <a name="and-operator-visual-basic"></a><span data-ttu-id="60e43-102">And, opérateur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="60e43-102">And Operator (Visual Basic)</span></span>
<span data-ttu-id="60e43-103">Effectue une conjonction logique sur `Boolean` deux expressions ou une conjonction au niveau du bit sur deux expressions numériques.</span><span class="sxs-lookup"><span data-stu-id="60e43-103">Performs a logical conjunction on two `Boolean` expressions, or a bitwise conjunction on two numeric expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60e43-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="60e43-104">Syntax</span></span>  
  
```  
result = expression1 And expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="60e43-105">Composants</span><span class="sxs-lookup"><span data-stu-id="60e43-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="60e43-106">Requis.</span><span class="sxs-lookup"><span data-stu-id="60e43-106">Required.</span></span> <span data-ttu-id="60e43-107">Toute `Boolean` expression ou numérique.</span><span class="sxs-lookup"><span data-stu-id="60e43-107">Any `Boolean` or numeric expression.</span></span> <span data-ttu-id="60e43-108">Pour la comparaison booléenne `result` , est la conjonction logique `Boolean` de deux valeurs.</span><span class="sxs-lookup"><span data-stu-id="60e43-108">For Boolean comparison, `result` is the logical conjunction of two `Boolean` values.</span></span> <span data-ttu-id="60e43-109">Pour les opérations au `result` niveau du bit, est une valeur numérique représentant la conjonction au niveau du bit de deux modèles binaires numériques.</span><span class="sxs-lookup"><span data-stu-id="60e43-109">For bitwise operations, `result` is a numeric value representing the bitwise conjunction of two numeric bit patterns.</span></span>  
  
 `expression1`  
 <span data-ttu-id="60e43-110">Requis.</span><span class="sxs-lookup"><span data-stu-id="60e43-110">Required.</span></span> <span data-ttu-id="60e43-111">Toute `Boolean` expression ou numérique.</span><span class="sxs-lookup"><span data-stu-id="60e43-111">Any `Boolean` or numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="60e43-112">Requis.</span><span class="sxs-lookup"><span data-stu-id="60e43-112">Required.</span></span> <span data-ttu-id="60e43-113">Toute `Boolean` expression ou numérique.</span><span class="sxs-lookup"><span data-stu-id="60e43-113">Any `Boolean` or numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="60e43-114">Notes</span><span class="sxs-lookup"><span data-stu-id="60e43-114">Remarks</span></span>  
 <span data-ttu-id="60e43-115">Pour la comparaison booléenne `result` , `True` est `expression1` si et seulement `True`si et `expression2` ont la valeur.</span><span class="sxs-lookup"><span data-stu-id="60e43-115">For Boolean comparison, `result` is `True` if and only if both `expression1` and `expression2` evaluate to `True`.</span></span> <span data-ttu-id="60e43-116">Le tableau suivant illustre la façon `result` dont est déterminé.</span><span class="sxs-lookup"><span data-stu-id="60e43-116">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="60e43-117">Si `expression1` est</span><span class="sxs-lookup"><span data-stu-id="60e43-117">If `expression1` is</span></span>|<span data-ttu-id="60e43-118">Et `expression2` est</span><span class="sxs-lookup"><span data-stu-id="60e43-118">And `expression2` is</span></span>|<span data-ttu-id="60e43-119">La valeur de `result` est</span><span class="sxs-lookup"><span data-stu-id="60e43-119">The value of `result` is</span></span>|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|`True`|`False`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
> <span data-ttu-id="60e43-120">Dans une comparaison booléenne, l' `And` opérateur évalue toujours les deux expressions, ce qui peut inclure des appels de procédure.</span><span class="sxs-lookup"><span data-stu-id="60e43-120">In a Boolean comparison, the `And` operator always evaluates both expressions, which could include making procedure calls.</span></span> <span data-ttu-id="60e43-121">L' [opérateur AndAlso](../../../visual-basic/language-reference/operators/andalso-operator.md) effectue *un court-circuit*, ce qui signifie que `expression1` si `False`est, `expression2` n’est pas évalué.</span><span class="sxs-lookup"><span data-stu-id="60e43-121">The [AndAlso Operator](../../../visual-basic/language-reference/operators/andalso-operator.md) performs *short-circuiting*, which means that if `expression1` is `False`, then `expression2` is not evaluated.</span></span>  
  
 <span data-ttu-id="60e43-122">Lorsqu’il est appliqué à des valeurs `And` numériques, l’opérateur effectue une comparaison au niveau du bit des bits positionnés de manière identique dans deux `result` expressions numériques et définit le bit correspondant dans selon le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="60e43-122">When applied to numeric values, the `And` operator performs a bitwise comparison of identically positioned bits in two numeric expressions and sets the corresponding bit in `result` according to the following table.</span></span>  
  
|<span data-ttu-id="60e43-123">Si le bit `expression1` dans est</span><span class="sxs-lookup"><span data-stu-id="60e43-123">If bit in `expression1` is</span></span>|<span data-ttu-id="60e43-124">Et le bit `expression2` dans est</span><span class="sxs-lookup"><span data-stu-id="60e43-124">And bit in `expression2` is</span></span>|<span data-ttu-id="60e43-125">Le bit dans `result` est</span><span class="sxs-lookup"><span data-stu-id="60e43-125">The bit in `result` is</span></span>|  
|--------------------------------|---------------------------------|----------------------------|  
|<span data-ttu-id="60e43-126">1</span><span class="sxs-lookup"><span data-stu-id="60e43-126">1</span></span>|<span data-ttu-id="60e43-127">1</span><span class="sxs-lookup"><span data-stu-id="60e43-127">1</span></span>|<span data-ttu-id="60e43-128">1</span><span class="sxs-lookup"><span data-stu-id="60e43-128">1</span></span>|  
|<span data-ttu-id="60e43-129">1</span><span class="sxs-lookup"><span data-stu-id="60e43-129">1</span></span>|<span data-ttu-id="60e43-130">0</span><span class="sxs-lookup"><span data-stu-id="60e43-130">0</span></span>|<span data-ttu-id="60e43-131">0</span><span class="sxs-lookup"><span data-stu-id="60e43-131">0</span></span>|  
|<span data-ttu-id="60e43-132">0</span><span class="sxs-lookup"><span data-stu-id="60e43-132">0</span></span>|<span data-ttu-id="60e43-133">1</span><span class="sxs-lookup"><span data-stu-id="60e43-133">1</span></span>|<span data-ttu-id="60e43-134">0</span><span class="sxs-lookup"><span data-stu-id="60e43-134">0</span></span>|  
|<span data-ttu-id="60e43-135">0</span><span class="sxs-lookup"><span data-stu-id="60e43-135">0</span></span>|<span data-ttu-id="60e43-136">0</span><span class="sxs-lookup"><span data-stu-id="60e43-136">0</span></span>|<span data-ttu-id="60e43-137">0</span><span class="sxs-lookup"><span data-stu-id="60e43-137">0</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="60e43-138">Étant donné que les opérateurs logiques et au niveau du bit ont une priorité inférieure à celle des autres opérateurs arithmétiques et relationnels, toutes les opérations au niveau du bit doivent être mises entre parenthèses pour garantir des résultats précis.</span><span class="sxs-lookup"><span data-stu-id="60e43-138">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate results.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="60e43-139">Types de données</span><span class="sxs-lookup"><span data-stu-id="60e43-139">Data Types</span></span>  
 <span data-ttu-id="60e43-140">Si `Boolean` les opérandes se composent d’une expression et d’une expression numérique, Visual Basic convertit l’expression en une valeur numérique (– 1 pour `True` et 0 pour `False`) et effectue une opération au niveau du `Boolean` bit.</span><span class="sxs-lookup"><span data-stu-id="60e43-140">If the operands consist of one `Boolean` expression and one numeric expression, Visual Basic converts the `Boolean` expression to a numeric value (–1 for `True` and 0 for `False`) and performs a bitwise operation.</span></span>  
  
 <span data-ttu-id="60e43-141">Pour une comparaison booléenne, le type de données du résultat est `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="60e43-141">For a Boolean comparison, the data type of the result is `Boolean`.</span></span> <span data-ttu-id="60e43-142">Pour une comparaison au niveau du bit, le type de données de résultat est un type numérique approprié `expression1` pour `expression2`les types de données de et.</span><span class="sxs-lookup"><span data-stu-id="60e43-142">For a bitwise comparison, the result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="60e43-143">Consultez la table «comparaisons et comparaisons au niveau du bit» dans [types de données des résultats d’opérateur](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span><span class="sxs-lookup"><span data-stu-id="60e43-143">See the "Relational and Bitwise Comparisons" table in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="60e43-144">L' `And` opérateur peut être *surchargé*, ce qui signifie qu’une classe ou une structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou de cette structure.</span><span class="sxs-lookup"><span data-stu-id="60e43-144">The `And` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="60e43-145">Si votre code utilise cet opérateur sur une classe ou une structure de ce type, veillez à bien comprendre son comportement redéfini.</span><span class="sxs-lookup"><span data-stu-id="60e43-145">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="60e43-146">Pour plus d'informations, consultez [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="60e43-146">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="60e43-147">Exemple</span><span class="sxs-lookup"><span data-stu-id="60e43-147">Example</span></span>  
 <span data-ttu-id="60e43-148">L’exemple suivant utilise l' `And` opérateur pour effectuer une conjonction logique sur deux expressions.</span><span class="sxs-lookup"><span data-stu-id="60e43-148">The following example uses the `And` operator to perform a logical conjunction on two expressions.</span></span> <span data-ttu-id="60e43-149">Le résultat est une `Boolean` valeur qui indique si les deux expressions sont. `True`</span><span class="sxs-lookup"><span data-stu-id="60e43-149">The result is a `Boolean` value that represents whether both of the expressions are `True`.</span></span>  
  
 [!code-vb[VbVbalrOperators#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#22)]  
  
 <span data-ttu-id="60e43-150">L’exemple précédent produit les résultats `True` de `False`et, respectivement.</span><span class="sxs-lookup"><span data-stu-id="60e43-150">The preceding example produces results of `True` and `False`, respectively.</span></span>  
  
## <a name="example"></a><span data-ttu-id="60e43-151">Exemples</span><span class="sxs-lookup"><span data-stu-id="60e43-151">Example</span></span>  
 <span data-ttu-id="60e43-152">L’exemple suivant utilise l' `And` opérateur pour effectuer une conjonction logique sur les bits individuels de deux expressions numériques.</span><span class="sxs-lookup"><span data-stu-id="60e43-152">The following example uses the `And` operator to perform logical conjunction on the individual bits of two numeric expressions.</span></span> <span data-ttu-id="60e43-153">Le bit dans le modèle de résultat est défini si les bits correspondants dans les opérandes ont tous les deux la valeur 1.</span><span class="sxs-lookup"><span data-stu-id="60e43-153">The bit in the result pattern is set if the corresponding bits in the operands are both set to 1.</span></span>  
  
 [!code-vb[VbVbalrOperators#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#23)]  
  
 <span data-ttu-id="60e43-154">L’exemple précédent produit respectivement les résultats 8, 2 et 0.</span><span class="sxs-lookup"><span data-stu-id="60e43-154">The preceding example produces results of 8, 2, and 0, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60e43-155">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="60e43-155">See also</span></span>

- [<span data-ttu-id="60e43-156">Opérateurs logiques/de bits (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="60e43-156">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [<span data-ttu-id="60e43-157">Priorité des opérateurs en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="60e43-157">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="60e43-158">Opérateurs répertoriés par fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="60e43-158">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="60e43-159">AndAlso (opérateur)</span><span class="sxs-lookup"><span data-stu-id="60e43-159">AndAlso Operator</span></span>](../../../visual-basic/language-reference/operators/andalso-operator.md)
- [<span data-ttu-id="60e43-160">Opérateurs logiques et au niveau du bit dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="60e43-160">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
