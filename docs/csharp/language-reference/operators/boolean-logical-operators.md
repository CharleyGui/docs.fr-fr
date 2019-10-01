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
ms.openlocfilehash: cc25d4bfd444dc0acb30fc1c6e6c3c9918af537c
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698684"
---
# <a name="boolean-logical-operators-c-reference"></a><span data-ttu-id="7f767-103">Opérateurs logiques booléens (référence C#)</span><span class="sxs-lookup"><span data-stu-id="7f767-103">Boolean logical operators (C# reference)</span></span>

<span data-ttu-id="7f767-104">Les opérateurs suivants effectuent des opérations logiques avec les opérandes [booléens](../keywords/bool.md) :</span><span class="sxs-lookup"><span data-stu-id="7f767-104">The following operators perform logical operations with the [bool](../keywords/bool.md) operands:</span></span>

- <span data-ttu-id="7f767-105">opérateur unaire [`!` (négation logique)](#logical-negation-operator-) ;</span><span class="sxs-lookup"><span data-stu-id="7f767-105">Unary [`!` (logical negation)](#logical-negation-operator-) operator.</span></span>
- <span data-ttu-id="7f767-106">opérateurs binaires [`&` (AND logique)](#logical-and-operator-), [`|` (OR logique)](#logical-or-operator-) et [`^` (OR exclusif logique)](#logical-exclusive-or-operator-),</span><span class="sxs-lookup"><span data-stu-id="7f767-106">Binary [`&` (logical AND)](#logical-and-operator-), [`|` (logical OR)](#logical-or-operator-), and [`^` (logical exclusive OR)](#logical-exclusive-or-operator-) operators.</span></span> <span data-ttu-id="7f767-107">qui évaluent toujours les deux opérandes ;</span><span class="sxs-lookup"><span data-stu-id="7f767-107">Those operators always evaluate both operands.</span></span>
- <span data-ttu-id="7f767-108">opérateurs binaires [`&&` (AND logique conditionnel)](#conditional-logical-and-operator-) et [`||` (OR logique conditionnel)](#conditional-logical-or-operator-),</span><span class="sxs-lookup"><span data-stu-id="7f767-108">Binary [`&&` (conditional logical AND)](#conditional-logical-and-operator-) and [`||` (conditional logical OR)](#conditional-logical-or-operator-) operators.</span></span> <span data-ttu-id="7f767-109">Ces opérateurs n’évaluent l’opérande de partie droite que si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="7f767-109">Those operators evaluate the right-hand operand only if it's necessary.</span></span>

<span data-ttu-id="7f767-110">En ce qui concerne les opérandes de type [intégral](../builtin-types/integral-numeric-types.md), les opérateurs `&`, `|` et `^` effectuent des opérations logiques au niveau du bit.</span><span class="sxs-lookup"><span data-stu-id="7f767-110">For the operands of the [integral](../builtin-types/integral-numeric-types.md) types, the `&`, `|`, and `^` operators perform bitwise logical operations.</span></span> <span data-ttu-id="7f767-111">Pour plus d’informations, consultez [Opérateurs de bits et de décalage](bitwise-and-shift-operators.md).</span><span class="sxs-lookup"><span data-stu-id="7f767-111">For more information, see [Bitwise and shift operators](bitwise-and-shift-operators.md).</span></span>

## <a name="logical-negation-operator-"></a><span data-ttu-id="7f767-112">L’opérateur de négation logique !</span><span class="sxs-lookup"><span data-stu-id="7f767-112">Logical negation operator !</span></span>

<span data-ttu-id="7f767-113">L’opérateur `!` calcule la négation logique de son opérande.</span><span class="sxs-lookup"><span data-stu-id="7f767-113">The `!` operator computes logical negation of its operand.</span></span> <span data-ttu-id="7f767-114">Autrement dit, il produit `true` si l’opérande donne `false` et `false` si l’opérande donne `true` :</span><span class="sxs-lookup"><span data-stu-id="7f767-114">That is, it produces `true`, if the operand evaluates to `false`, and `false`, if the operand evaluates to `true`:</span></span>

[!code-csharp-interactive[logical negation](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#Negation)]

<span data-ttu-id="7f767-115">À partir C# de 8,0, l’opérateur unaire postfixé `!` est un opérateur null-indulgent avec.</span><span class="sxs-lookup"><span data-stu-id="7f767-115">Starting with C# 8.0, the unary postfix `!` operator is a null-forgiving operator.</span></span> <span data-ttu-id="7f767-116">Dans un contexte d’annotation Nullable activé, vous l’utilisez pour déclarer que l’expression `x` d’un type référence Nullable n’a pas la valeur NULL : `x!`.</span><span class="sxs-lookup"><span data-stu-id="7f767-116">In an enabled nullable annotation context, you use it to declare that expression `x` of a nullable reference type isn't null: `x!`.</span></span> <span data-ttu-id="7f767-117">Pour plus d’informations, consultez [types de référence Nullable](../../nullable-references.md).</span><span class="sxs-lookup"><span data-stu-id="7f767-117">For more information, see [Nullable reference types](../../nullable-references.md).</span></span>

## <a name="logical-and-operator-"></a><span data-ttu-id="7f767-118">Opérateur ET logique &amp;</span><span class="sxs-lookup"><span data-stu-id="7f767-118">Logical AND operator &amp;</span></span>

<span data-ttu-id="7f767-119">L’opérateur `&` calcule le AND logique de ses opérandes.</span><span class="sxs-lookup"><span data-stu-id="7f767-119">The `&` operator computes the logical AND of its operands.</span></span> <span data-ttu-id="7f767-120">Le résultat de `x & y` est `true` si `x` et `y` prennent la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="7f767-120">The result of `x & y` is `true` if both `x` and `y` evaluate to `true`.</span></span> <span data-ttu-id="7f767-121">Sinon, le résultat est `false`.</span><span class="sxs-lookup"><span data-stu-id="7f767-121">Otherwise, the result is `false`.</span></span>

<span data-ttu-id="7f767-122">L’opérateur `&` évalue les deux opérandes, même si l’opérande de partie gauche donne la valeur de `false`. Le résultat doit donc être `false` quelle que soit la valeur de l’opérande de partie droite.</span><span class="sxs-lookup"><span data-stu-id="7f767-122">The `&` operator evaluates both operands even if the left-hand operand evaluates to `false`, so that the result must be `false` regardless of the value of the right-hand operand.</span></span>

<span data-ttu-id="7f767-123">Dans l’exemple suivant, l’opérande de partie droite de l’opérateur `&` est un appel de méthode, effectué indépendamment de la valeur de l’opérande de partie gauche :</span><span class="sxs-lookup"><span data-stu-id="7f767-123">In the following example, the right-hand operand of the `&` operator is a method call, which is performed regardless of the value of the left-hand operand:</span></span>

[!code-csharp-interactive[logical AND](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#And)]

<span data-ttu-id="7f767-124">[L’opérateur AND logique conditionnel](#conditional-logical-and-operator-) `&&` calcule également le AND logique de ses opérandes, mais n’évalue pas l’opérande de partie droite si l’opérande de partie gauche donne la valeur de `false`.</span><span class="sxs-lookup"><span data-stu-id="7f767-124">The [conditional logical AND operator](#conditional-logical-and-operator-) `&&` also computes the logical AND of its operands, but doesn't evaluate the right-hand operand if the left-hand operand evaluates to `false`.</span></span>

<span data-ttu-id="7f767-125">Dans le cas des opérandes de type intégral, l’opérateur `&` calcule le [AND logique au niveau du bit](bitwise-and-shift-operators.md#logical-and-operator-) de ses opérandes.</span><span class="sxs-lookup"><span data-stu-id="7f767-125">For the operands of the integral types, the `&` operator computes the [bitwise logical AND](bitwise-and-shift-operators.md#logical-and-operator-) of its operands.</span></span> <span data-ttu-id="7f767-126">L’opérateur unaire `&` est [l’opérateur address-of](pointer-related-operators.md#address-of-operator-).</span><span class="sxs-lookup"><span data-stu-id="7f767-126">The unary `&` operator is the [address-of operator](pointer-related-operators.md#address-of-operator-).</span></span>

## <a name="logical-exclusive-or-operator-"></a><span data-ttu-id="7f767-127">L’opérateur OR exclusif logique ^</span><span class="sxs-lookup"><span data-stu-id="7f767-127">Logical exclusive OR operator ^</span></span>

<span data-ttu-id="7f767-128">L’opérateur `^` calcule le OR exclusif logique, également appelé XOR logique, de ses opérandes.</span><span class="sxs-lookup"><span data-stu-id="7f767-128">The `^` operator computes the logical exclusive OR, also known as the logical XOR, of its operands.</span></span> <span data-ttu-id="7f767-129">Le résultat de `x ^ y` est `true` si `x` donne `true` et `y` donne `false`, ou `x` donne `false` et `y` donne `true`.</span><span class="sxs-lookup"><span data-stu-id="7f767-129">The result of `x ^ y` is `true` if `x` evaluates to `true` and `y` evaluates to `false`, or `x` evaluates to `false` and `y` evaluates to `true`.</span></span> <span data-ttu-id="7f767-130">Sinon, le résultat est `false`.</span><span class="sxs-lookup"><span data-stu-id="7f767-130">Otherwise, the result is `false`.</span></span> <span data-ttu-id="7f767-131">Autrement dit, pour les opérandes `bool`, l’opérateur `^` calcule le même résultat que [l’opérateur d’inégalité](equality-operators.md#inequality-operator-) `!=`.</span><span class="sxs-lookup"><span data-stu-id="7f767-131">That is, for the `bool` operands, the `^` operator computes the same result as the [inequality operator](equality-operators.md#inequality-operator-) `!=`.</span></span>

[!code-csharp-interactive[logical exclusive OR](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#Xor)]

<span data-ttu-id="7f767-132">Dans le cas des opérandes de type intégral, l’opérateur `^` calcule le [OR exclusif logique au niveau du bit](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) de ses opérandes.</span><span class="sxs-lookup"><span data-stu-id="7f767-132">For the operands of the integral types, the `^` operator computes the [bitwise logical exclusive OR](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) of its operands.</span></span>

## <a name="logical-or-operator-"></a><span data-ttu-id="7f767-133">L’opérateur OU logique |</span><span class="sxs-lookup"><span data-stu-id="7f767-133">Logical OR operator |</span></span>

<span data-ttu-id="7f767-134">L’opérateur `|` calcule le OR logique de ses opérandes.</span><span class="sxs-lookup"><span data-stu-id="7f767-134">The `|` operator computes the logical OR of its operands.</span></span> <span data-ttu-id="7f767-135">Le résultat de `x | y` est `true` si `x` ou `y` prend la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="7f767-135">The result of `x | y` is `true` if either `x` or `y` evaluates to `true`.</span></span> <span data-ttu-id="7f767-136">Sinon, le résultat est `false`.</span><span class="sxs-lookup"><span data-stu-id="7f767-136">Otherwise, the result is `false`.</span></span>

<span data-ttu-id="7f767-137">L’opérateur `|` évalue les deux opérandes, même si l’opérande de partie gauche donne la valeur de `true`. Le résultat doit donc être `true` quelle que soit la valeur de l’opérande de partie droite.</span><span class="sxs-lookup"><span data-stu-id="7f767-137">The `|` operator evaluates both operands even if the left-hand operand evaluates to `true`, so that the result must be `true` regardless of the value of the right-hand operand.</span></span>

<span data-ttu-id="7f767-138">Dans l’exemple suivant, l’opérande de partie droite de l’opérateur `|` est un appel de méthode, effectué indépendamment de la valeur de l’opérande de partie gauche :</span><span class="sxs-lookup"><span data-stu-id="7f767-138">In the following example, the right-hand operand of the `|` operator is a method call, which is performed regardless of the value of the left-hand operand:</span></span>

[!code-csharp-interactive[logical OR](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#Or)]

<span data-ttu-id="7f767-139">[L’opérateur OR logique conditionnel](#conditional-logical-or-operator-) `||` calcule également le OR logique de ses opérandes, mais n’évalue pas l’opérande de partie droite si l’opérande de partie gauche donne la valeur de `true`.</span><span class="sxs-lookup"><span data-stu-id="7f767-139">The [conditional logical OR operator](#conditional-logical-or-operator-) `||` also computes the logical OR of its operands, but doesn't evaluate the right-hand operand if the left-hand operand evaluates to `true`.</span></span>

<span data-ttu-id="7f767-140">Dans le cas des opérandes de type intégral, l’opérateur `|` calcule le [OR logique au niveau du bit](bitwise-and-shift-operators.md#logical-or-operator-) de ses opérandes.</span><span class="sxs-lookup"><span data-stu-id="7f767-140">For the operands of the integral types, the `|` operator computes the [bitwise logical OR](bitwise-and-shift-operators.md#logical-or-operator-) of its operands.</span></span>

## <a name="conditional-logical-and-operator-"></a> <span data-ttu-id="7f767-141">Opérateur AND logique conditionnel &amp;&amp;</span><span class="sxs-lookup"><span data-stu-id="7f767-141">Conditional logical AND operator &amp;&amp;</span></span>

<span data-ttu-id="7f767-142">L’opérateur AND logique conditionnel `&&`, également appelé opérateur AND logique de « court-circuit », calcule le AND logique de ses opérandes.</span><span class="sxs-lookup"><span data-stu-id="7f767-142">The conditional logical AND operator `&&`, also known as the "short-circuiting" logical AND operator, computes the logical AND of its operands.</span></span> <span data-ttu-id="7f767-143">Le résultat de `x && y` est `true` si `x` et `y` prennent la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="7f767-143">The result of `x && y` is `true` if both `x` and `y` evaluate to `true`.</span></span> <span data-ttu-id="7f767-144">Sinon, le résultat est `false`.</span><span class="sxs-lookup"><span data-stu-id="7f767-144">Otherwise, the result is `false`.</span></span> <span data-ttu-id="7f767-145">Si `x` donne la valeur de `false`, `y` n’est pas évalué.</span><span class="sxs-lookup"><span data-stu-id="7f767-145">If `x` evaluates to `false`, `y` is not evaluated.</span></span>

<span data-ttu-id="7f767-146">Dans l’exemple suivant, l’opérande de partie droite de l’opérateur `&&` est un appel de méthode, non effectué si l’opérande de partie gauche donne la valeur de `false` :</span><span class="sxs-lookup"><span data-stu-id="7f767-146">In the following example, the right-hand operand of the `&&` operator is a method call, which isn't performed if the left-hand operand evaluates to `false`:</span></span>

[!code-csharp-interactive[conditional logical AND](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#ConditionalAnd)]

<span data-ttu-id="7f767-147">[L’opérateur AND logique](#logical-and-operator-) `&` calcule également le AND logique de ses opérandes, mais évalue toujours les deux opérandes.</span><span class="sxs-lookup"><span data-stu-id="7f767-147">The [logical AND operator](#logical-and-operator-) `&` also computes the logical AND of its operands, but always evaluates both operands.</span></span>

## <a name="conditional-logical-or-operator-"></a><span data-ttu-id="7f767-148">L’opérateur OR logique conditionnel ||</span><span class="sxs-lookup"><span data-stu-id="7f767-148">Conditional logical OR operator ||</span></span>

<span data-ttu-id="7f767-149">L’opérateur OR logique conditionnel `||`, également appelé opérateur OR logique de « court-circuit », calcule le OR logique de ses opérandes.</span><span class="sxs-lookup"><span data-stu-id="7f767-149">The conditional logical OR operator `||`, also known as the "short-circuiting" logical OR operator, computes the logical OR of its operands.</span></span> <span data-ttu-id="7f767-150">Le résultat de `x || y` est `true` si `x` ou `y` prend la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="7f767-150">The result of `x || y` is `true` if either `x` or `y` evaluates to `true`.</span></span> <span data-ttu-id="7f767-151">Sinon, le résultat est `false`.</span><span class="sxs-lookup"><span data-stu-id="7f767-151">Otherwise, the result is `false`.</span></span> <span data-ttu-id="7f767-152">Si `x` donne la valeur de `true`, `y` n’est pas évalué.</span><span class="sxs-lookup"><span data-stu-id="7f767-152">If `x` evaluates to `true`, `y` is not evaluated.</span></span>

<span data-ttu-id="7f767-153">Dans l’exemple suivant, l’opérande de partie droite de l’opérateur `||` est un appel de méthode, non effectué si l’opérande de partie gauche donne la valeur de `true` :</span><span class="sxs-lookup"><span data-stu-id="7f767-153">In the following example, the right-hand operand of the `||` operator is a method call, which isn't performed if the left-hand operand evaluates to `true`:</span></span>

[!code-csharp-interactive[conditional logical OR](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#ConditionalOr)]

<span data-ttu-id="7f767-154">[L’opérateur OR logique](#logical-or-operator-) `|` calcule également le OR logique de ses opérandes, mais évalue toujours les deux opérandes.</span><span class="sxs-lookup"><span data-stu-id="7f767-154">The [logical OR operator](#logical-or-operator-) `|` also computes the logical OR of its operands, but always evaluates both operands.</span></span>

## <a name="nullable-boolean-logical-operators"></a><span data-ttu-id="7f767-155">Les opérateurs logiques booléens Nullable</span><span class="sxs-lookup"><span data-stu-id="7f767-155">Nullable Boolean logical operators</span></span>

<span data-ttu-id="7f767-156">Dans le cas des opérandes `bool?`, les opérateurs `&` et `|` prennent en charge la logique à trois valeurs.</span><span class="sxs-lookup"><span data-stu-id="7f767-156">For the `bool?` operands, the `&` and `|` operators support the three-valued logic.</span></span> <span data-ttu-id="7f767-157">La sémantique de ces opérateurs est définie par le tableau suivant :</span><span class="sxs-lookup"><span data-stu-id="7f767-157">The semantics of these operators is defined by the following table:</span></span>  
  
|<span data-ttu-id="7f767-158">x</span><span class="sxs-lookup"><span data-stu-id="7f767-158">x</span></span>|<span data-ttu-id="7f767-159">o</span><span class="sxs-lookup"><span data-stu-id="7f767-159">y</span></span>|<span data-ttu-id="7f767-160">x&y</span><span class="sxs-lookup"><span data-stu-id="7f767-160">x&y</span></span>|<span data-ttu-id="7f767-161">x&#124;y</span><span class="sxs-lookup"><span data-stu-id="7f767-161">x&#124;y</span></span>|  
|----|----|----|----|  
|<span data-ttu-id="7f767-162">true</span><span class="sxs-lookup"><span data-stu-id="7f767-162">true</span></span>|<span data-ttu-id="7f767-163">true</span><span class="sxs-lookup"><span data-stu-id="7f767-163">true</span></span>|<span data-ttu-id="7f767-164">true</span><span class="sxs-lookup"><span data-stu-id="7f767-164">true</span></span>|<span data-ttu-id="7f767-165">true</span><span class="sxs-lookup"><span data-stu-id="7f767-165">true</span></span>|  
|<span data-ttu-id="7f767-166">true</span><span class="sxs-lookup"><span data-stu-id="7f767-166">true</span></span>|<span data-ttu-id="7f767-167">false</span><span class="sxs-lookup"><span data-stu-id="7f767-167">false</span></span>|<span data-ttu-id="7f767-168">false</span><span class="sxs-lookup"><span data-stu-id="7f767-168">false</span></span>|<span data-ttu-id="7f767-169">true</span><span class="sxs-lookup"><span data-stu-id="7f767-169">true</span></span>|  
|<span data-ttu-id="7f767-170">true</span><span class="sxs-lookup"><span data-stu-id="7f767-170">true</span></span>|<span data-ttu-id="7f767-171">Null</span><span class="sxs-lookup"><span data-stu-id="7f767-171">null</span></span>|<span data-ttu-id="7f767-172">Null</span><span class="sxs-lookup"><span data-stu-id="7f767-172">null</span></span>|<span data-ttu-id="7f767-173">true</span><span class="sxs-lookup"><span data-stu-id="7f767-173">true</span></span>|  
|<span data-ttu-id="7f767-174">false</span><span class="sxs-lookup"><span data-stu-id="7f767-174">false</span></span>|<span data-ttu-id="7f767-175">true</span><span class="sxs-lookup"><span data-stu-id="7f767-175">true</span></span>|<span data-ttu-id="7f767-176">false</span><span class="sxs-lookup"><span data-stu-id="7f767-176">false</span></span>|<span data-ttu-id="7f767-177">true</span><span class="sxs-lookup"><span data-stu-id="7f767-177">true</span></span>|  
|<span data-ttu-id="7f767-178">false</span><span class="sxs-lookup"><span data-stu-id="7f767-178">false</span></span>|<span data-ttu-id="7f767-179">false</span><span class="sxs-lookup"><span data-stu-id="7f767-179">false</span></span>|<span data-ttu-id="7f767-180">false</span><span class="sxs-lookup"><span data-stu-id="7f767-180">false</span></span>|<span data-ttu-id="7f767-181">false</span><span class="sxs-lookup"><span data-stu-id="7f767-181">false</span></span>|  
|<span data-ttu-id="7f767-182">false</span><span class="sxs-lookup"><span data-stu-id="7f767-182">false</span></span>|<span data-ttu-id="7f767-183">Null</span><span class="sxs-lookup"><span data-stu-id="7f767-183">null</span></span>|<span data-ttu-id="7f767-184">false</span><span class="sxs-lookup"><span data-stu-id="7f767-184">false</span></span>|<span data-ttu-id="7f767-185">null</span><span class="sxs-lookup"><span data-stu-id="7f767-185">null</span></span>|  
|<span data-ttu-id="7f767-186">Null</span><span class="sxs-lookup"><span data-stu-id="7f767-186">null</span></span>|<span data-ttu-id="7f767-187">true</span><span class="sxs-lookup"><span data-stu-id="7f767-187">true</span></span>|<span data-ttu-id="7f767-188">Null</span><span class="sxs-lookup"><span data-stu-id="7f767-188">null</span></span>|<span data-ttu-id="7f767-189">true</span><span class="sxs-lookup"><span data-stu-id="7f767-189">true</span></span>|  
|<span data-ttu-id="7f767-190">Null</span><span class="sxs-lookup"><span data-stu-id="7f767-190">null</span></span>|<span data-ttu-id="7f767-191">false</span><span class="sxs-lookup"><span data-stu-id="7f767-191">false</span></span>|<span data-ttu-id="7f767-192">false</span><span class="sxs-lookup"><span data-stu-id="7f767-192">false</span></span>|<span data-ttu-id="7f767-193">null</span><span class="sxs-lookup"><span data-stu-id="7f767-193">null</span></span>|  
|<span data-ttu-id="7f767-194">Null</span><span class="sxs-lookup"><span data-stu-id="7f767-194">null</span></span>|<span data-ttu-id="7f767-195">Null</span><span class="sxs-lookup"><span data-stu-id="7f767-195">null</span></span>|<span data-ttu-id="7f767-196">Null</span><span class="sxs-lookup"><span data-stu-id="7f767-196">null</span></span>|<span data-ttu-id="7f767-197">Null</span><span class="sxs-lookup"><span data-stu-id="7f767-197">null</span></span>|  

<span data-ttu-id="7f767-198">Le comportement de ces opérateurs diffère du comportement classique des opérateurs avec des types valeur Nullable.</span><span class="sxs-lookup"><span data-stu-id="7f767-198">The behavior of those operators differs from the typical operator behavior with nullable value types.</span></span> <span data-ttu-id="7f767-199">En règle générale, un opérateur défini pour les opérandes d’un type valeur peut être également utilisé avec des opérandes du type valeur Nullable correspondant.</span><span class="sxs-lookup"><span data-stu-id="7f767-199">Typically, an operator which is defined for operands of a value type can be also used with operands of the corresponding nullable value type.</span></span> <span data-ttu-id="7f767-200">Il produit `null` si l’un de ses opérandes est `null`.</span><span class="sxs-lookup"><span data-stu-id="7f767-200">Such an operator produces `null` if any of its operands is `null`.</span></span> <span data-ttu-id="7f767-201">Toutefois, les opérateurs `&` et `|` peuvent produire une valeur non Null même si l’un des opérandes est `null`.</span><span class="sxs-lookup"><span data-stu-id="7f767-201">However, the `&` and `|` operators can produce non-null even if one of the operands is `null`.</span></span> <span data-ttu-id="7f767-202">Pour plus d’informations sur le comportement de l’opérateur avec les types valeur Nullable, consultez la section [opérateurs](../../programming-guide/nullable-types/using-nullable-types.md#operators) de l’article [utilisation de types valeur Nullable](../../programming-guide/nullable-types/using-nullable-types.md) .</span><span class="sxs-lookup"><span data-stu-id="7f767-202">For more information about the operator behavior with nullable value types, see the [Operators](../../programming-guide/nullable-types/using-nullable-types.md#operators) section of the [Using nullable value types](../../programming-guide/nullable-types/using-nullable-types.md) article.</span></span>

<span data-ttu-id="7f767-203">Vous pouvez également utiliser les opérateurs `!` et `^` avec les opérandes `bool?`, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="7f767-203">You can also use the `!` and `^` operators with the `bool?` operands, as the following example shows:</span></span>

[!code-csharp-interactive[lifted negation and xor](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#WithNullableBoolean)]

<span data-ttu-id="7f767-204">Les opérateurs logiques conditionnels `&&` et `||` ne prennent pas en charge les opérandes `bool?`.</span><span class="sxs-lookup"><span data-stu-id="7f767-204">The conditional logical operators `&&` and `||` don't support the `bool?` operands.</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="7f767-205">Assignation composée</span><span class="sxs-lookup"><span data-stu-id="7f767-205">Compound assignment</span></span>

<span data-ttu-id="7f767-206">Pour un opérateur binaire `op`, une expression d’assignation composée du formulaire</span><span class="sxs-lookup"><span data-stu-id="7f767-206">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="7f767-207">est équivalent à</span><span class="sxs-lookup"><span data-stu-id="7f767-207">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="7f767-208">sauf que `x` n’est évalué qu’une seule fois.</span><span class="sxs-lookup"><span data-stu-id="7f767-208">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="7f767-209">Les opérateurs `&`, `|` et `^` prennent en charge l’assignation composée, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="7f767-209">The `&`, `|`, and `^` operators support compound assignment, as the following example shows:</span></span>

[!code-csharp-interactive[compound assignment](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#CompoundAssignment)]

<span data-ttu-id="7f767-210">Les opérateurs logiques conditionnels `&&` et `||` ne prennent pas en charge l’assignation composée.</span><span class="sxs-lookup"><span data-stu-id="7f767-210">The conditional logical operators `&&` and `||` don't support compound assignment.</span></span>

## <a name="operator-precedence"></a><span data-ttu-id="7f767-211">Précédence des opérateurs</span><span class="sxs-lookup"><span data-stu-id="7f767-211">Operator precedence</span></span>

<span data-ttu-id="7f767-212">La liste suivante présente les opérateurs logiques par ordre de précédence, de la plus élevée à la plus basse :</span><span class="sxs-lookup"><span data-stu-id="7f767-212">The following list orders logical operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="7f767-213">Opérateur de négation logique `!`</span><span class="sxs-lookup"><span data-stu-id="7f767-213">Logical negation operator `!`</span></span>
- <span data-ttu-id="7f767-214">L’opérateur AND logique `&`</span><span class="sxs-lookup"><span data-stu-id="7f767-214">Logical AND operator `&`</span></span>
- <span data-ttu-id="7f767-215">Opérateur OR exclusif logique `^`</span><span class="sxs-lookup"><span data-stu-id="7f767-215">Logical exclusive OR operator `^`</span></span>
- <span data-ttu-id="7f767-216">Opérateur OR logique `|`</span><span class="sxs-lookup"><span data-stu-id="7f767-216">Logical OR operator `|`</span></span>
- <span data-ttu-id="7f767-217">Opérateur AND logique conditionnel `&&`</span><span class="sxs-lookup"><span data-stu-id="7f767-217">Conditional logical AND operator `&&`</span></span>
- <span data-ttu-id="7f767-218">Opérateur OR logique conditionnel `||`</span><span class="sxs-lookup"><span data-stu-id="7f767-218">Conditional logical OR operator `||`</span></span>

<span data-ttu-id="7f767-219">Utilisez des parenthèses, `()`, pour modifier l’ordre d’évaluation imposé par la précédence des opérateurs :</span><span class="sxs-lookup"><span data-stu-id="7f767-219">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence:</span></span>

[!code-csharp-interactive[operator precedence](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#Precedence)]

<span data-ttu-id="7f767-220">Pour obtenir la liste complète des opérateurs C# classés par niveau de priorité, consultez [Opérateurs C#](index.md).</span><span class="sxs-lookup"><span data-stu-id="7f767-220">For the complete list of C# operators ordered by precedence level, see [C# operators](index.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="7f767-221">Capacité de surcharge de l’opérateur</span><span class="sxs-lookup"><span data-stu-id="7f767-221">Operator overloadability</span></span>

<span data-ttu-id="7f767-222">Un type défini par l’utilisateur peut [surcharger](operator-overloading.md) les opérateurs `!`, `&`, `|` et `^`.</span><span class="sxs-lookup"><span data-stu-id="7f767-222">A user-defined type can [overload](operator-overloading.md) the `!`, `&`, `|`, and `^` operators.</span></span> <span data-ttu-id="7f767-223">Quand un opérateur binaire est surchargé, l’opérateur d’assignation composée correspondant est aussi implicitement surchargé.</span><span class="sxs-lookup"><span data-stu-id="7f767-223">When a binary operator is overloaded, the corresponding compound assignment operator is also implicitly overloaded.</span></span> <span data-ttu-id="7f767-224">Un type défini par l’utilisateur ne peut pas surcharger explicitement un opérateur d’assignation composée.</span><span class="sxs-lookup"><span data-stu-id="7f767-224">A user-defined type cannot explicitly overload a compound assignment operator.</span></span>

<span data-ttu-id="7f767-225">Un type défini par l’utilisateur ne peut pas surcharger les opérateurs logiques conditionnels `&&` et `||`.</span><span class="sxs-lookup"><span data-stu-id="7f767-225">A user-defined type cannot overload the conditional logical operators `&&` and `||`.</span></span> <span data-ttu-id="7f767-226">Toutefois, si un type défini par l’utilisateur surcharge les [opérateurs true et false](true-false-operators.md) et l’opérateur `&` ou `|` d’une certaine manière, l’opération `&&` ou `||` peut être évaluée respectivement pour les opérandes de ce type.</span><span class="sxs-lookup"><span data-stu-id="7f767-226">However, if a user-defined type overloads the [true and false operators](true-false-operators.md) and the `&` or `|` operator in a certain way, the `&&` or `||` operation, respectively, can be evaluated for the operands of that type.</span></span> <span data-ttu-id="7f767-227">Pour plus d’informations, consultez la section [Opérateurs logiques conditionnels définis par l’utilisateur](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="7f767-227">For more information, see the [User-defined conditional logical operators](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="7f767-228">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="7f767-228">C# language specification</span></span>

<span data-ttu-id="7f767-229">Pour plus d’informations, consultez les sections suivantes de la [spécification du langage C#](~/_csharplang/spec/introduction.md) :</span><span class="sxs-lookup"><span data-stu-id="7f767-229">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="7f767-230">Opérateur de négation logique</span><span class="sxs-lookup"><span data-stu-id="7f767-230">Logical negation operator</span></span>](~/_csharplang/spec/expressions.md#logical-negation-operator)
- [<span data-ttu-id="7f767-231">Opérateurs logiques</span><span class="sxs-lookup"><span data-stu-id="7f767-231">Logical operators</span></span>](~/_csharplang/spec/expressions.md#logical-operators)
- [<span data-ttu-id="7f767-232">Opérateurs logiques conditionnels</span><span class="sxs-lookup"><span data-stu-id="7f767-232">Conditional logical operators</span></span>](~/_csharplang/spec/expressions.md#conditional-logical-operators)
- [<span data-ttu-id="7f767-233">Assignation composée</span><span class="sxs-lookup"><span data-stu-id="7f767-233">Compound assignment</span></span>](~/_csharplang/spec/expressions.md#compound-assignment)

## <a name="see-also"></a><span data-ttu-id="7f767-234">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7f767-234">See also</span></span>

- [<span data-ttu-id="7f767-235">Informations de référence sur C#</span><span class="sxs-lookup"><span data-stu-id="7f767-235">C# reference</span></span>](../index.md)
- [<span data-ttu-id="7f767-236">Opérateurs C#</span><span class="sxs-lookup"><span data-stu-id="7f767-236">C# operators</span></span>](index.md)
- [<span data-ttu-id="7f767-237">Opérateurs de bits et de décalage</span><span class="sxs-lookup"><span data-stu-id="7f767-237">Bitwise and shift operators</span></span>](bitwise-and-shift-operators.md)
