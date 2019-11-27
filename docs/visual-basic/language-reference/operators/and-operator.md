---
title: And, opérateur
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
ms.openlocfilehash: 78a65843a449bd15d5615710e1685f40d94c37f7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350251"
---
# <a name="and-operator-visual-basic"></a><span data-ttu-id="15064-102">And, opérateur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="15064-102">And Operator (Visual Basic)</span></span>
<span data-ttu-id="15064-103">Effectue une conjonction logique sur deux expressions `Boolean`, ou une conjonction d’opérations de bits sur deux expressions numériques.</span><span class="sxs-lookup"><span data-stu-id="15064-103">Performs a logical conjunction on two `Boolean` expressions, or a bitwise conjunction on two numeric expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15064-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="15064-104">Syntax</span></span>  
  
```vb  
result = expression1 And expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="15064-105">Composants</span><span class="sxs-lookup"><span data-stu-id="15064-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="15064-106">Requis.</span><span class="sxs-lookup"><span data-stu-id="15064-106">Required.</span></span> <span data-ttu-id="15064-107">Toute expression `Boolean` ou numérique.</span><span class="sxs-lookup"><span data-stu-id="15064-107">Any `Boolean` or numeric expression.</span></span> <span data-ttu-id="15064-108">Pour la comparaison booléenne, `result` est la conjonction logique de deux valeurs `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="15064-108">For Boolean comparison, `result` is the logical conjunction of two `Boolean` values.</span></span> <span data-ttu-id="15064-109">Pour les opérations au niveau du bit, `result` est une valeur numérique représentant la conjonction au niveau du bit de deux modèles binaires numériques.</span><span class="sxs-lookup"><span data-stu-id="15064-109">For bitwise operations, `result` is a numeric value representing the bitwise conjunction of two numeric bit patterns.</span></span>  
  
 `expression1`  
 <span data-ttu-id="15064-110">Requis.</span><span class="sxs-lookup"><span data-stu-id="15064-110">Required.</span></span> <span data-ttu-id="15064-111">Toute expression `Boolean` ou numérique.</span><span class="sxs-lookup"><span data-stu-id="15064-111">Any `Boolean` or numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="15064-112">Requis.</span><span class="sxs-lookup"><span data-stu-id="15064-112">Required.</span></span> <span data-ttu-id="15064-113">Toute expression `Boolean` ou numérique.</span><span class="sxs-lookup"><span data-stu-id="15064-113">Any `Boolean` or numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="15064-114">Notes</span><span class="sxs-lookup"><span data-stu-id="15064-114">Remarks</span></span>  
 <span data-ttu-id="15064-115">Pour la comparaison booléenne, `result` est `True` si et uniquement si `expression1` et `expression2` prennent la valeur `True`.</span><span class="sxs-lookup"><span data-stu-id="15064-115">For Boolean comparison, `result` is `True` if and only if both `expression1` and `expression2` evaluate to `True`.</span></span> <span data-ttu-id="15064-116">Le tableau suivant illustre la façon dont `result` est déterminé.</span><span class="sxs-lookup"><span data-stu-id="15064-116">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="15064-117">Si `expression1` est</span><span class="sxs-lookup"><span data-stu-id="15064-117">If `expression1` is</span></span>|<span data-ttu-id="15064-118">Et `expression2` est</span><span class="sxs-lookup"><span data-stu-id="15064-118">And `expression2` is</span></span>|<span data-ttu-id="15064-119">La valeur de `result` est</span><span class="sxs-lookup"><span data-stu-id="15064-119">The value of `result` is</span></span>|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|`True`|`False`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
