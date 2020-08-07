---
title: Opérateurs arithmétiques - Référence C#
description: Découvrez les opérateurs C# qui effectuent des opérations de multiplication, division, reste, addition et soustraction avec des types numériques.
ms.date: 05/11/2020
author: pkulikov
f1_keywords:
- ++_CSharpKeyword
- --_CSharpKeyword
- '*_CSharpKeyword'
- /_CSharpKeyword
- '%_CSharpKeyword'
- +_CSharpKeyword
- -_CSharpKeyword
- '%=_CSharpKeyword'
- '*=_CSharpKeyword'
helpviewer_keywords:
- arithmetic operators [C#]
- increment operator [C#]
- ++ operator [C#]
- decrement operator [C#]
- -- operator [C#]
- multiplication operator [C#]
- '* operator [C#]'
- division operator [C#]
- / operator [C#]
- remainder operator [C#]
- '% operator [C#]'
- addition operator [C#]
- + operator [C#]
- subtraction operator [C#]
- '- operator [C#]'
ms.openlocfilehash: f5da9c4433ffcf3e6a110bbb1543343289240778
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2020
ms.locfileid: "87916946"
---
# <a name="arithmetic-operators-c-reference"></a><span data-ttu-id="dbb93-103">Opérateurs arithmétiques (référence C#)</span><span class="sxs-lookup"><span data-stu-id="dbb93-103">Arithmetic operators (C# reference)</span></span>

<span data-ttu-id="dbb93-104">Les opérateurs suivants effectuent des opérations arithmétiques avec des opérandes de types numériques :</span><span class="sxs-lookup"><span data-stu-id="dbb93-104">The following operators perform arithmetic operations with operands of numeric types:</span></span>

- <span data-ttu-id="dbb93-105">Opérateurs unaires [ `++` (incrémentation](#increment-operator-)), [ `--` (décrémentation)](#decrement-operator---), [ `+` (plus)](#unary-plus-and-minus-operators)et [ `-` (moins)](#unary-plus-and-minus-operators)</span><span class="sxs-lookup"><span data-stu-id="dbb93-105">Unary [`++` (increment)](#increment-operator-), [`--` (decrement)](#decrement-operator---), [`+` (plus)](#unary-plus-and-minus-operators), and [`-` (minus)](#unary-plus-and-minus-operators) operators</span></span>
- <span data-ttu-id="dbb93-106">Opérateurs binaires [ `*` (multiplication](#multiplication-operator-)), ( [ `/` Division)](#division-operator-), [ `%` (reste)](#remainder-operator-), [ `+` (addition)](#addition-operator-)et [ `-` (soustraction)](#subtraction-operator--)</span><span class="sxs-lookup"><span data-stu-id="dbb93-106">Binary [`*` (multiplication)](#multiplication-operator-), [`/` (division)](#division-operator-), [`%` (remainder)](#remainder-operator-), [`+` (addition)](#addition-operator-), and [`-` (subtraction)](#subtraction-operator--) operators</span></span>

<span data-ttu-id="dbb93-107">Ces opérateurs sont pris en charge par tous les types numériques [intégraux](../builtin-types/integral-numeric-types.md) et [à virgule flottante](../builtin-types/floating-point-numeric-types.md) .</span><span class="sxs-lookup"><span data-stu-id="dbb93-107">Those operators are supported by all [integral](../builtin-types/integral-numeric-types.md) and [floating-point](../builtin-types/floating-point-numeric-types.md) numeric types.</span></span>

<span data-ttu-id="dbb93-108">Dans le cas des types intégraux, ces opérateurs (à l’exception des `++` `--` opérateurs et) sont définis pour les `int` `uint` types,, `long` et `ulong` .</span><span class="sxs-lookup"><span data-stu-id="dbb93-108">In the case of integral types, those operators (except the `++` and `--` operators) are defined for the `int`, `uint`, `long`, and `ulong` types.</span></span> <span data-ttu-id="dbb93-109">Lorsque les opérandes sont d’autres types intégraux ( `sbyte` , `byte` ,, `short` `ushort` ou `char` ), leurs valeurs sont converties vers le `int` type, qui est également le type de résultat d’une opération.</span><span class="sxs-lookup"><span data-stu-id="dbb93-109">When operands are of other integral types (`sbyte`, `byte`, `short`, `ushort`, or `char`), their values are converted to the `int` type, which is also the result type of an operation.</span></span> <span data-ttu-id="dbb93-110">Quand les opérandes sont de types intégraux ou à virgule flottante différents, leurs valeurs sont converties dans le type conteneur le plus proche, si un tel type existe.</span><span class="sxs-lookup"><span data-stu-id="dbb93-110">When operands are of different integral or floating-point types, their values are converted to the closest containing type, if such a type exists.</span></span> <span data-ttu-id="dbb93-111">Pour plus d’informations, consultez la section [Promotions numériques](~/_csharplang/spec/expressions.md#numeric-promotions) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="dbb93-111">For more information, see the [Numeric promotions](~/_csharplang/spec/expressions.md#numeric-promotions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span> <span data-ttu-id="dbb93-112">Les `++` `--` opérateurs et sont définis pour tous les types numériques intégraux et à virgule flottante, ainsi que le type [char](../builtin-types/char.md) .</span><span class="sxs-lookup"><span data-stu-id="dbb93-112">The `++` and `--` operators are defined for all integral and floating-point numeric types and the [char](../builtin-types/char.md) type.</span></span>

## <a name="increment-operator-"></a><span data-ttu-id="dbb93-113">Opérateur d’incrémentation ++</span><span class="sxs-lookup"><span data-stu-id="dbb93-113">Increment operator ++</span></span>

<span data-ttu-id="dbb93-114">L’opérateur d’incrémentation unaire `++` incrémente son opérande de 1.</span><span class="sxs-lookup"><span data-stu-id="dbb93-114">The unary increment operator `++` increments its operand by 1.</span></span> <span data-ttu-id="dbb93-115">L’opérande doit être une variable, un accès [propriété](../../programming-guide/classes-and-structs/properties.md) ou un accès [indexeur](../../programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="dbb93-115">The operand must be a variable, a [property](../../programming-guide/classes-and-structs/properties.md) access, or an [indexer](../../programming-guide/indexers/index.md) access.</span></span>

<span data-ttu-id="dbb93-116">L’opérateur d’incrémentation est pris en charge sous deux formes : l’opérateur d’incrémentation suffixé, `x++`, et l’opérateur d’incrémentation préfixé, `++x`.</span><span class="sxs-lookup"><span data-stu-id="dbb93-116">The increment operator is supported in two forms: the postfix increment operator, `x++`, and the prefix increment operator, `++x`.</span></span>

### <a name="postfix-increment-operator"></a><span data-ttu-id="dbb93-117">Opérateur d'incrément suffixé</span><span class="sxs-lookup"><span data-stu-id="dbb93-117">Postfix increment operator</span></span>

<span data-ttu-id="dbb93-118">Le résultat de `x++` est la valeur de `x` *avant* l’opération, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="dbb93-118">The result of `x++` is the value of `x` *before* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[postfix increment](snippets/shared/ArithmeticOperators.cs#PostfixIncrement)]

### <a name="prefix-increment-operator"></a><span data-ttu-id="dbb93-119">Opérateur d'incrémentation préfixé</span><span class="sxs-lookup"><span data-stu-id="dbb93-119">Prefix increment operator</span></span>

<span data-ttu-id="dbb93-120">Le résultat de `++x` est la valeur de `x` *après* l’opération, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="dbb93-120">The result of `++x` is the value of `x` *after* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[prefix increment](snippets/shared/ArithmeticOperators.cs#PrefixIncrement)]

## <a name="decrement-operator---"></a><span data-ttu-id="dbb93-121">Opérateur de décrémentation --</span><span class="sxs-lookup"><span data-stu-id="dbb93-121">Decrement operator --</span></span>

<span data-ttu-id="dbb93-122">L’opérateur de décrémentation unaire `--` décrémente son opérande de 1.</span><span class="sxs-lookup"><span data-stu-id="dbb93-122">The unary decrement operator `--` decrements its operand by 1.</span></span> <span data-ttu-id="dbb93-123">L’opérande doit être une variable, un accès [propriété](../../programming-guide/classes-and-structs/properties.md) ou un accès [indexeur](../../programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="dbb93-123">The operand must be a variable, a [property](../../programming-guide/classes-and-structs/properties.md) access, or an [indexer](../../programming-guide/indexers/index.md) access.</span></span>

<span data-ttu-id="dbb93-124">L’opérateur de décrémentation est pris en charge sous deux formes : l’opérateur de décrémentation suffixé, `x--`, et l’opérateur de décrémentation préfixé, `--x`.</span><span class="sxs-lookup"><span data-stu-id="dbb93-124">The decrement operator is supported in two forms: the postfix decrement operator, `x--`, and the prefix decrement operator, `--x`.</span></span>

### <a name="postfix-decrement-operator"></a><span data-ttu-id="dbb93-125">Opérateur de décrémentation suffixé</span><span class="sxs-lookup"><span data-stu-id="dbb93-125">Postfix decrement operator</span></span>

<span data-ttu-id="dbb93-126">Le résultat de `x--` est la valeur de `x` *avant* l’opération, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="dbb93-126">The result of `x--` is the value of `x` *before* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[postfix decrement](snippets/shared/ArithmeticOperators.cs#PostfixDecrement)]

### <a name="prefix-decrement-operator"></a><span data-ttu-id="dbb93-127">Opérateur de décrémentation préfixé</span><span class="sxs-lookup"><span data-stu-id="dbb93-127">Prefix decrement operator</span></span>

<span data-ttu-id="dbb93-128">Le résultat de `--x` est la valeur de `x` *après* l’opération, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="dbb93-128">The result of `--x` is the value of `x` *after* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[prefix decrement](snippets/shared/ArithmeticOperators.cs#PrefixDecrement)]

## <a name="unary-plus-and-minus-operators"></a><span data-ttu-id="dbb93-129">Opérateurs plus et moins unaires</span><span class="sxs-lookup"><span data-stu-id="dbb93-129">Unary plus and minus operators</span></span>

<span data-ttu-id="dbb93-130">L’opérateur unaire `+` retourne la valeur de son opérande.</span><span class="sxs-lookup"><span data-stu-id="dbb93-130">The unary `+` operator returns the value of its operand.</span></span> <span data-ttu-id="dbb93-131">L’opérateur unaire `-` calcule la négation numérique de son opérande.</span><span class="sxs-lookup"><span data-stu-id="dbb93-131">The unary `-` operator computes the numeric negation of its operand.</span></span>

[!code-csharp-interactive[unary plus and minus](snippets/shared/ArithmeticOperators.cs#UnaryPlusAndMinus)]

<span data-ttu-id="dbb93-132">Le type [ULong](../builtin-types/integral-numeric-types.md) ne prend pas en charge l’opérateur unaire `-` .</span><span class="sxs-lookup"><span data-stu-id="dbb93-132">The [ulong](../builtin-types/integral-numeric-types.md) type doesn't support the unary `-` operator.</span></span>

## <a name="multiplication-operator-"></a><span data-ttu-id="dbb93-133">Opérateur de multiplication \*</span><span class="sxs-lookup"><span data-stu-id="dbb93-133">Multiplication operator \*</span></span>

<span data-ttu-id="dbb93-134">L’opérateur de multiplication `*` calcule le produit de ses opérandes :</span><span class="sxs-lookup"><span data-stu-id="dbb93-134">The multiplication operator `*` computes the product of its operands:</span></span>

[!code-csharp-interactive[multiplication operator](snippets/shared/ArithmeticOperators.cs#Multiplication)]

<span data-ttu-id="dbb93-135">L’opérateur unaire `*` est [l’opérateur d’indirection de pointeur](pointer-related-operators.md#pointer-indirection-operator-).</span><span class="sxs-lookup"><span data-stu-id="dbb93-135">The unary `*` operator is the [pointer indirection operator](pointer-related-operators.md#pointer-indirection-operator-).</span></span>

## <a name="division-operator-"></a><span data-ttu-id="dbb93-136">Opérateur de division /</span><span class="sxs-lookup"><span data-stu-id="dbb93-136">Division operator /</span></span>

<span data-ttu-id="dbb93-137">L’opérateur de division `/` divise son opérande de partie gauche par son opérande de partie droite.</span><span class="sxs-lookup"><span data-stu-id="dbb93-137">The division operator `/` divides its left-hand operand by its right-hand operand.</span></span>

### <a name="integer-division"></a><span data-ttu-id="dbb93-138">Division d'entier</span><span class="sxs-lookup"><span data-stu-id="dbb93-138">Integer division</span></span>

<span data-ttu-id="dbb93-139">Pour les opérandes des types entiers, le résultat de l’opérateur `/` est de type entier et égal au quotient de deux opérandes arrondis vers le zéro :</span><span class="sxs-lookup"><span data-stu-id="dbb93-139">For the operands of integer types, the result of the `/` operator is of an integer type and equals the quotient of the two operands rounded towards zero:</span></span>

[!code-csharp-interactive[integer division](snippets/shared/ArithmeticOperators.cs#IntegerDivision)]

<span data-ttu-id="dbb93-140">Pour obtenir le quotient de deux opérandes comme un nombre à virgule flottante, utilisez le type `float`, `double` ou `decimal` :</span><span class="sxs-lookup"><span data-stu-id="dbb93-140">To obtain the quotient of the two operands as a floating-point number, use the `float`, `double`, or `decimal` type:</span></span>

[!code-csharp-interactive[integer as floating-point division](snippets/shared/ArithmeticOperators.cs#IntegerAsFloatingPointDivision)]

### <a name="floating-point-division"></a><span data-ttu-id="dbb93-141">Division à virgule flottante</span><span class="sxs-lookup"><span data-stu-id="dbb93-141">Floating-point division</span></span>

<span data-ttu-id="dbb93-142">Pour les types `float`, `double` et `decimal`, le résultat de l’opérateur `/` est le quotient de deux opérandes :</span><span class="sxs-lookup"><span data-stu-id="dbb93-142">For the `float`, `double`, and `decimal` types, the result of the `/` operator is the quotient of the two operands:</span></span>

[!code-csharp-interactive[floating-point division](snippets/shared/ArithmeticOperators.cs#FloatingPointDivision)]

<span data-ttu-id="dbb93-143">Si l’un des opérandes est `decimal`, un autre opérande ne peut être `float` ni `double`, car ni `float` ni `double` ne sont implicitement convertibles en `decimal`.</span><span class="sxs-lookup"><span data-stu-id="dbb93-143">If one of the operands is `decimal`, another operand can be neither `float` nor `double`, because neither `float` nor `double` is implicitly convertible to `decimal`.</span></span> <span data-ttu-id="dbb93-144">Vous devez convertir explicitement l’opérande `float` ou `double` en type `decimal`.</span><span class="sxs-lookup"><span data-stu-id="dbb93-144">You must explicitly convert the `float` or `double` operand to the `decimal` type.</span></span> <span data-ttu-id="dbb93-145">Pour plus d’informations sur les conversions entre les types numériques, consultez [conversions numériques intégrées](../builtin-types/numeric-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="dbb93-145">For more information about conversions between numeric types, see [Built-in numeric conversions](../builtin-types/numeric-conversions.md).</span></span>

## <a name="remainder-operator-"></a><span data-ttu-id="dbb93-146">Opérateur de reste %</span><span class="sxs-lookup"><span data-stu-id="dbb93-146">Remainder operator %</span></span>

<span data-ttu-id="dbb93-147">L’opérateur restant `%` calcule le reste après la division de son opérande de partie gauche par son opérande de partie droite.</span><span class="sxs-lookup"><span data-stu-id="dbb93-147">The remainder operator `%` computes the remainder after dividing its left-hand operand by its right-hand operand.</span></span>

### <a name="integer-remainder"></a><span data-ttu-id="dbb93-148">Reste entier</span><span class="sxs-lookup"><span data-stu-id="dbb93-148">Integer remainder</span></span>

<span data-ttu-id="dbb93-149">Pour les opérandes des types entiers, le résultat de `a % b` est la valeur produite par `a - (a / b) * b`.</span><span class="sxs-lookup"><span data-stu-id="dbb93-149">For the operands of integer types, the result of `a % b` is the value produced by `a - (a / b) * b`.</span></span> <span data-ttu-id="dbb93-150">Le signe du reste non zéro est le même que celui de l’opérande de partie gauche, comme l’indique l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="dbb93-150">The sign of the non-zero remainder is the same as that of the left-hand operand, as the following example shows:</span></span>

[!code-csharp-interactive[integer remainder](snippets/shared/ArithmeticOperators.cs#IntegerRemainder)]

<span data-ttu-id="dbb93-151">Utilisez la méthode <xref:System.Math.DivRem%2A?displayProperty=nameWithType> pour calculer à la fois la division entière et les résultats du reste.</span><span class="sxs-lookup"><span data-stu-id="dbb93-151">Use the <xref:System.Math.DivRem%2A?displayProperty=nameWithType> method to compute both integer division and remainder results.</span></span>

### <a name="floating-point-remainder"></a><span data-ttu-id="dbb93-152">Reste à virgule flottante</span><span class="sxs-lookup"><span data-stu-id="dbb93-152">Floating-point remainder</span></span>

<span data-ttu-id="dbb93-153">En ce qui concerne les opérandes `float` et `double`, le résultat de `x % y` pour le `x` et le `y` finis est la valeur `z` afin que</span><span class="sxs-lookup"><span data-stu-id="dbb93-153">For the `float` and `double` operands, the result of `x % y` for the finite `x` and `y` is the value `z` such that</span></span>

- <span data-ttu-id="dbb93-154">Le signe de `z`, s’il est différent de zéro, soit identique au signe de `x`.</span><span class="sxs-lookup"><span data-stu-id="dbb93-154">The sign of `z`, if non-zero, is the same as the sign of `x`.</span></span>
- <span data-ttu-id="dbb93-155">La valeur absolue de `z` soit la valeur produite par `|x| - n * |y|`, où `n` représente le plus grand entier possible inférieur ou égal à `|x| / |y|`, et où `|x|` et `|y|` sont les valeurs absolues de `x` et `y`, respectivement.</span><span class="sxs-lookup"><span data-stu-id="dbb93-155">The absolute value of `z` is the value produced by `|x| - n * |y|` where `n` is the largest possible integer that is less than or equal to `|x| / |y|` and `|x|` and `|y|` are the absolute values of `x` and `y`, respectively.</span></span>

> [!NOTE]
> <span data-ttu-id="dbb93-156">Cette méthode de calcul du reste est analogue à celle utilisée pour les opérandes entiers, mais différente de la spécification IEEE 754.</span><span class="sxs-lookup"><span data-stu-id="dbb93-156">This method of computing the remainder is analogous to that used for integer operands, but different from the IEEE 754 specification.</span></span> <span data-ttu-id="dbb93-157">Si vous avez besoin de l’opération de reste qui est conforme à la spécification IEEE 754, utilisez la <xref:System.Math.IEEERemainder%2A?displayProperty=nameWithType> méthode.</span><span class="sxs-lookup"><span data-stu-id="dbb93-157">If you need the remainder operation that complies with the IEEE 754 specification, use the <xref:System.Math.IEEERemainder%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="dbb93-158">Pour plus d’informations sur le comportement de l’opérateur `%` avec des opérandes non finis, consultez la section [Opérateur de reste](~/_csharplang/spec/expressions.md#remainder-operator) dans la [Spécification du langage C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="dbb93-158">For information about the behavior of the `%` operator with non-finite operands, see the [Remainder operator](~/_csharplang/spec/expressions.md#remainder-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="dbb93-159">Pour les opérandes `decimal`, l’opérateur de reste `%` équivaut à l’[opérateur de reste](<xref:System.Decimal.op_Modulus(System.Decimal,System.Decimal)>) de type <xref:System.Decimal?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="dbb93-159">For the `decimal` operands, the remainder operator `%` is equivalent to the [remainder operator](<xref:System.Decimal.op_Modulus(System.Decimal,System.Decimal)>) of the <xref:System.Decimal?displayProperty=nameWithType> type.</span></span>

<span data-ttu-id="dbb93-160">L’exemple suivant illustre le comportement de l’opérateur de reste pour les opérandes à virgule flottante :</span><span class="sxs-lookup"><span data-stu-id="dbb93-160">The following example demonstrates the behavior of the remainder operator with floating-point operands:</span></span>

[!code-csharp-interactive[floating-point remainder](snippets/shared/ArithmeticOperators.cs#FloatingPointRemainder)]

## <a name="addition-operator-"></a><span data-ttu-id="dbb93-161">Opérateur d’addition +</span><span class="sxs-lookup"><span data-stu-id="dbb93-161">Addition operator +</span></span>

<span data-ttu-id="dbb93-162">L’opérateur d’addition `+` calcule la somme de ses opérandes :</span><span class="sxs-lookup"><span data-stu-id="dbb93-162">The addition operator `+` computes the sum of its operands:</span></span>

[!code-csharp-interactive[addition operator](snippets/shared/ArithmeticOperators.cs#Addition)]

<span data-ttu-id="dbb93-163">Vous pouvez également utiliser l' `+` opérateur pour la concaténation de chaînes et la combinaison de délégués.</span><span class="sxs-lookup"><span data-stu-id="dbb93-163">You can also use the `+` operator for string concatenation and delegate combination.</span></span> <span data-ttu-id="dbb93-164">Pour plus d’informations, consultez l’article [ `+` `+=` opérateurs et](addition-operator.md) .</span><span class="sxs-lookup"><span data-stu-id="dbb93-164">For more information, see the [`+` and `+=` operators](addition-operator.md) article.</span></span>

## <a name="subtraction-operator--"></a><span data-ttu-id="dbb93-165">Opérateur de soustraction -</span><span class="sxs-lookup"><span data-stu-id="dbb93-165">Subtraction operator -</span></span>

<span data-ttu-id="dbb93-166">L’opérateur de soustraction `-` soustrait son opérande de partie droite de son opérande de partie gauche :</span><span class="sxs-lookup"><span data-stu-id="dbb93-166">The subtraction operator `-` subtracts its right-hand operand from its left-hand operand:</span></span>

[!code-csharp-interactive[subtraction operator](snippets/shared/ArithmeticOperators.cs#Subtraction)]

<span data-ttu-id="dbb93-167">Vous pouvez également utiliser l' `-` opérateur pour la suppression d’un délégué.</span><span class="sxs-lookup"><span data-stu-id="dbb93-167">You can also use the `-` operator for delegate removal.</span></span> <span data-ttu-id="dbb93-168">Pour plus d’informations, consultez l’article [ `-` `-=` opérateurs et](subtraction-operator.md) .</span><span class="sxs-lookup"><span data-stu-id="dbb93-168">For more information, see the [`-` and `-=` operators](subtraction-operator.md) article.</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="dbb93-169">Assignation composée</span><span class="sxs-lookup"><span data-stu-id="dbb93-169">Compound assignment</span></span>

<span data-ttu-id="dbb93-170">Pour un opérateur binaire `op`, une expression d’assignation composée du formulaire</span><span class="sxs-lookup"><span data-stu-id="dbb93-170">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="dbb93-171">équivaut à :</span><span class="sxs-lookup"><span data-stu-id="dbb93-171">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="dbb93-172">sauf que `x` n’est évalué qu’une seule fois.</span><span class="sxs-lookup"><span data-stu-id="dbb93-172">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="dbb93-173">L’exemple suivant illustre l’utilisation de l’assignation composée avec des opérateurs arithmétiques :</span><span class="sxs-lookup"><span data-stu-id="dbb93-173">The following example demonstrates the usage of compound assignment with arithmetic operators:</span></span>

[!code-csharp-interactive[compound assignment](snippets/shared/ArithmeticOperators.cs#CompoundAssignment)]

<span data-ttu-id="dbb93-174">En raison des [promotions numériques](~/_csharplang/spec/expressions.md#numeric-promotions), le résultat de l’opération `op` risque de ne pas être implicitement convertible en type `T` de `x`.</span><span class="sxs-lookup"><span data-stu-id="dbb93-174">Because of [numeric promotions](~/_csharplang/spec/expressions.md#numeric-promotions), the result of the `op` operation might be not implicitly convertible to the type `T` of `x`.</span></span> <span data-ttu-id="dbb93-175">Dans ce cas, si `op` est un opérateur prédéfini et que le résultat de l’opération est explicitement convertible en type `T` de `x`, une expression d’assignation composée de la forme `x op= y` équivaut à `x = (T)(x op y)`, sauf que `x` n’est évalué qu’une seule fois.</span><span class="sxs-lookup"><span data-stu-id="dbb93-175">In such a case, if `op` is a predefined operator and the result of the operation is explicitly convertible to the type `T` of `x`, a compound assignment expression of the form `x op= y` is equivalent to `x = (T)(x op y)`, except that `x` is only evaluated once.</span></span> <span data-ttu-id="dbb93-176">L’exemple suivant illustre ce comportement :</span><span class="sxs-lookup"><span data-stu-id="dbb93-176">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[compound assignment with cast](snippets/shared/ArithmeticOperators.cs#CompoundAssignmentWithCast)]

<span data-ttu-id="dbb93-177">Vous pouvez également utiliser `+=` les `-=` opérateurs et pour vous abonner et vous désabonner d’un [événement](../keywords/event.md), respectivement.</span><span class="sxs-lookup"><span data-stu-id="dbb93-177">You also use the `+=` and `-=` operators to subscribe to and unsubscribe from an [event](../keywords/event.md), respectively.</span></span> <span data-ttu-id="dbb93-178">Pour plus d’informations, consultez [Comment s’abonner et annuler l’abonnement à des événements](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="dbb93-178">For more information, see [How to subscribe to and unsubscribe from events](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>

## <a name="operator-precedence-and-associativity"></a><span data-ttu-id="dbb93-179">Priorité des opérateurs et associativité</span><span class="sxs-lookup"><span data-stu-id="dbb93-179">Operator precedence and associativity</span></span>

<span data-ttu-id="dbb93-180">La liste suivante présente les opérateurs arithmétiques de la priorité la plus élevée à la plus basse :</span><span class="sxs-lookup"><span data-stu-id="dbb93-180">The following list orders arithmetic operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="dbb93-181">Opérateurs suffixés d’incrémentation `x++` et de décrémentation `x--`</span><span class="sxs-lookup"><span data-stu-id="dbb93-181">Postfix increment `x++` and decrement `x--` operators</span></span>
- <span data-ttu-id="dbb93-182">Opérateurs préfixés d’incrémentation `++x` et de décrémentation `--x` et opérateurs unaires `+` et `-`</span><span class="sxs-lookup"><span data-stu-id="dbb93-182">Prefix increment `++x` and decrement `--x` and unary `+` and `-` operators</span></span>
- <span data-ttu-id="dbb93-183">Opérateurs multiplicatifs `*`, `/` et `%`</span><span class="sxs-lookup"><span data-stu-id="dbb93-183">Multiplicative `*`, `/`, and `%` operators</span></span>
- <span data-ttu-id="dbb93-184">Opérateurs additifs `+` et `-`</span><span class="sxs-lookup"><span data-stu-id="dbb93-184">Additive `+` and `-` operators</span></span>

<span data-ttu-id="dbb93-185">Les opérateurs arithmétiques binaires sont associatifs sur leur gauche.</span><span class="sxs-lookup"><span data-stu-id="dbb93-185">Binary arithmetic operators are left-associative.</span></span> <span data-ttu-id="dbb93-186">Autrement dit, les opérateurs de même niveau de priorité sont évalués de gauche à droite.</span><span class="sxs-lookup"><span data-stu-id="dbb93-186">That is, operators with the same precedence level are evaluated from left to right.</span></span>

<span data-ttu-id="dbb93-187">Utilisez des parenthèses, `()`, pour modifier l’ordre d’évaluation imposé par la priorité et l’associativité de l’opérateur.</span><span class="sxs-lookup"><span data-stu-id="dbb93-187">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence and associativity.</span></span>

[!code-csharp-interactive[precedence and associativity](snippets/shared/ArithmeticOperators.cs#PrecedenceAndAssociativity)]

<span data-ttu-id="dbb93-188">Pour obtenir la liste complète des opérateurs C# classés par niveau de priorité, consultez la section [priorité d’opérateur](index.md#operator-precedence) de l’article [opérateurs c#](index.md) .</span><span class="sxs-lookup"><span data-stu-id="dbb93-188">For the complete list of C# operators ordered by precedence level, see the [Operator precedence](index.md#operator-precedence) section of the [C# operators](index.md) article.</span></span>

## <a name="arithmetic-overflow-and-division-by-zero"></a><span data-ttu-id="dbb93-189">Débordement arithmétique et division par zéro</span><span class="sxs-lookup"><span data-stu-id="dbb93-189">Arithmetic overflow and division by zero</span></span>

<span data-ttu-id="dbb93-190">Quand le résultat d’une opération arithmétique n’est pas compris dans la plage de valeurs finies possibles du type numérique impliqué, le comportement d’un opérateur arithmétique varie selon le type de ses opérandes.</span><span class="sxs-lookup"><span data-stu-id="dbb93-190">When the result of an arithmetic operation is outside the range of possible finite values of the involved numeric type, the behavior of an arithmetic operator depends on the type of its operands.</span></span>

### <a name="integer-arithmetic-overflow"></a><span data-ttu-id="dbb93-191">Débordement arithmétique entier</span><span class="sxs-lookup"><span data-stu-id="dbb93-191">Integer arithmetic overflow</span></span>

<span data-ttu-id="dbb93-192">La division d'un entier par zéro lève toujours une exception <xref:System.DivideByZeroException>.</span><span class="sxs-lookup"><span data-stu-id="dbb93-192">Integer division by zero always throws a <xref:System.DivideByZeroException>.</span></span>

<span data-ttu-id="dbb93-193">En cas de débordement arithmétique entier, un contexte de vérification de débordement, qui peut être [vérifié ou non vérifié](../keywords/checked-and-unchecked.md), contrôle le comportement qui en résulte :</span><span class="sxs-lookup"><span data-stu-id="dbb93-193">In case of integer arithmetic overflow, an overflow checking context, which can be [checked or unchecked](../keywords/checked-and-unchecked.md), controls the resulting behavior:</span></span>

- <span data-ttu-id="dbb93-194">Dans un contexte vérifié, si le débordement se produit dans une expression constante, une erreur de compilation se produit.</span><span class="sxs-lookup"><span data-stu-id="dbb93-194">In a checked context, if overflow happens in a constant expression, a compile-time error occurs.</span></span> <span data-ttu-id="dbb93-195">Sinon, un <xref:System.OverflowException> est levé quand l’opération est effectuée au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="dbb93-195">Otherwise, when the operation is performed at run time, an <xref:System.OverflowException> is thrown.</span></span>
- <span data-ttu-id="dbb93-196">Dans un contexte non vérifié, le résultat est tronqué en supprimant tous les bits de poids fort qui ne tiennent pas dans le type destinataire.</span><span class="sxs-lookup"><span data-stu-id="dbb93-196">In an unchecked context, the result is truncated by discarding any high-order bits that don't fit in the destination type.</span></span>

<span data-ttu-id="dbb93-197">Avec les instructions [vérifiées et non vérifiées](../keywords/checked-and-unchecked.md), vous pouvez utiliser les opérateurs `checked` et `unchecked` pour contrôler le contexte de vérification de débordement, dans lequel une expression est évaluée :</span><span class="sxs-lookup"><span data-stu-id="dbb93-197">Along with the [checked and unchecked](../keywords/checked-and-unchecked.md) statements, you can use the `checked` and `unchecked` operators to control the overflow checking context, in which an expression is evaluated:</span></span>

[!code-csharp-interactive[checked and unchecked](snippets/shared/ArithmeticOperators.cs#CheckedUnchecked)]

<span data-ttu-id="dbb93-198">Par défaut, les opérations arithmétiques se produisent dans un contexte *unchecked*.</span><span class="sxs-lookup"><span data-stu-id="dbb93-198">By default, arithmetic operations occur in an *unchecked* context.</span></span>

### <a name="floating-point-arithmetic-overflow"></a><span data-ttu-id="dbb93-199">Débordement arithmétique à virgule flottante</span><span class="sxs-lookup"><span data-stu-id="dbb93-199">Floating-point arithmetic overflow</span></span>

<span data-ttu-id="dbb93-200">Les opérations arithmétiques avec les types `float` et `double` ne lèvent jamais d’exceptions.</span><span class="sxs-lookup"><span data-stu-id="dbb93-200">Arithmetic operations with the `float` and `double` types never throw an exception.</span></span> <span data-ttu-id="dbb93-201">Le résultat des opérations arithmétiques avec ces types peut être une des valeurs spéciales qui représentent l’infini et non un nombre :</span><span class="sxs-lookup"><span data-stu-id="dbb93-201">The result of arithmetic operations with those types can be one of special values that represent infinity and not-a-number:</span></span>

[!code-csharp-interactive[double non-finite values](snippets/shared/ArithmeticOperators.cs#FloatingPointOverflow)]

<span data-ttu-id="dbb93-202">Pour les opérandes du type `decimal`, le débordement arithmétique lève toujours un <xref:System.OverflowException> et la division par zéro lève toujours un <xref:System.DivideByZeroException>.</span><span class="sxs-lookup"><span data-stu-id="dbb93-202">For the operands of the `decimal` type, arithmetic overflow always throws an <xref:System.OverflowException> and division by zero always throws a <xref:System.DivideByZeroException>.</span></span>

## <a name="round-off-errors"></a><span data-ttu-id="dbb93-203">Erreurs d’arrondi</span><span class="sxs-lookup"><span data-stu-id="dbb93-203">Round-off errors</span></span>

<span data-ttu-id="dbb93-204">En raison des limitations générales de la représentation à virgule flottante des nombres réels et de l’arithmétique à virgule flottante, des erreurs d’arrondi peuvent se produire dans les calculs avec des types à virgule flottante.</span><span class="sxs-lookup"><span data-stu-id="dbb93-204">Because of general limitations of the floating-point representation of real numbers and floating-point arithmetic, round-off errors might occur in calculations with floating-point types.</span></span> <span data-ttu-id="dbb93-205">Autrement dit, le résultat d’une expression peut différer du résultat mathématique attendu.</span><span class="sxs-lookup"><span data-stu-id="dbb93-205">That is, the produced result of an expression might differ from the expected mathematical result.</span></span> <span data-ttu-id="dbb93-206">L’exemple suivant illustre plusieurs cas de ce genre :</span><span class="sxs-lookup"><span data-stu-id="dbb93-206">The following example demonstrates several such cases:</span></span>

[!code-csharp-interactive[round-off errors](snippets/shared/ArithmeticOperators.cs#RoundOffErrors)]

<span data-ttu-id="dbb93-207">Pour plus d’informations, consultez la section Notes sur les pages de référence System. [double](/dotnet/api/system.double#remarks), [System. Single](/dotnet/api/system.single#remarks)ou [System. Decimal](/dotnet/api/system.decimal#remarks) .</span><span class="sxs-lookup"><span data-stu-id="dbb93-207">For more information, see remarks at the [System.Double](/dotnet/api/system.double#remarks), [System.Single](/dotnet/api/system.single#remarks), or [System.Decimal](/dotnet/api/system.decimal#remarks) reference pages.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="dbb93-208">Capacité de surcharge de l’opérateur</span><span class="sxs-lookup"><span data-stu-id="dbb93-208">Operator overloadability</span></span>

<span data-ttu-id="dbb93-209">Un type défini par l’utilisateur peut [surcharger](operator-overloading.md) les `++` opérateurs arithmétiques unaires (,, `--` `+` et `-` ) et binaires ( `*` ,,, `/` `%` `+` et `-` ).</span><span class="sxs-lookup"><span data-stu-id="dbb93-209">A user-defined type can [overload](operator-overloading.md) the unary (`++`, `--`, `+`, and `-`) and binary (`*`, `/`, `%`, `+`, and `-`) arithmetic operators.</span></span> <span data-ttu-id="dbb93-210">Quand un opérateur binaire est surchargé, l’opérateur d’assignation composée correspondant est aussi implicitement surchargé.</span><span class="sxs-lookup"><span data-stu-id="dbb93-210">When a binary operator is overloaded, the corresponding compound assignment operator is also implicitly overloaded.</span></span> <span data-ttu-id="dbb93-211">Un type défini par l’utilisateur ne peut pas surcharger explicitement un opérateur d’assignation composée.</span><span class="sxs-lookup"><span data-stu-id="dbb93-211">A user-defined type cannot explicitly overload a compound assignment operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="dbb93-212">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="dbb93-212">C# language specification</span></span>

<span data-ttu-id="dbb93-213">Pour plus d’informations, consultez les sections suivantes de la [spécification du langage C#](~/_csharplang/spec/introduction.md) :</span><span class="sxs-lookup"><span data-stu-id="dbb93-213">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="dbb93-214">Opérateurs suffixés d’incrémentation et de décrémentation</span><span class="sxs-lookup"><span data-stu-id="dbb93-214">Postfix increment and decrement operators</span></span>](~/_csharplang/spec/expressions.md#postfix-increment-and-decrement-operators)
- [<span data-ttu-id="dbb93-215">Opérateurs préfixés d’incrémentation et de décrémentation</span><span class="sxs-lookup"><span data-stu-id="dbb93-215">Prefix increment and decrement operators</span></span>](~/_csharplang/spec/expressions.md#prefix-increment-and-decrement-operators)
- [<span data-ttu-id="dbb93-216">Opérateur plus unaire</span><span class="sxs-lookup"><span data-stu-id="dbb93-216">Unary plus operator</span></span>](~/_csharplang/spec/expressions.md#unary-plus-operator)
- [<span data-ttu-id="dbb93-217">Opérateur moins unaire</span><span class="sxs-lookup"><span data-stu-id="dbb93-217">Unary minus operator</span></span>](~/_csharplang/spec/expressions.md#unary-minus-operator)
- [<span data-ttu-id="dbb93-218">Opérateur de multiplication</span><span class="sxs-lookup"><span data-stu-id="dbb93-218">Multiplication operator</span></span>](~/_csharplang/spec/expressions.md#multiplication-operator)
- [<span data-ttu-id="dbb93-219">Opérateur de division</span><span class="sxs-lookup"><span data-stu-id="dbb93-219">Division operator</span></span>](~/_csharplang/spec/expressions.md#division-operator)
- [<span data-ttu-id="dbb93-220">Remainder (opérateur)</span><span class="sxs-lookup"><span data-stu-id="dbb93-220">Remainder operator</span></span>](~/_csharplang/spec/expressions.md#remainder-operator)
- [<span data-ttu-id="dbb93-221">Opérateur d’addition</span><span class="sxs-lookup"><span data-stu-id="dbb93-221">Addition operator</span></span>](~/_csharplang/spec/expressions.md#addition-operator)
- [<span data-ttu-id="dbb93-222">Opérateur de soustraction</span><span class="sxs-lookup"><span data-stu-id="dbb93-222">Subtraction operator</span></span>](~/_csharplang/spec/expressions.md#subtraction-operator)
- [<span data-ttu-id="dbb93-223">Assignation composée</span><span class="sxs-lookup"><span data-stu-id="dbb93-223">Compound assignment</span></span>](~/_csharplang/spec/expressions.md#compound-assignment)
- [<span data-ttu-id="dbb93-224">Opérateurs vérifiés et non vérifiés</span><span class="sxs-lookup"><span data-stu-id="dbb93-224">The checked and unchecked operators</span></span>](~/_csharplang/spec/expressions.md#the-checked-and-unchecked-operators)
- [<span data-ttu-id="dbb93-225">Promotions numériques</span><span class="sxs-lookup"><span data-stu-id="dbb93-225">Numeric promotions</span></span>](~/_csharplang/spec/expressions.md#numeric-promotions)

## <a name="see-also"></a><span data-ttu-id="dbb93-226">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dbb93-226">See also</span></span>

- [<span data-ttu-id="dbb93-227">Informations de référence sur C#</span><span class="sxs-lookup"><span data-stu-id="dbb93-227">C# reference</span></span>](../index.md)
- [<span data-ttu-id="dbb93-228">Opérateurs et expressions C#</span><span class="sxs-lookup"><span data-stu-id="dbb93-228">C# operators and expressions</span></span>](index.md)
- <xref:System.Math?displayProperty=nameWithType>
- <xref:System.MathF?displayProperty=nameWithType>
- [<span data-ttu-id="dbb93-229">Valeurs numériques dans .NET</span><span class="sxs-lookup"><span data-stu-id="dbb93-229">Numerics in .NET</span></span>](../../../standard/numerics.md)
