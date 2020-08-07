---
title: Opérateurs au niveau du bit et opérateurs de décalage - Référence C#
description: Découvrez les opérateurs C# qui effectuent des opérations logiques de décalage ou au niveau du bit avec des opérandes de types intégraux.
ms.date: 04/18/2019
author: pkulikov
f1_keywords:
- ~_CSharpKeyword
- <<_CSharpKeyword
- '>>_CSharpKeyword'
- '&_CSharpKeyword'
- ^_CSharpKeyword
- '|_CSharpKeyword'
- <<=_CSharpKeyword
- '>>=_CSharpKeyword'
helpviewer_keywords:
- bitwise logical operators [C#]
- shift operators [C#]
- tilde operator [C#]
- one's complement operator [C#]
- bitwise complement operator [C#]
- ~ operator [C#]
- left shift operator [C#]
- << operator [C#]
- right shift operator [C#]
- '>> operator [C#]'
- bitwise logical AND operator [C#]
- ampersand operator [C#]
- '& operator [C#]'
- bitwise logical exclusive OR operator [C#]
- bitwise logical XOR operator [C#]
- ^ operator [C#]
- bitwise logical OR operator [C#]
- '| operator [C#]'
ms.openlocfilehash: 99181855fdf8e937676e44e8b347510f9405aa3d
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2020
ms.locfileid: "87916913"
---
# <a name="bitwise-and-shift-operators-c-reference"></a><span data-ttu-id="49c2a-103">Opérateurs au niveau du bit et opérateurs de décalage (référence C#)</span><span class="sxs-lookup"><span data-stu-id="49c2a-103">Bitwise and shift operators (C# reference)</span></span>

<span data-ttu-id="49c2a-104">Les opérateurs suivants effectuent des opérations de bits ou de décalage avec les opérandes des [types numériques intégraux](../builtin-types/integral-numeric-types.md) ou le type [char](../builtin-types/char.md) :</span><span class="sxs-lookup"><span data-stu-id="49c2a-104">The following operators perform bitwise or shift operations with operands of the [integral numeric types](../builtin-types/integral-numeric-types.md) or the [char](../builtin-types/char.md) type:</span></span>

- <span data-ttu-id="49c2a-105">Opérateur unaire [ `~` (complément de bits)](#bitwise-complement-operator-)</span><span class="sxs-lookup"><span data-stu-id="49c2a-105">Unary [`~` (bitwise complement)](#bitwise-complement-operator-) operator</span></span>
- <span data-ttu-id="49c2a-106">Opérateurs de décalage binaire [ `<<` (décalage vers la gauche)](#left-shift-operator-) et [ `>>` (décalage vers la droite)](#right-shift-operator-)</span><span class="sxs-lookup"><span data-stu-id="49c2a-106">Binary [`<<` (left shift)](#left-shift-operator-) and [`>>` (right shift)](#right-shift-operator-) shift operators</span></span>
- <span data-ttu-id="49c2a-107">Opérateurs binaires [ `&` (and logique)](#logical-and-operator-), [ `|` (or logique)](#logical-or-operator-)et (opérateur or [ `^` exclusif logique)](#logical-exclusive-or-operator-)</span><span class="sxs-lookup"><span data-stu-id="49c2a-107">Binary [`&` (logical AND)](#logical-and-operator-), [`|` (logical OR)](#logical-or-operator-), and [`^` (logical exclusive OR)](#logical-exclusive-or-operator-) operators</span></span>

<span data-ttu-id="49c2a-108">Ces opérateurs sont définis pour les types `int`, `uint`, `long` et `ulong`.</span><span class="sxs-lookup"><span data-stu-id="49c2a-108">Those operators are defined for the `int`, `uint`, `long`, and `ulong` types.</span></span> <span data-ttu-id="49c2a-109">Lorsque les deux opérandes sont d’autres types intégraux (`sbyte`, `byte`, `short`, `ushort` ou `char`), leurs valeurs sont converties en valeurs de type `int`, qui est également le type de résultat d’une opération.</span><span class="sxs-lookup"><span data-stu-id="49c2a-109">When both operands are of other integral types (`sbyte`, `byte`, `short`, `ushort`, or `char`), their values are converted to the `int` type, which is also the result type of an operation.</span></span> <span data-ttu-id="49c2a-110">Lorsque les opérandes sont de différents types intégraux, leurs valeurs sont converties vers le type intégral le plus proche.</span><span class="sxs-lookup"><span data-stu-id="49c2a-110">When operands are of different integral types, their values are converted to the closest containing integral type.</span></span> <span data-ttu-id="49c2a-111">Pour plus d’informations, consultez la section [Promotions numériques](~/_csharplang/spec/expressions.md#numeric-promotions) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="49c2a-111">For more information, see the [Numeric promotions](~/_csharplang/spec/expressions.md#numeric-promotions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="49c2a-112">Les `&` `|` opérateurs, et `^` sont également définis pour les opérandes du `bool` type.</span><span class="sxs-lookup"><span data-stu-id="49c2a-112">The `&`, `|`, and `^` operators are also defined for operands of the `bool` type.</span></span> <span data-ttu-id="49c2a-113">Pour plus d’informations, consultez [Opérateurs logiques booléens](boolean-logical-operators.md).</span><span class="sxs-lookup"><span data-stu-id="49c2a-113">For more information, see [Boolean logical operators](boolean-logical-operators.md).</span></span>

<span data-ttu-id="49c2a-114">Les opérations de décalage et au niveau du bit ne provoquent jamais de dépassements de capacité et donnent les mêmes résultats dans des contextes [checked et unchecked](../keywords/checked-and-unchecked.md).</span><span class="sxs-lookup"><span data-stu-id="49c2a-114">Bitwise and shift operations never cause overflow and produce the same results in [checked and unchecked](../keywords/checked-and-unchecked.md) contexts.</span></span>

## <a name="bitwise-complement-operator-"></a><span data-ttu-id="49c2a-115">Opérateur de complément de bits ~</span><span class="sxs-lookup"><span data-stu-id="49c2a-115">Bitwise complement operator ~</span></span>

<span data-ttu-id="49c2a-116">L’opérateur `~` produit un complément de bits de son opérande en inversant chaque bit :</span><span class="sxs-lookup"><span data-stu-id="49c2a-116">The `~` operator produces a bitwise complement of its operand by reversing each bit:</span></span>

[!code-csharp-interactive[bitwise NOT](snippets/shared/BitwiseAndShiftOperators.cs#BitwiseComplement)]

<span data-ttu-id="49c2a-117">Vous pouvez également utiliser le symbole `~` pour déclarer des finaliseurs.</span><span class="sxs-lookup"><span data-stu-id="49c2a-117">You can also use the `~` symbol to declare finalizers.</span></span> <span data-ttu-id="49c2a-118">Pour plus d’informations, consultez [Finaliseurs](../../programming-guide/classes-and-structs/destructors.md).</span><span class="sxs-lookup"><span data-stu-id="49c2a-118">For more information, see [Finalizers](../../programming-guide/classes-and-structs/destructors.md).</span></span>

## <a name="left-shift-operator-"></a><span data-ttu-id="49c2a-119">Opérateur de décalage gauche \<\<</span><span class="sxs-lookup"><span data-stu-id="49c2a-119">Left-shift operator \<\<</span></span>

<span data-ttu-id="49c2a-120">L' `<<` opérateur décale son opérande de gauche vers la gauche du [nombre de bits défini par son opérande de droite](#shift-count-of-the-shift-operators).</span><span class="sxs-lookup"><span data-stu-id="49c2a-120">The `<<` operator shifts its left-hand operand left by the [number of bits defined by its right-hand operand](#shift-count-of-the-shift-operators).</span></span>

<span data-ttu-id="49c2a-121">L’opération de décalage gauche supprime les bits d’ordre supérieur qui sont en dehors de la plage du type de résultat, et définit les positions de bits vides d’ordre inférieur sur zéro, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="49c2a-121">The left-shift operation discards the high-order bits that are outside the range of the result type and sets the low-order empty bit positions to zero, as the following example shows:</span></span>

[!code-csharp-interactive[left shift](snippets/shared/BitwiseAndShiftOperators.cs#LeftShift)]

<span data-ttu-id="49c2a-122">Étant donné que les opérateurs de décalage sont définis uniquement pour les types `int`, `uint`, `long` et `ulong`, le résultat d’une opération contient toujours au moins 32 bits.</span><span class="sxs-lookup"><span data-stu-id="49c2a-122">Because the shift operators are defined only for the `int`, `uint`, `long`, and `ulong` types, the result of an operation always contains at least 32 bits.</span></span> <span data-ttu-id="49c2a-123">Si l’opérande de partie gauche est d’un autre type intégral (`sbyte`, `byte`, `short`, `ushort` ou `char`), sa valeur est convertie en type `int`, comme l’indique l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="49c2a-123">If the left-hand operand is of another integral type (`sbyte`, `byte`, `short`, `ushort`, or `char`), its value is converted to the `int` type, as the following example shows:</span></span>

[!code-csharp-interactive[left shift with promotion](snippets/shared/BitwiseAndShiftOperators.cs#LeftShiftPromoted)]

<span data-ttu-id="49c2a-124">Pour plus d’informations sur la façon dont l’opérande de partie droite de l’opérateur `<<` définit la valeur de décalage, consultez la section [Valeur de décalage des opérateurs de décalage](#shift-count-of-the-shift-operators).</span><span class="sxs-lookup"><span data-stu-id="49c2a-124">For information about how the right-hand operand of the `<<` operator defines the shift count, see the [Shift count of the shift operators](#shift-count-of-the-shift-operators) section.</span></span>

## <a name="right-shift-operator-"></a><span data-ttu-id="49c2a-125">Opérateur de décalage vers la droite >></span><span class="sxs-lookup"><span data-stu-id="49c2a-125">Right-shift operator >></span></span>

<span data-ttu-id="49c2a-126">L' `>>` opérateur décale son opérande de gauche vers la droite du [nombre de bits défini par son opérande de droite](#shift-count-of-the-shift-operators).</span><span class="sxs-lookup"><span data-stu-id="49c2a-126">The `>>` operator shifts its left-hand operand right by the [number of bits defined by its right-hand operand](#shift-count-of-the-shift-operators).</span></span>

<span data-ttu-id="49c2a-127">L’opération de décalage vers la droite ignore les bits d’ordre inférieur, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="49c2a-127">The right-shift operation discards the low-order bits, as the following example shows:</span></span>

[!code-csharp-interactive[right shift](snippets/shared/BitwiseAndShiftOperators.cs#RightShift)]

<span data-ttu-id="49c2a-128">Les positions de bits vides d’ordre supérieur sont définies en fonction du type de l’opérande de partie gauche comme suit :</span><span class="sxs-lookup"><span data-stu-id="49c2a-128">The high-order empty bit positions are set based on the type of the left-hand operand as follows:</span></span>

- <span data-ttu-id="49c2a-129">Si l’opérande de gauche est de type `int` ou `long` , l’opérateur de décalage vers la droite effectue un décalage *arithmétique* : la valeur du bit le plus significatif (le bit de signe) de l’opérande de gauche est propagée aux positions de bits vides de poids fort.</span><span class="sxs-lookup"><span data-stu-id="49c2a-129">If the left-hand operand is of type `int` or `long`, the right-shift operator performs an *arithmetic* shift: the value of the most significant bit (the sign bit) of the left-hand operand is propagated to the high-order empty bit positions.</span></span> <span data-ttu-id="49c2a-130">Autrement dit, les positions de bits vides d’ordre supérieur sont définies sur zéro si l’opérande de partir gauche n’est pas négatif et sur un s’il est négatif.</span><span class="sxs-lookup"><span data-stu-id="49c2a-130">That is, the high-order empty bit positions are set to zero if the left-hand operand is non-negative and set to one if it's negative.</span></span>

  [!code-csharp-interactive[arithmetic right shift](snippets/shared/BitwiseAndShiftOperators.cs#ArithmeticRightShift)]

- <span data-ttu-id="49c2a-131">Si l’opérande de gauche est de type `uint` ou `ulong` , l’opérateur de décalage vers la droite effectue un décalage *logique* : les positions de bits vides de poids fort ont toujours la valeur zéro.</span><span class="sxs-lookup"><span data-stu-id="49c2a-131">If the left-hand operand is of type `uint` or `ulong`, the right-shift operator performs a *logical* shift: the high-order empty bit positions are always set to zero.</span></span>

  [!code-csharp-interactive[logical right shift](snippets/shared/BitwiseAndShiftOperators.cs#LogicalRightShift)]

<span data-ttu-id="49c2a-132">Pour plus d’informations sur la façon dont l’opérande de partie droite de l’opérateur `>>` définit la valeur de décalage, consultez la section [Valeur de décalage des opérateurs de décalage](#shift-count-of-the-shift-operators).</span><span class="sxs-lookup"><span data-stu-id="49c2a-132">For information about how the right-hand operand of the `>>` operator defines the shift count, see the [Shift count of the shift operators](#shift-count-of-the-shift-operators) section.</span></span>

## <a name="logical-and-operator-amp"></a><a name="logical-and-operator-"></a><span data-ttu-id="49c2a-133">Opérateur AND logique&amp;</span><span class="sxs-lookup"><span data-stu-id="49c2a-133">Logical AND operator &amp;</span></span>

<span data-ttu-id="49c2a-134">L’opérateur `&` calcule le AND logique au niveau du bit de ses opérandes :</span><span class="sxs-lookup"><span data-stu-id="49c2a-134">The `&` operator computes the bitwise logical AND of its operands:</span></span>

[!code-csharp-interactive[bitwise AND](snippets/shared/BitwiseAndShiftOperators.cs#BitwiseAnd)]

<span data-ttu-id="49c2a-135">Pour les `bool` opérandes, l' `&` opérateur calcule le [and logique](boolean-logical-operators.md#logical-and-operator-) de ses opérandes.</span><span class="sxs-lookup"><span data-stu-id="49c2a-135">For `bool` operands, the `&` operator computes the [logical AND](boolean-logical-operators.md#logical-and-operator-) of its operands.</span></span> <span data-ttu-id="49c2a-136">L’opérateur unaire `&` est [l’opérateur address-of](pointer-related-operators.md#address-of-operator-).</span><span class="sxs-lookup"><span data-stu-id="49c2a-136">The unary `&` operator is the [address-of operator](pointer-related-operators.md#address-of-operator-).</span></span>

## <a name="logical-exclusive-or-operator-"></a><span data-ttu-id="49c2a-137">L’opérateur OR exclusif logique ^</span><span class="sxs-lookup"><span data-stu-id="49c2a-137">Logical exclusive OR operator ^</span></span>

<span data-ttu-id="49c2a-138">L’opérateur `^` calcule le OR exclusif logique au niveau du bit (également appelé XOR logique au niveau du bit) de ses opérandes.</span><span class="sxs-lookup"><span data-stu-id="49c2a-138">The `^` operator computes the bitwise logical exclusive OR, also known as the bitwise logical XOR, of its operands:</span></span>

[!code-csharp-interactive[bitwise XOR](snippets/shared/BitwiseAndShiftOperators.cs#BitwiseXor)]

<span data-ttu-id="49c2a-139">Pour les `bool` opérandes, l' `^` opérateur calcule l' [or exclusif logique](boolean-logical-operators.md#logical-exclusive-or-operator-) de ses opérandes.</span><span class="sxs-lookup"><span data-stu-id="49c2a-139">For `bool` operands, the `^` operator computes the [logical exclusive OR](boolean-logical-operators.md#logical-exclusive-or-operator-) of its operands.</span></span>

## <a name="logical-or-operator-"></a><span data-ttu-id="49c2a-140">L’opérateur OU logique |</span><span class="sxs-lookup"><span data-stu-id="49c2a-140">Logical OR operator |</span></span>

<span data-ttu-id="49c2a-141">L’opérateur `|` calcule le OR logique au niveau du bit de ses opérandes :</span><span class="sxs-lookup"><span data-stu-id="49c2a-141">The `|` operator computes the bitwise logical OR of its operands:</span></span>

[!code-csharp-interactive[bitwise OR](snippets/shared/BitwiseAndShiftOperators.cs#BitwiseOr)]

<span data-ttu-id="49c2a-142">Pour les `bool` opérandes, l' `|` opérateur calcule le [or logique](boolean-logical-operators.md#logical-or-operator-) de ses opérandes.</span><span class="sxs-lookup"><span data-stu-id="49c2a-142">For `bool` operands, the `|` operator computes the [logical OR](boolean-logical-operators.md#logical-or-operator-) of its operands.</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="49c2a-143">Assignation composée</span><span class="sxs-lookup"><span data-stu-id="49c2a-143">Compound assignment</span></span>

<span data-ttu-id="49c2a-144">Pour un opérateur binaire `op`, une expression d’assignation composée du formulaire</span><span class="sxs-lookup"><span data-stu-id="49c2a-144">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="49c2a-145">équivaut à :</span><span class="sxs-lookup"><span data-stu-id="49c2a-145">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="49c2a-146">sauf que `x` n’est évalué qu’une seule fois.</span><span class="sxs-lookup"><span data-stu-id="49c2a-146">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="49c2a-147">L’exemple suivant montre l’utilisation de l’assignation composée avec des opérateurs de décalage et des opérateurs au niveau du bit :</span><span class="sxs-lookup"><span data-stu-id="49c2a-147">The following example demonstrates the usage of compound assignment with bitwise and shift operators:</span></span>

[!code-csharp-interactive[compound assignment](snippets/shared/BitwiseAndShiftOperators.cs#CompoundAssignment)]

<span data-ttu-id="49c2a-148">En raison des [promotions numériques](~/_csharplang/spec/expressions.md#numeric-promotions), le résultat de l’opération `op` risque de ne pas être implicitement convertible en type `T` de `x`.</span><span class="sxs-lookup"><span data-stu-id="49c2a-148">Because of [numeric promotions](~/_csharplang/spec/expressions.md#numeric-promotions), the result of the `op` operation might be not implicitly convertible to the type `T` of `x`.</span></span> <span data-ttu-id="49c2a-149">Dans ce cas, si `op` est un opérateur prédéfini et que le résultat de l’opération est explicitement convertible en type `T` de `x`, une expression d’assignation composée de la forme `x op= y` équivaut à `x = (T)(x op y)`, sauf que `x` n’est évalué qu’une seule fois.</span><span class="sxs-lookup"><span data-stu-id="49c2a-149">In such a case, if `op` is a predefined operator and the result of the operation is explicitly convertible to the type `T` of `x`, a compound assignment expression of the form `x op= y` is equivalent to `x = (T)(x op y)`, except that `x` is only evaluated once.</span></span> <span data-ttu-id="49c2a-150">L’exemple suivant illustre ce comportement :</span><span class="sxs-lookup"><span data-stu-id="49c2a-150">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[compound assignment with cast](snippets/shared/BitwiseAndShiftOperators.cs#CompoundAssignmentWithCast)]

## <a name="operator-precedence"></a><span data-ttu-id="49c2a-151">Précédence des opérateurs</span><span class="sxs-lookup"><span data-stu-id="49c2a-151">Operator precedence</span></span>

<span data-ttu-id="49c2a-152">La liste suivante présente les opérateurs au niveau du bit et les opérateurs de décalage par ordre de précédence, de la plus élevée à la plus basse :</span><span class="sxs-lookup"><span data-stu-id="49c2a-152">The following list orders bitwise and shift operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="49c2a-153">Opérateur de complément de bits `~`</span><span class="sxs-lookup"><span data-stu-id="49c2a-153">Bitwise complement operator `~`</span></span>
- <span data-ttu-id="49c2a-154">Opérateurs de décalage `<<` et `>>`</span><span class="sxs-lookup"><span data-stu-id="49c2a-154">Shift operators `<<` and `>>`</span></span>
- <span data-ttu-id="49c2a-155">L’opérateur AND logique `&`</span><span class="sxs-lookup"><span data-stu-id="49c2a-155">Logical AND operator `&`</span></span>
- <span data-ttu-id="49c2a-156">Opérateur OR exclusif logique `^`</span><span class="sxs-lookup"><span data-stu-id="49c2a-156">Logical exclusive OR operator `^`</span></span>
- <span data-ttu-id="49c2a-157">Opérateur OR logique `|`</span><span class="sxs-lookup"><span data-stu-id="49c2a-157">Logical OR operator `|`</span></span>

<span data-ttu-id="49c2a-158">Utilisez des parenthèses, `()`, pour modifier l’ordre d’évaluation imposé par la précédence des opérateurs :</span><span class="sxs-lookup"><span data-stu-id="49c2a-158">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence:</span></span>

[!code-csharp-interactive[operator precedence](snippets/shared/BitwiseAndShiftOperators.cs#Precedence)]

<span data-ttu-id="49c2a-159">Pour obtenir la liste complète des opérateurs C# classés par niveau de priorité, consultez la section [priorité d’opérateur](index.md#operator-precedence) de l’article [opérateurs c#](index.md) .</span><span class="sxs-lookup"><span data-stu-id="49c2a-159">For the complete list of C# operators ordered by precedence level, see the [Operator precedence](index.md#operator-precedence) section of the [C# operators](index.md) article.</span></span>

## <a name="shift-count-of-the-shift-operators"></a><span data-ttu-id="49c2a-160">Valeur de décalage des opérateurs de décalage</span><span class="sxs-lookup"><span data-stu-id="49c2a-160">Shift count of the shift operators</span></span>

<span data-ttu-id="49c2a-161">Pour les opérateurs de décalage `<<` et `>>` , le type de l’opérande de droite doit être `int` ou un type qui a une [conversion numérique implicite prédéfinie](../builtin-types/numeric-conversions.md#implicit-numeric-conversions) en `int` .</span><span class="sxs-lookup"><span data-stu-id="49c2a-161">For the shift operators `<<` and `>>`, the type of the right-hand operand must be `int` or a type that has a [predefined implicit numeric conversion](../builtin-types/numeric-conversions.md#implicit-numeric-conversions) to `int`.</span></span>

<span data-ttu-id="49c2a-162">Pour les expressions `x << count` et `x >> count`, la valeur réelle du décalage varie selon le type de `x` :</span><span class="sxs-lookup"><span data-stu-id="49c2a-162">For the `x << count` and `x >> count` expressions, the actual shift count depends on the type of `x` as follows:</span></span>

- <span data-ttu-id="49c2a-163">Si le type de `x` est `int` ou `uint` , le nombre de décalages est défini par les *cinq* bits de poids faible de l’opérande de droite.</span><span class="sxs-lookup"><span data-stu-id="49c2a-163">If the type of `x` is `int` or `uint`, the shift count is defined by the low-order *five* bits of the right-hand operand.</span></span> <span data-ttu-id="49c2a-164">La valeur de décalage est donc calculée à partir de `count & 0x1F` (ou de `count & 0b_1_1111`).</span><span class="sxs-lookup"><span data-stu-id="49c2a-164">That is, the shift count is computed from `count & 0x1F` (or `count & 0b_1_1111`).</span></span>

- <span data-ttu-id="49c2a-165">Si le type de `x` est `long` ou `ulong` , le nombre de décalages est défini par les *six* bits de poids faible de l’opérande de droite.</span><span class="sxs-lookup"><span data-stu-id="49c2a-165">If the type of `x` is `long` or `ulong`, the shift count is defined by the low-order *six* bits of the right-hand operand.</span></span> <span data-ttu-id="49c2a-166">La valeur de décalage est donc calculée à partir de `count & 0x3F` (ou de `count & 0b_11_1111`).</span><span class="sxs-lookup"><span data-stu-id="49c2a-166">That is, the shift count is computed from `count & 0x3F` (or `count & 0b_11_1111`).</span></span>

<span data-ttu-id="49c2a-167">L’exemple suivant illustre ce comportement :</span><span class="sxs-lookup"><span data-stu-id="49c2a-167">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[shift count example](snippets/shared/BitwiseAndShiftOperators.cs#ShiftCount)]

> [!NOTE]
> <span data-ttu-id="49c2a-168">Comme le montre l’exemple précédent, le résultat d’une opération de décalage peut être différent de zéro même si la valeur de l’opérande de droite est supérieure au nombre de bits dans l’opérande de gauche.</span><span class="sxs-lookup"><span data-stu-id="49c2a-168">As the preceding example shows, the result of a shift operation can be non-zero even if the value of the right-hand operand is greater than the number of bits in the left-hand operand.</span></span>

## <a name="enumeration-logical-operators"></a><span data-ttu-id="49c2a-169">Opérateurs logiques d’énumération</span><span class="sxs-lookup"><span data-stu-id="49c2a-169">Enumeration logical operators</span></span>

<span data-ttu-id="49c2a-170">Les `~` opérateurs,, `&` `|` et `^` sont également pris en charge par n’importe quel type [énumération](../builtin-types/enum.md) .</span><span class="sxs-lookup"><span data-stu-id="49c2a-170">The `~`, `&`, `|`, and `^` operators are also supported by any [enumeration](../builtin-types/enum.md) type.</span></span> <span data-ttu-id="49c2a-171">Pour les opérandes du même type d’énumération, une opération logique est effectuée sur les valeurs correspondantes du type intégral sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="49c2a-171">For operands of the same enumeration type, a logical operation is performed on the corresponding values of the underlying integral type.</span></span> <span data-ttu-id="49c2a-172">Par exemple, pour tout `x` et `y` d’un type énumération `T` avec un type sous-jacent `U`, l’expression `x & y` produit le même résultat que l’expression `(T)((U)x & (U)y)`.</span><span class="sxs-lookup"><span data-stu-id="49c2a-172">For example, for any `x` and `y` of an enumeration type `T` with an underlying type `U`, the `x & y` expression produces the same result as the `(T)((U)x & (U)y)` expression.</span></span>

<span data-ttu-id="49c2a-173">En général, vous utilisez des opérateurs logiques au niveau du bit avec un type d’énumération défini avec l’attribut [Flags](xref:System.FlagsAttribute) .</span><span class="sxs-lookup"><span data-stu-id="49c2a-173">You typically use bitwise logical operators with an enumeration type that is defined with the [Flags](xref:System.FlagsAttribute) attribute.</span></span> <span data-ttu-id="49c2a-174">Pour plus d’informations, consultez la section [Types énumération comme indicateurs binaires](../builtin-types/enum.md#enumeration-types-as-bit-flags) de l’article[Types énumération](../builtin-types/enum.md).</span><span class="sxs-lookup"><span data-stu-id="49c2a-174">For more information, see the [Enumeration types as bit flags](../builtin-types/enum.md#enumeration-types-as-bit-flags) section of the [Enumeration types](../builtin-types/enum.md) article.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="49c2a-175">Capacité de surcharge de l’opérateur</span><span class="sxs-lookup"><span data-stu-id="49c2a-175">Operator overloadability</span></span>

<span data-ttu-id="49c2a-176">Un type défini par l’utilisateur peut [surcharger](operator-overloading.md) les opérateurs,,,, `~` `<<` `>>` `&` `|` et `^` .</span><span class="sxs-lookup"><span data-stu-id="49c2a-176">A user-defined type can [overload](operator-overloading.md) the `~`, `<<`, `>>`, `&`, `|`, and `^` operators.</span></span> <span data-ttu-id="49c2a-177">Quand un opérateur binaire est surchargé, l’opérateur d’assignation composée correspondant est aussi implicitement surchargé.</span><span class="sxs-lookup"><span data-stu-id="49c2a-177">When a binary operator is overloaded, the corresponding compound assignment operator is also implicitly overloaded.</span></span> <span data-ttu-id="49c2a-178">Un type défini par l’utilisateur ne peut pas surcharger explicitement un opérateur d’assignation composée.</span><span class="sxs-lookup"><span data-stu-id="49c2a-178">A user-defined type cannot explicitly overload a compound assignment operator.</span></span>

<span data-ttu-id="49c2a-179">Si un type `T` défini par l’utilisateur surcharge l’opérateur `<<` ou `>>`, l’opérande de partie gauche doit être de type `T` et l’opérande de partie droite de type `int`.</span><span class="sxs-lookup"><span data-stu-id="49c2a-179">If a user-defined type `T` overloads the `<<` or `>>` operator, the type of the left-hand operand must be `T` and the type of the right-hand operand must be `int`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="49c2a-180">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="49c2a-180">C# language specification</span></span>

<span data-ttu-id="49c2a-181">Pour plus d’informations, consultez les sections suivantes de la [spécification du langage C#](~/_csharplang/spec/introduction.md) :</span><span class="sxs-lookup"><span data-stu-id="49c2a-181">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="49c2a-182">Opérateur de complément de bits</span><span class="sxs-lookup"><span data-stu-id="49c2a-182">Bitwise complement operator</span></span>](~/_csharplang/spec/expressions.md#bitwise-complement-operator)
- [<span data-ttu-id="49c2a-183">Opérateurs de décalage</span><span class="sxs-lookup"><span data-stu-id="49c2a-183">Shift operators</span></span>](~/_csharplang/spec/expressions.md#shift-operators)
- [<span data-ttu-id="49c2a-184">Opérateurs logiques</span><span class="sxs-lookup"><span data-stu-id="49c2a-184">Logical operators</span></span>](~/_csharplang/spec/expressions.md#logical-operators)
- [<span data-ttu-id="49c2a-185">Assignation composée</span><span class="sxs-lookup"><span data-stu-id="49c2a-185">Compound assignment</span></span>](~/_csharplang/spec/expressions.md#compound-assignment)
- [<span data-ttu-id="49c2a-186">Promotions numériques</span><span class="sxs-lookup"><span data-stu-id="49c2a-186">Numeric promotions</span></span>](~/_csharplang/spec/expressions.md#numeric-promotions)

## <a name="see-also"></a><span data-ttu-id="49c2a-187">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="49c2a-187">See also</span></span>

- [<span data-ttu-id="49c2a-188">Informations de référence sur C#</span><span class="sxs-lookup"><span data-stu-id="49c2a-188">C# reference</span></span>](../index.md)
- [<span data-ttu-id="49c2a-189">Opérateurs et expressions C#</span><span class="sxs-lookup"><span data-stu-id="49c2a-189">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="49c2a-190">Opérateurs logiques booléens</span><span class="sxs-lookup"><span data-stu-id="49c2a-190">Boolean logical operators</span></span>](boolean-logical-operators.md)
