---
title: Opérateurs logiques booléens - Référence C#
description: Découvrez les opérateurs C# qui effectuent des opérations de négation logique, de conjonction (AND) et de disjonction inclusive et exclusive (OR) avec des opérandes booléens.
ms.date: 06/29/2020
author: pkulikov
f1_keywords:
- '!_CSharpKeyword'
- '&_CSharpKeyword'
- ^_CSharpKeyword
- '|_CSharpKeyword'
- '&&_CSharpKeyword'
- '||_CSharpKeyword'
- '|=_CSharpKeyword'
- ^=_CSharpKeyword
- '&=_CSharpKeyword'
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
ms.openlocfilehash: 00b1523029ed6562fda6947415029cd3b7a9b405
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2020
ms.locfileid: "87916899"
---
# <a name="boolean-logical-operators-c-reference"></a><span data-ttu-id="ab110-103">Opérateurs logiques booléens (référence C#)</span><span class="sxs-lookup"><span data-stu-id="ab110-103">Boolean logical operators (C# reference)</span></span>

<span data-ttu-id="ab110-104">Les opérateurs suivants effectuent des opérations logiques avec des opérandes [bool](../builtin-types/bool.md) :</span><span class="sxs-lookup"><span data-stu-id="ab110-104">The following operators perform logical operations with [bool](../builtin-types/bool.md) operands:</span></span>

