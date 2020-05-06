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
ms.openlocfilehash: 5f85b88236c2e643f97453c64173a3f4f7159a35
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82794999"
---
# <a name="boolean-logical-operators-c-reference"></a><span data-ttu-id="2f52b-103">Opérateurs logiques booléens (référence C#)</span><span class="sxs-lookup"><span data-stu-id="2f52b-103">Boolean logical operators (C# reference)</span></span>

<span data-ttu-id="2f52b-104">Les opérateurs suivants effectuent des opérations logiques avec des opérandes [bool](../builtin-types/bool.md) :</span><span class="sxs-lookup"><span data-stu-id="2f52b-104">The following operators perform logical operations with [bool](../builtin-types/bool.md) operands:</span></span>

- <span data-ttu-id="2f52b-105">Opérateur unaire [ `!` (négation logique)](#logical-negation-operator-) .</span><span class="sxs-lookup"><span data-stu-id="2f52b-105">Unary [`!` (logical negation)](#logical-negation-operator-) operator.</span></span>
- <span data-ttu-id="2f52b-106">Opérateurs binaires [ `&` (and logique)](#logical-and-operator-), [ `|` (or logique)](#logical-or-operator-)et [ `^` (or exclusif logique)](#logical-exclusive-or-operator-) .</span><span class="sxs-lookup"><span data-stu-id="2f52b-106">Binary [`&` (logical AND)](#logical-and-operator-), [`|` (logical OR)](#logical-or-operator-), and [`^` (logical exclusive OR)](#logical-exclusive-or-operator-) operators.</span></span> <span data-ttu-id="2f52b-107">qui évaluent toujours les deux opérandes ;</span><span class="sxs-lookup"><span data-stu-id="2f52b-107">Those operators always evaluate both operands.</span></span>
- <span data-ttu-id="2f52b-108">Opérateurs binaires [ `&&` (conditionnels and logiques)](#conditional-logical-and-operator-) et [ `||` (opérateurs logiques conditionnels)](#conditional-logical-or-operator-) .</span><span class="sxs-lookup"><span data-stu-id="2f52b-108">Binary [`&&` (conditional logical AND)](#conditional-logical-and-operator-) and [`||` (conditional logical OR)](#conditional-logical-or-operator-) operators.</span></span> <span data-ttu-id="2f52b-109">Ces opérateurs n’évaluent l’opérande de partie droite que si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="2f52b-109">Those operators evaluate the right-hand operand only if it's necessary.</span></span>

<span data-ttu-id="2f52b-110">Pour les opérandes des [types numériques intégraux](../builtin-types/integral-numeric-types.md), `&`les `|`opérateurs, `^` et effectuent des opérations logiques au niveau du bit.</span><span class="sxs-lookup"><span data-stu-id="2f52b-110">For operands of the [integral numeric types](../builtin-types/integral-numeric-types.md), the `&`, `|`, and `^` operators perform bitwise logical operations.</span></span> <span data-ttu-id="2f52b-111">Pour plus d’informations, consultez [Opérateurs de bits et de décalage](bitwise-and-shift-operators.md).</span><span class="sxs-lookup"><span data-stu-id="2f52b-111">For more information, see [Bitwise and shift operators](bitwise-and-shift-operators.md).</span></span>

## <a name="logical-negation-operator-"></a><span data-ttu-id="2f52b-112">L’opérateur de négation logique !</span><span class="sxs-lookup"><span data-stu-id="2f52b-112">Logical negation operator !</span></span>

<span data-ttu-id="2f52b-113">L’opérateur préfixé `!` unaire calcule la négation logique de son opérande.</span><span class="sxs-lookup"><span data-stu-id="2f52b-113">The unary prefix `!` operator computes logical negation of its operand.</span></span> <span data-ttu-id="2f52b-114">Autrement dit, il produit `true` si l’opérande donne `false` et `false` si l’opérande donne `true` :</span><span class="sxs-lookup"><span data-stu-id="2f52b-114">That is, it produces `true`, if the operand evaluates to `false`, and `false`, if the operand evaluates to `true`:</span></span>

[!code-csharp-interactive[logical negation](snippets/BooleanLogicalOperators.cs#Negation)]

<span data-ttu-id="2f52b-115">À compter de C# 8,0, l’opérateur `!` postfix unaire est l' [opérateur null-indulgent avec](null-forgiving.md).</span><span class="sxs-lookup"><span data-stu-id="2f52b-115">Beginning with C# 8.0, the unary postfix `!` operator is the [null-forgiving operator](null-forgiving.md).</span></span>

## <a name="logical-and-operator-amp"></a><a name="logical-and-operator-"></a><span data-ttu-id="2f52b-116">Opérateur AND logique&amp;</span><span class="sxs-lookup"><span data-stu-id="2f52b-116">Logical AND operator &amp;</span></span>

<span data-ttu-id="2f52b-117">L’opérateur `&` calcule le AND logique de ses opérandes.</span><span class="sxs-lookup"><span data-stu-id="2f52b-117">The `&` operator computes the logical AND of its operands.</span></span> <span data-ttu-id="2f52b-118">Le résultat de `x & y` est `true` si `x` et `y` prennent la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="2f52b-118">The result of `x & y` is `true` if both `x` and `y` evaluate to `true`.</span></span> <span data-ttu-id="2f52b-119">Sinon, le résultat est `false`.</span><span class="sxs-lookup"><span data-stu-id="2f52b-119">Otherwise, the result is `false`.</span></span>

<span data-ttu-id="2f52b-120">L' `&` opérateur évalue les deux opérandes même si l’opérande de gauche est évalué à `false`, de sorte que le résultat de `false` l’opération est indépendamment de la valeur de l’opérande de droite.</span><span class="sxs-lookup"><span data-stu-id="2f52b-120">The `&` operator evaluates both operands even if the left-hand operand evaluates to `false`, so that the operation result is `false` regardless of the value of the right-hand operand.</span></span>

<span data-ttu-id="2f52b-121">Dans l’exemple suivant, l’opérande de partie droite de l’opérateur `&` est un appel de méthode, effectué indépendamment de la valeur de l’opérande de partie gauche :</span><span class="sxs-lookup"><span data-stu-id="2f52b-121">In the following example, the right-hand operand of the `&` operator is a method call, which is performed regardless of the value of the left-hand operand:</span></span>

[!code-csharp-interactive[logical AND](snippets/BooleanLogicalOperators.cs#And)]

<span data-ttu-id="2f52b-122">[L’opérateur AND logique conditionnel](#conditional-logical-and-operator-) `&&` calcule également le AND logique de ses opérandes, mais n’évalue pas l’opérande de partie droite si l’opérande de partie gauche donne la valeur de `false`.</span><span class="sxs-lookup"><span data-stu-id="2f52b-122">The [conditional logical AND operator](#conditional-logical-and-operator-) `&&` also computes the logical AND of its operands, but doesn't evaluate the right-hand operand if the left-hand operand evaluates to `false`.</span></span>

<span data-ttu-id="2f52b-123">Pour les opérandes des [types numériques intégraux](../builtin-types/integral-numeric-types.md), `&` l’opérateur calcule le [and logique au niveau du bit](bitwise-and-shift-operators.md#logical-and-operator-) de ses opérandes.</span><span class="sxs-lookup"><span data-stu-id="2f52b-123">For operands of the [integral numeric types](../builtin-types/integral-numeric-types.md), the `&` operator computes the [bitwise logical AND](bitwise-and-shift-operators.md#logical-and-operator-) of its operands.</span></span> <span data-ttu-id="2f52b-124">L’opérateur unaire `&` est [l’opérateur address-of](pointer-related-operators.md#address-of-operator-).</span><span class="sxs-lookup"><span data-stu-id="2f52b-124">The unary `&` operator is the [address-of operator](pointer-related-operators.md#address-of-operator-).</span></span>

## <a name="logical-exclusive-or-operator-"></a><span data-ttu-id="2f52b-125">L’opérateur OR exclusif logique ^</span><span class="sxs-lookup"><span data-stu-id="2f52b-125">Logical exclusive OR operator ^</span></span>

<span data-ttu-id="2f52b-126">L’opérateur `^` calcule le OR exclusif logique, également appelé XOR logique, de ses opérandes.</span><span class="sxs-lookup"><span data-stu-id="2f52b-126">The `^` operator computes the logical exclusive OR, also known as the logical XOR, of its operands.</span></span> <span data-ttu-id="2f52b-127">Le résultat de `x ^ y` est `true` si `x` donne `true` et `y` donne `false`, ou `x` donne `false` et `y` donne `true`.</span><span class="sxs-lookup"><span data-stu-id="2f52b-127">The result of `x ^ y` is `true` if `x` evaluates to `true` and `y` evaluates to `false`, or `x` evaluates to `false` and `y` evaluates to `true`.</span></span> <span data-ttu-id="2f52b-128">Sinon, le résultat est `false`.</span><span class="sxs-lookup"><span data-stu-id="2f52b-128">Otherwise, the result is `false`.</span></span> <span data-ttu-id="2f52b-129">Autrement dit, pour les opérandes `bool`, l’opérateur `^` calcule le même résultat que [l’opérateur d’inégalité](equality-operators.md#inequality-operator-) `!=`.</span><span class="sxs-lookup"><span data-stu-id="2f52b-129">That is, for the `bool` operands, the `^` operator computes the same result as the [inequality operator](equality-operators.md#inequality-operator-) `!=`.</span></span>

[!code-csharp-interactive[logical exclusive OR](snippets/BooleanLogicalOperators.cs#Xor)]

<span data-ttu-id="2f52b-130">Pour les opérandes des [types numériques intégraux](../builtin-types/integral-numeric-types.md), `^` l’opérateur calcule l' [or exclusif logique au niveau du bit](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) de ses opérandes.</span><span class="sxs-lookup"><span data-stu-id="2f52b-130">For operands of the [integral numeric types](../builtin-types/integral-numeric-types.md), the `^` operator computes the [bitwise logical exclusive OR](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) of its operands.</span></span>

## <a name="logical-or-operator-"></a><span data-ttu-id="2f52b-131">L’opérateur OU logique |</span><span class="sxs-lookup"><span data-stu-id="2f52b-131">Logical OR operator |</span></span>

<span data-ttu-id="2f52b-132">L’opérateur `|` calcule le OR logique de ses opérandes.</span><span class="sxs-lookup"><span data-stu-id="2f52b-132">The `|` operator computes the logical OR of its operands.</span></span> <span data-ttu-id="2f52b-133">Le résultat de `x | y` est `true` si `x` ou `y` prend la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="2f52b-133">The result of `x | y` is `true` if either `x` or `y` evaluates to `true`.</span></span> <span data-ttu-id="2f52b-134">Sinon, le résultat est `false`.</span><span class="sxs-lookup"><span data-stu-id="2f52b-134">Otherwise, the result is `false`.</span></span>

<span data-ttu-id="2f52b-135">L' `|` opérateur évalue les deux opérandes même si l’opérande de gauche est évalué à `true`, de sorte que le résultat de `true` l’opération est indépendamment de la valeur de l’opérande de droite.</span><span class="sxs-lookup"><span data-stu-id="2f52b-135">The `|` operator evaluates both operands even if the left-hand operand evaluates to `true`, so that the operation result is `true` regardless of the value of the right-hand operand.</span></span>

<span data-ttu-id="2f52b-136">Dans l’exemple suivant, l’opérande de partie droite de l’opérateur `|` est un appel de méthode, effectué indépendamment de la valeur de l’opérande de partie gauche :</span><span class="sxs-lookup"><span data-stu-id="2f52b-136">In the following example, the right-hand operand of the `|` operator is a method call, which is performed regardless of the value of the left-hand operand:</span></span>

[!code-csharp-interactive[logical OR](snippets/BooleanLogicalOperators.cs#Or)]

<span data-ttu-id="2f52b-137">[L’opérateur OR logique conditionnel](#conditional-logical-or-operator-) `||` calcule également le OR logique de ses opérandes, mais n’évalue pas l’opérande de partie droite si l’opérande de partie gauche donne la valeur de `true`.</span><span class="sxs-lookup"><span data-stu-id="2f52b-137">The [conditional logical OR operator](#conditional-logical-or-operator-) `||` also computes the logical OR of its operands, but doesn't evaluate the right-hand operand if the left-hand operand evaluates to `true`.</span></span>

<span data-ttu-id="2f52b-138">Pour les opérandes des [types numériques intégraux](../builtin-types/integral-numeric-types.md), `|` l’opérateur calcule le or [logique au niveau du bit](bitwise-and-shift-operators.md#logical-or-operator-) de ses opérandes.</span><span class="sxs-lookup"><span data-stu-id="2f52b-138">For operands of the [integral numeric types](../builtin-types/integral-numeric-types.md), the `|` operator computes the [bitwise logical OR](bitwise-and-shift-operators.md#logical-or-operator-) of its operands.</span></span>

## <a name="conditional-logical-and-operator-ampamp"></a><a name="conditional-logical-and-operator-"></a><span data-ttu-id="2f52b-139">Opérateur logique AND conditionnel&amp;&amp;</span><span class="sxs-lookup"><span data-stu-id="2f52b-139">Conditional logical AND operator &amp;&amp;</span></span>

<span data-ttu-id="2f52b-140">L’opérateur AND logique conditionnel `&&`, également appelé opérateur AND logique de « court-circuit », calcule le AND logique de ses opérandes.</span><span class="sxs-lookup"><span data-stu-id="2f52b-140">The conditional logical AND operator `&&`, also known as the "short-circuiting" logical AND operator, computes the logical AND of its operands.</span></span> <span data-ttu-id="2f52b-141">Le résultat de `x && y` est `true` si `x` et `y` prennent la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="2f52b-141">The result of `x && y` is `true` if both `x` and `y` evaluate to `true`.</span></span> <span data-ttu-id="2f52b-142">Sinon, le résultat est `false`.</span><span class="sxs-lookup"><span data-stu-id="2f52b-142">Otherwise, the result is `false`.</span></span> <span data-ttu-id="2f52b-143">Si `x` donne la valeur de `false`, `y` n’est pas évalué.</span><span class="sxs-lookup"><span data-stu-id="2f52b-143">If `x` evaluates to `false`, `y` is not evaluated.</span></span>

<span data-ttu-id="2f52b-144">Dans l’exemple suivant, l’opérande de partie droite de l’opérateur `&&` est un appel de méthode, non effectué si l’opérande de partie gauche donne la valeur de `false` :</span><span class="sxs-lookup"><span data-stu-id="2f52b-144">In the following example, the right-hand operand of the `&&` operator is a method call, which isn't performed if the left-hand operand evaluates to `false`:</span></span>

[!code-csharp-interactive[conditional logical AND](snippets/BooleanLogicalOperators.cs#ConditionalAnd)]

<span data-ttu-id="2f52b-145">[L’opérateur AND logique](#logical-and-operator-) `&` calcule également le AND logique de ses opérandes, mais évalue toujours les deux opérandes.</span><span class="sxs-lookup"><span data-stu-id="2f52b-145">The [logical AND operator](#logical-and-operator-) `&` also computes the logical AND of its operands, but always evaluates both operands.</span></span>

## <a name="conditional-logical-or-operator-"></a><span data-ttu-id="2f52b-146">L’opérateur OR logique conditionnel ||</span><span class="sxs-lookup"><span data-stu-id="2f52b-146">Conditional logical OR operator ||</span></span>

<span data-ttu-id="2f52b-147">L’opérateur OR logique conditionnel `||`, également appelé opérateur OR logique de « court-circuit », calcule le OR logique de ses opérandes.</span><span class="sxs-lookup"><span data-stu-id="2f52b-147">The conditional logical OR operator `||`, also known as the "short-circuiting" logical OR operator, computes the logical OR of its operands.</span></span> <span data-ttu-id="2f52b-148">Le résultat de `x || y` est `true` si `x` ou `y` prend la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="2f52b-148">The result of `x || y` is `true` if either `x` or `y` evaluates to `true`.</span></span> <span data-ttu-id="2f52b-149">Sinon, le résultat est `false`.</span><span class="sxs-lookup"><span data-stu-id="2f52b-149">Otherwise, the result is `false`.</span></span> <span data-ttu-id="2f52b-150">Si `x` donne la valeur de `true`, `y` n’est pas évalué.</span><span class="sxs-lookup"><span data-stu-id="2f52b-150">If `x` evaluates to `true`, `y` is not evaluated.</span></span>

<span data-ttu-id="2f52b-151">Dans l’exemple suivant, l’opérande de partie droite de l’opérateur `||` est un appel de méthode, non effectué si l’opérande de partie gauche donne la valeur de `true` :</span><span class="sxs-lookup"><span data-stu-id="2f52b-151">In the following example, the right-hand operand of the `||` operator is a method call, which isn't performed if the left-hand operand evaluates to `true`:</span></span>

[!code-csharp-interactive[conditional logical OR](snippets/BooleanLogicalOperators.cs#ConditionalOr)]

<span data-ttu-id="2f52b-152">`|` L' [opérateur OR logique](#logical-or-operator-) calcule également le or logique de ses opérandes, mais évalue toujours les deux opérandes.</span><span class="sxs-lookup"><span data-stu-id="2f52b-152">The [logical OR operator](#logical-or-operator-) `|` also computes the logical OR of its operands, but always evaluates both operands.</span></span>

## <a name="nullable-boolean-logical-operators"></a><span data-ttu-id="2f52b-153">Les opérateurs logiques booléens Nullable</span><span class="sxs-lookup"><span data-stu-id="2f52b-153">Nullable Boolean logical operators</span></span>

<span data-ttu-id="2f52b-154">Pour `bool?` les opérandes, `&` les `|` opérateurs et prennent en charge la logique à trois valeurs.</span><span class="sxs-lookup"><span data-stu-id="2f52b-154">For `bool?` operands, the `&` and `|` operators support the three-valued logic.</span></span> <span data-ttu-id="2f52b-155">La sémantique de ces opérateurs est définie par le tableau suivant :</span><span class="sxs-lookup"><span data-stu-id="2f52b-155">The semantics of these operators is defined by the following table:</span></span>  
  
|<span data-ttu-id="2f52b-156">x</span><span class="sxs-lookup"><span data-stu-id="2f52b-156">x</span></span>|<span data-ttu-id="2f52b-157">y</span><span class="sxs-lookup"><span data-stu-id="2f52b-157">y</span></span>|<span data-ttu-id="2f52b-158">x&y</span><span class="sxs-lookup"><span data-stu-id="2f52b-158">x&y</span></span>|<span data-ttu-id="2f52b-159">x&#124;y</span><span class="sxs-lookup"><span data-stu-id="2f52b-159">x&#124;y</span></span>|  
|----|----|----|----|  
|<span data-ttu-id="2f52b-160">true</span><span class="sxs-lookup"><span data-stu-id="2f52b-160">true</span></span>|<span data-ttu-id="2f52b-161">true</span><span class="sxs-lookup"><span data-stu-id="2f52b-161">true</span></span>|<span data-ttu-id="2f52b-162">true</span><span class="sxs-lookup"><span data-stu-id="2f52b-162">true</span></span>|<span data-ttu-id="2f52b-163">true</span><span class="sxs-lookup"><span data-stu-id="2f52b-163">true</span></span>|  
|<span data-ttu-id="2f52b-164">true</span><span class="sxs-lookup"><span data-stu-id="2f52b-164">true</span></span>|<span data-ttu-id="2f52b-165">false</span><span class="sxs-lookup"><span data-stu-id="2f52b-165">false</span></span>|<span data-ttu-id="2f52b-166">false</span><span class="sxs-lookup"><span data-stu-id="2f52b-166">false</span></span>|<span data-ttu-id="2f52b-167">true</span><span class="sxs-lookup"><span data-stu-id="2f52b-167">true</span></span>|  
|<span data-ttu-id="2f52b-168">true</span><span class="sxs-lookup"><span data-stu-id="2f52b-168">true</span></span>|<span data-ttu-id="2f52b-169">null</span><span class="sxs-lookup"><span data-stu-id="2f52b-169">null</span></span>|<span data-ttu-id="2f52b-170">null</span><span class="sxs-lookup"><span data-stu-id="2f52b-170">null</span></span>|<span data-ttu-id="2f52b-171">true</span><span class="sxs-lookup"><span data-stu-id="2f52b-171">true</span></span>|  
|<span data-ttu-id="2f52b-172">false</span><span class="sxs-lookup"><span data-stu-id="2f52b-172">false</span></span>|<span data-ttu-id="2f52b-173">true</span><span class="sxs-lookup"><span data-stu-id="2f52b-173">true</span></span>|<span data-ttu-id="2f52b-174">false</span><span class="sxs-lookup"><span data-stu-id="2f52b-174">false</span></span>|<span data-ttu-id="2f52b-175">true</span><span class="sxs-lookup"><span data-stu-id="2f52b-175">true</span></span>|  
|<span data-ttu-id="2f52b-176">false</span><span class="sxs-lookup"><span data-stu-id="2f52b-176">false</span></span>|<span data-ttu-id="2f52b-177">false</span><span class="sxs-lookup"><span data-stu-id="2f52b-177">false</span></span>|<span data-ttu-id="2f52b-178">false</span><span class="sxs-lookup"><span data-stu-id="2f52b-178">false</span></span>|<span data-ttu-id="2f52b-179">false</span><span class="sxs-lookup"><span data-stu-id="2f52b-179">false</span></span>|  
|<span data-ttu-id="2f52b-180">false</span><span class="sxs-lookup"><span data-stu-id="2f52b-180">false</span></span>|<span data-ttu-id="2f52b-181">null</span><span class="sxs-lookup"><span data-stu-id="2f52b-181">null</span></span>|<span data-ttu-id="2f52b-182">false</span><span class="sxs-lookup"><span data-stu-id="2f52b-182">false</span></span>|<span data-ttu-id="2f52b-183">null</span><span class="sxs-lookup"><span data-stu-id="2f52b-183">null</span></span>|  
|<span data-ttu-id="2f52b-184">null</span><span class="sxs-lookup"><span data-stu-id="2f52b-184">null</span></span>|<span data-ttu-id="2f52b-185">true</span><span class="sxs-lookup"><span data-stu-id="2f52b-185">true</span></span>|<span data-ttu-id="2f52b-186">null</span><span class="sxs-lookup"><span data-stu-id="2f52b-186">null</span></span>|<span data-ttu-id="2f52b-187">true</span><span class="sxs-lookup"><span data-stu-id="2f52b-187">true</span></span>|  
|<span data-ttu-id="2f52b-188">null</span><span class="sxs-lookup"><span data-stu-id="2f52b-188">null</span></span>|<span data-ttu-id="2f52b-189">false</span><span class="sxs-lookup"><span data-stu-id="2f52b-189">false</span></span>|<span data-ttu-id="2f52b-190">false</span><span class="sxs-lookup"><span data-stu-id="2f52b-190">false</span></span>|<span data-ttu-id="2f52b-191">null</span><span class="sxs-lookup"><span data-stu-id="2f52b-191">null</span></span>|  
|<span data-ttu-id="2f52b-192">null</span><span class="sxs-lookup"><span data-stu-id="2f52b-192">null</span></span>|<span data-ttu-id="2f52b-193">null</span><span class="sxs-lookup"><span data-stu-id="2f52b-193">null</span></span>|<span data-ttu-id="2f52b-194">null</span><span class="sxs-lookup"><span data-stu-id="2f52b-194">null</span></span>|<span data-ttu-id="2f52b-195">null</span><span class="sxs-lookup"><span data-stu-id="2f52b-195">null</span></span>|  

<span data-ttu-id="2f52b-196">Le comportement de ces opérateurs diffère du comportement classique des opérateurs avec des types valeur Nullable.</span><span class="sxs-lookup"><span data-stu-id="2f52b-196">The behavior of those operators differs from the typical operator behavior with nullable value types.</span></span> <span data-ttu-id="2f52b-197">En règle générale, un opérateur défini pour les opérandes d’un type valeur peut être également utilisé avec des opérandes du type valeur Nullable correspondant.</span><span class="sxs-lookup"><span data-stu-id="2f52b-197">Typically, an operator which is defined for operands of a value type can be also used with operands of the corresponding nullable value type.</span></span> <span data-ttu-id="2f52b-198">Un tel opérateur produit `null` si l’un de ses opérandes a la `null`valeur.</span><span class="sxs-lookup"><span data-stu-id="2f52b-198">Such an operator produces `null` if any of its operands evaluates to `null`.</span></span> <span data-ttu-id="2f52b-199">Toutefois, les `&` opérateurs `|` et peuvent produire des valeurs non null, même si l’un des opérandes a `null`la valeur.</span><span class="sxs-lookup"><span data-stu-id="2f52b-199">However, the `&` and `|` operators can produce non-null even if one of the operands evaluates to `null`.</span></span> <span data-ttu-id="2f52b-200">Pour plus d’informations sur le comportement de l’opérateur avec les types valeur Nullable, consultez la section [opérateurs levés](../builtin-types/nullable-value-types.md#lifted-operators) de l’article [types valeur Nullable](../builtin-types/nullable-value-types.md) .</span><span class="sxs-lookup"><span data-stu-id="2f52b-200">For more information about the operator behavior with nullable value types, see the [Lifted operators](../builtin-types/nullable-value-types.md#lifted-operators) section of the [Nullable value types](../builtin-types/nullable-value-types.md) article.</span></span>

<span data-ttu-id="2f52b-201">Vous pouvez également utiliser les `!` opérateurs `^` et avec `bool?` des opérandes, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="2f52b-201">You can also use the `!` and `^` operators with `bool?` operands, as the following example shows:</span></span>

[!code-csharp-interactive[lifted negation and xor](snippets/BooleanLogicalOperators.cs#WithNullableBoolean)]

<span data-ttu-id="2f52b-202">Les opérateurs `&&` logiques conditionnels et `||` ne prennent pas en charge `bool?` les opérandes.</span><span class="sxs-lookup"><span data-stu-id="2f52b-202">The conditional logical operators `&&` and `||` don't support `bool?` operands.</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="2f52b-203">Assignation composée</span><span class="sxs-lookup"><span data-stu-id="2f52b-203">Compound assignment</span></span>

<span data-ttu-id="2f52b-204">Pour un opérateur binaire `op`, une expression d’assignation composée du formulaire</span><span class="sxs-lookup"><span data-stu-id="2f52b-204">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="2f52b-205">équivaut à :</span><span class="sxs-lookup"><span data-stu-id="2f52b-205">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="2f52b-206">sauf que `x` n’est évalué qu’une seule fois.</span><span class="sxs-lookup"><span data-stu-id="2f52b-206">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="2f52b-207">Les opérateurs `&`, `|` et `^` prennent en charge l’assignation composée, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="2f52b-207">The `&`, `|`, and `^` operators support compound assignment, as the following example shows:</span></span>

[!code-csharp-interactive[compound assignment](snippets/BooleanLogicalOperators.cs#CompoundAssignment)]

> [!NOTE]
> <span data-ttu-id="2f52b-208">Les opérateurs logiques conditionnels `&&` et `||` ne prennent pas en charge l’assignation composée.</span><span class="sxs-lookup"><span data-stu-id="2f52b-208">The conditional logical operators `&&` and `||` don't support compound assignment.</span></span>

## <a name="operator-precedence"></a><span data-ttu-id="2f52b-209">Précédence des opérateurs</span><span class="sxs-lookup"><span data-stu-id="2f52b-209">Operator precedence</span></span>

<span data-ttu-id="2f52b-210">La liste suivante présente les opérateurs logiques par ordre de précédence, de la plus élevée à la plus basse :</span><span class="sxs-lookup"><span data-stu-id="2f52b-210">The following list orders logical operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="2f52b-211">Opérateur de négation logique `!`</span><span class="sxs-lookup"><span data-stu-id="2f52b-211">Logical negation operator `!`</span></span>
- <span data-ttu-id="2f52b-212">L’opérateur AND logique `&`</span><span class="sxs-lookup"><span data-stu-id="2f52b-212">Logical AND operator `&`</span></span>
- <span data-ttu-id="2f52b-213">Opérateur OR exclusif logique `^`</span><span class="sxs-lookup"><span data-stu-id="2f52b-213">Logical exclusive OR operator `^`</span></span>
- <span data-ttu-id="2f52b-214">Opérateur OR logique `|`</span><span class="sxs-lookup"><span data-stu-id="2f52b-214">Logical OR operator `|`</span></span>
- <span data-ttu-id="2f52b-215">Opérateur AND logique conditionnel `&&`</span><span class="sxs-lookup"><span data-stu-id="2f52b-215">Conditional logical AND operator `&&`</span></span>
- <span data-ttu-id="2f52b-216">Opérateur OR logique conditionnel `||`</span><span class="sxs-lookup"><span data-stu-id="2f52b-216">Conditional logical OR operator `||`</span></span>

<span data-ttu-id="2f52b-217">Utilisez des parenthèses, `()`, pour modifier l’ordre d’évaluation imposé par la précédence des opérateurs :</span><span class="sxs-lookup"><span data-stu-id="2f52b-217">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence:</span></span>

[!code-csharp-interactive[operator precedence](snippets/BooleanLogicalOperators.cs#Precedence)]

<span data-ttu-id="2f52b-218">Pour obtenir la liste complète des opérateurs C# classés par niveau de priorité, consultez la section [priorité d’opérateur](index.md#operator-precedence) de l’article [opérateurs c#](index.md) .</span><span class="sxs-lookup"><span data-stu-id="2f52b-218">For the complete list of C# operators ordered by precedence level, see the [Operator precedence](index.md#operator-precedence) section of the [C# operators](index.md) article.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="2f52b-219">Capacité de surcharge de l’opérateur</span><span class="sxs-lookup"><span data-stu-id="2f52b-219">Operator overloadability</span></span>

<span data-ttu-id="2f52b-220">Un type défini par l’utilisateur peut [surcharger](operator-overloading.md) les `!`opérateurs, `&` `|`, et `^` .</span><span class="sxs-lookup"><span data-stu-id="2f52b-220">A user-defined type can [overload](operator-overloading.md) the `!`, `&`, `|`, and `^` operators.</span></span> <span data-ttu-id="2f52b-221">Quand un opérateur binaire est surchargé, l’opérateur d’assignation composée correspondant est aussi implicitement surchargé.</span><span class="sxs-lookup"><span data-stu-id="2f52b-221">When a binary operator is overloaded, the corresponding compound assignment operator is also implicitly overloaded.</span></span> <span data-ttu-id="2f52b-222">Un type défini par l’utilisateur ne peut pas surcharger explicitement un opérateur d’assignation composée.</span><span class="sxs-lookup"><span data-stu-id="2f52b-222">A user-defined type cannot explicitly overload a compound assignment operator.</span></span>

<span data-ttu-id="2f52b-223">Un type défini par l’utilisateur ne peut pas surcharger les opérateurs logiques conditionnels `&&` et `||`.</span><span class="sxs-lookup"><span data-stu-id="2f52b-223">A user-defined type cannot overload the conditional logical operators `&&` and `||`.</span></span> <span data-ttu-id="2f52b-224">Toutefois, si un type défini par l’utilisateur surcharge les [opérateurs true et false](true-false-operators.md) et l’opérateur `&` ou `|` d’une certaine manière, l’opération `&&` ou `||` peut être évaluée respectivement pour les opérandes de ce type.</span><span class="sxs-lookup"><span data-stu-id="2f52b-224">However, if a user-defined type overloads the [true and false operators](true-false-operators.md) and the `&` or `|` operator in a certain way, the `&&` or `||` operation, respectively, can be evaluated for the operands of that type.</span></span> <span data-ttu-id="2f52b-225">Pour plus d’informations, consultez la section [Opérateurs logiques conditionnels définis par l’utilisateur](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="2f52b-225">For more information, see the [User-defined conditional logical operators](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="2f52b-226">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="2f52b-226">C# language specification</span></span>

<span data-ttu-id="2f52b-227">Pour plus d’informations, consultez les sections suivantes de la [spécification du langage C#](~/_csharplang/spec/introduction.md) :</span><span class="sxs-lookup"><span data-stu-id="2f52b-227">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="2f52b-228">Opérateur de négation logique</span><span class="sxs-lookup"><span data-stu-id="2f52b-228">Logical negation operator</span></span>](~/_csharplang/spec/expressions.md#logical-negation-operator)
- [<span data-ttu-id="2f52b-229">Opérateurs logiques</span><span class="sxs-lookup"><span data-stu-id="2f52b-229">Logical operators</span></span>](~/_csharplang/spec/expressions.md#logical-operators)
- [<span data-ttu-id="2f52b-230">Opérateurs logiques conditionnels</span><span class="sxs-lookup"><span data-stu-id="2f52b-230">Conditional logical operators</span></span>](~/_csharplang/spec/expressions.md#conditional-logical-operators)
- [<span data-ttu-id="2f52b-231">Assignation composée</span><span class="sxs-lookup"><span data-stu-id="2f52b-231">Compound assignment</span></span>](~/_csharplang/spec/expressions.md#compound-assignment)

## <a name="see-also"></a><span data-ttu-id="2f52b-232">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2f52b-232">See also</span></span>

- [<span data-ttu-id="2f52b-233">Référence C#</span><span class="sxs-lookup"><span data-stu-id="2f52b-233">C# reference</span></span>](../index.md)
- [<span data-ttu-id="2f52b-234">Opérateurs C#</span><span class="sxs-lookup"><span data-stu-id="2f52b-234">C# operators</span></span>](index.md)
- [<span data-ttu-id="2f52b-235">Opérateurs de bits et de décalage</span><span class="sxs-lookup"><span data-stu-id="2f52b-235">Bitwise and shift operators</span></span>](bitwise-and-shift-operators.md)
