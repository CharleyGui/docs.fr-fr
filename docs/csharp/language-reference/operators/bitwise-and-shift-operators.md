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
ms.openlocfilehash: bf42a53a89676f457d3d2df8d193a83299c3e4cc
ms.sourcegitcommit: 904b98d8d706f0e2d5ceaa00ce17ffbd92adfb88
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66758373"
---
# <a name="bitwise-and-shift-operators-c-reference"></a><span data-ttu-id="d5b62-103">Opérateurs au niveau du bit et opérateurs de décalage (référence C#)</span><span class="sxs-lookup"><span data-stu-id="d5b62-103">Bitwise and shift operators (C# Reference)</span></span>

<span data-ttu-id="d5b62-104">Les opérateurs suivants effectuent des opérations logiques de décalage ou au niveau du bit avec des opérandes de [types intégraux](../keywords/integral-types-table.md) :</span><span class="sxs-lookup"><span data-stu-id="d5b62-104">The following operators perform bitwise or shift operations with operands of the [integral types](../keywords/integral-types-table.md):</span></span>

- <span data-ttu-id="d5b62-105">Opérateur unaire [`~` (complément de bits)](#bitwise-complement-operator-)</span><span class="sxs-lookup"><span data-stu-id="d5b62-105">Unary [`~` (bitwise complement)](#bitwise-complement-operator-) operator</span></span>
- <span data-ttu-id="d5b62-106">Opérateurs de décalage binaires [`<<` (décalage gauche)](#left-shift-operator-) et [`>>` (décalage droite)](#right-shift-operator-)</span><span class="sxs-lookup"><span data-stu-id="d5b62-106">Binary [`<<` (left shift)](#left-shift-operator-) and [`>>` (right shift)](#right-shift-operator-) shift operators</span></span>
- <span data-ttu-id="d5b62-107">Opérateurs binaires [`&` (AND logique)](#logical-and-operator-), [`|` (OR logique)](#logical-or-operator-) et [`^` (OR exclusif logique)](#logical-exclusive-or-operator-)</span><span class="sxs-lookup"><span data-stu-id="d5b62-107">Binary [`&` (logical AND)](#logical-and-operator-), [`|` (logical OR)](#logical-or-operator-), and [`^` (logical exclusive OR)](#logical-exclusive-or-operator-) operators</span></span>

<span data-ttu-id="d5b62-108">Ces opérateurs sont définis pour les types `int`, `uint`, `long` et `ulong`.</span><span class="sxs-lookup"><span data-stu-id="d5b62-108">Those operators are defined for the `int`, `uint`, `long`, and `ulong` types.</span></span> <span data-ttu-id="d5b62-109">Lorsque les deux opérandes sont d’autres types intégraux (`sbyte`, `byte`, `short`, `ushort` ou `char`), leurs valeurs sont converties en valeurs de type `int`, qui est également le type de résultat d’une opération.</span><span class="sxs-lookup"><span data-stu-id="d5b62-109">When both operands are of other integral types (`sbyte`, `byte`, `short`, `ushort`, or `char`), their values are converted to the `int` type, which is also the result type of an operation.</span></span> <span data-ttu-id="d5b62-110">Lorsque les opérandes sont de différents types intégraux, leurs valeurs sont converties vers le type intégral le plus proche.</span><span class="sxs-lookup"><span data-stu-id="d5b62-110">When operands are of different integral types, their values are converted to the closest containing integral type.</span></span> <span data-ttu-id="d5b62-111">Pour plus d’informations, consultez la section [Promotions numériques](~/_csharplang/spec/expressions.md#numeric-promotions) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="d5b62-111">For more information, see the [Numeric promotions](~/_csharplang/spec/expressions.md#numeric-promotions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="d5b62-112">Les opérateurs `&`, `|` et `^` sont également définis pour les opérandes de type `bool`.</span><span class="sxs-lookup"><span data-stu-id="d5b62-112">The `&`, `|`, and `^` operators are also defined for the operands of the `bool` type.</span></span> <span data-ttu-id="d5b62-113">Pour plus d’informations, consultez [Opérateurs logiques booléens](boolean-logical-operators.md).</span><span class="sxs-lookup"><span data-stu-id="d5b62-113">For more information, see [Boolean logical operators](boolean-logical-operators.md).</span></span>

<span data-ttu-id="d5b62-114">Les opérations de décalage et au niveau du bit ne provoquent jamais de dépassements de capacité et donnent les mêmes résultats dans des contextes [checked et unchecked](../keywords/checked-and-unchecked.md).</span><span class="sxs-lookup"><span data-stu-id="d5b62-114">Bitwise and shift operations never cause overflow and produce the same results in [checked and unchecked](../keywords/checked-and-unchecked.md) contexts.</span></span>

## <a name="bitwise-complement-operator-"></a><span data-ttu-id="d5b62-115">Opérateur de complément de bits ~</span><span class="sxs-lookup"><span data-stu-id="d5b62-115">Bitwise complement operator ~</span></span>

<span data-ttu-id="d5b62-116">L’opérateur `~` produit un complément de bits de son opérande en inversant chaque bit :</span><span class="sxs-lookup"><span data-stu-id="d5b62-116">The `~` operator produces a bitwise complement of its operand by reversing each bit:</span></span>

[!code-csharp-interactive[bitwise NOT](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#BitwiseComplement)]

<span data-ttu-id="d5b62-117">Vous pouvez également utiliser le symbole `~` pour déclarer des finaliseurs.</span><span class="sxs-lookup"><span data-stu-id="d5b62-117">You can also use the `~` symbol to declare finalizers.</span></span> <span data-ttu-id="d5b62-118">Pour plus d’informations, consultez [Finaliseurs](../../programming-guide/classes-and-structs/destructors.md).</span><span class="sxs-lookup"><span data-stu-id="d5b62-118">For more information, see [Finalizers](../../programming-guide/classes-and-structs/destructors.md).</span></span>

## <a name="left-shift-operator-"></a><span data-ttu-id="d5b62-119">Opérateur de décalage gauche \<\<</span><span class="sxs-lookup"><span data-stu-id="d5b62-119">Left-shift operator \<\<</span></span>

<span data-ttu-id="d5b62-120">L’opérateur `<<` décale son premier opérande vers la gauche du nombre de bits spécifié par son deuxième opérande.</span><span class="sxs-lookup"><span data-stu-id="d5b62-120">The `<<` operator shifts its first operand left by the number of bits defined by its second operand.</span></span>

<span data-ttu-id="d5b62-121">L’opération de décalage gauche supprime les bits d’ordre supérieur qui sont en dehors de la plage du type de résultat, et définit les positions de bits vides d’ordre inférieur sur zéro, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="d5b62-121">The left-shift operation discards the high-order bits that are outside the range of the result type and sets the low-order empty bit positions to zero, as the following example shows:</span></span>

[!code-csharp-interactive[left shift](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#LeftShift)]

<span data-ttu-id="d5b62-122">Étant donné que les opérateurs de décalage sont définis uniquement pour les types `int`, `uint`, `long` et `ulong`, le résultat d’une opération contient toujours au moins 32 bits.</span><span class="sxs-lookup"><span data-stu-id="d5b62-122">Because the shift operators are defined only for the `int`, `uint`, `long`, and `ulong` types, the result of an operation always contains at least 32 bits.</span></span> <span data-ttu-id="d5b62-123">Si le premier opérande est d’un autre type intégral (`sbyte`, `byte`, `short`, `ushort` ou `char`), sa valeur est convertie en une valeur de type `int`, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="d5b62-123">If the first operand is of another integral type (`sbyte`, `byte`, `short`, `ushort`, or `char`), its value is converted to the `int` type, as the following example shows:</span></span>

[!code-csharp-interactive[left shift with promotion](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#LeftShiftPromoted)]

<span data-ttu-id="d5b62-124">Pour plus d’informations sur la façon dont le deuxième opérande de l’opérateur `<<` définit la valeur de décalage, consultez la section [Valeur de décalage des opérateurs de décalage](#shift-count-of-the-shift-operators).</span><span class="sxs-lookup"><span data-stu-id="d5b62-124">For information about how the second operand of the `<<` operator defines the shift count, see the [Shift count of the shift operators](#shift-count-of-the-shift-operators) section.</span></span>

## <a name="right-shift-operator-"></a><span data-ttu-id="d5b62-125">Opérateur de décalage vers la droite >></span><span class="sxs-lookup"><span data-stu-id="d5b62-125">Right-shift operator >></span></span>

<span data-ttu-id="d5b62-126">L’opérateur `>>` décale son premier opérande vers la droite du nombre de bits spécifié par son deuxième opérande.</span><span class="sxs-lookup"><span data-stu-id="d5b62-126">The `>>` operator shifts its first operand right by the number of bits defined by its second operand.</span></span>

<span data-ttu-id="d5b62-127">L’opération de décalage vers la droite ignore les bits d’ordre inférieur, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="d5b62-127">The right-shift operation discards the low-order bits, as the following example shows:</span></span>

[!code-csharp-interactive[right shift](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#RightShift)]

<span data-ttu-id="d5b62-128">Les positions de bits vides d’ordre supérieur sont définies en fonction du type du premier opérande comme suit :</span><span class="sxs-lookup"><span data-stu-id="d5b62-128">The high-order empty bit positions are set based on the type of the first operand as follows:</span></span>

- <span data-ttu-id="d5b62-129">si le premier opérande est de type [int](../keywords/int.md) ou [long](../keywords/long.md), l’opérateur de décalage vers la droite effectue un décalage *arithmétique* : la valeur du bit le plus significatif (le bit de signe) du premier opérande est propagée vers les positions des bits vides d’ordre supérieur.</span><span class="sxs-lookup"><span data-stu-id="d5b62-129">If the first operand is of type [int](../keywords/int.md) or [long](../keywords/long.md), the right-shift operator performs an *arithmetic* shift: the value of the most significant bit (the sign bit) of the first operand is propagated to the high-order empty bit positions.</span></span> <span data-ttu-id="d5b62-130">Autrement dit, les positions de bits vides d’ordre supérieur sont définies sur zéro si le premier opérande n’est pas négatif et sur un s’il est négatif.</span><span class="sxs-lookup"><span data-stu-id="d5b62-130">That is, the high-order empty bit positions are set to zero if the first operand is non-negative and set to one if it's negative.</span></span>

  [!code-csharp-interactive[arithmetic right shift](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#ArithmeticRightShift)]

- <span data-ttu-id="d5b62-131">Si le premier opérande est de type [uint](../keywords/uint.md) ou [ulong](../keywords/ulong.md), l’opérateur de décalage vers la droite effectue un décalage *logique* : les positions des bits vides d’ordre supérieur sont toujours définies sur zéro.</span><span class="sxs-lookup"><span data-stu-id="d5b62-131">If the first operand is of type [uint](../keywords/uint.md) or [ulong](../keywords/ulong.md), the right-shift operator performs a *logical* shift: the high-order empty bit positions are always set to zero.</span></span>

  [!code-csharp-interactive[logical right shift](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#LogicalRightShift)]

<span data-ttu-id="d5b62-132">Pour plus d’informations sur la façon dont le deuxième opérande de l’opérateur `>>` définit la valeur de décalage, consultez la section [Valeur de décalage des opérateurs de décalage](#shift-count-of-the-shift-operators).</span><span class="sxs-lookup"><span data-stu-id="d5b62-132">For information about how the second operand of the `>>` operator defines the shift count, see the [Shift count of the shift operators](#shift-count-of-the-shift-operators) section.</span></span>

## <a name="logical-and-operator-amp"></a><span data-ttu-id="d5b62-133">L’opérateur AND logique &amp;</span><span class="sxs-lookup"><span data-stu-id="d5b62-133">Logical AND operator &amp;</span></span>

<span data-ttu-id="d5b62-134">L’opérateur `&` calcule le AND logique au niveau du bit de ses opérandes :</span><span class="sxs-lookup"><span data-stu-id="d5b62-134">The `&` operator computes the bitwise logical AND of its operands:</span></span>

[!code-csharp-interactive[bitwise AND](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#BitwiseAnd)]

<span data-ttu-id="d5b62-135">Pour les opérandes de type `bool`, l’opérateur `&` calcule le [AND logique](boolean-logical-operators.md#logical-and-operator-) de ses opérandes.</span><span class="sxs-lookup"><span data-stu-id="d5b62-135">For the operands of the `bool` type, the `&` operator computes the [logical AND](boolean-logical-operators.md#logical-and-operator-) of its operands.</span></span> <span data-ttu-id="d5b62-136">L’opérateur unaire `&` est [l’opérateur address-of](pointer-related-operators.md#address-of-operator-).</span><span class="sxs-lookup"><span data-stu-id="d5b62-136">The unary `&` operator is the [address-of operator](pointer-related-operators.md#address-of-operator-).</span></span>

## <a name="logical-exclusive-or-operator-"></a><span data-ttu-id="d5b62-137">L’opérateur OR exclusif logique ^</span><span class="sxs-lookup"><span data-stu-id="d5b62-137">Logical exclusive OR operator ^</span></span>

<span data-ttu-id="d5b62-138">L’opérateur `^` calcule le OR exclusif logique au niveau du bit (également appelé XOR logique au niveau du bit) de ses opérandes.</span><span class="sxs-lookup"><span data-stu-id="d5b62-138">The `^` operator computes the bitwise logical exclusive OR, also known as the bitwise logical XOR, of its operands:</span></span>

[!code-csharp-interactive[bitwise XOR](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#BitwiseXor)]

<span data-ttu-id="d5b62-139">Pour les opérandes de type `bool`, l’opérateur `^` calcule le [OR exclusif logique](boolean-logical-operators.md#logical-exclusive-or-operator-) de ses opérandes.</span><span class="sxs-lookup"><span data-stu-id="d5b62-139">For the operands of the `bool` type, the `^` operator computes the [logical exclusive OR](boolean-logical-operators.md#logical-exclusive-or-operator-) of its operands.</span></span>

## <a name="logical-or-operator-"></a><span data-ttu-id="d5b62-140">L’opérateur OU logique |</span><span class="sxs-lookup"><span data-stu-id="d5b62-140">Logical OR operator |</span></span>

<span data-ttu-id="d5b62-141">L’opérateur `|` calcule le OR logique au niveau du bit de ses opérandes :</span><span class="sxs-lookup"><span data-stu-id="d5b62-141">The `|` operator computes the bitwise logical OR of its operands:</span></span>

[!code-csharp-interactive[bitwise OR](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#BitwiseOr)]

<span data-ttu-id="d5b62-142">Pour les opérandes de type `bool`, l’opérateur `|` calcule le [OR logique](boolean-logical-operators.md#logical-or-operator-) de ses opérandes.</span><span class="sxs-lookup"><span data-stu-id="d5b62-142">For the operands of the `bool` type, the `|` operator computes the [logical OR](boolean-logical-operators.md#logical-or-operator-) of its operands.</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="d5b62-143">Assignation composée</span><span class="sxs-lookup"><span data-stu-id="d5b62-143">Compound assignment</span></span>

<span data-ttu-id="d5b62-144">Pour un opérateur binaire `op`, une expression d’assignation composée du formulaire</span><span class="sxs-lookup"><span data-stu-id="d5b62-144">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="d5b62-145">est équivalent à</span><span class="sxs-lookup"><span data-stu-id="d5b62-145">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="d5b62-146">sauf que `x` n’est évalué qu’une seule fois.</span><span class="sxs-lookup"><span data-stu-id="d5b62-146">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="d5b62-147">L’exemple suivant montre l’utilisation de l’assignation composée avec des opérateurs de décalage et des opérateurs au niveau du bit :</span><span class="sxs-lookup"><span data-stu-id="d5b62-147">The following example demonstrates the usage of compound assignment with bitwise and shift operators:</span></span>

[!code-csharp-interactive[compound assignment](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#CompoundAssignment)]

<span data-ttu-id="d5b62-148">En raison des [promotions numériques](~/_csharplang/spec/expressions.md#numeric-promotions), le résultat de l’opération `op` risque de ne pas être implicitement convertible en type `T` de `x`.</span><span class="sxs-lookup"><span data-stu-id="d5b62-148">Because of [numeric promotions](~/_csharplang/spec/expressions.md#numeric-promotions), the result of the `op` operation might be not implicitly convertible to the type `T` of `x`.</span></span> <span data-ttu-id="d5b62-149">Dans ce cas, si `op` est un opérateur prédéfini et que le résultat de l’opération est explicitement convertible en type `T` de `x`, une expression d’assignation composée de la forme `x op= y` équivaut à `x = (T)(x op y)`, sauf que `x` n’est évalué qu’une seule fois.</span><span class="sxs-lookup"><span data-stu-id="d5b62-149">In such a case, if `op` is a predefined operator and the result of the operation is explicitly convertible to the type `T` of `x`, a compound assignment expression of the form `x op= y` is equivalent to `x = (T)(x op y)`, except that `x` is only evaluated once.</span></span> <span data-ttu-id="d5b62-150">L’exemple suivant illustre ce comportement :</span><span class="sxs-lookup"><span data-stu-id="d5b62-150">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[compound assignment with cast](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#CompoundAssignmentWithCast)]

## <a name="operator-precedence"></a><span data-ttu-id="d5b62-151">Précédence des opérateurs</span><span class="sxs-lookup"><span data-stu-id="d5b62-151">Operator precedence</span></span>

<span data-ttu-id="d5b62-152">La liste suivante présente les opérateurs au niveau du bit et les opérateurs de décalage par ordre de précédence, de la plus élevée à la plus basse :</span><span class="sxs-lookup"><span data-stu-id="d5b62-152">The following list orders bitwise and shift operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="d5b62-153">Opérateur de complément de bits `~`</span><span class="sxs-lookup"><span data-stu-id="d5b62-153">Bitwise complement operator `~`</span></span>
- <span data-ttu-id="d5b62-154">Opérateurs de décalage `<<` et `>>`</span><span class="sxs-lookup"><span data-stu-id="d5b62-154">Shift operators `<<` and `>>`</span></span>
- <span data-ttu-id="d5b62-155">L’opérateur AND logique `&`</span><span class="sxs-lookup"><span data-stu-id="d5b62-155">Logical AND operator `&`</span></span>
- <span data-ttu-id="d5b62-156">Opérateur OR exclusif logique `^`</span><span class="sxs-lookup"><span data-stu-id="d5b62-156">Logical exclusive OR operator `^`</span></span>
- <span data-ttu-id="d5b62-157">Opérateur OR logique `|`</span><span class="sxs-lookup"><span data-stu-id="d5b62-157">Logical OR operator `|`</span></span>

<span data-ttu-id="d5b62-158">Utilisez des parenthèses, `()`, pour modifier l’ordre d’évaluation imposé par la précédence des opérateurs :</span><span class="sxs-lookup"><span data-stu-id="d5b62-158">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence:</span></span>

[!code-csharp-interactive[operator precedence](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#Precedence)]

<span data-ttu-id="d5b62-159">Pour obtenir la liste complète des opérateurs C# classés par niveau de priorité, consultez [Opérateurs C#](index.md).</span><span class="sxs-lookup"><span data-stu-id="d5b62-159">For the complete list of C# operators ordered by precedence level, see [C# operators](index.md).</span></span>

## <a name="shift-count-of-the-shift-operators"></a><span data-ttu-id="d5b62-160">Valeur de décalage des opérateurs de décalage</span><span class="sxs-lookup"><span data-stu-id="d5b62-160">Shift count of the shift operators</span></span>

<span data-ttu-id="d5b62-161">Pour les opérateurs de décalage `<<` et `>>`, le deuxième opérande doit être de type [int](../keywords/int.md) ou d’un type pour lequel une [conversion numérique implicite prédéfinie](../keywords/implicit-numeric-conversions-table.md) est effectuée vers `int`.</span><span class="sxs-lookup"><span data-stu-id="d5b62-161">For the shift operators `<<` and `>>`, the type of the second operand must be [int](../keywords/int.md) or a type that has a [predefined implicit numeric conversion](../keywords/implicit-numeric-conversions-table.md) to `int`.</span></span>

<span data-ttu-id="d5b62-162">Pour les expressions `x << count` et `x >> count`, la valeur réelle du décalage varie selon le type de `x` :</span><span class="sxs-lookup"><span data-stu-id="d5b62-162">For the `x << count` and `x >> count` expressions, the actual shift count depends on the type of `x` as follows:</span></span>

- <span data-ttu-id="d5b62-163">Si le type `x` est [int](../keywords/int.md) ou [uint](../keywords/uint.md), la valeur du décalage est définie par les *cinq* bits d’ordre inférieur du deuxième opérande.</span><span class="sxs-lookup"><span data-stu-id="d5b62-163">If the type of `x` is [int](../keywords/int.md) or [uint](../keywords/uint.md), the shift count is defined by the low-order *five* bits of the second operand.</span></span> <span data-ttu-id="d5b62-164">La valeur de décalage est donc calculée à partir de `count & 0x1F` (ou de `count & 0b_1_1111`).</span><span class="sxs-lookup"><span data-stu-id="d5b62-164">That is, the shift count is computed from `count & 0x1F` (or `count & 0b_1_1111`).</span></span>

- <span data-ttu-id="d5b62-165">Si le type `x` est [long](../keywords/long.md) ou [ulong](../keywords/ulong.md), la valeur du décalage est définie par les *six* bits d’ordre inférieur du deuxième opérande.</span><span class="sxs-lookup"><span data-stu-id="d5b62-165">If the type of `x` is [long](../keywords/long.md) or [ulong](../keywords/ulong.md), the shift count is defined by the low-order *six* bits of the second operand.</span></span> <span data-ttu-id="d5b62-166">La valeur de décalage est donc calculée à partir de `count & 0x3F` (ou de `count & 0b_11_1111`).</span><span class="sxs-lookup"><span data-stu-id="d5b62-166">That is, the shift count is computed from `count & 0x3F` (or `count & 0b_11_1111`).</span></span>

<span data-ttu-id="d5b62-167">L’exemple suivant illustre ce comportement :</span><span class="sxs-lookup"><span data-stu-id="d5b62-167">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[shift count example](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#ShiftCount)]

## <a name="enumeration-logical-operators"></a><span data-ttu-id="d5b62-168">Opérateurs logiques d’énumération</span><span class="sxs-lookup"><span data-stu-id="d5b62-168">Enumeration logical operators</span></span>

<span data-ttu-id="d5b62-169">Les opérateurs `~`, `&`, `|` et `^` sont également définis pour tous les types d’[énumération](../keywords/enum.md).</span><span class="sxs-lookup"><span data-stu-id="d5b62-169">The `~`, `&`, `|`, and `^` operators are also defined for any [enumeration](../keywords/enum.md) type.</span></span> <span data-ttu-id="d5b62-170">Pour les opérandes du même type énumération, une opération logique est effectuée sur les valeurs correspondantes du type intégral sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="d5b62-170">For the operands of the same enumeration type, a logical operation is performed on the corresponding values of the underlying integral type.</span></span> <span data-ttu-id="d5b62-171">Par exemple, pour tout `x` et `y` d’un type énumération `T` avec un type sous-jacent `U`, l’expression `x & y` produit le même résultat que l’expression `(T)((U)x & (U)y)`.</span><span class="sxs-lookup"><span data-stu-id="d5b62-171">For example, for any `x` and `y` of an enumeration type `T` with an underlying type `U`, the `x & y` expression produces the same result as the `(T)((U)x & (U)y)` expression.</span></span>

<span data-ttu-id="d5b62-172">Vous utilisez généralement des opérateurs logiques au niveau du bit avec un type énumération qui est défini à l’aide de l’attribut [Flags](xref:System.FlagsAttribute).</span><span class="sxs-lookup"><span data-stu-id="d5b62-172">You typically use bitwise logical operators with an enumeration type which is defined with the [Flags](xref:System.FlagsAttribute) attribute.</span></span> <span data-ttu-id="d5b62-173">Pour plus d’informations, consultez la section [Types énumération comme indicateurs binaires](../../programming-guide/enumeration-types.md#enumeration-types-as-bit-flags) de l’article[Types énumération](../../programming-guide/enumeration-types.md).</span><span class="sxs-lookup"><span data-stu-id="d5b62-173">For more information, see the [Enumeration types as bit flags](../../programming-guide/enumeration-types.md#enumeration-types-as-bit-flags) section of the [Enumeration types](../../programming-guide/enumeration-types.md) article.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="d5b62-174">Capacité de surcharge de l’opérateur</span><span class="sxs-lookup"><span data-stu-id="d5b62-174">Operator overloadability</span></span>

<span data-ttu-id="d5b62-175">Un type défini par l’utilisateur peut [surcharger](../keywords/operator.md) les opérateurs `~`, `<<`, `>>`, `&`, `|` et `^`.</span><span class="sxs-lookup"><span data-stu-id="d5b62-175">A user-defined type can [overload](../keywords/operator.md) the `~`, `<<`, `>>`, `&`, `|`, and `^` operators.</span></span> <span data-ttu-id="d5b62-176">Quand un opérateur binaire est surchargé, l’opérateur d’assignation composée correspondant est aussi implicitement surchargé.</span><span class="sxs-lookup"><span data-stu-id="d5b62-176">When a binary operator is overloaded, the corresponding compound assignment operator is also implicitly overloaded.</span></span> <span data-ttu-id="d5b62-177">Un type défini par l’utilisateur ne peut pas surcharger explicitement un opérateur d’assignation composée.</span><span class="sxs-lookup"><span data-stu-id="d5b62-177">A user-defined type cannot explicitly overload a compound assignment operator.</span></span>

<span data-ttu-id="d5b62-178">Si un type `T` défini par l’utilisateur surcharge l’opérateur `<<` ou `>>`, le premier opérande doit être de type `T` et le deuxième de type `int`.</span><span class="sxs-lookup"><span data-stu-id="d5b62-178">If a user-defined type `T` overloads the `<<` or `>>` operator, the type of the first operand must be `T` and the type of the second operand must be `int`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="d5b62-179">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="d5b62-179">C# language specification</span></span>

<span data-ttu-id="d5b62-180">Pour plus d’informations, consultez les sections suivantes de la [spécification du langage C#](~/_csharplang/spec/introduction.md) :</span><span class="sxs-lookup"><span data-stu-id="d5b62-180">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="d5b62-181">Opérateur de complément de bits</span><span class="sxs-lookup"><span data-stu-id="d5b62-181">Bitwise complement operator</span></span>](~/_csharplang/spec/expressions.md#bitwise-complement-operator)
- [<span data-ttu-id="d5b62-182">Opérateurs de décalage</span><span class="sxs-lookup"><span data-stu-id="d5b62-182">Shift operators</span></span>](~/_csharplang/spec/expressions.md#shift-operators)
- [<span data-ttu-id="d5b62-183">Opérateurs logiques</span><span class="sxs-lookup"><span data-stu-id="d5b62-183">Logical operators</span></span>](~/_csharplang/spec/expressions.md#logical-operators)
- [<span data-ttu-id="d5b62-184">Assignation composée</span><span class="sxs-lookup"><span data-stu-id="d5b62-184">Compound assignment</span></span>](~/_csharplang/spec/expressions.md#compound-assignment)
- [<span data-ttu-id="d5b62-185">Promotions numériques</span><span class="sxs-lookup"><span data-stu-id="d5b62-185">Numeric promotions</span></span>](~/_csharplang/spec/expressions.md#numeric-promotions)

## <a name="see-also"></a><span data-ttu-id="d5b62-186">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d5b62-186">See also</span></span>

- [<span data-ttu-id="d5b62-187">Référence C#</span><span class="sxs-lookup"><span data-stu-id="d5b62-187">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="d5b62-188">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="d5b62-188">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="d5b62-189">Opérateurs C#</span><span class="sxs-lookup"><span data-stu-id="d5b62-189">C# Operators</span></span>](index.md)
- [<span data-ttu-id="d5b62-190">Opérateurs logiques booléens</span><span class="sxs-lookup"><span data-stu-id="d5b62-190">Boolean logical operators</span></span>](boolean-logical-operators.md)