> <span data-ttu-id="15064-120">Dans une comparaison booléenne, l’opérateur `And` évalue toujours les deux expressions, ce qui peut inclure des appels de procédure.</span><span class="sxs-lookup"><span data-stu-id="15064-120">In a Boolean comparison, the `And` operator always evaluates both expressions, which could include making procedure calls.</span></span> <span data-ttu-id="15064-121">L' [opérateur AndAlso](../../../visual-basic/language-reference/operators/andalso-operator.md) effectue *un court-circuit*, ce qui signifie que si `expression1` est `False`, `expression2` n’est pas évalué.</span><span class="sxs-lookup"><span data-stu-id="15064-121">The [AndAlso Operator](../../../visual-basic/language-reference/operators/andalso-operator.md) performs *short-circuiting*, which means that if `expression1` is `False`, then `expression2` is not evaluated.</span></span>  
  
 <span data-ttu-id="15064-122">Lorsqu’il est appliqué à des valeurs numériques, l’opérateur `And` effectue une comparaison au niveau du bit des bits positionnés de manière identique dans deux expressions numériques et définit le bit correspondant dans `result` selon le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="15064-122">When applied to numeric values, the `And` operator performs a bitwise comparison of identically positioned bits in two numeric expressions and sets the corresponding bit in `result` according to the following table.</span></span>  
  
