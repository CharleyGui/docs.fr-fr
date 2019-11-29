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
ms.openlocfilehash: e4efb283c835a703ec64b6ec5995b821c995dc60
ms.sourcegitcommit: 93762e1a0dae1b5f64d82eebb7b705a6d566d839
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/27/2019
ms.locfileid: "74552489"
---
# <a name="boolean-logical-operators-c-reference"></a><span data-ttu-id="0b5f1-103">Opérateurs logiques booléens (référence C#)</span><span class="sxs-lookup"><span data-stu-id="0b5f1-103">Boolean logical operators (C# reference)</span></span>

<span data-ttu-id="0b5f1-104">Les opérateurs suivants effectuent des opérations logiques avec des opérandes [bool](../builtin-types/bool.md) :</span><span class="sxs-lookup"><span data-stu-id="0b5f1-104">The following operators perform logical operations with [bool](../builtin-types/bool.md) operands:</span></span>

- <span data-ttu-id="0b5f1-105">opérateur unaire [`!` (négation logique)](#logical-negation-operator-) ;</span><span class="sxs-lookup"><span data-stu-id="0b5f1-105">Unary [`!` (logical negation)](#logical-negation-operator-) operator.</span></span>
- <span data-ttu-id="0b5f1-106">opérateurs binaires [`&` (AND logique)](#logical-and-operator-), [`|` (OR logique)](#logical-or-operator-) et [`^` (OR exclusif logique)](#logical-exclusive-or-operator-),</span><span class="sxs-lookup"><span data-stu-id="0b5f1-106">Binary [`&` (logical AND)](#logical-and-operator-), [`|` (logical OR)](#logical-or-operator-), and [`^` (logical exclusive OR)](#logical-exclusive-or-operator-) operators.</span></span> <span data-ttu-id="0b5f1-107">qui évaluent toujours les deux opérandes ;</span><span class="sxs-lookup"><span data-stu-id="0b5f1-107">Those operators always evaluate both operands.</span></span>
- <span data-ttu-id="0b5f1-108">opérateurs binaires [`&&` (AND logique conditionnel)](#conditional-logical-and-operator-) et [`||` (OR logique conditionnel)](#conditional-logical-or-operator-),</span><span class="sxs-lookup"><span data-stu-id="0b5f1-108">Binary [`&&` (conditional logical AND)](#conditional-logical-and-operator-) and [`||` (conditional logical OR)](#conditional-logical-or-operator-) operators.</span></span> <span data-ttu-id="0b5f1-109">Ces opérateurs n’évaluent l’opérande de partie droite que si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="0b5f1-109">Those operators evaluate the right-hand operand only if it's necessary.</span></span>

<span data-ttu-id="0b5f1-110">Pour les opérandes des [types numériques intégraux](../builtin-types/integral-numeric-types.md), les opérateurs `&`, `|`et `^` effectuent des opérations logiques au niveau du bit.</span><span class="sxs-lookup"><span data-stu-id="0b5f1-110">For operands of the [integral numeric types](../builtin-types/integral-numeric-types.md), the `&`, `|`, and `^` operators perform bitwise logical operations.</span></span> <span data-ttu-id="0b5f1-111">Pour plus d’informations, consultez [Opérateurs de bits et de décalage](bitwise-and-shift-operators.md).</span><span class="sxs-lookup"><span data-stu-id="0b5f1-111">For more information, see [Bitwise and shift operators](bitwise-and-shift-operators.md).</span></span>

## <a name="logical-negation-operator-"></a><span data-ttu-id="0b5f1-112">L’opérateur de négation logique !</span><span class="sxs-lookup"><span data-stu-id="0b5f1-112">Logical negation operator !</span></span>

<span data-ttu-id="0b5f1-113">L’opérateur de préfixe unaire `!` calcule la négation logique de son opérande.</span><span class="sxs-lookup"><span data-stu-id="0b5f1-113">The unary prefix `!` operator computes logical negation of its operand.</span></span> <span data-ttu-id="0b5f1-114">Autrement dit, il produit `true` si l’opérande donne `false` et `false` si l’opérande donne `true` :</span><span class="sxs-lookup"><span data-stu-id="0b5f1-114">That is, it produces `true`, if the operand evaluates to `false`, and `false`, if the operand evaluates to `true`:</span></span>

[!code-csharp-interactive[logical negation](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#Negation)]

<span data-ttu-id="0b5f1-115">À partir C# de 8,0, l’opérateur unaire postfixé`!`est l' [opérateur null-indulgent avec](null-forgiving.md).</span><span class="sxs-lookup"><span data-stu-id="0b5f1-115">Beginning with C# 8.0, the unary postfix `!` operator is the [null-forgiving operator](null-forgiving.md).</span></span>

## <a name="logical-and-operator-"></a> <span data-ttu-id="0b5f1-116">Opérateur AND logique &amp;</span><span class="sxs-lookup"><span data-stu-id="0b5f1-116">Logical AND operator &amp;</span></span>

<span data-ttu-id="0b5f1-117">L’opérateur `&` calcule le AND logique de ses opérandes.</span><span class="sxs-lookup"><span data-stu-id="0b5f1-117">The `&` operator computes the logical AND of its operands.</span></span> <span data-ttu-id="0b5f1-118">Le résultat de `x & y` est `true` si `x` et `y` prennent la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="0b5f1-118">The result of `x & y` is `true` if both `x` and `y` evaluate to `true`.</span></span> <span data-ttu-id="0b5f1-119">Sinon, le résultat est `false`.</span><span class="sxs-lookup"><span data-stu-id="0b5f1-119">Otherwise, the result is `false`.</span></span>

<span data-ttu-id="0b5f1-120">L’opérateur `&` évalue les deux opérandes même si l’opérande de gauche a la valeur `false`, afin que le résultat de l’opération soit `false` quelle que soit la valeur de l’opérande de droite.</span><span class="sxs-lookup"><span data-stu-id="0b5f1-120">The `&` operator evaluates both operands even if the left-hand operand evaluates to `false`, so that the operation result is `false` regardless of the value of the right-hand operand.</span></span>

<span data-ttu-id="0b5f1-121">Dans l’exemple suivant, l’opérande de partie droite de l’opérateur `&` est un appel de méthode, effectué indépendamment de la valeur de l’opérande de partie gauche :</span><span class="sxs-lookup"><span data-stu-id="0b5f1-121">In the following example, the right-hand operand of the `&` operator is a method call, which is performed regardless of the value of the left-hand operand:</span></span>

[!code-csharp-interactive[logical AND](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#And)]

<span data-ttu-id="0b5f1-122">[L’opérateur AND logique conditionnel](#conditional-logical-and-operator-) `&&` calcule également le AND logique de ses opérandes, mais n’évalue pas l’opérande de partie droite si l’opérande de partie gauche donne la valeur de `false`.</span><span class="sxs-lookup"><span data-stu-id="0b5f1-122">The [conditional logical AND operator](#conditional-logical-and-operator-) `&&` also computes the logical AND of its operands, but doesn't evaluate the right-hand operand if the left-hand operand evaluates to `false`.</span></span>

<span data-ttu-id="0b5f1-123">Pour les opérandes des [types numériques intégraux](../builtin-types/integral-numeric-types.md), l’opérateur `&` calcule le [and logique au niveau du bit](bitwise-and-shift-operators.md#logical-and-operator-) de ses opérandes.</span><span class="sxs-lookup"><span data-stu-id="0b5f1-123">For operands of the [integral numeric types](../builtin-types/integral-numeric-types.md), the `&` operator computes the [bitwise logical AND](bitwise-and-shift-operators.md#logical-and-operator-) of its operands.</span></span> <span data-ttu-id="0b5f1-124">L’opérateur unaire `&` est [l’opérateur address-of](pointer-related-operators.md#address-of-operator-).</span><span class="sxs-lookup"><span data-stu-id="0b5f1-124">The unary `&` operator is the [address-of operator](pointer-related-operators.md#address-of-operator-).</span></span>

## <a name="logical-exclusive-or-operator-"></a><span data-ttu-id="0b5f1-125">L’opérateur OR exclusif logique ^</span><span class="sxs-lookup"><span data-stu-id="0b5f1-125">Logical exclusive OR operator ^</span></span>

<span data-ttu-id="0b5f1-126">L’opérateur `^` calcule le OR exclusif logique, également appelé XOR logique, de ses opérandes.</span><span class="sxs-lookup"><span data-stu-id="0b5f1-126">The `^` operator computes the logical exclusive OR, also known as the logical XOR, of its operands.</span></span> <span data-ttu-id="0b5f1-127">Le résultat de `x ^ y` est `true` si `x` donne `true` et `y` donne `false`, ou `x` donne `false` et `y` donne `true`.</span><span class="sxs-lookup"><span data-stu-id="0b5f1-127">The result of `x ^ y` is `true` if `x` evaluates to `true` and `y` evaluates to `false`, or `x` evaluates to `false` and `y` evaluates to `true`.</span></span> <span data-ttu-id="0b5f1-128">Sinon, le résultat est `false`.</span><span class="sxs-lookup"><span data-stu-id="0b5f1-128">Otherwise, the result is `false`.</span></span> <span data-ttu-id="0b5f1-129">Autrement dit, pour les opérandes `bool`, l’opérateur `^` calcule le même résultat que [l’opérateur d’inégalité](equality-operators.md#inequality-operator-) `!=`.</span><span class="sxs-lookup"><span data-stu-id="0b5f1-129">That is, for the `bool` operands, the `^` operator computes the same result as the [inequality operator](equality-operators.md#inequality-operator-) `!=`.</span></span>

[!code-csharp-interactive[logical exclusive OR](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#Xor)]

<span data-ttu-id="0b5f1-130">Pour les opérandes des [types numériques intégraux](../builtin-types/integral-numeric-types.md), l’opérateur `^` calcule l' [or exclusif logique au niveau du bit](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) de ses opérandes.</span><span class="sxs-lookup"><span data-stu-id="0b5f1-130">For operands of the [integral numeric types](../builtin-types/integral-numeric-types.md), the `^` operator computes the [bitwise logical exclusive OR](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) of its operands.</span></span>

## <a name="logical-or-operator-"></a><span data-ttu-id="0b5f1-131">L’opérateur OU logique |</span><span class="sxs-lookup"><span data-stu-id="0b5f1-131">Logical OR operator |</span></span>

<span data-ttu-id="0b5f1-132">L’opérateur `|` calcule le OR logique de ses opérandes.</span><span class="sxs-lookup"><span data-stu-id="0b5f1-132">The `|` operator computes the logical OR of its operands.</span></span> <span data-ttu-id="0b5f1-133">Le résultat de `x | y` est `true` si `x` ou `y` prend la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="0b5f1-133">The result of `x | y` is `true` if either `x` or `y` evaluates to `true`.</span></span> <span data-ttu-id="0b5f1-134">Sinon, le résultat est `false`.</span><span class="sxs-lookup"><span data-stu-id="0b5f1-134">Otherwise, the result is `false`.</span></span>

<span data-ttu-id="0b5f1-135">L’opérateur `|` évalue les deux opérandes même si l’opérande de gauche a la valeur `true`, afin que le résultat de l’opération soit `true` quelle que soit la valeur de l’opérande de droite.</span><span class="sxs-lookup"><span data-stu-id="0b5f1-135">The `|` operator evaluates both operands even if the left-hand operand evaluates to `true`, so that the operation result is `true` regardless of the value of the right-hand operand.</span></span>

<span data-ttu-id="0b5f1-136">Dans l’exemple suivant, l’opérande de partie droite de l’opérateur `|` est un appel de méthode, effectué indépendamment de la valeur de l’opérande de partie gauche :</span><span class="sxs-lookup"><span data-stu-id="0b5f1-136">In the following example, the right-hand operand of the `|` operator is a method call, which is performed regardless of the value of the left-hand operand:</span></span>

[!code-csharp-interactive[logical OR](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#Or)]

<span data-ttu-id="0b5f1-137">[L’opérateur OR logique conditionnel](#conditional-logical-or-operator-) `||` calcule également le OR logique de ses opérandes, mais n’évalue pas l’opérande de partie droite si l’opérande de partie gauche donne la valeur de `true`.</span><span class="sxs-lookup"><span data-stu-id="0b5f1-137">The [conditional logical OR operator](#conditional-logical-or-operator-) `||` also computes the logical OR of its operands, but doesn't evaluate the right-hand operand if the left-hand operand evaluates to `true`.</span></span>

<span data-ttu-id="0b5f1-138">Pour les opérandes des [types numériques intégraux](../builtin-types/integral-numeric-types.md), l’opérateur `|` calcule le or [logique au niveau du bit](bitwise-and-shift-operators.md#logical-or-operator-) de ses opérandes.</span><span class="sxs-lookup"><span data-stu-id="0b5f1-138">For operands of the [integral numeric types](../builtin-types/integral-numeric-types.md), the `|` operator computes the [bitwise logical OR](bitwise-and-shift-operators.md#logical-or-operator-) of its operands.</span></span>

## <a name="conditional-logical-and-operator-"></a> <span data-ttu-id="0b5f1-139">Opérateur AND logique conditionnel &amp;&amp;</span><span class="sxs-lookup"><span data-stu-id="0b5f1-139">Conditional logical AND operator &amp;&amp;</span></span>

<span data-ttu-id="0b5f1-140">L’opérateur AND logique conditionnel `&&`, également appelé opérateur AND logique de « court-circuit », calcule le AND logique de ses opérandes.</span><span class="sxs-lookup"><span data-stu-id="0b5f1-140">The conditional logical AND operator `&&`, also known as the "short-circuiting" logical AND operator, computes the logical AND of its operands.</span></span> <span data-ttu-id="0b5f1-141">Le résultat de `x && y` est `true` si `x` et `y` prennent la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="0b5f1-141">The result of `x && y` is `true` if both `x` and `y` evaluate to `true`.</span></span> <span data-ttu-id="0b5f1-142">Sinon, le résultat est `false`.</span><span class="sxs-lookup"><span data-stu-id="0b5f1-142">Otherwise, the result is `false`.</span></span> <span data-ttu-id="0b5f1-143">Si `x` donne la valeur de `false`, `y` n’est pas évalué.</span><span class="sxs-lookup"><span data-stu-id="0b5f1-143">If `x` evaluates to `false`, `y` is not evaluated.</span></span>

<span data-ttu-id="0b5f1-144">Dans l’exemple suivant, l’opérande de partie droite de l’opérateur `&&` est un appel de méthode, non effectué si l’opérande de partie gauche donne la valeur de `false` :</span><span class="sxs-lookup"><span data-stu-id="0b5f1-144">In the following example, the right-hand operand of the `&&` operator is a method call, which isn't performed if the left-hand operand evaluates to `false`:</span></span>

[!code-csharp-interactive[conditional logical AND](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#ConditionalAnd)]

<span data-ttu-id="0b5f1-145">[L’opérateur AND logique](#logical-and-operator-) `&` calcule également le AND logique de ses opérandes, mais évalue toujours les deux opérandes.</span><span class="sxs-lookup"><span data-stu-id="0b5f1-145">The [logical AND operator](#logical-and-operator-) `&` also computes the logical AND of its operands, but always evaluates both operands.</span></span>

## <a name="conditional-logical-or-operator-"></a><span data-ttu-id="0b5f1-146">L’opérateur OR logique conditionnel ||</span><span class="sxs-lookup"><span data-stu-id="0b5f1-146">Conditional logical OR operator ||</span></span>

<span data-ttu-id="0b5f1-147">L’opérateur OR logique conditionnel `||`, également appelé opérateur OR logique de « court-circuit », calcule le OR logique de ses opérandes.</span><span class="sxs-lookup"><span data-stu-id="0b5f1-147">The conditional logical OR operator `||`, also known as the "short-circuiting" logical OR operator, computes the logical OR of its operands.</span></span> <span data-ttu-id="0b5f1-148">Le résultat de `x || y` est `true` si `x` ou `y` prend la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="0b5f1-148">The result of `x || y` is `true` if either `x` or `y` evaluates to `true`.</span></span> <span data-ttu-id="0b5f1-149">Sinon, le résultat est `false`.</span><span class="sxs-lookup"><span data-stu-id="0b5f1-149">Otherwise, the result is `false`.</span></span> <span data-ttu-id="0b5f1-150">Si `x` donne la valeur de `true`, `y` n’est pas évalué.</span><span class="sxs-lookup"><span data-stu-id="0b5f1-150">If `x` evaluates to `true`, `y` is not evaluated.</span></span>

<span data-ttu-id="0b5f1-151">Dans l’exemple suivant, l’opérande de partie droite de l’opérateur `||` est un appel de méthode, non effectué si l’opérande de partie gauche donne la valeur de `true` :</span><span class="sxs-lookup"><span data-stu-id="0b5f1-151">In the following example, the right-hand operand of the `||` operator is a method call, which isn't performed if the left-hand operand evaluates to `true`:</span></span>

[!code-csharp-interactive[conditional logical OR](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#ConditionalOr)]

<span data-ttu-id="0b5f1-152">[L’opérateur OR logique](#logical-or-operator-) `|` calcule également le OR logique de ses opérandes, mais évalue toujours les deux opérandes.</span><span class="sxs-lookup"><span data-stu-id="0b5f1-152">The [logical OR operator](#logical-or-operator-) `|` also computes the logical OR of its operands, but always evaluates both operands.</span></span>

## <a name="nullable-boolean-logical-operators"></a><span data-ttu-id="0b5f1-153">Les opérateurs logiques booléens Nullable</span><span class="sxs-lookup"><span data-stu-id="0b5f1-153">Nullable Boolean logical operators</span></span>

<span data-ttu-id="0b5f1-154">Pour les opérandes `bool?`, les opérateurs `&` et `|` prennent en charge la logique à trois valeurs.</span><span class="sxs-lookup"><span data-stu-id="0b5f1-154">For `bool?` operands, the `&` and `|` operators support the three-valued logic.</span></span> <span data-ttu-id="0b5f1-155">La sémantique de ces opérateurs est définie par le tableau suivant :</span><span class="sxs-lookup"><span data-stu-id="0b5f1-155">The semantics of these operators is defined by the following table:</span></span>  
  
|<span data-ttu-id="0b5f1-156">x</span><span class="sxs-lookup"><span data-stu-id="0b5f1-156">x</span></span>|<span data-ttu-id="0b5f1-157">o</span><span class="sxs-lookup"><span data-stu-id="0b5f1-157">y</span></span>|<span data-ttu-id="0b5f1-158">x&y</span><span class="sxs-lookup"><span data-stu-id="0b5f1-158">x&y</span></span>|<span data-ttu-id="0b5f1-159">x&#124;y</span><span class="sxs-lookup"><span data-stu-id="0b5f1-159">x&#124;y</span></span>|  
|----|----|----|----|  
|<span data-ttu-id="0b5f1-160">true</span><span class="sxs-lookup"><span data-stu-id="0b5f1-160">true</span></span>|<span data-ttu-id="0b5f1-161">true</span><span class="sxs-lookup"><span data-stu-id="0b5f1-161">true</span></span>|<span data-ttu-id="0b5f1-162">true</span><span class="sxs-lookup"><span data-stu-id="0b5f1-162">true</span></span>|<span data-ttu-id="0b5f1-163">true</span><span class="sxs-lookup"><span data-stu-id="0b5f1-163">true</span></span>|  
|<span data-ttu-id="0b5f1-164">true</span><span class="sxs-lookup"><span data-stu-id="0b5f1-164">true</span></span>|<span data-ttu-id="0b5f1-165">false</span><span class="sxs-lookup"><span data-stu-id="0b5f1-165">false</span></span>|<span data-ttu-id="0b5f1-166">false</span><span class="sxs-lookup"><span data-stu-id="0b5f1-166">false</span></span>|<span data-ttu-id="0b5f1-167">true</span><span class="sxs-lookup"><span data-stu-id="0b5f1-167">true</span></span>|  
|<span data-ttu-id="0b5f1-168">true</span><span class="sxs-lookup"><span data-stu-id="0b5f1-168">true</span></span>|<span data-ttu-id="0b5f1-169">null</span><span class="sxs-lookup"><span data-stu-id="0b5f1-169">null</span></span>|<span data-ttu-id="0b5f1-170">null</span><span class="sxs-lookup"><span data-stu-id="0b5f1-170">null</span></span>|<span data-ttu-id="0b5f1-171">true</span><span class="sxs-lookup"><span data-stu-id="0b5f1-171">true</span></span>|  
|<span data-ttu-id="0b5f1-172">false</span><span class="sxs-lookup"><span data-stu-id="0b5f1-172">false</span></span>|<span data-ttu-id="0b5f1-173">true</span><span class="sxs-lookup"><span data-stu-id="0b5f1-173">true</span></span>|<span data-ttu-id="0b5f1-174">false</span><span class="sxs-lookup"><span data-stu-id="0b5f1-174">false</span></span>|<span data-ttu-id="0b5f1-175">true</span><span class="sxs-lookup"><span data-stu-id="0b5f1-175">true</span></span>|  
|<span data-ttu-id="0b5f1-176">false</span><span class="sxs-lookup"><span data-stu-id="0b5f1-176">false</span></span>|<span data-ttu-id="0b5f1-177">false</span><span class="sxs-lookup"><span data-stu-id="0b5f1-177">false</span></span>|<span data-ttu-id="0b5f1-178">false</span><span class="sxs-lookup"><span data-stu-id="0b5f1-178">false</span></span>|<span data-ttu-id="0b5f1-179">false</span><span class="sxs-lookup"><span data-stu-id="0b5f1-179">false</span></span>|  
|<span data-ttu-id="0b5f1-180">false</span><span class="sxs-lookup"><span data-stu-id="0b5f1-180">false</span></span>|<span data-ttu-id="0b5f1-181">null</span><span class="sxs-lookup"><span data-stu-id="0b5f1-181">null</span></span>|<span data-ttu-id="0b5f1-182">false</span><span class="sxs-lookup"><span data-stu-id="0b5f1-182">false</span></span>|<span data-ttu-id="0b5f1-183">null</span><span class="sxs-lookup"><span data-stu-id="0b5f1-183">null</span></span>|  
|<span data-ttu-id="0b5f1-184">null</span><span class="sxs-lookup"><span data-stu-id="0b5f1-184">null</span></span>|<span data-ttu-id="0b5f1-185">true</span><span class="sxs-lookup"><span data-stu-id="0b5f1-185">true</span></span>|<span data-ttu-id="0b5f1-186">null</span><span class="sxs-lookup"><span data-stu-id="0b5f1-186">null</span></span>|<span data-ttu-id="0b5f1-187">true</span><span class="sxs-lookup"><span data-stu-id="0b5f1-187">true</span></span>|  
|<span data-ttu-id="0b5f1-188">null</span><span class="sxs-lookup"><span data-stu-id="0b5f1-188">null</span></span>|<span data-ttu-id="0b5f1-189">false</span><span class="sxs-lookup"><span data-stu-id="0b5f1-189">false</span></span>|<span data-ttu-id="0b5f1-190">false</span><span class="sxs-lookup"><span data-stu-id="0b5f1-190">false</span></span>|<span data-ttu-id="0b5f1-191">null</span><span class="sxs-lookup"><span data-stu-id="0b5f1-191">null</span></span>|  
|<span data-ttu-id="0b5f1-192">null</span><span class="sxs-lookup"><span data-stu-id="0b5f1-192">null</span></span>|<span data-ttu-id="0b5f1-193">null</span><span class="sxs-lookup"><span data-stu-id="0b5f1-193">null</span></span>|<span data-ttu-id="0b5f1-194">null</span><span class="sxs-lookup"><span data-stu-id="0b5f1-194">null</span></span>|<span data-ttu-id="0b5f1-195">null</span><span class="sxs-lookup"><span data-stu-id="0b5f1-195">null</span></span>|  

<span data-ttu-id="0b5f1-196">Le comportement de ces opérateurs diffère du comportement classique des opérateurs avec des types valeur Nullable.</span><span class="sxs-lookup"><span data-stu-id="0b5f1-196">The behavior of those operators differs from the typical operator behavior with nullable value types.</span></span> <span data-ttu-id="0b5f1-197">En règle générale, un opérateur défini pour les opérandes d’un type valeur peut être également utilisé avec des opérandes du type valeur Nullable correspondant.</span><span class="sxs-lookup"><span data-stu-id="0b5f1-197">Typically, an operator which is defined for operands of a value type can be also used with operands of the corresponding nullable value type.</span></span> <span data-ttu-id="0b5f1-198">Un tel opérateur produit `null` si l’un de ses opérandes a la valeur `null`.</span><span class="sxs-lookup"><span data-stu-id="0b5f1-198">Such an operator produces `null` if any of its operands evaluates to `null`.</span></span> <span data-ttu-id="0b5f1-199">Toutefois, les opérateurs `&` et `|` peuvent produire des valeurs non null, même si l’un des opérandes prend la valeur `null`.</span><span class="sxs-lookup"><span data-stu-id="0b5f1-199">However, the `&` and `|` operators can produce non-null even if one of the operands evaluates to `null`.</span></span> <span data-ttu-id="0b5f1-200">Pour plus d’informations sur le comportement de l’opérateur avec les types valeur Nullable, consultez la section [opérateurs levés](../builtin-types/nullable-value-types.md#lifted-operators) de l’article [types valeur Nullable](../builtin-types/nullable-value-types.md) .</span><span class="sxs-lookup"><span data-stu-id="0b5f1-200">For more information about the operator behavior with nullable value types, see the [Lifted operators](../builtin-types/nullable-value-types.md#lifted-operators) section of the [Nullable value types](../builtin-types/nullable-value-types.md) article.</span></span>

<span data-ttu-id="0b5f1-201">Vous pouvez également utiliser les opérateurs `!` et `^` avec des opérandes `bool?`, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="0b5f1-201">You can also use the `!` and `^` operators with `bool?` operands, as the following example shows:</span></span>

[!code-csharp-interactive[lifted negation and xor](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#WithNullableBoolean)]

<span data-ttu-id="0b5f1-202">Les opérateurs logiques conditionnels `&&` et `||` ne prennent pas en charge les opérandes `bool?`.</span><span class="sxs-lookup"><span data-stu-id="0b5f1-202">The conditional logical operators `&&` and `||` don't support `bool?` operands.</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="0b5f1-203">Assignation composée</span><span class="sxs-lookup"><span data-stu-id="0b5f1-203">Compound assignment</span></span>

<span data-ttu-id="0b5f1-204">Pour un opérateur binaire `op`, une expression d’assignation composée du formulaire</span><span class="sxs-lookup"><span data-stu-id="0b5f1-204">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="0b5f1-205">est équivalent à</span><span class="sxs-lookup"><span data-stu-id="0b5f1-205">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="0b5f1-206">sauf que `x` n’est évalué qu’une seule fois.</span><span class="sxs-lookup"><span data-stu-id="0b5f1-206">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="0b5f1-207">Les opérateurs `&`, `|` et `^` prennent en charge l’assignation composée, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="0b5f1-207">The `&`, `|`, and `^` operators support compound assignment, as the following example shows:</span></span>

[!code-csharp-interactive[compound assignment](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#CompoundAssignment)]

<span data-ttu-id="0b5f1-208">Les opérateurs logiques conditionnels `&&` et `||` ne prennent pas en charge l’assignation composée.</span><span class="sxs-lookup"><span data-stu-id="0b5f1-208">The conditional logical operators `&&` and `||` don't support compound assignment.</span></span>

## <a name="operator-precedence"></a><span data-ttu-id="0b5f1-209">Priorité des opérateurs</span><span class="sxs-lookup"><span data-stu-id="0b5f1-209">Operator precedence</span></span>

<span data-ttu-id="0b5f1-210">La liste suivante présente les opérateurs logiques par ordre de précédence, de la plus élevée à la plus basse :</span><span class="sxs-lookup"><span data-stu-id="0b5f1-210">The following list orders logical operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="0b5f1-211">Opérateur de négation logique `!`</span><span class="sxs-lookup"><span data-stu-id="0b5f1-211">Logical negation operator `!`</span></span>
- <span data-ttu-id="0b5f1-212">L’opérateur AND logique `&`</span><span class="sxs-lookup"><span data-stu-id="0b5f1-212">Logical AND operator `&`</span></span>
- <span data-ttu-id="0b5f1-213">Opérateur OR exclusif logique `^`</span><span class="sxs-lookup"><span data-stu-id="0b5f1-213">Logical exclusive OR operator `^`</span></span>
- <span data-ttu-id="0b5f1-214">Opérateur OR logique `|`</span><span class="sxs-lookup"><span data-stu-id="0b5f1-214">Logical OR operator `|`</span></span>
- <span data-ttu-id="0b5f1-215">Opérateur AND logique conditionnel `&&`</span><span class="sxs-lookup"><span data-stu-id="0b5f1-215">Conditional logical AND operator `&&`</span></span>
- <span data-ttu-id="0b5f1-216">Opérateur OR logique conditionnel `||`</span><span class="sxs-lookup"><span data-stu-id="0b5f1-216">Conditional logical OR operator `||`</span></span>

<span data-ttu-id="0b5f1-217">Utilisez des parenthèses, `()`, pour modifier l’ordre d’évaluation imposé par la précédence des opérateurs :</span><span class="sxs-lookup"><span data-stu-id="0b5f1-217">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence:</span></span>

[!code-csharp-interactive[operator precedence](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#Precedence)]

<span data-ttu-id="0b5f1-218">Pour obtenir la liste complète C# des opérateurs classés par niveau de priorité, consultez la section priorité d' [ C# ](index.md) [opérateur](index.md#operator-precedence) de l’article opérateurs.</span><span class="sxs-lookup"><span data-stu-id="0b5f1-218">For the complete list of C# operators ordered by precedence level, see the [Operator precedence](index.md#operator-precedence) section of the [C# operators](index.md) article.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="0b5f1-219">Capacité de surcharge de l’opérateur</span><span class="sxs-lookup"><span data-stu-id="0b5f1-219">Operator overloadability</span></span>

<span data-ttu-id="0b5f1-220">Un type défini par l’utilisateur peut [surcharger](operator-overloading.md) les opérateurs `!`, `&`, `|` et `^`.</span><span class="sxs-lookup"><span data-stu-id="0b5f1-220">A user-defined type can [overload](operator-overloading.md) the `!`, `&`, `|`, and `^` operators.</span></span> <span data-ttu-id="0b5f1-221">Quand un opérateur binaire est surchargé, l’opérateur d’assignation composée correspondant est aussi implicitement surchargé.</span><span class="sxs-lookup"><span data-stu-id="0b5f1-221">When a binary operator is overloaded, the corresponding compound assignment operator is also implicitly overloaded.</span></span> <span data-ttu-id="0b5f1-222">Un type défini par l’utilisateur ne peut pas surcharger explicitement un opérateur d’assignation composée.</span><span class="sxs-lookup"><span data-stu-id="0b5f1-222">A user-defined type cannot explicitly overload a compound assignment operator.</span></span>

<span data-ttu-id="0b5f1-223">Un type défini par l’utilisateur ne peut pas surcharger les opérateurs logiques conditionnels `&&` et `||`.</span><span class="sxs-lookup"><span data-stu-id="0b5f1-223">A user-defined type cannot overload the conditional logical operators `&&` and `||`.</span></span> <span data-ttu-id="0b5f1-224">Toutefois, si un type défini par l’utilisateur surcharge les [opérateurs true et false](true-false-operators.md) et l’opérateur `&` ou `|` d’une certaine manière, l’opération `&&` ou `||` peut être évaluée respectivement pour les opérandes de ce type.</span><span class="sxs-lookup"><span data-stu-id="0b5f1-224">However, if a user-defined type overloads the [true and false operators](true-false-operators.md) and the `&` or `|` operator in a certain way, the `&&` or `||` operation, respectively, can be evaluated for the operands of that type.</span></span> <span data-ttu-id="0b5f1-225">Pour plus d’informations, consultez la section [Opérateurs logiques conditionnels définis par l’utilisateur](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="0b5f1-225">For more information, see the [User-defined conditional logical operators](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="0b5f1-226">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="0b5f1-226">C# language specification</span></span>

<span data-ttu-id="0b5f1-227">Pour plus d’informations, consultez les sections suivantes de la [spécification du langage C#](~/_csharplang/spec/introduction.md) :</span><span class="sxs-lookup"><span data-stu-id="0b5f1-227">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="0b5f1-228">Opérateur de négation logique</span><span class="sxs-lookup"><span data-stu-id="0b5f1-228">Logical negation operator</span></span>](~/_csharplang/spec/expressions.md#logical-negation-operator)
- [<span data-ttu-id="0b5f1-229">Opérateurs logiques</span><span class="sxs-lookup"><span data-stu-id="0b5f1-229">Logical operators</span></span>](~/_csharplang/spec/expressions.md#logical-operators)
- [<span data-ttu-id="0b5f1-230">Opérateurs logiques conditionnels</span><span class="sxs-lookup"><span data-stu-id="0b5f1-230">Conditional logical operators</span></span>](~/_csharplang/spec/expressions.md#conditional-logical-operators)
- [<span data-ttu-id="0b5f1-231">Assignation composée</span><span class="sxs-lookup"><span data-stu-id="0b5f1-231">Compound assignment</span></span>](~/_csharplang/spec/expressions.md#compound-assignment)

## <a name="see-also"></a><span data-ttu-id="0b5f1-232">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0b5f1-232">See also</span></span>

- [<span data-ttu-id="0b5f1-233">Informations de référence sur C#</span><span class="sxs-lookup"><span data-stu-id="0b5f1-233">C# reference</span></span>](../index.md)
- [<span data-ttu-id="0b5f1-234">Opérateurs C#</span><span class="sxs-lookup"><span data-stu-id="0b5f1-234">C# operators</span></span>](index.md)
- [<span data-ttu-id="0b5f1-235">Opérateurs de bits et de décalage</span><span class="sxs-lookup"><span data-stu-id="0b5f1-235">Bitwise and shift operators</span></span>](bitwise-and-shift-operators.md)
