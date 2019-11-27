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
ms.openlocfilehash: 27f7cf46bd3e344503f74527df34506d38ad4545
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428437"
---
# <a name="bitwise-and-shift-operators-c-reference"></a><span data-ttu-id="44252-103">Opérateurs au niveau du bit et opérateurs de décalage (référence C#)</span><span class="sxs-lookup"><span data-stu-id="44252-103">Bitwise and shift operators (C# reference)</span></span>

<span data-ttu-id="44252-104">Les opérateurs suivants effectuent des opérations de bits ou de décalage avec les opérandes des [types numériques intégraux](../builtin-types/integral-numeric-types.md) ou le type [char](../builtin-types/char.md) :</span><span class="sxs-lookup"><span data-stu-id="44252-104">The following operators perform bitwise or shift operations with operands of the [integral numeric types](../builtin-types/integral-numeric-types.md) or the [char](../builtin-types/char.md) type:</span></span>

- <span data-ttu-id="44252-105">Opérateur unaire [`~` (complément de bits)](#bitwise-complement-operator-)</span><span class="sxs-lookup"><span data-stu-id="44252-105">Unary [`~` (bitwise complement)](#bitwise-complement-operator-) operator</span></span>
- <span data-ttu-id="44252-106">Opérateurs de décalage binaires [`<<` (décalage gauche)](#left-shift-operator-) et [`>>` (décalage droite)](#right-shift-operator-)</span><span class="sxs-lookup"><span data-stu-id="44252-106">Binary [`<<` (left shift)](#left-shift-operator-) and [`>>` (right shift)](#right-shift-operator-) shift operators</span></span>
- <span data-ttu-id="44252-107">Opérateurs binaires [`&` (AND logique)](#logical-and-operator-), [`|` (OR logique)](#logical-or-operator-) et [`^` (OR exclusif logique)](#logical-exclusive-or-operator-)</span><span class="sxs-lookup"><span data-stu-id="44252-107">Binary [`&` (logical AND)](#logical-and-operator-), [`|` (logical OR)](#logical-or-operator-), and [`^` (logical exclusive OR)](#logical-exclusive-or-operator-) operators</span></span>

<span data-ttu-id="44252-108">Ces opérateurs sont définis pour les types `int`, `uint`, `long` et `ulong`.</span><span class="sxs-lookup"><span data-stu-id="44252-108">Those operators are defined for the `int`, `uint`, `long`, and `ulong` types.</span></span> <span data-ttu-id="44252-109">Lorsque les deux opérandes sont d’autres types intégraux (`sbyte`, `byte`, `short`, `ushort` ou `char`), leurs valeurs sont converties en valeurs de type `int`, qui est également le type de résultat d’une opération.</span><span class="sxs-lookup"><span data-stu-id="44252-109">When both operands are of other integral types (`sbyte`, `byte`, `short`, `ushort`, or `char`), their values are converted to the `int` type, which is also the result type of an operation.</span></span> <span data-ttu-id="44252-110">Lorsque les opérandes sont de différents types intégraux, leurs valeurs sont converties vers le type intégral le plus proche.</span><span class="sxs-lookup"><span data-stu-id="44252-110">When operands are of different integral types, their values are converted to the closest containing integral type.</span></span> <span data-ttu-id="44252-111">Pour plus d’informations, consultez la section [Promotions numériques](~/_csharplang/spec/expressions.md#numeric-promotions) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="44252-111">For more information, see the [Numeric promotions](~/_csharplang/spec/expressions.md#numeric-promotions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="44252-112">Les opérateurs `&`, `|`et `^` sont également définis pour les opérandes du type de `bool`.</span><span class="sxs-lookup"><span data-stu-id="44252-112">The `&`, `|`, and `^` operators are also defined for operands of the `bool` type.</span></span> <span data-ttu-id="44252-113">Pour plus d’informations, consultez [Opérateurs logiques booléens](boolean-logical-operators.md).</span><span class="sxs-lookup"><span data-stu-id="44252-113">For more information, see [Boolean logical operators](boolean-logical-operators.md).</span></span>

<span data-ttu-id="44252-114">Les opérations de décalage et au niveau du bit ne provoquent jamais de dépassements de capacité et donnent les mêmes résultats dans des contextes [checked et unchecked](../keywords/checked-and-unchecked.md).</span><span class="sxs-lookup"><span data-stu-id="44252-114">Bitwise and shift operations never cause overflow and produce the same results in [checked and unchecked](../keywords/checked-and-unchecked.md) contexts.</span></span>

## <a name="bitwise-complement-operator-"></a><span data-ttu-id="44252-115">Opérateur de complément de bits ~</span><span class="sxs-lookup"><span data-stu-id="44252-115">Bitwise complement operator ~</span></span>

<span data-ttu-id="44252-116">L’opérateur `~` produit un complément de bits de son opérande en inversant chaque bit :</span><span class="sxs-lookup"><span data-stu-id="44252-116">The `~` operator produces a bitwise complement of its operand by reversing each bit:</span></span>

[!code-csharp-interactive[bitwise NOT](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#BitwiseComplement)]

<span data-ttu-id="44252-117">Vous pouvez également utiliser le symbole `~` pour déclarer des finaliseurs.</span><span class="sxs-lookup"><span data-stu-id="44252-117">You can also use the `~` symbol to declare finalizers.</span></span> <span data-ttu-id="44252-118">Pour plus d’informations, consultez [Finaliseurs](../../programming-guide/classes-and-structs/destructors.md).</span><span class="sxs-lookup"><span data-stu-id="44252-118">For more information, see [Finalizers](../../programming-guide/classes-and-structs/destructors.md).</span></span>

## <a name="left-shift-operator-"></a><span data-ttu-id="44252-119">Opérateur de décalage gauche \<\<</span><span class="sxs-lookup"><span data-stu-id="44252-119">Left-shift operator \<\<</span></span>

<span data-ttu-id="44252-120">L’opérateur `<<` décale son opérande de partie gauche vers le nombre de bits spécifié par son opérande de partie droite.</span><span class="sxs-lookup"><span data-stu-id="44252-120">The `<<` operator shifts its left-hand operand left by the number of bits defined by its right-hand operand.</span></span>

<span data-ttu-id="44252-121">L’opération de décalage gauche supprime les bits d’ordre supérieur qui sont en dehors de la plage du type de résultat, et définit les positions de bits vides d’ordre inférieur sur zéro, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="44252-121">The left-shift operation discards the high-order bits that are outside the range of the result type and sets the low-order empty bit positions to zero, as the following example shows:</span></span>

[!code-csharp-interactive[left shift](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#LeftShift)]

<span data-ttu-id="44252-122">Étant donné que les opérateurs de décalage sont définis uniquement pour les types `int`, `uint`, `long` et `ulong`, le résultat d’une opération contient toujours au moins 32 bits.</span><span class="sxs-lookup"><span data-stu-id="44252-122">Because the shift operators are defined only for the `int`, `uint`, `long`, and `ulong` types, the result of an operation always contains at least 32 bits.</span></span> <span data-ttu-id="44252-123">Si l’opérande de partie gauche est d’un autre type intégral (`sbyte`, `byte`, `short`, `ushort` ou `char`), sa valeur est convertie en type `int`, comme l’indique l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="44252-123">If the left-hand operand is of another integral type (`sbyte`, `byte`, `short`, `ushort`, or `char`), its value is converted to the `int` type, as the following example shows:</span></span>

[!code-csharp-interactive[left shift with promotion](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#LeftShiftPromoted)]

<span data-ttu-id="44252-124">Pour plus d’informations sur la façon dont l’opérande de partie droite de l’opérateur `<<` définit la valeur de décalage, consultez la section [Valeur de décalage des opérateurs de décalage](#shift-count-of-the-shift-operators).</span><span class="sxs-lookup"><span data-stu-id="44252-124">For information about how the right-hand operand of the `<<` operator defines the shift count, see the [Shift count of the shift operators](#shift-count-of-the-shift-operators) section.</span></span>

## <a name="right-shift-operator-"></a><span data-ttu-id="44252-125">Opérateur de décalage vers la droite >></span><span class="sxs-lookup"><span data-stu-id="44252-125">Right-shift operator >></span></span>

<span data-ttu-id="44252-126">L’opérateur `>>` décale son opérande de partie gauche vers le nombre de bits défini par son opérande de partie droite.</span><span class="sxs-lookup"><span data-stu-id="44252-126">The `>>` operator shifts its left-hand operand right by the number of bits defined by its right-hand operand.</span></span>

<span data-ttu-id="44252-127">L’opération de décalage vers la droite ignore les bits d’ordre inférieur, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="44252-127">The right-shift operation discards the low-order bits, as the following example shows:</span></span>

[!code-csharp-interactive[right shift](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#RightShift)]

<span data-ttu-id="44252-128">Les positions de bits vides d’ordre supérieur sont définies en fonction du type de l’opérande de partie gauche comme suit :</span><span class="sxs-lookup"><span data-stu-id="44252-128">The high-order empty bit positions are set based on the type of the left-hand operand as follows:</span></span>

- <span data-ttu-id="44252-129">Si l’opérande de gauche est de type `int` ou `long`, l’opérateur de décalage vers la droite effectue un décalage *arithmétique* : la valeur du bit le plus significatif (le bit de signe) de l’opérande de gauche est propagée aux positions de bits vides de poids fort.</span><span class="sxs-lookup"><span data-stu-id="44252-129">If the left-hand operand is of type `int` or `long`, the right-shift operator performs an *arithmetic* shift: the value of the most significant bit (the sign bit) of the left-hand operand is propagated to the high-order empty bit positions.</span></span> <span data-ttu-id="44252-130">Autrement dit, les positions de bits vides d’ordre supérieur sont définies sur zéro si l’opérande de partir gauche n’est pas négatif et sur un s’il est négatif.</span><span class="sxs-lookup"><span data-stu-id="44252-130">That is, the high-order empty bit positions are set to zero if the left-hand operand is non-negative and set to one if it's negative.</span></span>

  [!code-csharp-interactive[arithmetic right shift](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#ArithmeticRightShift)]

- <span data-ttu-id="44252-131">Si l’opérande de gauche est de type `uint` ou `ulong`, l’opérateur de décalage vers la droite effectue un décalage *logique* : les positions de bits vides de poids fort ont toujours la valeur zéro.</span><span class="sxs-lookup"><span data-stu-id="44252-131">If the left-hand operand is of type `uint` or `ulong`, the right-shift operator performs a *logical* shift: the high-order empty bit positions are always set to zero.</span></span>

  [!code-csharp-interactive[logical right shift](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#LogicalRightShift)]

<span data-ttu-id="44252-132">Pour plus d’informations sur la façon dont l’opérande de partie droite de l’opérateur `>>` définit la valeur de décalage, consultez la section [Valeur de décalage des opérateurs de décalage](#shift-count-of-the-shift-operators).</span><span class="sxs-lookup"><span data-stu-id="44252-132">For information about how the right-hand operand of the `>>` operator defines the shift count, see the [Shift count of the shift operators](#shift-count-of-the-shift-operators) section.</span></span>

## <a name="logical-and-operator-"></a> <span data-ttu-id="44252-133">Opérateur AND logique &amp;</span><span class="sxs-lookup"><span data-stu-id="44252-133">Logical AND operator &amp;</span></span>

<span data-ttu-id="44252-134">L’opérateur `&` calcule le AND logique au niveau du bit de ses opérandes :</span><span class="sxs-lookup"><span data-stu-id="44252-134">The `&` operator computes the bitwise logical AND of its operands:</span></span>

[!code-csharp-interactive[bitwise AND](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#BitwiseAnd)]

<span data-ttu-id="44252-135">Pour les opérandes `bool`, l’opérateur `&` calcule le [and logique](boolean-logical-operators.md#logical-and-operator-) de ses opérandes.</span><span class="sxs-lookup"><span data-stu-id="44252-135">For `bool` operands, the `&` operator computes the [logical AND](boolean-logical-operators.md#logical-and-operator-) of its operands.</span></span> <span data-ttu-id="44252-136">L’opérateur unaire `&` est [l’opérateur address-of](pointer-related-operators.md#address-of-operator-).</span><span class="sxs-lookup"><span data-stu-id="44252-136">The unary `&` operator is the [address-of operator](pointer-related-operators.md#address-of-operator-).</span></span>

## <a name="logical-exclusive-or-operator-"></a><span data-ttu-id="44252-137">L’opérateur OR exclusif logique ^</span><span class="sxs-lookup"><span data-stu-id="44252-137">Logical exclusive OR operator ^</span></span>

<span data-ttu-id="44252-138">L’opérateur `^` calcule le OR exclusif logique au niveau du bit (également appelé XOR logique au niveau du bit) de ses opérandes.</span><span class="sxs-lookup"><span data-stu-id="44252-138">The `^` operator computes the bitwise logical exclusive OR, also known as the bitwise logical XOR, of its operands:</span></span>

[!code-csharp-interactive[bitwise XOR](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#BitwiseXor)]

<span data-ttu-id="44252-139">Pour les opérandes de `bool`, l’opérateur `^` calcule le [ou exclusif logique](boolean-logical-operators.md#logical-exclusive-or-operator-) de ses opérandes.</span><span class="sxs-lookup"><span data-stu-id="44252-139">For `bool` operands, the `^` operator computes the [logical exclusive OR](boolean-logical-operators.md#logical-exclusive-or-operator-) of its operands.</span></span>

## <a name="logical-or-operator-"></a><span data-ttu-id="44252-140">L’opérateur OU logique |</span><span class="sxs-lookup"><span data-stu-id="44252-140">Logical OR operator |</span></span>

<span data-ttu-id="44252-141">L’opérateur `|` calcule le OR logique au niveau du bit de ses opérandes :</span><span class="sxs-lookup"><span data-stu-id="44252-141">The `|` operator computes the bitwise logical OR of its operands:</span></span>

[!code-csharp-interactive[bitwise OR](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#BitwiseOr)]

<span data-ttu-id="44252-142">Pour les opérandes `bool`, l’opérateur `|` calcule le [or logique](boolean-logical-operators.md#logical-or-operator-) de ses opérandes.</span><span class="sxs-lookup"><span data-stu-id="44252-142">For `bool` operands, the `|` operator computes the [logical OR](boolean-logical-operators.md#logical-or-operator-) of its operands.</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="44252-143">Assignation composée</span><span class="sxs-lookup"><span data-stu-id="44252-143">Compound assignment</span></span>

<span data-ttu-id="44252-144">Pour un opérateur binaire `op`, une expression d’assignation composée du formulaire</span><span class="sxs-lookup"><span data-stu-id="44252-144">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="44252-145">est équivalent à</span><span class="sxs-lookup"><span data-stu-id="44252-145">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="44252-146">sauf que `x` n’est évalué qu’une seule fois.</span><span class="sxs-lookup"><span data-stu-id="44252-146">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="44252-147">L’exemple suivant montre l’utilisation de l’assignation composée avec des opérateurs de décalage et des opérateurs au niveau du bit :</span><span class="sxs-lookup"><span data-stu-id="44252-147">The following example demonstrates the usage of compound assignment with bitwise and shift operators:</span></span>

[!code-csharp-interactive[compound assignment](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#CompoundAssignment)]

<span data-ttu-id="44252-148">En raison des [promotions numériques](~/_csharplang/spec/expressions.md#numeric-promotions), le résultat de l’opération `op` risque de ne pas être implicitement convertible en type `T` de `x`.</span><span class="sxs-lookup"><span data-stu-id="44252-148">Because of [numeric promotions](~/_csharplang/spec/expressions.md#numeric-promotions), the result of the `op` operation might be not implicitly convertible to the type `T` of `x`.</span></span> <span data-ttu-id="44252-149">Dans ce cas, si `op` est un opérateur prédéfini et que le résultat de l’opération est explicitement convertible en type `T` de `x`, une expression d’assignation composée de la forme `x op= y` équivaut à `x = (T)(x op y)`, sauf que `x` n’est évalué qu’une seule fois.</span><span class="sxs-lookup"><span data-stu-id="44252-149">In such a case, if `op` is a predefined operator and the result of the operation is explicitly convertible to the type `T` of `x`, a compound assignment expression of the form `x op= y` is equivalent to `x = (T)(x op y)`, except that `x` is only evaluated once.</span></span> <span data-ttu-id="44252-150">L’exemple suivant illustre ce comportement :</span><span class="sxs-lookup"><span data-stu-id="44252-150">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[compound assignment with cast](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#CompoundAssignmentWithCast)]

## <a name="operator-precedence"></a><span data-ttu-id="44252-151">Priorité des opérateurs</span><span class="sxs-lookup"><span data-stu-id="44252-151">Operator precedence</span></span>

<span data-ttu-id="44252-152">La liste suivante présente les opérateurs au niveau du bit et les opérateurs de décalage par ordre de précédence, de la plus élevée à la plus basse :</span><span class="sxs-lookup"><span data-stu-id="44252-152">The following list orders bitwise and shift operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="44252-153">Opérateur de complément de bits `~`</span><span class="sxs-lookup"><span data-stu-id="44252-153">Bitwise complement operator `~`</span></span>
- <span data-ttu-id="44252-154">Opérateurs de décalage `<<` et `>>`</span><span class="sxs-lookup"><span data-stu-id="44252-154">Shift operators `<<` and `>>`</span></span>
- <span data-ttu-id="44252-155">L’opérateur AND logique `&`</span><span class="sxs-lookup"><span data-stu-id="44252-155">Logical AND operator `&`</span></span>
- <span data-ttu-id="44252-156">Opérateur OR exclusif logique `^`</span><span class="sxs-lookup"><span data-stu-id="44252-156">Logical exclusive OR operator `^`</span></span>
- <span data-ttu-id="44252-157">Opérateur OR logique `|`</span><span class="sxs-lookup"><span data-stu-id="44252-157">Logical OR operator `|`</span></span>

<span data-ttu-id="44252-158">Utilisez des parenthèses, `()`, pour modifier l’ordre d’évaluation imposé par la précédence des opérateurs :</span><span class="sxs-lookup"><span data-stu-id="44252-158">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence:</span></span>

[!code-csharp-interactive[operator precedence](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#Precedence)]

<span data-ttu-id="44252-159">Pour obtenir la liste complète C# des opérateurs classés par niveau de priorité, consultez la section priorité d' [ C# ](index.md) [opérateur](index.md#operator-precedence) de l’article opérateurs.</span><span class="sxs-lookup"><span data-stu-id="44252-159">For the complete list of C# operators ordered by precedence level, see the [Operator precedence](index.md#operator-precedence) section of the [C# operators](index.md) article.</span></span>

## <a name="shift-count-of-the-shift-operators"></a><span data-ttu-id="44252-160">Valeur de décalage des opérateurs de décalage</span><span class="sxs-lookup"><span data-stu-id="44252-160">Shift count of the shift operators</span></span>

<span data-ttu-id="44252-161">Pour les opérateurs de décalage `<<` et `>>`, le type de l’opérande de droite doit être `int` ou un type qui a une [conversion numérique implicite prédéfinie](../builtin-types/numeric-conversions.md#implicit-numeric-conversions) en `int`.</span><span class="sxs-lookup"><span data-stu-id="44252-161">For the shift operators `<<` and `>>`, the type of the right-hand operand must be `int` or a type that has a [predefined implicit numeric conversion](../builtin-types/numeric-conversions.md#implicit-numeric-conversions) to `int`.</span></span>

<span data-ttu-id="44252-162">Pour les expressions `x << count` et `x >> count`, la valeur réelle du décalage varie selon le type de `x` :</span><span class="sxs-lookup"><span data-stu-id="44252-162">For the `x << count` and `x >> count` expressions, the actual shift count depends on the type of `x` as follows:</span></span>

- <span data-ttu-id="44252-163">Si le type de `x` est `int` ou `uint`, le nombre de décalages est défini par les *cinq* bits de poids faible de l’opérande de droite.</span><span class="sxs-lookup"><span data-stu-id="44252-163">If the type of `x` is `int` or `uint`, the shift count is defined by the low-order *five* bits of the right-hand operand.</span></span> <span data-ttu-id="44252-164">La valeur de décalage est donc calculée à partir de `count & 0x1F` (ou de `count & 0b_1_1111`).</span><span class="sxs-lookup"><span data-stu-id="44252-164">That is, the shift count is computed from `count & 0x1F` (or `count & 0b_1_1111`).</span></span>

- <span data-ttu-id="44252-165">Si le type de `x` est `long` ou `ulong`, le nombre de décalages est défini par les *six* bits de poids faible de l’opérande de droite.</span><span class="sxs-lookup"><span data-stu-id="44252-165">If the type of `x` is `long` or `ulong`, the shift count is defined by the low-order *six* bits of the right-hand operand.</span></span> <span data-ttu-id="44252-166">La valeur de décalage est donc calculée à partir de `count & 0x3F` (ou de `count & 0b_11_1111`).</span><span class="sxs-lookup"><span data-stu-id="44252-166">That is, the shift count is computed from `count & 0x3F` (or `count & 0b_11_1111`).</span></span>

<span data-ttu-id="44252-167">L’exemple suivant illustre ce comportement :</span><span class="sxs-lookup"><span data-stu-id="44252-167">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[shift count example](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#ShiftCount)]

## <a name="enumeration-logical-operators"></a><span data-ttu-id="44252-168">Opérateurs logiques d’énumération</span><span class="sxs-lookup"><span data-stu-id="44252-168">Enumeration logical operators</span></span>

<span data-ttu-id="44252-169">Les opérateurs `~`, `&`, `|`et `^` sont également pris en charge par n’importe quel type [énumération](../keywords/enum.md) .</span><span class="sxs-lookup"><span data-stu-id="44252-169">The `~`, `&`, `|`, and `^` operators are also supported by any [enumeration](../keywords/enum.md) type.</span></span> <span data-ttu-id="44252-170">Pour les opérandes du même type d’énumération, une opération logique est effectuée sur les valeurs correspondantes du type intégral sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="44252-170">For operands of the same enumeration type, a logical operation is performed on the corresponding values of the underlying integral type.</span></span> <span data-ttu-id="44252-171">Par exemple, pour tout `x` et `y` d’un type énumération `T` avec un type sous-jacent `U`, l’expression `x & y` produit le même résultat que l’expression `(T)((U)x & (U)y)`.</span><span class="sxs-lookup"><span data-stu-id="44252-171">For example, for any `x` and `y` of an enumeration type `T` with an underlying type `U`, the `x & y` expression produces the same result as the `(T)((U)x & (U)y)` expression.</span></span>

<span data-ttu-id="44252-172">Vous utilisez généralement des opérateurs logiques au niveau du bit avec un type énumération qui est défini à l’aide de l’attribut [Flags](xref:System.FlagsAttribute).</span><span class="sxs-lookup"><span data-stu-id="44252-172">You typically use bitwise logical operators with an enumeration type which is defined with the [Flags](xref:System.FlagsAttribute) attribute.</span></span> <span data-ttu-id="44252-173">Pour plus d’informations, consultez la section [Types énumération comme indicateurs binaires](../../programming-guide/enumeration-types.md#enumeration-types-as-bit-flags) de l’article[Types énumération](../../programming-guide/enumeration-types.md).</span><span class="sxs-lookup"><span data-stu-id="44252-173">For more information, see the [Enumeration types as bit flags](../../programming-guide/enumeration-types.md#enumeration-types-as-bit-flags) section of the [Enumeration types](../../programming-guide/enumeration-types.md) article.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="44252-174">Capacité de surcharge de l’opérateur</span><span class="sxs-lookup"><span data-stu-id="44252-174">Operator overloadability</span></span>

<span data-ttu-id="44252-175">Un type défini par l’utilisateur peut [surcharger](operator-overloading.md) les opérateurs `~`, `<<`, `>>`, `&`, `|` et `^`.</span><span class="sxs-lookup"><span data-stu-id="44252-175">A user-defined type can [overload](operator-overloading.md) the `~`, `<<`, `>>`, `&`, `|`, and `^` operators.</span></span> <span data-ttu-id="44252-176">Quand un opérateur binaire est surchargé, l’opérateur d’assignation composée correspondant est aussi implicitement surchargé.</span><span class="sxs-lookup"><span data-stu-id="44252-176">When a binary operator is overloaded, the corresponding compound assignment operator is also implicitly overloaded.</span></span> <span data-ttu-id="44252-177">Un type défini par l’utilisateur ne peut pas surcharger explicitement un opérateur d’assignation composée.</span><span class="sxs-lookup"><span data-stu-id="44252-177">A user-defined type cannot explicitly overload a compound assignment operator.</span></span>

<span data-ttu-id="44252-178">Si un type `T` défini par l’utilisateur surcharge l’opérateur `<<` ou `>>`, l’opérande de partie gauche doit être de type `T` et l’opérande de partie droite de type `int`.</span><span class="sxs-lookup"><span data-stu-id="44252-178">If a user-defined type `T` overloads the `<<` or `>>` operator, the type of the left-hand operand must be `T` and the type of the right-hand operand must be `int`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="44252-179">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="44252-179">C# language specification</span></span>

<span data-ttu-id="44252-180">Pour plus d’informations, consultez les sections suivantes de la [spécification du langage C#](~/_csharplang/spec/introduction.md) :</span><span class="sxs-lookup"><span data-stu-id="44252-180">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="44252-181">Opérateur de complément de bits</span><span class="sxs-lookup"><span data-stu-id="44252-181">Bitwise complement operator</span></span>](~/_csharplang/spec/expressions.md#bitwise-complement-operator)
- [<span data-ttu-id="44252-182">Opérateurs de décalage</span><span class="sxs-lookup"><span data-stu-id="44252-182">Shift operators</span></span>](~/_csharplang/spec/expressions.md#shift-operators)
- [<span data-ttu-id="44252-183">Opérateurs logiques</span><span class="sxs-lookup"><span data-stu-id="44252-183">Logical operators</span></span>](~/_csharplang/spec/expressions.md#logical-operators)
- [<span data-ttu-id="44252-184">Assignation composée</span><span class="sxs-lookup"><span data-stu-id="44252-184">Compound assignment</span></span>](~/_csharplang/spec/expressions.md#compound-assignment)
- [<span data-ttu-id="44252-185">Promotions numériques</span><span class="sxs-lookup"><span data-stu-id="44252-185">Numeric promotions</span></span>](~/_csharplang/spec/expressions.md#numeric-promotions)

## <a name="see-also"></a><span data-ttu-id="44252-186">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="44252-186">See also</span></span>

- [<span data-ttu-id="44252-187">Informations de référence sur C#</span><span class="sxs-lookup"><span data-stu-id="44252-187">C# reference</span></span>](../index.md)
- [<span data-ttu-id="44252-188">Opérateurs C#</span><span class="sxs-lookup"><span data-stu-id="44252-188">C# operators</span></span>](index.md)
- [<span data-ttu-id="44252-189">Opérateurs logiques booléens</span><span class="sxs-lookup"><span data-stu-id="44252-189">Boolean logical operators</span></span>](boolean-logical-operators.md)