|<span data-ttu-id="15064-123">Si le bit de `expression1` est</span><span class="sxs-lookup"><span data-stu-id="15064-123">If bit in `expression1` is</span></span>|<span data-ttu-id="15064-124">Et le bit de `expression2` est</span><span class="sxs-lookup"><span data-stu-id="15064-124">And bit in `expression2` is</span></span>|<span data-ttu-id="15064-125">Le bit de `result` est</span><span class="sxs-lookup"><span data-stu-id="15064-125">The bit in `result` is</span></span>|  
|--------------------------------|---------------------------------|----------------------------|  
|<span data-ttu-id="15064-126">1</span><span class="sxs-lookup"><span data-stu-id="15064-126">1</span></span>|<span data-ttu-id="15064-127">1</span><span class="sxs-lookup"><span data-stu-id="15064-127">1</span></span>|<span data-ttu-id="15064-128">1</span><span class="sxs-lookup"><span data-stu-id="15064-128">1</span></span>|  
|<span data-ttu-id="15064-129">1</span><span class="sxs-lookup"><span data-stu-id="15064-129">1</span></span>|<span data-ttu-id="15064-130">0</span><span class="sxs-lookup"><span data-stu-id="15064-130">0</span></span>|<span data-ttu-id="15064-131">0</span><span class="sxs-lookup"><span data-stu-id="15064-131">0</span></span>|  
|<span data-ttu-id="15064-132">0</span><span class="sxs-lookup"><span data-stu-id="15064-132">0</span></span>|<span data-ttu-id="15064-133">1</span><span class="sxs-lookup"><span data-stu-id="15064-133">1</span></span>|<span data-ttu-id="15064-134">0</span><span class="sxs-lookup"><span data-stu-id="15064-134">0</span></span>|  
|<span data-ttu-id="15064-135">0</span><span class="sxs-lookup"><span data-stu-id="15064-135">0</span></span>|<span data-ttu-id="15064-136">0</span><span class="sxs-lookup"><span data-stu-id="15064-136">0</span></span>|<span data-ttu-id="15064-137">0</span><span class="sxs-lookup"><span data-stu-id="15064-137">0</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="15064-138">Étant donné que les opérateurs logiques et au niveau du bit ont une priorité inférieure à celle des autres opérateurs arithmétiques et relationnels, toutes les opérations au niveau du bit doivent être mises entre parenthèses pour garantir des résultats précis.</span><span class="sxs-lookup"><span data-stu-id="15064-138">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate results.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="15064-139">Types de données</span><span class="sxs-lookup"><span data-stu-id="15064-139">Data Types</span></span>  
 <span data-ttu-id="15064-140">Si les opérandes se composent d’une expression `Boolean` et d’une expression numérique, Visual Basic convertit l’expression `Boolean` en valeur numérique (– 1 pour `True` et 0 pour `False`) et effectue une opération au niveau du bit.</span><span class="sxs-lookup"><span data-stu-id="15064-140">If the operands consist of one `Boolean` expression and one numeric expression, Visual Basic converts the `Boolean` expression to a numeric value (–1 for `True` and 0 for `False`) and performs a bitwise operation.</span></span>  
  
 <span data-ttu-id="15064-141">Pour une comparaison booléenne, le type de données du résultat est `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="15064-141">For a Boolean comparison, the data type of the result is `Boolean`.</span></span> <span data-ttu-id="15064-142">Pour une comparaison au niveau du bit, le type de données de résultat est un type numérique approprié pour les types de données de `expression1` et `expression2`.</span><span class="sxs-lookup"><span data-stu-id="15064-142">For a bitwise comparison, the result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="15064-143">Consultez la table « comparaisons et comparaisons au niveau du bit » dans [types de données des résultats d’opérateur](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span><span class="sxs-lookup"><span data-stu-id="15064-143">See the "Relational and Bitwise Comparisons" table in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="15064-144">L’opérateur `And` peut être *surchargé*, ce qui signifie qu’une classe ou une structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou de cette structure.</span><span class="sxs-lookup"><span data-stu-id="15064-144">The `And` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="15064-145">Si votre code utilise cet opérateur sur une classe ou une structure de ce type, veillez à bien comprendre son comportement redéfini.</span><span class="sxs-lookup"><span data-stu-id="15064-145">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="15064-146">Pour plus d'informations, consultez [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="15064-146">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="15064-147">Exemple</span><span class="sxs-lookup"><span data-stu-id="15064-147">Example</span></span>  
 <span data-ttu-id="15064-148">L’exemple suivant utilise l’opérateur `And` pour effectuer une conjonction logique sur deux expressions.</span><span class="sxs-lookup"><span data-stu-id="15064-148">The following example uses the `And` operator to perform a logical conjunction on two expressions.</span></span> <span data-ttu-id="15064-149">Le résultat est une valeur `Boolean` qui indique si les deux expressions sont `True`.</span><span class="sxs-lookup"><span data-stu-id="15064-149">The result is a `Boolean` value that represents whether both of the expressions are `True`.</span></span>  
  
 [!code-vb[VbVbalrOperators#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#22)]  
  
 <span data-ttu-id="15064-150">L’exemple précédent produit les résultats de `True` et `False`, respectivement.</span><span class="sxs-lookup"><span data-stu-id="15064-150">The preceding example produces results of `True` and `False`, respectively.</span></span>  
  
## <a name="example"></a><span data-ttu-id="15064-151">Exemple</span><span class="sxs-lookup"><span data-stu-id="15064-151">Example</span></span>  
 <span data-ttu-id="15064-152">L’exemple suivant utilise l’opérateur `And` pour effectuer une conjonction logique sur les bits individuels de deux expressions numériques.</span><span class="sxs-lookup"><span data-stu-id="15064-152">The following example uses the `And` operator to perform logical conjunction on the individual bits of two numeric expressions.</span></span> <span data-ttu-id="15064-153">Le bit dans le modèle de résultat est défini si les bits correspondants dans les opérandes ont tous les deux la valeur 1.</span><span class="sxs-lookup"><span data-stu-id="15064-153">The bit in the result pattern is set if the corresponding bits in the operands are both set to 1.</span></span>  
  
 [!code-vb[VbVbalrOperators#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#23)]  
  
 <span data-ttu-id="15064-154">L’exemple précédent produit respectivement les résultats 8, 2 et 0.</span><span class="sxs-lookup"><span data-stu-id="15064-154">The preceding example produces results of 8, 2, and 0, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15064-155">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="15064-155">See also</span></span>

- [<span data-ttu-id="15064-156">Opérateurs logiques/de bits (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="15064-156">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [<span data-ttu-id="15064-157">Priorité des opérateurs en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="15064-157">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="15064-158">Opérateurs répertoriés par fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="15064-158">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="15064-159">AndAlso (opérateur)</span><span class="sxs-lookup"><span data-stu-id="15064-159">AndAlso Operator</span></span>](../../../visual-basic/language-reference/operators/andalso-operator.md)
- [<span data-ttu-id="15064-160">Opérateurs logiques et au niveau du bit dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="15064-160">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
