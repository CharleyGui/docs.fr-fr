---
title: Opérateurs de bits et opérateurs logiques
ms.date: 07/20/2015
helpviewer_keywords:
- short-circuiting
- Boolean expressions
- logical operators [Visual Basic], Boolean expressions
- operators [Visual Basic], logical
- AndAlso operator [Visual Basic]
- Not operator [Visual Basic], Boolean expressions
- Xor operator [Visual Basic], Boolean expressions
- And operator [Visual Basic], logical operators
- logical operators [Visual Basic]
- expressions [Visual Basic], Boolean
- Or operator [Visual Basic], logical operators
- Visual Basic code, operators
- short-circuiting [Visual Basic], logical operators
- logical operators [Visual Basic], short-circuiting
- Visual Basic code, expressions
- logical operators [Visual Basic], binary
- OrElse operator [Visual Basic]
- logical operators [Visual Basic], unary
ms.assetid: ca474e13-567d-4b1d-a18b-301433705e57
ms.openlocfilehash: c15b9337f262563941699c0ff8fe5219ca6a5c93
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91085995"
---
# <a name="logical-and-bitwise-operators-in-visual-basic"></a><span data-ttu-id="6f441-102">Opérateurs de bits et opérateurs logiques en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6f441-102">Logical and Bitwise Operators in Visual Basic</span></span>

<span data-ttu-id="6f441-103">Les opérateurs logiques comparent `Boolean` les expressions et retournent un `Boolean` résultat.</span><span class="sxs-lookup"><span data-stu-id="6f441-103">Logical operators compare `Boolean` expressions and return a `Boolean` result.</span></span> <span data-ttu-id="6f441-104">Les `And` `Or` opérateurs,,, `AndAlso` `OrElse` et `Xor` sont *binaires* , car ils prennent deux opérandes, tandis que l' `Not` opérateur est *unaire* , car il accepte un seul opérande.</span><span class="sxs-lookup"><span data-stu-id="6f441-104">The `And`, `Or`, `AndAlso`, `OrElse`, and `Xor` operators are *binary* because they take two operands, while the `Not` operator is *unary* because it takes a single operand.</span></span> <span data-ttu-id="6f441-105">Certains de ces opérateurs peuvent également effectuer des opérations logiques au niveau du bit sur des valeurs intégrales.</span><span class="sxs-lookup"><span data-stu-id="6f441-105">Some of these operators can also perform bitwise logical operations on integral values.</span></span>  
  
