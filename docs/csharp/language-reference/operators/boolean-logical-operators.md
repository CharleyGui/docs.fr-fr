---
title: Opérateurs logiques booléens - Référence C#
description: Découvrez les opérateurs C# qui effectuent des opérations de négation logique, de conjonction (AND) et de disjonction inclusive et exclusive (OR) avec des opérandes booléens.
ms.date: 09/27/2019
author: pkulikov
f1_keywords:
- '!_CSharpKeyword'
- '&_CSharpKeyword'
- ^_CSharpKeyword
- '|_CSharpKeyword'
- '&&_CSharpKeyword'
- '||_CSharpKeyword'
helpviewer_keywords:
- logical operators [C#]
- short-circuiting operators [C#]
- logical negation operator [C#]
- NOT operator [C#]
- '! operator [C#]'
- AND operator [C#]
- ampersand operator [C#]
- conjunction operator [C#]
- '& operator [C#]'
- exclusive OR operator [C#]
- XOR operator [C#]
- ^ operator [C#]
- OR operator [C#]
- disjunction operator [C#]
- '| operator [C#]'
- conditional AND operator [C#]
- short-circuiting AND operator [C#]
- '&& operator [C#]'
- conditional OR operator [C#]
- short-circuiting OR operator [C#]
- '|| operator [C#]'
ms.openlocfilehash: f711bd04aeadb584eac1ecb0b644a36e2e496d08
ms.sourcegitcommit: 9c3a4f2d3babca8919a1e490a159c1500ba7a844
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72290941"
---
# <a name="boolean-logical-operators-c-reference"></a><span data-ttu-id="cd1fd-103">Opérateurs logiques booléens (référence C#)</span><span class="sxs-lookup"><span data-stu-id="cd1fd-103">Boolean logical operators (C# reference)</span></span>

<span data-ttu-id="cd1fd-104">Les opérateurs suivants effectuent des opérations logiques avec les opérandes [booléens](../keywords/bool.md) :</span><span class="sxs-lookup"><span data-stu-id="cd1fd-104">The following operators perform logical operations with the [bool](../keywords/bool.md) operands:</span></span>

- <span data-ttu-id="cd1fd-105">opérateur unaire [`!` (négation logique)](#logical-negation-operator-) ;</span><span class="sxs-lookup"><span data-stu-id="cd1fd-105">Unary [`!` (logical negation)](#logical-negation-operator-) operator.</span></span>
- <span data-ttu-id="cd1fd-106">opérateurs binaires [`&` (AND logique)](#logical-and-operator-), [`|` (OR logique)](#logical-or-operator-) et [`^` (OR exclusif logique)](#logical-exclusive-or-operator-),</span><span class="sxs-lookup"><span data-stu-id="cd1fd-106">Binary [`&` (logical AND)](#logical-and-operator-), [`|` (logical OR)](#logical-or-operator-), and [`^` (logical exclusive OR)](#logical-exclusive-or-operator-) operators.</span></span> <span data-ttu-id="cd1fd-107">qui évaluent toujours les deux opérandes ;</span><span class="sxs-lookup"><span data-stu-id="cd1fd-107">Those operators always evaluate both operands.</span></span>
- <span data-ttu-id="cd1fd-108">opérateurs binaires [`&&` (AND logique conditionnel)](#conditional-logical-and-operator-) et [`||` (OR logique conditionnel)](#conditional-logical-or-operator-),</span><span class="sxs-lookup"><span data-stu-id="cd1fd-108">Binary [`&&` (conditional logical AND)](#conditional-logical-and-operator-) and [`||` (conditional logical OR)](#conditional-logical-or-operator-) operators.</span></span> <span data-ttu-id="cd1fd-109">Ces opérateurs n’évaluent l’opérande de partie droite que si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="cd1fd-109">Those operators evaluate the right-hand operand only if it's necessary.</span></span>

<span data-ttu-id="cd1fd-110">En ce qui concerne les opérandes de type [intégral](../builtin-types/integral-numeric-types.md), les opérateurs `&`, `|` et `^` effectuent des opérations logiques au niveau du bit.</span><span class="sxs-lookup"><span data-stu-id="cd1fd-110">For the operands of the [integral](../builtin-types/integral-numeric-types.md) types, the `&`, `|`, and `^` operators perform bitwise logical operations.</span></span> <span data-ttu-id="cd1fd-111">Pour plus d’informations, consultez [Opérateurs de bits et de décalage](bitwise-and-shift-operators.md).</span><span class="sxs-lookup"><span data-stu-id="cd1fd-111">For more information, see [Bitwise and shift operators](bitwise-and-shift-operators.md).</span></span>

## <a name="logical-negation-operator-"></a><span data-ttu-id="cd1fd-112">L’opérateur de négation logique !</span><span class="sxs-lookup"><span data-stu-id="cd1fd-112">Logical negation operator !</span></span>

<span data-ttu-id="cd1fd-113">L’opérateur de préfixe unaire `!` calcule la négation logique de son opérande.</span><span class="sxs-lookup"><span data-stu-id="cd1fd-113">The unary prefix `!` operator computes logical negation of its operand.</span></span> <span data-ttu-id="cd1fd-114">Autrement dit, il produit `true` si l’opérande donne `false` et `false` si l’opérande donne `true` :</span><span class="sxs-lookup"><span data-stu-id="cd1fd-114">That is, it produces `true`, if the operand evaluates to `false`, and `false`, if the operand evaluates to `true`:</span></span>

[!code-csharp-interactive[logical negation](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#Negation)]

<span data-ttu-id="cd1fd-115">À partir C# de 8,0, l’opérateur unaire postfixé `!` est un [opérateur null-indulgent avec](null-forgiving.md).</span><span class="sxs-lookup"><span data-stu-id="cd1fd-115">Starting with C# 8.0, the unary postfix `!` operator is a [null-forgiving operator](null-forgiving.md).</span></span>

## <a name="logical-and-operator-"></a><span data-ttu-id="cd1fd-116">Opérateur ET logique &amp;</span><span class="sxs-lookup"><span data-stu-id="cd1fd-116">Logical AND operator &amp;</span></span>

<span data-ttu-id="cd1fd-117">L’opérateur `&` calcule le AND logique de ses opérandes.</span><span class="sxs-lookup"><span data-stu-id="cd1fd-117">The `&` operator computes the logical AND of its operands.</span></span> <span data-ttu-id="cd1fd-118">Le résultat de `x & y` est `true` si `x` et `y` prennent la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="cd1fd-118">The result of `x & y` is `true` if both `x` and `y` evaluate to `true`.</span></span> <span data-ttu-id="cd1fd-119">Sinon, le résultat est `false`.</span><span class="sxs-lookup"><span data-stu-id="cd1fd-119">Otherwise, the result is `false`.</span></span>

<span data-ttu-id="cd1fd-120">L’opérateur `&` évalue les deux opérandes, même si l’opérande de partie gauche donne la valeur de `false`. Le résultat doit donc être `false` quelle que soit la valeur de l’opérande de partie droite.</span><span class="sxs-lookup"><span data-stu-id="cd1fd-120">The `&` operator evaluates both operands even if the left-hand operand evaluates to `false`, so that the result must be `false` regardless of the value of the right-hand operand.</span></span>

<span data-ttu-id="cd1fd-121">Dans l’exemple suivant, l’opérande de partie droite de l’opérateur `&` est un appel de méthode, effectué indépendamment de la valeur de l’opérande de partie gauche :</span><span class="sxs-lookup"><span data-stu-id="cd1fd-121">In the following example, the right-hand operand of the `&` operator is a method call, which is performed regardless of the value of the left-hand operand:</span></span>

[!code-csharp-interactive[logical AND](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#And)]

<span data-ttu-id="cd1fd-122">[L’opérateur AND logique conditionnel](#conditional-logical-and-operator-) `&&` calcule également le AND logique de ses opérandes, mais n’évalue pas l’opérande de partie droite si l’opérande de partie gauche donne la valeur de `false`.</span><span class="sxs-lookup"><span data-stu-id="cd1fd-122">The [conditional logical AND operator](#conditional-logical-and-operator-) `&&` also computes the logical AND of its operands, but doesn't evaluate the right-hand operand if the left-hand operand evaluates to `false`.</span></span>

<span data-ttu-id="cd1fd-123">Dans le cas des opérandes de type intégral, l’opérateur `&` calcule le [AND logique au niveau du bit](bitwise-and-shift-operators.md#logical-and-operator-) de ses opérandes.</span><span class="sxs-lookup"><span data-stu-id="cd1fd-123">For the operands of the integral types, the `&` operator computes the [bitwise logical AND](bitwise-and-shift-operators.md#logical-and-operator-) of its operands.</span></span> <span data-ttu-id="cd1fd-124">L’opérateur unaire `&` est [l’opérateur address-of](pointer-related-operators.md#address-of-operator-).</span><span class="sxs-lookup"><span data-stu-id="cd1fd-124">The unary `&` operator is the [address-of operator](pointer-related-operators.md#address-of-operator-).</span></span>

## <a name="logical-exclusive-or-operator-"></a><span data-ttu-id="cd1fd-125">L’opérateur OR exclusif logique ^</span><span class="sxs-lookup"><span data-stu-id="cd1fd-125">Logical exclusive OR operator ^</span></span>

<span data-ttu-id="cd1fd-126">L’opérateur `^` calcule le OR exclusif logique, également appelé XOR logique, de ses opérandes.</span><span class="sxs-lookup"><span data-stu-id="cd1fd-126">The `^` operator computes the logical exclusive OR, also known as the logical XOR, of its operands.</span></span> <span data-ttu-id="cd1fd-127">Le résultat de `x ^ y` est `true` si `x` donne `true` et `y` donne `false`, ou `x` donne `false` et `y` donne `true`.</span><span class="sxs-lookup"><span data-stu-id="cd1fd-127">The result of `x ^ y` is `true` if `x` evaluates to `true` and `y` evaluates to `false`, or `x` evaluates to `false` and `y` evaluates to `true`.</span></span> <span data-ttu-id="cd1fd-128">Sinon, le résultat est `false`.</span><span class="sxs-lookup"><span data-stu-id="cd1fd-128">Otherwise, the result is `false`.</span></span> <span data-ttu-id="cd1fd-129">Autrement dit, pour les opérandes `bool`, l’opérateur `^` calcule le même résultat que [l’opérateur d’inégalité](equality-operators.md#inequality-operator-) `!=`.</span><span class="sxs-lookup"><span data-stu-id="cd1fd-129">That is, for the `bool` operands, the `^` operator computes the same result as the [inequality operator](equality-operators.md#inequality-operator-) `!=`.</span></span>

[!code-csharp-interactive[logical exclusive OR](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#Xor)]

<span data-ttu-id="cd1fd-130">Dans le cas des opérandes de type intégral, l’opérateur `^` calcule le [OR exclusif logique au niveau du bit](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) de ses opérandes.</span><span class="sxs-lookup"><span data-stu-id="cd1fd-130">For the operands of the integral types, the `^` operator computes the [bitwise logical exclusive OR](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) of its operands.</span></span>

## <a name="logical-or-operator-"></a><span data-ttu-id="cd1fd-131">L’opérateur OU logique |</span><span class="sxs-lookup"><span data-stu-id="cd1fd-131">Logical OR operator |</span></span>

<span data-ttu-id="cd1fd-132">L’opérateur `|` calcule le OR logique de ses opérandes.</span><span class="sxs-lookup"><span data-stu-id="cd1fd-132">The `|` operator computes the logical OR of its operands.</span></span> <span data-ttu-id="cd1fd-133">Le résultat de `x | y` est `true` si `x` ou `y` prend la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="cd1fd-133">The result of `x | y` is `true` if either `x` or `y` evaluates to `true`.</span></span> <span data-ttu-id="cd1fd-134">Sinon, le résultat est `false`.</span><span class="sxs-lookup"><span data-stu-id="cd1fd-134">Otherwise, the result is `false`.</span></span>

<span data-ttu-id="cd1fd-135">L’opérateur `|` évalue les deux opérandes, même si l’opérande de partie gauche donne la valeur de `true`. Le résultat doit donc être `true` quelle que soit la valeur de l’opérande de partie droite.</span><span class="sxs-lookup"><span data-stu-id="cd1fd-135">The `|` operator evaluates both operands even if the left-hand operand evaluates to `true`, so that the result must be `true` regardless of the value of the right-hand operand.</span></span>

<span data-ttu-id="cd1fd-136">Dans l’exemple suivant, l’opérande de partie droite de l’opérateur `|` est un appel de méthode, effectué indépendamment de la valeur de l’opérande de partie gauche :</span><span class="sxs-lookup"><span data-stu-id="cd1fd-136">In the following example, the right-hand operand of the `|` operator is a method call, which is performed regardless of the value of the left-hand operand:</span></span>

[!code-csharp-interactive[logical OR](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#Or)]

<span data-ttu-id="cd1fd-137">[L’opérateur OR logique conditionnel](#conditional-logical-or-operator-) `||` calcule également le OR logique de ses opérandes, mais n’évalue pas l’opérande de partie droite si l’opérande de partie gauche donne la valeur de `true`.</span><span class="sxs-lookup"><span data-stu-id="cd1fd-137">The [conditional logical OR operator](#conditional-logical-or-operator-) `||` also computes the logical OR of its operands, but doesn't evaluate the right-hand operand if the left-hand operand evaluates to `true`.</span></span>

<span data-ttu-id="cd1fd-138">Dans le cas des opérandes de type intégral, l’opérateur `|` calcule le [OR logique au niveau du bit](bitwise-and-shift-operators.md#logical-or-operator-) de ses opérandes.</span><span class="sxs-lookup"><span data-stu-id="cd1fd-138">For the operands of the integral types, the `|` operator computes the [bitwise logical OR](bitwise-and-shift-operators.md#logical-or-operator-) of its operands.</span></span>

## <a name="conditional-logical-and-operator-"></a> <span data-ttu-id="cd1fd-139">Opérateur AND logique conditionnel &amp;&amp;</span><span class="sxs-lookup"><span data-stu-id="cd1fd-139">Conditional logical AND operator &amp;&amp;</span></span>

<span data-ttu-id="cd1fd-140">L’opérateur AND logique conditionnel `&&`, également appelé opérateur AND logique de « court-circuit », calcule le AND logique de ses opérandes.</span><span class="sxs-lookup"><span data-stu-id="cd1fd-140">The conditional logical AND operator `&&`, also known as the "short-circuiting" logical AND operator, computes the logical AND of its operands.</span></span> <span data-ttu-id="cd1fd-141">Le résultat de `x && y` est `true` si `x` et `y` prennent la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="cd1fd-141">The result of `x && y` is `true` if both `x` and `y` evaluate to `true`.</span></span> <span data-ttu-id="cd1fd-142">Sinon, le résultat est `false`.</span><span class="sxs-lookup"><span data-stu-id="cd1fd-142">Otherwise, the result is `false`.</span></span> <span data-ttu-id="cd1fd-143">Si `x` donne la valeur de `false`, `y` n’est pas évalué.</span><span class="sxs-lookup"><span data-stu-id="cd1fd-143">If `x` evaluates to `false`, `y` is not evaluated.</span></span>

<span data-ttu-id="cd1fd-144">Dans l’exemple suivant, l’opérande de partie droite de l’opérateur `&&` est un appel de méthode, non effectué si l’opérande de partie gauche donne la valeur de `false` :</span><span class="sxs-lookup"><span data-stu-id="cd1fd-144">In the following example, the right-hand operand of the `&&` operator is a method call, which isn't performed if the left-hand operand evaluates to `false`:</span></span>

[!code-csharp-interactive[conditional logical AND](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#ConditionalAnd)]

<span data-ttu-id="cd1fd-145">[L’opérateur AND logique](#logical-and-operator-) `&` calcule également le AND logique de ses opérandes, mais évalue toujours les deux opérandes.</span><span class="sxs-lookup"><span data-stu-id="cd1fd-145">The [logical AND operator](#logical-and-operator-) `&` also computes the logical AND of its operands, but always evaluates both operands.</span></span>

## <a name="conditional-logical-or-operator-"></a><span data-ttu-id="cd1fd-146">L’opérateur OR logique conditionnel ||</span><span class="sxs-lookup"><span data-stu-id="cd1fd-146">Conditional logical OR operator ||</span></span>

<span data-ttu-id="cd1fd-147">L’opérateur OR logique conditionnel `||`, également appelé opérateur OR logique de « court-circuit », calcule le OR logique de ses opérandes.</span><span class="sxs-lookup"><span data-stu-id="cd1fd-147">The conditional logical OR operator `||`, also known as the "short-circuiting" logical OR operator, computes the logical OR of its operands.</span></span> <span data-ttu-id="cd1fd-148">Le résultat de `x || y` est `true` si `x` ou `y` prend la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="cd1fd-148">The result of `x || y` is `true` if either `x` or `y` evaluates to `true`.</span></span> <span data-ttu-id="cd1fd-149">Sinon, le résultat est `false`.</span><span class="sxs-lookup"><span data-stu-id="cd1fd-149">Otherwise, the result is `false`.</span></span> <span data-ttu-id="cd1fd-150">Si `x` donne la valeur de `true`, `y` n’est pas évalué.</span><span class="sxs-lookup"><span data-stu-id="cd1fd-150">If `x` evaluates to `true`, `y` is not evaluated.</span></span>

<span data-ttu-id="cd1fd-151">Dans l’exemple suivant, l’opérande de partie droite de l’opérateur `||` est un appel de méthode, non effectué si l’opérande de partie gauche donne la valeur de `true` :</span><span class="sxs-lookup"><span data-stu-id="cd1fd-151">In the following example, the right-hand operand of the `||` operator is a method call, which isn't performed if the left-hand operand evaluates to `true`:</span></span>

[!code-csharp-interactive[conditional logical OR](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#ConditionalOr)]

<span data-ttu-id="cd1fd-152">[L’opérateur OR logique](#logical-or-operator-) `|` calcule également le OR logique de ses opérandes, mais évalue toujours les deux opérandes.</span><span class="sxs-lookup"><span data-stu-id="cd1fd-152">The [logical OR operator](#logical-or-operator-) `|` also computes the logical OR of its operands, but always evaluates both operands.</span></span>

## <a name="nullable-boolean-logical-operators"></a><span data-ttu-id="cd1fd-153">Les opérateurs logiques booléens Nullable</span><span class="sxs-lookup"><span data-stu-id="cd1fd-153">Nullable Boolean logical operators</span></span>

<span data-ttu-id="cd1fd-154">Dans le cas des opérandes `bool?`, les opérateurs `&` et `|` prennent en charge la logique à trois valeurs.</span><span class="sxs-lookup"><span data-stu-id="cd1fd-154">For the `bool?` operands, the `&` and `|` operators support the three-valued logic.</span></span> <span data-ttu-id="cd1fd-155">La sémantique de ces opérateurs est définie par le tableau suivant :</span><span class="sxs-lookup"><span data-stu-id="cd1fd-155">The semantics of these operators is defined by the following table:</span></span>  
  
|<span data-ttu-id="cd1fd-156">x</span><span class="sxs-lookup"><span data-stu-id="cd1fd-156">x</span></span>|<span data-ttu-id="cd1fd-157">o</span><span class="sxs-lookup"><span data-stu-id="cd1fd-157">y</span></span>|<span data-ttu-id="cd1fd-158">x&y</span><span class="sxs-lookup"><span data-stu-id="cd1fd-158">x&y</span></span>|<span data-ttu-id="cd1fd-159">x&#124;y</span><span class="sxs-lookup"><span data-stu-id="cd1fd-159">x&#124;y</span></span>|  
|----|----|----|----|  
|<span data-ttu-id="cd1fd-160">true</span><span class="sxs-lookup"><span data-stu-id="cd1fd-160">true</span></span>|<span data-ttu-id="cd1fd-161">true</span><span class="sxs-lookup"><span data-stu-id="cd1fd-161">true</span></span>|<span data-ttu-id="cd1fd-162">true</span><span class="sxs-lookup"><span data-stu-id="cd1fd-162">true</span></span>|<span data-ttu-id="cd1fd-163">true</span><span class="sxs-lookup"><span data-stu-id="cd1fd-163">true</span></span>|  
|<span data-ttu-id="cd1fd-164">true</span><span class="sxs-lookup"><span data-stu-id="cd1fd-164">true</span></span>|<span data-ttu-id="cd1fd-165">false</span><span class="sxs-lookup"><span data-stu-id="cd1fd-165">false</span></span>|<span data-ttu-id="cd1fd-166">false</span><span class="sxs-lookup"><span data-stu-id="cd1fd-166">false</span></span>|<span data-ttu-id="cd1fd-167">true</span><span class="sxs-lookup"><span data-stu-id="cd1fd-167">true</span></span>|  
|<span data-ttu-id="cd1fd-168">true</span><span class="sxs-lookup"><span data-stu-id="cd1fd-168">true</span></span>|<span data-ttu-id="cd1fd-169">Null</span><span class="sxs-lookup"><span data-stu-id="cd1fd-169">null</span></span>|<span data-ttu-id="cd1fd-170">Null</span><span class="sxs-lookup"><span data-stu-id="cd1fd-170">null</span></span>|<span data-ttu-id="cd1fd-171">true</span><span class="sxs-lookup"><span data-stu-id="cd1fd-171">true</span></span>|  
|<span data-ttu-id="cd1fd-172">false</span><span class="sxs-lookup"><span data-stu-id="cd1fd-172">false</span></span>|<span data-ttu-id="cd1fd-173">true</span><span class="sxs-lookup"><span data-stu-id="cd1fd-173">true</span></span>|<span data-ttu-id="cd1fd-174">false</span><span class="sxs-lookup"><span data-stu-id="cd1fd-174">false</span></span>|<span data-ttu-id="cd1fd-175">true</span><span class="sxs-lookup"><span data-stu-id="cd1fd-175">true</span></span>|  
|<span data-ttu-id="cd1fd-176">false</span><span class="sxs-lookup"><span data-stu-id="cd1fd-176">false</span></span>|<span data-ttu-id="cd1fd-177">false</span><span class="sxs-lookup"><span data-stu-id="cd1fd-177">false</span></span>|<span data-ttu-id="cd1fd-178">false</span><span class="sxs-lookup"><span data-stu-id="cd1fd-178">false</span></span>|<span data-ttu-id="cd1fd-179">false</span><span class="sxs-lookup"><span data-stu-id="cd1fd-179">false</span></span>|  
|<span data-ttu-id="cd1fd-180">false</span><span class="sxs-lookup"><span data-stu-id="cd1fd-180">false</span></span>|<span data-ttu-id="cd1fd-181">Null</span><span class="sxs-lookup"><span data-stu-id="cd1fd-181">null</span></span>|<span data-ttu-id="cd1fd-182">false</span><span class="sxs-lookup"><span data-stu-id="cd1fd-182">false</span></span>|<span data-ttu-id="cd1fd-183">null</span><span class="sxs-lookup"><span data-stu-id="cd1fd-183">null</span></span>|  
|<span data-ttu-id="cd1fd-184">Null</span><span class="sxs-lookup"><span data-stu-id="cd1fd-184">null</span></span>|<span data-ttu-id="cd1fd-185">true</span><span class="sxs-lookup"><span data-stu-id="cd1fd-185">true</span></span>|<span data-ttu-id="cd1fd-186">Null</span><span class="sxs-lookup"><span data-stu-id="cd1fd-186">null</span></span>|<span data-ttu-id="cd1fd-187">true</span><span class="sxs-lookup"><span data-stu-id="cd1fd-187">true</span></span>|  
|<span data-ttu-id="cd1fd-188">Null</span><span class="sxs-lookup"><span data-stu-id="cd1fd-188">null</span></span>|<span data-ttu-id="cd1fd-189">false</span><span class="sxs-lookup"><span data-stu-id="cd1fd-189">false</span></span>|<span data-ttu-id="cd1fd-190">false</span><span class="sxs-lookup"><span data-stu-id="cd1fd-190">false</span></span>|<span data-ttu-id="cd1fd-191">null</span><span class="sxs-lookup"><span data-stu-id="cd1fd-191">null</span></span>|  
|<span data-ttu-id="cd1fd-192">Null</span><span class="sxs-lookup"><span data-stu-id="cd1fd-192">null</span></span>|<span data-ttu-id="cd1fd-193">Null</span><span class="sxs-lookup"><span data-stu-id="cd1fd-193">null</span></span>|<span data-ttu-id="cd1fd-194">Null</span><span class="sxs-lookup"><span data-stu-id="cd1fd-194">null</span></span>|<span data-ttu-id="cd1fd-195">Null</span><span class="sxs-lookup"><span data-stu-id="cd1fd-195">null</span></span>|  

<span data-ttu-id="cd1fd-196">Le comportement de ces opérateurs diffère du comportement classique des opérateurs avec des types valeur Nullable.</span><span class="sxs-lookup"><span data-stu-id="cd1fd-196">The behavior of those operators differs from the typical operator behavior with nullable value types.</span></span> <span data-ttu-id="cd1fd-197">En règle générale, un opérateur défini pour les opérandes d’un type valeur peut être également utilisé avec des opérandes du type valeur Nullable correspondant.</span><span class="sxs-lookup"><span data-stu-id="cd1fd-197">Typically, an operator which is defined for operands of a value type can be also used with operands of the corresponding nullable value type.</span></span> <span data-ttu-id="cd1fd-198">Il produit `null` si l’un de ses opérandes est `null`.</span><span class="sxs-lookup"><span data-stu-id="cd1fd-198">Such an operator produces `null` if any of its operands is `null`.</span></span> <span data-ttu-id="cd1fd-199">Toutefois, les opérateurs `&` et `|` peuvent produire une valeur non Null même si l’un des opérandes est `null`.</span><span class="sxs-lookup"><span data-stu-id="cd1fd-199">However, the `&` and `|` operators can produce non-null even if one of the operands is `null`.</span></span> <span data-ttu-id="cd1fd-200">Pour plus d’informations sur le comportement de l’opérateur avec les types valeur Nullable, consultez la section [opérateurs](../../programming-guide/nullable-types/using-nullable-types.md#operators) de l’article [utilisation de types valeur Nullable](../../programming-guide/nullable-types/using-nullable-types.md) .</span><span class="sxs-lookup"><span data-stu-id="cd1fd-200">For more information about the operator behavior with nullable value types, see the [Operators](../../programming-guide/nullable-types/using-nullable-types.md#operators) section of the [Using nullable value types](../../programming-guide/nullable-types/using-nullable-types.md) article.</span></span>

<span data-ttu-id="cd1fd-201">Vous pouvez également utiliser les opérateurs `!` et `^` avec les opérandes `bool?`, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="cd1fd-201">You can also use the `!` and `^` operators with the `bool?` operands, as the following example shows:</span></span>

[!code-csharp-interactive[lifted negation and xor](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#WithNullableBoolean)]

<span data-ttu-id="cd1fd-202">Les opérateurs logiques conditionnels `&&` et `||` ne prennent pas en charge les opérandes `bool?`.</span><span class="sxs-lookup"><span data-stu-id="cd1fd-202">The conditional logical operators `&&` and `||` don't support the `bool?` operands.</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="cd1fd-203">Assignation composée</span><span class="sxs-lookup"><span data-stu-id="cd1fd-203">Compound assignment</span></span>

<span data-ttu-id="cd1fd-204">Pour un opérateur binaire `op`, une expression d’assignation composée du formulaire</span><span class="sxs-lookup"><span data-stu-id="cd1fd-204">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="cd1fd-205">est équivalent à</span><span class="sxs-lookup"><span data-stu-id="cd1fd-205">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="cd1fd-206">sauf que `x` n’est évalué qu’une seule fois.</span><span class="sxs-lookup"><span data-stu-id="cd1fd-206">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="cd1fd-207">Les opérateurs `&`, `|` et `^` prennent en charge l’assignation composée, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="cd1fd-207">The `&`, `|`, and `^` operators support compound assignment, as the following example shows:</span></span>

[!code-csharp-interactive[compound assignment](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#CompoundAssignment)]

<span data-ttu-id="cd1fd-208">Les opérateurs logiques conditionnels `&&` et `||` ne prennent pas en charge l’assignation composée.</span><span class="sxs-lookup"><span data-stu-id="cd1fd-208">The conditional logical operators `&&` and `||` don't support compound assignment.</span></span>

## <a name="operator-precedence"></a><span data-ttu-id="cd1fd-209">Précédence des opérateurs</span><span class="sxs-lookup"><span data-stu-id="cd1fd-209">Operator precedence</span></span>

<span data-ttu-id="cd1fd-210">La liste suivante présente les opérateurs logiques par ordre de précédence, de la plus élevée à la plus basse :</span><span class="sxs-lookup"><span data-stu-id="cd1fd-210">The following list orders logical operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="cd1fd-211">Opérateur de négation logique `!`</span><span class="sxs-lookup"><span data-stu-id="cd1fd-211">Logical negation operator `!`</span></span>
- <span data-ttu-id="cd1fd-212">L’opérateur AND logique `&`</span><span class="sxs-lookup"><span data-stu-id="cd1fd-212">Logical AND operator `&`</span></span>
- <span data-ttu-id="cd1fd-213">Opérateur OR exclusif logique `^`</span><span class="sxs-lookup"><span data-stu-id="cd1fd-213">Logical exclusive OR operator `^`</span></span>
- <span data-ttu-id="cd1fd-214">Opérateur OR logique `|`</span><span class="sxs-lookup"><span data-stu-id="cd1fd-214">Logical OR operator `|`</span></span>
- <span data-ttu-id="cd1fd-215">Opérateur AND logique conditionnel `&&`</span><span class="sxs-lookup"><span data-stu-id="cd1fd-215">Conditional logical AND operator `&&`</span></span>
- <span data-ttu-id="cd1fd-216">Opérateur OR logique conditionnel `||`</span><span class="sxs-lookup"><span data-stu-id="cd1fd-216">Conditional logical OR operator `||`</span></span>

<span data-ttu-id="cd1fd-217">Utilisez des parenthèses, `()`, pour modifier l’ordre d’évaluation imposé par la précédence des opérateurs :</span><span class="sxs-lookup"><span data-stu-id="cd1fd-217">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence:</span></span>

[!code-csharp-interactive[operator precedence](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#Precedence)]

<span data-ttu-id="cd1fd-218">Pour obtenir la liste complète des opérateurs C# classés par niveau de priorité, consultez [Opérateurs C#](index.md).</span><span class="sxs-lookup"><span data-stu-id="cd1fd-218">For the complete list of C# operators ordered by precedence level, see [C# operators](index.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="cd1fd-219">Capacité de surcharge de l’opérateur</span><span class="sxs-lookup"><span data-stu-id="cd1fd-219">Operator overloadability</span></span>

<span data-ttu-id="cd1fd-220">Un type défini par l’utilisateur peut [surcharger](operator-overloading.md) les opérateurs `!`, `&`, `|` et `^`.</span><span class="sxs-lookup"><span data-stu-id="cd1fd-220">A user-defined type can [overload](operator-overloading.md) the `!`, `&`, `|`, and `^` operators.</span></span> <span data-ttu-id="cd1fd-221">Quand un opérateur binaire est surchargé, l’opérateur d’assignation composée correspondant est aussi implicitement surchargé.</span><span class="sxs-lookup"><span data-stu-id="cd1fd-221">When a binary operator is overloaded, the corresponding compound assignment operator is also implicitly overloaded.</span></span> <span data-ttu-id="cd1fd-222">Un type défini par l’utilisateur ne peut pas surcharger explicitement un opérateur d’assignation composée.</span><span class="sxs-lookup"><span data-stu-id="cd1fd-222">A user-defined type cannot explicitly overload a compound assignment operator.</span></span>

<span data-ttu-id="cd1fd-223">Un type défini par l’utilisateur ne peut pas surcharger les opérateurs logiques conditionnels `&&` et `||`.</span><span class="sxs-lookup"><span data-stu-id="cd1fd-223">A user-defined type cannot overload the conditional logical operators `&&` and `||`.</span></span> <span data-ttu-id="cd1fd-224">Toutefois, si un type défini par l’utilisateur surcharge les [opérateurs true et false](true-false-operators.md) et l’opérateur `&` ou `|` d’une certaine manière, l’opération `&&` ou `||` peut être évaluée respectivement pour les opérandes de ce type.</span><span class="sxs-lookup"><span data-stu-id="cd1fd-224">However, if a user-defined type overloads the [true and false operators](true-false-operators.md) and the `&` or `|` operator in a certain way, the `&&` or `||` operation, respectively, can be evaluated for the operands of that type.</span></span> <span data-ttu-id="cd1fd-225">Pour plus d’informations, consultez la section [Opérateurs logiques conditionnels définis par l’utilisateur](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="cd1fd-225">For more information, see the [User-defined conditional logical operators](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="cd1fd-226">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="cd1fd-226">C# language specification</span></span>

<span data-ttu-id="cd1fd-227">Pour plus d’informations, consultez les sections suivantes de la [spécification du langage C#](~/_csharplang/spec/introduction.md) :</span><span class="sxs-lookup"><span data-stu-id="cd1fd-227">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="cd1fd-228">Opérateur de négation logique</span><span class="sxs-lookup"><span data-stu-id="cd1fd-228">Logical negation operator</span></span>](~/_csharplang/spec/expressions.md#logical-negation-operator)
- [<span data-ttu-id="cd1fd-229">Opérateurs logiques</span><span class="sxs-lookup"><span data-stu-id="cd1fd-229">Logical operators</span></span>](~/_csharplang/spec/expressions.md#logical-operators)
- [<span data-ttu-id="cd1fd-230">Opérateurs logiques conditionnels</span><span class="sxs-lookup"><span data-stu-id="cd1fd-230">Conditional logical operators</span></span>](~/_csharplang/spec/expressions.md#conditional-logical-operators)
- [<span data-ttu-id="cd1fd-231">Assignation composée</span><span class="sxs-lookup"><span data-stu-id="cd1fd-231">Compound assignment</span></span>](~/_csharplang/spec/expressions.md#compound-assignment)

## <a name="see-also"></a><span data-ttu-id="cd1fd-232">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cd1fd-232">See also</span></span>

- [<span data-ttu-id="cd1fd-233">Informations de référence sur C#</span><span class="sxs-lookup"><span data-stu-id="cd1fd-233">C# reference</span></span>](../index.md)
- [<span data-ttu-id="cd1fd-234">Opérateurs C#</span><span class="sxs-lookup"><span data-stu-id="cd1fd-234">C# operators</span></span>](index.md)
- [<span data-ttu-id="cd1fd-235">Opérateurs de bits et de décalage</span><span class="sxs-lookup"><span data-stu-id="cd1fd-235">Bitwise and shift operators</span></span>](bitwise-and-shift-operators.md)