- <span data-ttu-id="ab110-105">Opérateur unaire [ `!` (négation logique)](#logical-negation-operator-) .</span><span class="sxs-lookup"><span data-stu-id="ab110-105">Unary [`!` (logical negation)](#logical-negation-operator-) operator.</span></span>
- <span data-ttu-id="ab110-106">Opérateurs binaires [ `&` (and logique)](#logical-and-operator-), [ `|` (or logique)](#logical-or-operator-)et [ `^` (or exclusif logique)](#logical-exclusive-or-operator-) .</span><span class="sxs-lookup"><span data-stu-id="ab110-106">Binary [`&` (logical AND)](#logical-and-operator-), [`|` (logical OR)](#logical-or-operator-), and [`^` (logical exclusive OR)](#logical-exclusive-or-operator-) operators.</span></span> <span data-ttu-id="ab110-107">qui évaluent toujours les deux opérandes ;</span><span class="sxs-lookup"><span data-stu-id="ab110-107">Those operators always evaluate both operands.</span></span>
- <span data-ttu-id="ab110-108">Opérateurs binaires [ `&&` (conditionnels and logiques)](#conditional-logical-and-operator-) et [ `||` (opérateurs logiques conditionnels)](#conditional-logical-or-operator-) .</span><span class="sxs-lookup"><span data-stu-id="ab110-108">Binary [`&&` (conditional logical AND)](#conditional-logical-and-operator-) and [`||` (conditional logical OR)](#conditional-logical-or-operator-) operators.</span></span> <span data-ttu-id="ab110-109">Ces opérateurs n’évaluent l’opérande de partie droite que si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="ab110-109">Those operators evaluate the right-hand operand only if it's necessary.</span></span>

<span data-ttu-id="ab110-110">Pour les opérandes des [types numériques intégraux](../builtin-types/integral-numeric-types.md), `&` les `|` opérateurs, et `^` effectuent des opérations logiques au niveau du bit.</span><span class="sxs-lookup"><span data-stu-id="ab110-110">For operands of the [integral numeric types](../builtin-types/integral-numeric-types.md), the `&`, `|`, and `^` operators perform bitwise logical operations.</span></span> <span data-ttu-id="ab110-111">Pour plus d’informations, consultez [Opérateurs de bits et de décalage](bitwise-and-shift-operators.md).</span><span class="sxs-lookup"><span data-stu-id="ab110-111">For more information, see [Bitwise and shift operators](bitwise-and-shift-operators.md).</span></span>

## <a name="logical-negation-operator-"></a><span data-ttu-id="ab110-112">L’opérateur de négation logique !</span><span class="sxs-lookup"><span data-stu-id="ab110-112">Logical negation operator !</span></span>

<span data-ttu-id="ab110-113">L’opérateur préfixé unaire `!` calcule la négation logique de son opérande.</span><span class="sxs-lookup"><span data-stu-id="ab110-113">The unary prefix `!` operator computes logical negation of its operand.</span></span> <span data-ttu-id="ab110-114">Autrement dit, il produit `true` si l’opérande donne `false` et `false` si l’opérande donne `true` :</span><span class="sxs-lookup"><span data-stu-id="ab110-114">That is, it produces `true`, if the operand evaluates to `false`, and `false`, if the operand evaluates to `true`:</span></span>

[!code-csharp-interactive[logical negation](snippets/shared/BooleanLogicalOperators.cs#Negation)]

<span data-ttu-id="ab110-115">À compter de C# 8,0, l’opérateur postfix unaire `!` est l' [opérateur null-indulgent avec](null-forgiving.md).</span><span class="sxs-lookup"><span data-stu-id="ab110-115">Beginning with C# 8.0, the unary postfix `!` operator is the [null-forgiving operator](null-forgiving.md).</span></span>

## <a name="logical-and-operator-amp"></a><a name="logical-and-operator-"></a><span data-ttu-id="ab110-116">Opérateur AND logique&amp;</span><span class="sxs-lookup"><span data-stu-id="ab110-116">Logical AND operator &amp;</span></span>

<span data-ttu-id="ab110-117">L’opérateur `&` calcule le AND logique de ses opérandes.</span><span class="sxs-lookup"><span data-stu-id="ab110-117">The `&` operator computes the logical AND of its operands.</span></span> <span data-ttu-id="ab110-118">Le résultat de `x & y` est `true` si `x` et `y` prennent la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="ab110-118">The result of `x & y` is `true` if both `x` and `y` evaluate to `true`.</span></span> <span data-ttu-id="ab110-119">Sinon, le résultat est `false`.</span><span class="sxs-lookup"><span data-stu-id="ab110-119">Otherwise, the result is `false`.</span></span>

<span data-ttu-id="ab110-120">L' `&` opérateur évalue les deux opérandes même si l’opérande de gauche est évalué à `false` , de sorte que le résultat de l’opération est `false` indépendamment de la valeur de l’opérande de droite.</span><span class="sxs-lookup"><span data-stu-id="ab110-120">The `&` operator evaluates both operands even if the left-hand operand evaluates to `false`, so that the operation result is `false` regardless of the value of the right-hand operand.</span></span>

<span data-ttu-id="ab110-121">Dans l’exemple suivant, l’opérande de partie droite de l’opérateur `&` est un appel de méthode, effectué indépendamment de la valeur de l’opérande de partie gauche :</span><span class="sxs-lookup"><span data-stu-id="ab110-121">In the following example, the right-hand operand of the `&` operator is a method call, which is performed regardless of the value of the left-hand operand:</span></span>

[!code-csharp-interactive[logical AND](snippets/shared/BooleanLogicalOperators.cs#And)]

<span data-ttu-id="ab110-122">[L’opérateur AND logique conditionnel](#conditional-logical-and-operator-) `&&` calcule également le AND logique de ses opérandes, mais n’évalue pas l’opérande de partie droite si l’opérande de partie gauche donne la valeur de `false`.</span><span class="sxs-lookup"><span data-stu-id="ab110-122">The [conditional logical AND operator](#conditional-logical-and-operator-) `&&` also computes the logical AND of its operands, but doesn't evaluate the right-hand operand if the left-hand operand evaluates to `false`.</span></span>

<span data-ttu-id="ab110-123">Pour les opérandes des [types numériques intégraux](../builtin-types/integral-numeric-types.md), l' `&` opérateur calcule le [and logique au niveau du bit](bitwise-and-shift-operators.md#logical-and-operator-) de ses opérandes.</span><span class="sxs-lookup"><span data-stu-id="ab110-123">For operands of the [integral numeric types](../builtin-types/integral-numeric-types.md), the `&` operator computes the [bitwise logical AND](bitwise-and-shift-operators.md#logical-and-operator-) of its operands.</span></span> <span data-ttu-id="ab110-124">L’opérateur unaire `&` est [l’opérateur address-of](pointer-related-operators.md#address-of-operator-).</span><span class="sxs-lookup"><span data-stu-id="ab110-124">The unary `&` operator is the [address-of operator](pointer-related-operators.md#address-of-operator-).</span></span>

## <a name="logical-exclusive-or-operator-"></a><span data-ttu-id="ab110-125">L’opérateur OR exclusif logique ^</span><span class="sxs-lookup"><span data-stu-id="ab110-125">Logical exclusive OR operator ^</span></span>

<span data-ttu-id="ab110-126">L’opérateur `^` calcule le OR exclusif logique, également appelé XOR logique, de ses opérandes.</span><span class="sxs-lookup"><span data-stu-id="ab110-126">The `^` operator computes the logical exclusive OR, also known as the logical XOR, of its operands.</span></span> <span data-ttu-id="ab110-127">Le résultat de `x ^ y` est `true` si `x` donne `true` et `y` donne `false`, ou `x` donne `false` et `y` donne `true`.</span><span class="sxs-lookup"><span data-stu-id="ab110-127">The result of `x ^ y` is `true` if `x` evaluates to `true` and `y` evaluates to `false`, or `x` evaluates to `false` and `y` evaluates to `true`.</span></span> <span data-ttu-id="ab110-128">Sinon, le résultat est `false`.</span><span class="sxs-lookup"><span data-stu-id="ab110-128">Otherwise, the result is `false`.</span></span> <span data-ttu-id="ab110-129">Autrement dit, pour les opérandes `bool`, l’opérateur `^` calcule le même résultat que [l’opérateur d’inégalité](equality-operators.md#inequality-operator-) `!=`.</span><span class="sxs-lookup"><span data-stu-id="ab110-129">That is, for the `bool` operands, the `^` operator computes the same result as the [inequality operator](equality-operators.md#inequality-operator-) `!=`.</span></span>

[!code-csharp-interactive[logical exclusive OR](snippets/shared/BooleanLogicalOperators.cs#Xor)]

<span data-ttu-id="ab110-130">Pour les opérandes des [types numériques intégraux](../builtin-types/integral-numeric-types.md), l' `^` opérateur calcule l' [or exclusif logique au niveau du bit](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) de ses opérandes.</span><span class="sxs-lookup"><span data-stu-id="ab110-130">For operands of the [integral numeric types](../builtin-types/integral-numeric-types.md), the `^` operator computes the [bitwise logical exclusive OR](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) of its operands.</span></span>

## <a name="logical-or-operator-"></a><span data-ttu-id="ab110-131">L’opérateur OU logique |</span><span class="sxs-lookup"><span data-stu-id="ab110-131">Logical OR operator |</span></span>

<span data-ttu-id="ab110-132">L’opérateur `|` calcule le OR logique de ses opérandes.</span><span class="sxs-lookup"><span data-stu-id="ab110-132">The `|` operator computes the logical OR of its operands.</span></span> <span data-ttu-id="ab110-133">Le résultat de `x | y` est `true` si `x` ou `y` prend la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="ab110-133">The result of `x | y` is `true` if either `x` or `y` evaluates to `true`.</span></span> <span data-ttu-id="ab110-134">Sinon, le résultat est `false`.</span><span class="sxs-lookup"><span data-stu-id="ab110-134">Otherwise, the result is `false`.</span></span>

<span data-ttu-id="ab110-135">L' `|` opérateur évalue les deux opérandes même si l’opérande de gauche est évalué à `true` , de sorte que le résultat de l’opération est `true` indépendamment de la valeur de l’opérande de droite.</span><span class="sxs-lookup"><span data-stu-id="ab110-135">The `|` operator evaluates both operands even if the left-hand operand evaluates to `true`, so that the operation result is `true` regardless of the value of the right-hand operand.</span></span>

<span data-ttu-id="ab110-136">Dans l’exemple suivant, l’opérande de partie droite de l’opérateur `|` est un appel de méthode, effectué indépendamment de la valeur de l’opérande de partie gauche :</span><span class="sxs-lookup"><span data-stu-id="ab110-136">In the following example, the right-hand operand of the `|` operator is a method call, which is performed regardless of the value of the left-hand operand:</span></span>

[!code-csharp-interactive[logical OR](snippets/shared/BooleanLogicalOperators.cs#Or)]

<span data-ttu-id="ab110-137">[L’opérateur OR logique conditionnel](#conditional-logical-or-operator-) `||` calcule également le OR logique de ses opérandes, mais n’évalue pas l’opérande de partie droite si l’opérande de partie gauche donne la valeur de `true`.</span><span class="sxs-lookup"><span data-stu-id="ab110-137">The [conditional logical OR operator](#conditional-logical-or-operator-) `||` also computes the logical OR of its operands, but doesn't evaluate the right-hand operand if the left-hand operand evaluates to `true`.</span></span>

<span data-ttu-id="ab110-138">Pour les opérandes des [types numériques intégraux](../builtin-types/integral-numeric-types.md), l' `|` opérateur calcule le or [logique au niveau du bit](bitwise-and-shift-operators.md#logical-or-operator-) de ses opérandes.</span><span class="sxs-lookup"><span data-stu-id="ab110-138">For operands of the [integral numeric types](../builtin-types/integral-numeric-types.md), the `|` operator computes the [bitwise logical OR](bitwise-and-shift-operators.md#logical-or-operator-) of its operands.</span></span>

## <a name="conditional-logical-and-operator-ampamp"></a><a name="conditional-logical-and-operator-"></a><span data-ttu-id="ab110-139">Opérateur logique AND conditionnel&amp;&amp;</span><span class="sxs-lookup"><span data-stu-id="ab110-139">Conditional logical AND operator &amp;&amp;</span></span>

<span data-ttu-id="ab110-140">L’opérateur AND logique conditionnel `&&`, également appelé opérateur AND logique de « court-circuit », calcule le AND logique de ses opérandes.</span><span class="sxs-lookup"><span data-stu-id="ab110-140">The conditional logical AND operator `&&`, also known as the "short-circuiting" logical AND operator, computes the logical AND of its operands.</span></span> <span data-ttu-id="ab110-141">Le résultat de `x && y` est `true` si `x` et `y` prennent la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="ab110-141">The result of `x && y` is `true` if both `x` and `y` evaluate to `true`.</span></span> <span data-ttu-id="ab110-142">Sinon, le résultat est `false`.</span><span class="sxs-lookup"><span data-stu-id="ab110-142">Otherwise, the result is `false`.</span></span> <span data-ttu-id="ab110-143">Si `x` donne la valeur de `false`, `y` n’est pas évalué.</span><span class="sxs-lookup"><span data-stu-id="ab110-143">If `x` evaluates to `false`, `y` is not evaluated.</span></span>

<span data-ttu-id="ab110-144">Dans l’exemple suivant, l’opérande de partie droite de l’opérateur `&&` est un appel de méthode, non effectué si l’opérande de partie gauche donne la valeur de `false` :</span><span class="sxs-lookup"><span data-stu-id="ab110-144">In the following example, the right-hand operand of the `&&` operator is a method call, which isn't performed if the left-hand operand evaluates to `false`:</span></span>

[!code-csharp-interactive[conditional logical AND](snippets/shared/BooleanLogicalOperators.cs#ConditionalAnd)]

<span data-ttu-id="ab110-145">[L’opérateur AND logique](#logical-and-operator-) `&` calcule également le AND logique de ses opérandes, mais évalue toujours les deux opérandes.</span><span class="sxs-lookup"><span data-stu-id="ab110-145">The [logical AND operator](#logical-and-operator-) `&` also computes the logical AND of its operands, but always evaluates both operands.</span></span>

## <a name="conditional-logical-or-operator-"></a><span data-ttu-id="ab110-146">L’opérateur OR logique conditionnel ||</span><span class="sxs-lookup"><span data-stu-id="ab110-146">Conditional logical OR operator ||</span></span>

<span data-ttu-id="ab110-147">L’opérateur OR logique conditionnel `||`, également appelé opérateur OR logique de « court-circuit », calcule le OR logique de ses opérandes.</span><span class="sxs-lookup"><span data-stu-id="ab110-147">The conditional logical OR operator `||`, also known as the "short-circuiting" logical OR operator, computes the logical OR of its operands.</span></span> <span data-ttu-id="ab110-148">Le résultat de `x || y` est `true` si `x` ou `y` prend la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="ab110-148">The result of `x || y` is `true` if either `x` or `y` evaluates to `true`.</span></span> <span data-ttu-id="ab110-149">Sinon, le résultat est `false`.</span><span class="sxs-lookup"><span data-stu-id="ab110-149">Otherwise, the result is `false`.</span></span> <span data-ttu-id="ab110-150">Si `x` donne la valeur de `true`, `y` n’est pas évalué.</span><span class="sxs-lookup"><span data-stu-id="ab110-150">If `x` evaluates to `true`, `y` is not evaluated.</span></span>

<span data-ttu-id="ab110-151">Dans l’exemple suivant, l’opérande de partie droite de l’opérateur `||` est un appel de méthode, non effectué si l’opérande de partie gauche donne la valeur de `true` :</span><span class="sxs-lookup"><span data-stu-id="ab110-151">In the following example, the right-hand operand of the `||` operator is a method call, which isn't performed if the left-hand operand evaluates to `true`:</span></span>

[!code-csharp-interactive[conditional logical OR](snippets/shared/BooleanLogicalOperators.cs#ConditionalOr)]

<span data-ttu-id="ab110-152">L' [opérateur OR logique](#logical-or-operator-) `|` calcule également le or logique de ses opérandes, mais évalue toujours les deux opérandes.</span><span class="sxs-lookup"><span data-stu-id="ab110-152">The [logical OR operator](#logical-or-operator-) `|` also computes the logical OR of its operands, but always evaluates both operands.</span></span>

## <a name="nullable-boolean-logical-operators"></a><span data-ttu-id="ab110-153">Les opérateurs logiques booléens Nullable</span><span class="sxs-lookup"><span data-stu-id="ab110-153">Nullable Boolean logical operators</span></span>

<span data-ttu-id="ab110-154">Pour les `bool?` opérandes, les opérateurs [ `&` (logique and)](#logical-and-operator-) et [ `|` (logique or)](#logical-or-operator-) prennent en charge la logique à trois valeurs comme suit :</span><span class="sxs-lookup"><span data-stu-id="ab110-154">For `bool?` operands, the [`&` (logical AND)](#logical-and-operator-) and [`|` (logical OR)](#logical-or-operator-) operators support the three-valued logic as follows:</span></span>

- <span data-ttu-id="ab110-155">L' `&` opérateur produit `true` uniquement si ses opérandes ont tous les deux la valeur `true` .</span><span class="sxs-lookup"><span data-stu-id="ab110-155">The `&` operator produces `true` only if both its operands evaluate to `true`.</span></span> <span data-ttu-id="ab110-156">Si ou a la `x` `y` valeur `false` , `x & y` produit `false` (même si un autre opérande a la valeur `null` ).</span><span class="sxs-lookup"><span data-stu-id="ab110-156">If either `x` or `y` evaluates to `false`, `x & y` produces `false` (even if another operand evaluates to `null`).</span></span> <span data-ttu-id="ab110-157">Sinon, le résultat de `x & y` est `null` .</span><span class="sxs-lookup"><span data-stu-id="ab110-157">Otherwise, the result of `x & y` is `null`.</span></span>

- <span data-ttu-id="ab110-158">L' `|` opérateur produit `false` uniquement si ses opérandes ont tous les deux la valeur `false` .</span><span class="sxs-lookup"><span data-stu-id="ab110-158">The `|` operator produces `false` only if both its operands evaluate to `false`.</span></span> <span data-ttu-id="ab110-159">Si ou a la `x` `y` valeur `true` , `x | y` produit `true` (même si un autre opérande a la valeur `null` ).</span><span class="sxs-lookup"><span data-stu-id="ab110-159">If either `x` or `y` evaluates to `true`, `x | y` produces `true` (even if another operand evaluates to `null`).</span></span> <span data-ttu-id="ab110-160">Sinon, le résultat de `x | y` est `null` .</span><span class="sxs-lookup"><span data-stu-id="ab110-160">Otherwise, the result of `x | y` is `null`.</span></span>

<span data-ttu-id="ab110-161">Le tableau suivant présente cette sémantique :</span><span class="sxs-lookup"><span data-stu-id="ab110-161">The following table presents that semantics:</span></span>

|<span data-ttu-id="ab110-162">x</span><span class="sxs-lookup"><span data-stu-id="ab110-162">x</span></span>|<span data-ttu-id="ab110-163">y</span><span class="sxs-lookup"><span data-stu-id="ab110-163">y</span></span>|<span data-ttu-id="ab110-164">x&y</span><span class="sxs-lookup"><span data-stu-id="ab110-164">x&y</span></span>|<span data-ttu-id="ab110-165">x&#124;y</span><span class="sxs-lookup"><span data-stu-id="ab110-165">x&#124;y</span></span>|  
|----|----|----|----|  
|<span data-ttu-id="ab110-166">true</span><span class="sxs-lookup"><span data-stu-id="ab110-166">true</span></span>|<span data-ttu-id="ab110-167">true</span><span class="sxs-lookup"><span data-stu-id="ab110-167">true</span></span>|<span data-ttu-id="ab110-168">true</span><span class="sxs-lookup"><span data-stu-id="ab110-168">true</span></span>|<span data-ttu-id="ab110-169">true</span><span class="sxs-lookup"><span data-stu-id="ab110-169">true</span></span>|  
|<span data-ttu-id="ab110-170">true</span><span class="sxs-lookup"><span data-stu-id="ab110-170">true</span></span>|<span data-ttu-id="ab110-171">false</span><span class="sxs-lookup"><span data-stu-id="ab110-171">false</span></span>|<span data-ttu-id="ab110-172">false</span><span class="sxs-lookup"><span data-stu-id="ab110-172">false</span></span>|<span data-ttu-id="ab110-173">true</span><span class="sxs-lookup"><span data-stu-id="ab110-173">true</span></span>|  
|<span data-ttu-id="ab110-174">true</span><span class="sxs-lookup"><span data-stu-id="ab110-174">true</span></span>|<span data-ttu-id="ab110-175">null</span><span class="sxs-lookup"><span data-stu-id="ab110-175">null</span></span>|<span data-ttu-id="ab110-176">null</span><span class="sxs-lookup"><span data-stu-id="ab110-176">null</span></span>|<span data-ttu-id="ab110-177">true</span><span class="sxs-lookup"><span data-stu-id="ab110-177">true</span></span>|  
|<span data-ttu-id="ab110-178">false</span><span class="sxs-lookup"><span data-stu-id="ab110-178">false</span></span>|<span data-ttu-id="ab110-179">true</span><span class="sxs-lookup"><span data-stu-id="ab110-179">true</span></span>|<span data-ttu-id="ab110-180">false</span><span class="sxs-lookup"><span data-stu-id="ab110-180">false</span></span>|<span data-ttu-id="ab110-181">true</span><span class="sxs-lookup"><span data-stu-id="ab110-181">true</span></span>|  
|<span data-ttu-id="ab110-182">false</span><span class="sxs-lookup"><span data-stu-id="ab110-182">false</span></span>|<span data-ttu-id="ab110-183">false</span><span class="sxs-lookup"><span data-stu-id="ab110-183">false</span></span>|<span data-ttu-id="ab110-184">false</span><span class="sxs-lookup"><span data-stu-id="ab110-184">false</span></span>|<span data-ttu-id="ab110-185">false</span><span class="sxs-lookup"><span data-stu-id="ab110-185">false</span></span>|  
|<span data-ttu-id="ab110-186">false</span><span class="sxs-lookup"><span data-stu-id="ab110-186">false</span></span>|<span data-ttu-id="ab110-187">null</span><span class="sxs-lookup"><span data-stu-id="ab110-187">null</span></span>|<span data-ttu-id="ab110-188">false</span><span class="sxs-lookup"><span data-stu-id="ab110-188">false</span></span>|<span data-ttu-id="ab110-189">null</span><span class="sxs-lookup"><span data-stu-id="ab110-189">null</span></span>|  
|<span data-ttu-id="ab110-190">null</span><span class="sxs-lookup"><span data-stu-id="ab110-190">null</span></span>|<span data-ttu-id="ab110-191">true</span><span class="sxs-lookup"><span data-stu-id="ab110-191">true</span></span>|<span data-ttu-id="ab110-192">null</span><span class="sxs-lookup"><span data-stu-id="ab110-192">null</span></span>|<span data-ttu-id="ab110-193">true</span><span class="sxs-lookup"><span data-stu-id="ab110-193">true</span></span>|  
|<span data-ttu-id="ab110-194">null</span><span class="sxs-lookup"><span data-stu-id="ab110-194">null</span></span>|<span data-ttu-id="ab110-195">false</span><span class="sxs-lookup"><span data-stu-id="ab110-195">false</span></span>|<span data-ttu-id="ab110-196">false</span><span class="sxs-lookup"><span data-stu-id="ab110-196">false</span></span>|<span data-ttu-id="ab110-197">null</span><span class="sxs-lookup"><span data-stu-id="ab110-197">null</span></span>|  
|<span data-ttu-id="ab110-198">null</span><span class="sxs-lookup"><span data-stu-id="ab110-198">null</span></span>|<span data-ttu-id="ab110-199">null</span><span class="sxs-lookup"><span data-stu-id="ab110-199">null</span></span>|<span data-ttu-id="ab110-200">null</span><span class="sxs-lookup"><span data-stu-id="ab110-200">null</span></span>|<span data-ttu-id="ab110-201">null</span><span class="sxs-lookup"><span data-stu-id="ab110-201">null</span></span>|  

<span data-ttu-id="ab110-202">Le comportement de ces opérateurs diffère du comportement classique des opérateurs avec des types valeur Nullable.</span><span class="sxs-lookup"><span data-stu-id="ab110-202">The behavior of those operators differs from the typical operator behavior with nullable value types.</span></span> <span data-ttu-id="ab110-203">En règle générale, un opérateur défini pour les opérandes d’un type valeur peut être également utilisé avec des opérandes du type valeur Nullable correspondant.</span><span class="sxs-lookup"><span data-stu-id="ab110-203">Typically, an operator which is defined for operands of a value type can be also used with operands of the corresponding nullable value type.</span></span> <span data-ttu-id="ab110-204">Un tel opérateur produit `null` si l’un de ses opérandes a la valeur `null` .</span><span class="sxs-lookup"><span data-stu-id="ab110-204">Such an operator produces `null` if any of its operands evaluates to `null`.</span></span> <span data-ttu-id="ab110-205">Toutefois, les `&` `|` opérateurs et peuvent produire des valeurs non null, même si l’un des opérandes a la valeur `null` .</span><span class="sxs-lookup"><span data-stu-id="ab110-205">However, the `&` and `|` operators can produce non-null even if one of the operands evaluates to `null`.</span></span> <span data-ttu-id="ab110-206">Pour plus d’informations sur le comportement de l’opérateur avec les types valeur Nullable, consultez la section [opérateurs levés](../builtin-types/nullable-value-types.md#lifted-operators) de l’article [types valeur Nullable](../builtin-types/nullable-value-types.md) .</span><span class="sxs-lookup"><span data-stu-id="ab110-206">For more information about the operator behavior with nullable value types, see the [Lifted operators](../builtin-types/nullable-value-types.md#lifted-operators) section of the [Nullable value types](../builtin-types/nullable-value-types.md) article.</span></span>

<span data-ttu-id="ab110-207">Vous pouvez également utiliser les `!` `^` opérateurs et avec des `bool?` opérandes, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="ab110-207">You can also use the `!` and `^` operators with `bool?` operands, as the following example shows:</span></span>

[!code-csharp-interactive[lifted negation and xor](snippets/shared/BooleanLogicalOperators.cs#WithNullableBoolean)]

<span data-ttu-id="ab110-208">Les opérateurs logiques conditionnels `&&` et `||` ne prennent pas en charge les `bool?` opérandes.</span><span class="sxs-lookup"><span data-stu-id="ab110-208">The conditional logical operators `&&` and `||` don't support `bool?` operands.</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="ab110-209">Assignation composée</span><span class="sxs-lookup"><span data-stu-id="ab110-209">Compound assignment</span></span>

<span data-ttu-id="ab110-210">Pour un opérateur binaire `op`, une expression d’assignation composée du formulaire</span><span class="sxs-lookup"><span data-stu-id="ab110-210">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="ab110-211">équivaut à :</span><span class="sxs-lookup"><span data-stu-id="ab110-211">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="ab110-212">sauf que `x` n’est évalué qu’une seule fois.</span><span class="sxs-lookup"><span data-stu-id="ab110-212">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="ab110-213">Les opérateurs `&`, `|` et `^` prennent en charge l’assignation composée, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="ab110-213">The `&`, `|`, and `^` operators support compound assignment, as the following example shows:</span></span>

[!code-csharp-interactive[compound assignment](snippets/shared/BooleanLogicalOperators.cs#CompoundAssignment)]

> [!NOTE]
> <span data-ttu-id="ab110-214">Les opérateurs logiques conditionnels `&&` et `||` ne prennent pas en charge l’assignation composée.</span><span class="sxs-lookup"><span data-stu-id="ab110-214">The conditional logical operators `&&` and `||` don't support compound assignment.</span></span>

## <a name="operator-precedence"></a><span data-ttu-id="ab110-215">Précédence des opérateurs</span><span class="sxs-lookup"><span data-stu-id="ab110-215">Operator precedence</span></span>

<span data-ttu-id="ab110-216">La liste suivante présente les opérateurs logiques par ordre de précédence, de la plus élevée à la plus basse :</span><span class="sxs-lookup"><span data-stu-id="ab110-216">The following list orders logical operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="ab110-217">Opérateur de négation logique `!`</span><span class="sxs-lookup"><span data-stu-id="ab110-217">Logical negation operator `!`</span></span>
- <span data-ttu-id="ab110-218">L’opérateur AND logique `&`</span><span class="sxs-lookup"><span data-stu-id="ab110-218">Logical AND operator `&`</span></span>
- <span data-ttu-id="ab110-219">Opérateur OR exclusif logique `^`</span><span class="sxs-lookup"><span data-stu-id="ab110-219">Logical exclusive OR operator `^`</span></span>
- <span data-ttu-id="ab110-220">Opérateur OR logique `|`</span><span class="sxs-lookup"><span data-stu-id="ab110-220">Logical OR operator `|`</span></span>
- <span data-ttu-id="ab110-221">Opérateur AND logique conditionnel `&&`</span><span class="sxs-lookup"><span data-stu-id="ab110-221">Conditional logical AND operator `&&`</span></span>
- <span data-ttu-id="ab110-222">Opérateur OR logique conditionnel `||`</span><span class="sxs-lookup"><span data-stu-id="ab110-222">Conditional logical OR operator `||`</span></span>

<span data-ttu-id="ab110-223">Utilisez des parenthèses, `()`, pour modifier l’ordre d’évaluation imposé par la précédence des opérateurs :</span><span class="sxs-lookup"><span data-stu-id="ab110-223">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence:</span></span>

[!code-csharp-interactive[operator precedence](snippets/shared/BooleanLogicalOperators.cs#Precedence)]

<span data-ttu-id="ab110-224">Pour obtenir la liste complète des opérateurs C# classés par niveau de priorité, consultez la section [priorité d’opérateur](index.md#operator-precedence) de l’article [opérateurs c#](index.md) .</span><span class="sxs-lookup"><span data-stu-id="ab110-224">For the complete list of C# operators ordered by precedence level, see the [Operator precedence](index.md#operator-precedence) section of the [C# operators](index.md) article.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="ab110-225">Capacité de surcharge de l’opérateur</span><span class="sxs-lookup"><span data-stu-id="ab110-225">Operator overloadability</span></span>

<span data-ttu-id="ab110-226">Un type défini par l’utilisateur peut [surcharger](operator-overloading.md) les `!` opérateurs,, `&` `|` et `^` .</span><span class="sxs-lookup"><span data-stu-id="ab110-226">A user-defined type can [overload](operator-overloading.md) the `!`, `&`, `|`, and `^` operators.</span></span> <span data-ttu-id="ab110-227">Quand un opérateur binaire est surchargé, l’opérateur d’assignation composée correspondant est aussi implicitement surchargé.</span><span class="sxs-lookup"><span data-stu-id="ab110-227">When a binary operator is overloaded, the corresponding compound assignment operator is also implicitly overloaded.</span></span> <span data-ttu-id="ab110-228">Un type défini par l’utilisateur ne peut pas surcharger explicitement un opérateur d’assignation composée.</span><span class="sxs-lookup"><span data-stu-id="ab110-228">A user-defined type cannot explicitly overload a compound assignment operator.</span></span>

<span data-ttu-id="ab110-229">Un type défini par l’utilisateur ne peut pas surcharger les opérateurs logiques conditionnels `&&` et `||`.</span><span class="sxs-lookup"><span data-stu-id="ab110-229">A user-defined type cannot overload the conditional logical operators `&&` and `||`.</span></span> <span data-ttu-id="ab110-230">Toutefois, si un type défini par l’utilisateur surcharge les [opérateurs true et false](true-false-operators.md) et l’opérateur `&` ou `|` d’une certaine manière, l’opération `&&` ou `||` peut être évaluée respectivement pour les opérandes de ce type.</span><span class="sxs-lookup"><span data-stu-id="ab110-230">However, if a user-defined type overloads the [true and false operators](true-false-operators.md) and the `&` or `|` operator in a certain way, the `&&` or `||` operation, respectively, can be evaluated for the operands of that type.</span></span> <span data-ttu-id="ab110-231">Pour plus d’informations, consultez la section [Opérateurs logiques conditionnels définis par l’utilisateur](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="ab110-231">For more information, see the [User-defined conditional logical operators](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="ab110-232">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="ab110-232">C# language specification</span></span>

<span data-ttu-id="ab110-233">Pour plus d’informations, consultez les sections suivantes de la [spécification du langage C#](~/_csharplang/spec/introduction.md) :</span><span class="sxs-lookup"><span data-stu-id="ab110-233">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="ab110-234">Opérateur de négation logique</span><span class="sxs-lookup"><span data-stu-id="ab110-234">Logical negation operator</span></span>](~/_csharplang/spec/expressions.md#logical-negation-operator)
- [<span data-ttu-id="ab110-235">Opérateurs logiques</span><span class="sxs-lookup"><span data-stu-id="ab110-235">Logical operators</span></span>](~/_csharplang/spec/expressions.md#logical-operators)
- [<span data-ttu-id="ab110-236">Opérateurs logiques conditionnels</span><span class="sxs-lookup"><span data-stu-id="ab110-236">Conditional logical operators</span></span>](~/_csharplang/spec/expressions.md#conditional-logical-operators)
- [<span data-ttu-id="ab110-237">Assignation composée</span><span class="sxs-lookup"><span data-stu-id="ab110-237">Compound assignment</span></span>](~/_csharplang/spec/expressions.md#compound-assignment)

## <a name="see-also"></a><span data-ttu-id="ab110-238">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ab110-238">See also</span></span>

- [<span data-ttu-id="ab110-239">Informations de référence sur C#</span><span class="sxs-lookup"><span data-stu-id="ab110-239">C# reference</span></span>](../index.md)
- [<span data-ttu-id="ab110-240">Opérateurs et expressions C#</span><span class="sxs-lookup"><span data-stu-id="ab110-240">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="ab110-241">Opérateurs de bits et de décalage</span><span class="sxs-lookup"><span data-stu-id="ab110-241">Bitwise and shift operators</span></span>](bitwise-and-shift-operators.md)