## <a name="unary-logical-operator"></a><span data-ttu-id="6f441-106">Opérateur logique unaire</span><span class="sxs-lookup"><span data-stu-id="6f441-106">Unary Logical Operator</span></span>  

 <span data-ttu-id="6f441-107">L' [opérateur NOT](../../../language-reference/operators/not-operator.md) effectue une *négation* logique sur une `Boolean` expression.</span><span class="sxs-lookup"><span data-stu-id="6f441-107">The [Not Operator](../../../language-reference/operators/not-operator.md) performs logical *negation* on a `Boolean` expression.</span></span> <span data-ttu-id="6f441-108">Il produit l’opposé logique de son opérande.</span><span class="sxs-lookup"><span data-stu-id="6f441-108">It yields the logical opposite of its operand.</span></span> <span data-ttu-id="6f441-109">Si l’expression prend la valeur `True` , `Not` retourne `False` ; si l’expression prend la valeur `False` , `Not` retourne `True` .</span><span class="sxs-lookup"><span data-stu-id="6f441-109">If the expression evaluates to `True`, then `Not` returns `False`; if the expression evaluates to `False`, then `Not` returns `True`.</span></span> <span data-ttu-id="6f441-110">L'exemple suivant illustre ce comportement.</span><span class="sxs-lookup"><span data-stu-id="6f441-110">The following example illustrates this.</span></span>  
  
 [!code-vb[VbVbalrOperators#77](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#77)]  
  
## <a name="binary-logical-operators"></a><span data-ttu-id="6f441-111">Opérateurs logiques binaires</span><span class="sxs-lookup"><span data-stu-id="6f441-111">Binary Logical Operators</span></span>  

 <span data-ttu-id="6f441-112">L' [opérateur and](../../../language-reference/operators/and-operator.md) effectue une *conjonction* logique sur deux `Boolean` expressions.</span><span class="sxs-lookup"><span data-stu-id="6f441-112">The [And Operator](../../../language-reference/operators/and-operator.md) performs logical *conjunction* on two `Boolean` expressions.</span></span> <span data-ttu-id="6f441-113">Si les deux expressions ont la valeur `True` , `And` retourne `True` .</span><span class="sxs-lookup"><span data-stu-id="6f441-113">If both expressions evaluate to `True`, then `And` returns `True`.</span></span> <span data-ttu-id="6f441-114">Si au moins une des expressions prend la valeur `False` , `And` retourne `False` .</span><span class="sxs-lookup"><span data-stu-id="6f441-114">If at least one of the expressions evaluates to `False`, then `And` returns `False`.</span></span>  
  
 <span data-ttu-id="6f441-115">L' [opérateur or](../../../language-reference/operators/or-operator.md) effectue une *disjonction* ou une *inclusion* logique sur deux `Boolean` expressions.</span><span class="sxs-lookup"><span data-stu-id="6f441-115">The [Or Operator](../../../language-reference/operators/or-operator.md) performs logical *disjunction* or *inclusion* on two `Boolean` expressions.</span></span> <span data-ttu-id="6f441-116">Si l’une des expressions a la valeur `True` , ou si la valeur est égale à `True` , alors `Or` retourne `True` .</span><span class="sxs-lookup"><span data-stu-id="6f441-116">If either expression evaluates to `True`, or both evaluate to `True`, then `Or` returns `True`.</span></span> <span data-ttu-id="6f441-117">Si aucune des expressions n’a la valeur `True` , `Or` retourne `False` .</span><span class="sxs-lookup"><span data-stu-id="6f441-117">If neither expression evaluates to `True`, `Or` returns `False`.</span></span>  
  
 <span data-ttu-id="6f441-118">L' [opérateur XOR](../../../language-reference/operators/xor-operator.md) effectue une *exclusion* logique sur deux `Boolean` expressions.</span><span class="sxs-lookup"><span data-stu-id="6f441-118">The [Xor Operator](../../../language-reference/operators/xor-operator.md) performs logical *exclusion* on two `Boolean` expressions.</span></span> <span data-ttu-id="6f441-119">Si une seule expression prend la valeur `True` , mais pas les deux, `Xor` retourne `True` .</span><span class="sxs-lookup"><span data-stu-id="6f441-119">If exactly one expression evaluates to `True`, but not both, `Xor` returns `True`.</span></span> <span data-ttu-id="6f441-120">Si les deux expressions ont la valeur ou si la `True` valeur est `False` , `Xor` retourne `False` .</span><span class="sxs-lookup"><span data-stu-id="6f441-120">If both expressions evaluate to `True` or both evaluate to `False`, `Xor` returns `False`.</span></span>  
  
 <span data-ttu-id="6f441-121">L’exemple suivant illustre les `And` opérateurs, `Or` et `Xor` .</span><span class="sxs-lookup"><span data-stu-id="6f441-121">The following example illustrates the `And`, `Or`, and `Xor` operators.</span></span>  
  
 [!code-vb[VbVbalrOperators#78](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#78)]  
  
## <a name="short-circuiting-logical-operations"></a><span data-ttu-id="6f441-122">Opérations logiques de court-circuit</span><span class="sxs-lookup"><span data-stu-id="6f441-122">Short-Circuiting Logical Operations</span></span>  

 <span data-ttu-id="6f441-123">L' [opérateur AndAlso](../../../language-reference/operators/andalso-operator.md) est très similaire à l' `And` opérateur, en ce qu’il effectue également une conjonction logique sur deux `Boolean` expressions.</span><span class="sxs-lookup"><span data-stu-id="6f441-123">The [AndAlso Operator](../../../language-reference/operators/andalso-operator.md) is very similar to the `And` operator, in that it also performs logical conjunction on two `Boolean` expressions.</span></span> <span data-ttu-id="6f441-124">La principale différence entre les deux est que `AndAlso` présente *un comportement de court-circuit* .</span><span class="sxs-lookup"><span data-stu-id="6f441-124">The key difference between the two is that `AndAlso` exhibits *short-circuiting* behavior.</span></span> <span data-ttu-id="6f441-125">Si la première expression d’une `AndAlso` expression prend la valeur `False` , la deuxième expression n’est pas évaluée, car elle ne peut pas modifier le résultat final et `AndAlso` retourne `False` .</span><span class="sxs-lookup"><span data-stu-id="6f441-125">If the first expression in an `AndAlso` expression evaluates to `False`, then the second expression is not evaluated because it cannot alter the final result, and `AndAlso` returns `False`.</span></span>  
  
 <span data-ttu-id="6f441-126">De même, l' [opérateur OrElse](../../../language-reference/operators/orelse-operator.md) effectue une disjonction logique de court-circuit sur deux `Boolean` expressions.</span><span class="sxs-lookup"><span data-stu-id="6f441-126">Similarly, the [OrElse Operator](../../../language-reference/operators/orelse-operator.md) performs short-circuiting logical disjunction on two `Boolean` expressions.</span></span> <span data-ttu-id="6f441-127">Si la première expression d’une `OrElse` expression prend la valeur `True` , la deuxième expression n’est pas évaluée, car elle ne peut pas modifier le résultat final et `OrElse` retourne `True` .</span><span class="sxs-lookup"><span data-stu-id="6f441-127">If the first expression in an `OrElse` expression evaluates to `True`, then the second expression is not evaluated because it cannot alter the final result, and `OrElse` returns `True`.</span></span>  
  
### <a name="short-circuiting-trade-offs"></a><span data-ttu-id="6f441-128">Compromis de court-circuit</span><span class="sxs-lookup"><span data-stu-id="6f441-128">Short-Circuiting Trade-Offs</span></span>  

 <span data-ttu-id="6f441-129">Le court-circuit peut améliorer les performances en n’évaluant pas une expression qui ne peut pas modifier le résultat de l’opération logique.</span><span class="sxs-lookup"><span data-stu-id="6f441-129">Short-circuiting can improve performance by not evaluating an expression that cannot alter the result of the logical operation.</span></span> <span data-ttu-id="6f441-130">Toutefois, si cette expression effectue des actions supplémentaires, le court-circuit ignore ces actions.</span><span class="sxs-lookup"><span data-stu-id="6f441-130">However, if that expression performs additional actions, short-circuiting skips those actions.</span></span> <span data-ttu-id="6f441-131">Par exemple, si l’expression comprend un appel à une `Function` procédure, cette procédure n’est pas appelée si l’expression est court-circuitée et que tout code supplémentaire contenu dans le `Function` ne s’exécute pas.</span><span class="sxs-lookup"><span data-stu-id="6f441-131">For example, if the expression includes a call to a `Function` procedure, that procedure is not called if the expression is short-circuited, and any additional code contained in the `Function` does not run.</span></span> <span data-ttu-id="6f441-132">Par conséquent, la fonction peut s’exécuter uniquement occasionnellement et ne pas être testée correctement.</span><span class="sxs-lookup"><span data-stu-id="6f441-132">Therefore, the function might run only occasionally, and might not be tested correctly.</span></span> <span data-ttu-id="6f441-133">Ou la logique du programme peut dépendre du code dans `Function` .</span><span class="sxs-lookup"><span data-stu-id="6f441-133">Or the program logic might depend on the code in the `Function`.</span></span>  
  
 <span data-ttu-id="6f441-134">L’exemple suivant illustre la différence entre `And` , `Or` et leurs équivalents de court-circuit.</span><span class="sxs-lookup"><span data-stu-id="6f441-134">The following example illustrates the difference between `And`, `Or`, and their short-circuiting counterparts.</span></span>  
  
 [!code-vb[VbVbalrOperators#81](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#81)]  
  
 [!code-vb[VbVbalrOperators#80](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#80)]  
  
 [!code-vb[VbVbalrOperators#79](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#79)]  
  
 <span data-ttu-id="6f441-135">Dans l’exemple précédent, Notez que certains codes importants à l’intérieur de `checkIfValid()` ne s’exécutent pas lorsque l’appel est court-circuité.</span><span class="sxs-lookup"><span data-stu-id="6f441-135">In the preceding example, note that some important code inside `checkIfValid()` does not run when the call is short-circuited.</span></span> <span data-ttu-id="6f441-136">La première `If` instruction appelle `checkIfValid()` même si `12 > 45` retourne `False` , car `And` n’est pas un court-circuit.</span><span class="sxs-lookup"><span data-stu-id="6f441-136">The first `If` statement calls `checkIfValid()` even though `12 > 45` returns `False`, because `And` does not short-circuit.</span></span> <span data-ttu-id="6f441-137">La deuxième `If` instruction n’appelle pas `checkIfValid()` , car lorsque `12 > 45` retourne `False` , `AndAlso` les courts-circuits la seconde expression.</span><span class="sxs-lookup"><span data-stu-id="6f441-137">The second `If` statement does not call `checkIfValid()`, because when `12 > 45` returns `False`, `AndAlso` short-circuits the second expression.</span></span> <span data-ttu-id="6f441-138">La troisième `If` instruction appelle `checkIfValid()` même si `12 < 45` retourne `True` , car `Or` n’est pas un court-circuit.</span><span class="sxs-lookup"><span data-stu-id="6f441-138">The third `If` statement calls `checkIfValid()` even though `12 < 45` returns `True`, because `Or` does not short-circuit.</span></span> <span data-ttu-id="6f441-139">La quatrième `If` instruction n’appelle pas `checkIfValid()` , car lorsque `12 < 45` retourne `True` , `OrElse` les courts-circuits la seconde expression.</span><span class="sxs-lookup"><span data-stu-id="6f441-139">The fourth `If` statement does not call `checkIfValid()`, because when `12 < 45` returns `True`, `OrElse` short-circuits the second expression.</span></span>  
  
## <a name="bitwise-operations"></a><span data-ttu-id="6f441-140">Opérations au niveau du bit</span><span class="sxs-lookup"><span data-stu-id="6f441-140">Bitwise Operations</span></span>  

 <span data-ttu-id="6f441-141">Les opérations au niveau du bit évaluent deux valeurs intégrales sous forme binaire (base 2).</span><span class="sxs-lookup"><span data-stu-id="6f441-141">Bitwise operations evaluate two integral values in binary (base 2) form.</span></span> <span data-ttu-id="6f441-142">Ils comparent les bits aux positions correspondantes, puis attribuent des valeurs en fonction de la comparaison.</span><span class="sxs-lookup"><span data-stu-id="6f441-142">They compare the bits at corresponding positions and then assign values based on the comparison.</span></span> <span data-ttu-id="6f441-143">L’exemple suivant illustre l' `And` opérateur.</span><span class="sxs-lookup"><span data-stu-id="6f441-143">The following example illustrates the `And` operator.</span></span>  
  
 [!code-vb[VbVbalrConcepts#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConcepts/VB/Class1.vb#2)]  
  
 <span data-ttu-id="6f441-144">L’exemple précédent définit la valeur de `x` sur 1.</span><span class="sxs-lookup"><span data-stu-id="6f441-144">The preceding example sets the value of `x` to 1.</span></span> <span data-ttu-id="6f441-145">Cela se produit pour les raisons suivantes :</span><span class="sxs-lookup"><span data-stu-id="6f441-145">This happens for the following reasons:</span></span>  
  
- <span data-ttu-id="6f441-146">Les valeurs sont traitées comme binaires :</span><span class="sxs-lookup"><span data-stu-id="6f441-146">The values are treated as binary:</span></span>  
  
     <span data-ttu-id="6f441-147">3 sous forme binaire = 011</span><span class="sxs-lookup"><span data-stu-id="6f441-147">3 in binary form = 011</span></span>  
  
     <span data-ttu-id="6f441-148">5 sous forme binaire = 101</span><span class="sxs-lookup"><span data-stu-id="6f441-148">5 in binary form = 101</span></span>  
  
- <span data-ttu-id="6f441-149">L' `And` opérateur compare les représentations binaires, une position binaire (bit) à la fois.</span><span class="sxs-lookup"><span data-stu-id="6f441-149">The `And` operator compares the binary representations, one binary position (bit) at a time.</span></span> <span data-ttu-id="6f441-150">Si les deux bits à une position donnée sont 1, un 1 est placé à cette position dans le résultat.</span><span class="sxs-lookup"><span data-stu-id="6f441-150">If both bits at a given position are 1, then a 1 is placed in that position in the result.</span></span> <span data-ttu-id="6f441-151">Si un bit est égal à 0, la valeur 0 est placée à cette position dans le résultat.</span><span class="sxs-lookup"><span data-stu-id="6f441-151">If either bit is 0, then a 0 is placed in that position in the result.</span></span> <span data-ttu-id="6f441-152">Dans l’exemple précédent, cela fonctionne comme suit :</span><span class="sxs-lookup"><span data-stu-id="6f441-152">In the preceding example this works out as follows:</span></span>  
  
     <span data-ttu-id="6f441-153">011 (3 sous forme binaire)</span><span class="sxs-lookup"><span data-stu-id="6f441-153">011 (3 in binary form)</span></span>  
  
     <span data-ttu-id="6f441-154">101 (5 sous forme binaire)</span><span class="sxs-lookup"><span data-stu-id="6f441-154">101 (5 in binary form)</span></span>  
  
     <span data-ttu-id="6f441-155">001 (résultat, au format binaire)</span><span class="sxs-lookup"><span data-stu-id="6f441-155">001 (The result, in binary form)</span></span>  
  
- <span data-ttu-id="6f441-156">Le résultat est traité comme un nombre décimal.</span><span class="sxs-lookup"><span data-stu-id="6f441-156">The result is treated as decimal.</span></span> <span data-ttu-id="6f441-157">La valeur 001 est la représentation binaire de 1, donc `x` = 1.</span><span class="sxs-lookup"><span data-stu-id="6f441-157">The value 001 is the binary representation of 1, so `x` = 1.</span></span>  
  
 <span data-ttu-id="6f441-158">L’opération au niveau du bit `Or` est similaire, à ceci près qu’une valeur 1 est assignée au bit de résultat si l’un des deux bits comparés est 1.</span><span class="sxs-lookup"><span data-stu-id="6f441-158">The bitwise `Or` operation is similar, except that a 1 is assigned to the result bit if either or both of the compared bits is 1.</span></span> <span data-ttu-id="6f441-159">`Xor` assigne un 1 au bit de résultat si exactement l’un des bits comparés (pas les deux) est 1.</span><span class="sxs-lookup"><span data-stu-id="6f441-159">`Xor` assigns a 1 to the result bit if exactly one of the compared bits (not both) is 1.</span></span> <span data-ttu-id="6f441-160">`Not` prend un opérande unique et inverse tous les bits, y compris le bit de signe, et assigne cette valeur au résultat.</span><span class="sxs-lookup"><span data-stu-id="6f441-160">`Not` takes a single operand and inverts all the bits, including the sign bit, and assigns that value to the result.</span></span> <span data-ttu-id="6f441-161">Cela signifie que pour les nombres positifs signés, `Not` retourne toujours une valeur négative et, pour les nombres négatifs, `Not` retourne toujours une valeur positive ou nulle.</span><span class="sxs-lookup"><span data-stu-id="6f441-161">This means that for signed positive numbers, `Not` always returns a negative value, and for negative numbers, `Not` always returns a positive or zero value.</span></span>  
  
 <span data-ttu-id="6f441-162">Les `AndAlso` `OrElse` opérateurs et ne prennent pas en charge les opérations au niveau du bit.</span><span class="sxs-lookup"><span data-stu-id="6f441-162">The `AndAlso` and `OrElse` operators do not support bitwise operations.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6f441-163">Les opérations au niveau du bit ne peuvent être exécutées que sur des types intégraux.</span><span class="sxs-lookup"><span data-stu-id="6f441-163">Bitwise operations can be performed on integral types only.</span></span> <span data-ttu-id="6f441-164">Les valeurs à virgule flottante doivent être converties en types intégraux avant que l’opération au niveau du bit puisse se poursuivre.</span><span class="sxs-lookup"><span data-stu-id="6f441-164">Floating-point values must be converted to integral types before bitwise operation can proceed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f441-165">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6f441-165">See also</span></span>

- [<span data-ttu-id="6f441-166">Opérateurs logiques/de bits (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6f441-166">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../language-reference/operators/logical-bitwise-operators.md)
- [<span data-ttu-id="6f441-167">Expressions booléennes</span><span class="sxs-lookup"><span data-stu-id="6f441-167">Boolean Expressions</span></span>](boolean-expressions.md)
- [<span data-ttu-id="6f441-168">Opérateurs arithmétiques en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6f441-168">Arithmetic Operators in Visual Basic</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="6f441-169">Comparison Operators in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6f441-169">Comparison Operators in Visual Basic</span></span>](comparison-operators.md)
- [<span data-ttu-id="6f441-170">Opérateurs de concaténation (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6f441-170">Concatenation Operators in Visual Basic</span></span>](concatenation-operators.md)
- [<span data-ttu-id="6f441-171">Association efficace d’opérateurs</span><span class="sxs-lookup"><span data-stu-id="6f441-171">Efficient Combination of Operators</span></span>](efficient-combination-of-operators.md)
