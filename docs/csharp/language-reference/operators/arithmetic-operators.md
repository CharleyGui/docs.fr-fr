---
title: Opérateurs arithmétiques - Référence C#
description: Découvrez les opérateurs C# qui effectuent des opérations de multiplication, division, reste, addition et soustraction avec des types numériques.
ms.date: 03/27/2019
author: pkulikov
f1_keywords:
- ++_CSharpKeyword
- --_CSharpKeyword
- '*_CSharpKeyword'
- /_CSharpKeyword
- '%_CSharpKeyword'
- +_CSharpKeyword
- -_CSharpKeyword
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
ms.openlocfilehash: ea9bf9e065b2953fd20e0503a19d1dc143064c5d
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738733"
---
# <a name="arithmetic-operators-c-reference"></a><span data-ttu-id="7af48-103">Opérateurs arithmétiques (référence C#)</span><span class="sxs-lookup"><span data-stu-id="7af48-103">Arithmetic operators (C# reference)</span></span>

<span data-ttu-id="7af48-104">Les opérateurs suivants effectuent des opérations d’arithmétique avec des opérands de types numériques :</span><span class="sxs-lookup"><span data-stu-id="7af48-104">The following operators perform arithmetic operations with operands of numeric types:</span></span>

- <span data-ttu-id="7af48-105">Unary [ `++` (incrément)](#increment-operator-), [ `--` (decrement)](#decrement-operator---), [ `+` (plus)](#unary-plus-and-minus-operators), et [ `-` (moins)](#unary-plus-and-minus-operators) les opérateurs</span><span class="sxs-lookup"><span data-stu-id="7af48-105">Unary [`++` (increment)](#increment-operator-), [`--` (decrement)](#decrement-operator---), [`+` (plus)](#unary-plus-and-minus-operators), and [`-` (minus)](#unary-plus-and-minus-operators) operators</span></span>
- <span data-ttu-id="7af48-106">Opérateurs [ `*` binaires (multiplications)](#multiplication-operator-), [ `/` (division)](#division-operator-) [ `%` , (reste)](#remainder-operator-) [ `+` , (addition)](#addition-operator-)et [ `-` (soustraction)](#subtraction-operator--)</span><span class="sxs-lookup"><span data-stu-id="7af48-106">Binary [`*` (multiplication)](#multiplication-operator-), [`/` (division)](#division-operator-), [`%` (remainder)](#remainder-operator-), [`+` (addition)](#addition-operator-), and [`-` (subtraction)](#subtraction-operator--) operators</span></span>

<span data-ttu-id="7af48-107">Ces opérateurs sont soutenus par tous les types [numériques intégrals](../builtin-types/integral-numeric-types.md) et [à points flottants.](../builtin-types/floating-point-numeric-types.md)</span><span class="sxs-lookup"><span data-stu-id="7af48-107">Those operators are supported by all [integral](../builtin-types/integral-numeric-types.md) and [floating-point](../builtin-types/floating-point-numeric-types.md) numeric types.</span></span>

## <a name="increment-operator-"></a><span data-ttu-id="7af48-108">Opérateur d’incrémentation ++</span><span class="sxs-lookup"><span data-stu-id="7af48-108">Increment operator ++</span></span>

<span data-ttu-id="7af48-109">L’opérateur d’incrémentation unaire `++` incrémente son opérande de 1.</span><span class="sxs-lookup"><span data-stu-id="7af48-109">The unary increment operator `++` increments its operand by 1.</span></span> <span data-ttu-id="7af48-110">L’opérande doit être une variable, un accès [propriété](../../programming-guide/classes-and-structs/properties.md) ou un accès [indexeur](../../programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="7af48-110">The operand must be a variable, a [property](../../programming-guide/classes-and-structs/properties.md) access, or an [indexer](../../programming-guide/indexers/index.md) access.</span></span>

<span data-ttu-id="7af48-111">L’opérateur d’incrémentation est pris en charge sous deux formes : l’opérateur d’incrémentation suffixé, `x++`, et l’opérateur d’incrémentation préfixé, `++x`.</span><span class="sxs-lookup"><span data-stu-id="7af48-111">The increment operator is supported in two forms: the postfix increment operator, `x++`, and the prefix increment operator, `++x`.</span></span>

### <a name="postfix-increment-operator"></a><span data-ttu-id="7af48-112">Opérateur d'incrément suffixé</span><span class="sxs-lookup"><span data-stu-id="7af48-112">Postfix increment operator</span></span>

<span data-ttu-id="7af48-113">Le résultat de `x++` est la valeur de `x` *avant* l’opération, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="7af48-113">The result of `x++` is the value of `x` *before* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[postfix increment](snippets/ArithmeticOperators.cs#PostfixIncrement)]

### <a name="prefix-increment-operator"></a><span data-ttu-id="7af48-114">Opérateur d'incrémentation préfixé</span><span class="sxs-lookup"><span data-stu-id="7af48-114">Prefix increment operator</span></span>

<span data-ttu-id="7af48-115">Le résultat de `++x` est la valeur de `x` *après* l’opération, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="7af48-115">The result of `++x` is the value of `x` *after* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[prefix increment](snippets/ArithmeticOperators.cs#PrefixIncrement)]

## <a name="decrement-operator---"></a><span data-ttu-id="7af48-116">Opérateur de décrémentation --</span><span class="sxs-lookup"><span data-stu-id="7af48-116">Decrement operator --</span></span>

<span data-ttu-id="7af48-117">L’opérateur de décrémentation unaire `--` décrémente son opérande de 1.</span><span class="sxs-lookup"><span data-stu-id="7af48-117">The unary decrement operator `--` decrements its operand by 1.</span></span> <span data-ttu-id="7af48-118">L’opérande doit être une variable, un accès [propriété](../../programming-guide/classes-and-structs/properties.md) ou un accès [indexeur](../../programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="7af48-118">The operand must be a variable, a [property](../../programming-guide/classes-and-structs/properties.md) access, or an [indexer](../../programming-guide/indexers/index.md) access.</span></span>

<span data-ttu-id="7af48-119">L’opérateur de décrémentation est pris en charge sous deux formes : l’opérateur de décrémentation suffixé, `x--`, et l’opérateur de décrémentation préfixé, `--x`.</span><span class="sxs-lookup"><span data-stu-id="7af48-119">The decrement operator is supported in two forms: the postfix decrement operator, `x--`, and the prefix decrement operator, `--x`.</span></span>

### <a name="postfix-decrement-operator"></a><span data-ttu-id="7af48-120">Opérateur de décrémentation suffixé</span><span class="sxs-lookup"><span data-stu-id="7af48-120">Postfix decrement operator</span></span>

<span data-ttu-id="7af48-121">Le résultat de `x--` est la valeur de `x` *avant* l’opération, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="7af48-121">The result of `x--` is the value of `x` *before* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[postfix decrement](snippets/ArithmeticOperators.cs#PostfixDecrement)]

### <a name="prefix-decrement-operator"></a><span data-ttu-id="7af48-122">Opérateur de décrémentation préfixé</span><span class="sxs-lookup"><span data-stu-id="7af48-122">Prefix decrement operator</span></span>

<span data-ttu-id="7af48-123">Le résultat de `--x` est la valeur de `x` *après* l’opération, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="7af48-123">The result of `--x` is the value of `x` *after* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[prefix decrement](snippets/ArithmeticOperators.cs#PrefixDecrement)]

## <a name="unary-plus-and-minus-operators"></a><span data-ttu-id="7af48-124">Opérateurs plus et moins unaires</span><span class="sxs-lookup"><span data-stu-id="7af48-124">Unary plus and minus operators</span></span>

<span data-ttu-id="7af48-125">L’opérateur unaire `+` retourne la valeur de son opérande.</span><span class="sxs-lookup"><span data-stu-id="7af48-125">The unary `+` operator returns the value of its operand.</span></span> <span data-ttu-id="7af48-126">L’opérateur unaire `-` calcule la négation numérique de son opérande.</span><span class="sxs-lookup"><span data-stu-id="7af48-126">The unary `-` operator computes the numeric negation of its operand.</span></span>

[!code-csharp-interactive[unary plus and minus](snippets/ArithmeticOperators.cs#UnaryPlusAndMinus)]

<span data-ttu-id="7af48-127">Le type [ulong](../builtin-types/integral-numeric-types.md) ne prend `-` pas en charge l’opérateur unary.</span><span class="sxs-lookup"><span data-stu-id="7af48-127">The [ulong](../builtin-types/integral-numeric-types.md) type doesn't support the unary `-` operator.</span></span>

## <a name="multiplication-operator-"></a><span data-ttu-id="7af48-128">Opérateur de multiplication \*</span><span class="sxs-lookup"><span data-stu-id="7af48-128">Multiplication operator \*</span></span>

<span data-ttu-id="7af48-129">L’opérateur de multiplication `*` calcule le produit de ses opérandes :</span><span class="sxs-lookup"><span data-stu-id="7af48-129">The multiplication operator `*` computes the product of its operands:</span></span>

[!code-csharp-interactive[multiplication operator](snippets/ArithmeticOperators.cs#Multiplication)]

<span data-ttu-id="7af48-130">L’opérateur unaire `*` est [l’opérateur d’indirection de pointeur](pointer-related-operators.md#pointer-indirection-operator-).</span><span class="sxs-lookup"><span data-stu-id="7af48-130">The unary `*` operator is the [pointer indirection operator](pointer-related-operators.md#pointer-indirection-operator-).</span></span>

## <a name="division-operator-"></a><span data-ttu-id="7af48-131">Opérateur de division /</span><span class="sxs-lookup"><span data-stu-id="7af48-131">Division operator /</span></span>

<span data-ttu-id="7af48-132">L’opérateur de division `/` divise son opérande de partie gauche par son opérande de partie droite.</span><span class="sxs-lookup"><span data-stu-id="7af48-132">The division operator `/` divides its left-hand operand by its right-hand operand.</span></span>

### <a name="integer-division"></a><span data-ttu-id="7af48-133">Division d'entier</span><span class="sxs-lookup"><span data-stu-id="7af48-133">Integer division</span></span>

<span data-ttu-id="7af48-134">Pour les opérandes des types entiers, le résultat de l’opérateur `/` est de type entier et égal au quotient de deux opérandes arrondis vers le zéro :</span><span class="sxs-lookup"><span data-stu-id="7af48-134">For the operands of integer types, the result of the `/` operator is of an integer type and equals the quotient of the two operands rounded towards zero:</span></span>

[!code-csharp-interactive[integer division](snippets/ArithmeticOperators.cs#IntegerDivision)]

<span data-ttu-id="7af48-135">Pour obtenir le quotient de deux opérandes comme un nombre à virgule flottante, utilisez le type `float`, `double` ou `decimal` :</span><span class="sxs-lookup"><span data-stu-id="7af48-135">To obtain the quotient of the two operands as a floating-point number, use the `float`, `double`, or `decimal` type:</span></span>

[!code-csharp-interactive[integer as floating-point division](snippets/ArithmeticOperators.cs#IntegerAsFloatingPointDivision)]

### <a name="floating-point-division"></a><span data-ttu-id="7af48-136">Division à virgule flottante</span><span class="sxs-lookup"><span data-stu-id="7af48-136">Floating-point division</span></span>

<span data-ttu-id="7af48-137">Pour les types `float`, `double` et `decimal`, le résultat de l’opérateur `/` est le quotient de deux opérandes :</span><span class="sxs-lookup"><span data-stu-id="7af48-137">For the `float`, `double`, and `decimal` types, the result of the `/` operator is the quotient of the two operands:</span></span>

[!code-csharp-interactive[floating-point division](snippets/ArithmeticOperators.cs#FloatingPointDivision)]

<span data-ttu-id="7af48-138">Si l’un des opérandes est `decimal`, un autre opérande ne peut être `float` ni `double`, car ni `float` ni `double` ne sont implicitement convertibles en `decimal`.</span><span class="sxs-lookup"><span data-stu-id="7af48-138">If one of the operands is `decimal`, another operand can be neither `float` nor `double`, because neither `float` nor `double` is implicitly convertible to `decimal`.</span></span> <span data-ttu-id="7af48-139">Vous devez convertir explicitement l’opérande `float` ou `double` en type `decimal`.</span><span class="sxs-lookup"><span data-stu-id="7af48-139">You must explicitly convert the `float` or `double` operand to the `decimal` type.</span></span> <span data-ttu-id="7af48-140">Pour plus d’informations sur les conversions entre les types [numériques, voir conversions numériques intégrées](../builtin-types/numeric-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="7af48-140">For more information about conversions between numeric types, see [Built-in numeric conversions](../builtin-types/numeric-conversions.md).</span></span>

## <a name="remainder-operator-"></a><span data-ttu-id="7af48-141">Opérateur de reste %</span><span class="sxs-lookup"><span data-stu-id="7af48-141">Remainder operator %</span></span>

<span data-ttu-id="7af48-142">L’opérateur restant `%` calcule le reste après la division de son opérande de partie gauche par son opérande de partie droite.</span><span class="sxs-lookup"><span data-stu-id="7af48-142">The remainder operator `%` computes the remainder after dividing its left-hand operand by its right-hand operand.</span></span>

### <a name="integer-remainder"></a><span data-ttu-id="7af48-143">Reste entier</span><span class="sxs-lookup"><span data-stu-id="7af48-143">Integer remainder</span></span>

<span data-ttu-id="7af48-144">Pour les opérandes des types entiers, le résultat de `a % b` est la valeur produite par `a - (a / b) * b`.</span><span class="sxs-lookup"><span data-stu-id="7af48-144">For the operands of integer types, the result of `a % b` is the value produced by `a - (a / b) * b`.</span></span> <span data-ttu-id="7af48-145">Le signe du reste non zéro est le même que celui de l’opérande de partie gauche, comme l’indique l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="7af48-145">The sign of the non-zero remainder is the same as that of the left-hand operand, as the following example shows:</span></span>

[!code-csharp-interactive[integer remainder](snippets/ArithmeticOperators.cs#IntegerRemainder)]

<span data-ttu-id="7af48-146">Utilisez la méthode <xref:System.Math.DivRem%2A?displayProperty=nameWithType> pour calculer à la fois la division entière et les résultats du reste.</span><span class="sxs-lookup"><span data-stu-id="7af48-146">Use the <xref:System.Math.DivRem%2A?displayProperty=nameWithType> method to compute both integer division and remainder results.</span></span>

### <a name="floating-point-remainder"></a><span data-ttu-id="7af48-147">Reste à virgule flottante</span><span class="sxs-lookup"><span data-stu-id="7af48-147">Floating-point remainder</span></span>

<span data-ttu-id="7af48-148">En ce qui concerne les opérandes `float` et `double`, le résultat de `x % y` pour le `x` et le `y` finis est la valeur `z` afin que</span><span class="sxs-lookup"><span data-stu-id="7af48-148">For the `float` and `double` operands, the result of `x % y` for the finite `x` and `y` is the value `z` such that</span></span>

- <span data-ttu-id="7af48-149">Le signe de `z`, s’il est différent de zéro, soit identique au signe de `x`.</span><span class="sxs-lookup"><span data-stu-id="7af48-149">The sign of `z`, if non-zero, is the same as the sign of `x`.</span></span>
- <span data-ttu-id="7af48-150">La valeur absolue de `z` soit la valeur produite par `|x| - n * |y|`, où `n` représente le plus grand entier possible inférieur ou égal à `|x| / |y|`, et où `|x|` et `|y|` sont les valeurs absolues de `x` et `y`, respectivement.</span><span class="sxs-lookup"><span data-stu-id="7af48-150">The absolute value of `z` is the value produced by `|x| - n * |y|` where `n` is the largest possible integer that is less than or equal to `|x| / |y|` and `|x|` and `|y|` are the absolute values of `x` and `y`, respectively.</span></span>

> [!NOTE]
> <span data-ttu-id="7af48-151">Cette méthode de calcul du reste est analogue à celle utilisée pour les opérands integer, mais différente de la spécification IEEE 754.</span><span class="sxs-lookup"><span data-stu-id="7af48-151">This method of computing the remainder is analogous to that used for integer operands, but different from the IEEE 754 specification.</span></span> <span data-ttu-id="7af48-152">Si vous avez besoin du reste de l’opération conforme aux spécifications <xref:System.Math.IEEERemainder%2A?displayProperty=nameWithType> IEEE 754, utilisez la méthode.</span><span class="sxs-lookup"><span data-stu-id="7af48-152">If you need the remainder operation that complies with the IEEE 754 specification, use the <xref:System.Math.IEEERemainder%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="7af48-153">Pour plus d’informations sur le comportement de l’opérateur `%` avec des opérandes non finis, consultez la section [Opérateur de reste](~/_csharplang/spec/expressions.md#remainder-operator) dans la [Spécification du langage C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="7af48-153">For information about the behavior of the `%` operator with non-finite operands, see the [Remainder operator](~/_csharplang/spec/expressions.md#remainder-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="7af48-154">Pour les opérandes `decimal`, l’opérateur de reste `%` équivaut à l’[opérateur de reste](<xref:System.Decimal.op_Modulus(System.Decimal,System.Decimal)>) de type <xref:System.Decimal?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7af48-154">For the `decimal` operands, the remainder operator `%` is equivalent to the [remainder operator](<xref:System.Decimal.op_Modulus(System.Decimal,System.Decimal)>) of the <xref:System.Decimal?displayProperty=nameWithType> type.</span></span>

<span data-ttu-id="7af48-155">L’exemple suivant illustre le comportement de l’opérateur de reste pour les opérandes à virgule flottante :</span><span class="sxs-lookup"><span data-stu-id="7af48-155">The following example demonstrates the behavior of the remainder operator with floating-point operands:</span></span>

[!code-csharp-interactive[floating-point remainder](snippets/ArithmeticOperators.cs#FloatingPointRemainder)]

## <a name="addition-operator-"></a><span data-ttu-id="7af48-156">Opérateur d’addition +</span><span class="sxs-lookup"><span data-stu-id="7af48-156">Addition operator +</span></span>

<span data-ttu-id="7af48-157">L’opérateur d’addition `+` calcule la somme de ses opérandes :</span><span class="sxs-lookup"><span data-stu-id="7af48-157">The addition operator `+` computes the sum of its operands:</span></span>

[!code-csharp-interactive[addition operator](snippets/ArithmeticOperators.cs#Addition)]

<span data-ttu-id="7af48-158">Vous pouvez également `+` utiliser l’opérateur pour la concatenation des cordes et la combinaison de délégués.</span><span class="sxs-lookup"><span data-stu-id="7af48-158">You can also use the `+` operator for string concatenation and delegate combination.</span></span> <span data-ttu-id="7af48-159">Pour plus d’informations, voir l’article [ `+` et `+=` les opérateurs.](addition-operator.md)</span><span class="sxs-lookup"><span data-stu-id="7af48-159">For more information, see the [`+` and `+=` operators](addition-operator.md) article.</span></span>

## <a name="subtraction-operator--"></a><span data-ttu-id="7af48-160">Opérateur de soustraction -</span><span class="sxs-lookup"><span data-stu-id="7af48-160">Subtraction operator -</span></span>

<span data-ttu-id="7af48-161">L’opérateur de soustraction `-` soustrait son opérande de partie droite de son opérande de partie gauche :</span><span class="sxs-lookup"><span data-stu-id="7af48-161">The subtraction operator `-` subtracts its right-hand operand from its left-hand operand:</span></span>

[!code-csharp-interactive[subtraction operator](snippets/ArithmeticOperators.cs#Subtraction)]

<span data-ttu-id="7af48-162">Vous pouvez également `-` utiliser l’opérateur pour le retrait des délégués.</span><span class="sxs-lookup"><span data-stu-id="7af48-162">You can also use the `-` operator for delegate removal.</span></span> <span data-ttu-id="7af48-163">Pour plus d’informations, voir l’article [ `-` et `-=` les opérateurs.](subtraction-operator.md)</span><span class="sxs-lookup"><span data-stu-id="7af48-163">For more information, see the [`-` and `-=` operators](subtraction-operator.md) article.</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="7af48-164">Assignation composée</span><span class="sxs-lookup"><span data-stu-id="7af48-164">Compound assignment</span></span>

<span data-ttu-id="7af48-165">Pour un opérateur binaire `op`, une expression d’assignation composée du formulaire</span><span class="sxs-lookup"><span data-stu-id="7af48-165">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="7af48-166">équivaut à :</span><span class="sxs-lookup"><span data-stu-id="7af48-166">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="7af48-167">sauf que `x` n’est évalué qu’une seule fois.</span><span class="sxs-lookup"><span data-stu-id="7af48-167">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="7af48-168">L’exemple suivant illustre l’utilisation de l’assignation composée avec des opérateurs arithmétiques :</span><span class="sxs-lookup"><span data-stu-id="7af48-168">The following example demonstrates the usage of compound assignment with arithmetic operators:</span></span>

[!code-csharp-interactive[compound assignment](snippets/ArithmeticOperators.cs#CompoundAssignment)]

<span data-ttu-id="7af48-169">En raison des [promotions numériques](~/_csharplang/spec/expressions.md#numeric-promotions), le résultat de l’opération `op` risque de ne pas être implicitement convertible en type `T` de `x`.</span><span class="sxs-lookup"><span data-stu-id="7af48-169">Because of [numeric promotions](~/_csharplang/spec/expressions.md#numeric-promotions), the result of the `op` operation might be not implicitly convertible to the type `T` of `x`.</span></span> <span data-ttu-id="7af48-170">Dans ce cas, si `op` est un opérateur prédéfini et que le résultat de l’opération est explicitement convertible en type `T` de `x`, une expression d’assignation composée de la forme `x op= y` équivaut à `x = (T)(x op y)`, sauf que `x` n’est évalué qu’une seule fois.</span><span class="sxs-lookup"><span data-stu-id="7af48-170">In such a case, if `op` is a predefined operator and the result of the operation is explicitly convertible to the type `T` of `x`, a compound assignment expression of the form `x op= y` is equivalent to `x = (T)(x op y)`, except that `x` is only evaluated once.</span></span> <span data-ttu-id="7af48-171">L’exemple suivant illustre ce comportement :</span><span class="sxs-lookup"><span data-stu-id="7af48-171">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[compound assignment with cast](snippets/ArithmeticOperators.cs#CompoundAssignmentWithCast)]

<span data-ttu-id="7af48-172">Vous utilisez `+=` également `-=` les opérateurs et les opérateurs pour vous abonner à un événement et se désabonner d’un [événement,](../keywords/event.md)respectivement.</span><span class="sxs-lookup"><span data-stu-id="7af48-172">You also use the `+=` and `-=` operators to subscribe to and unsubscribe from an [event](../keywords/event.md), respectively.</span></span> <span data-ttu-id="7af48-173">Pour plus d’informations, voir [Comment vous abonner et désabonner des événements](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="7af48-173">For more information, see [How to subscribe to and unsubscribe from events](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>

## <a name="operator-precedence-and-associativity"></a><span data-ttu-id="7af48-174">Priorité des opérateurs et associativité</span><span class="sxs-lookup"><span data-stu-id="7af48-174">Operator precedence and associativity</span></span>

<span data-ttu-id="7af48-175">La liste suivante présente les opérateurs arithmétiques de la priorité la plus élevée à la plus basse :</span><span class="sxs-lookup"><span data-stu-id="7af48-175">The following list orders arithmetic operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="7af48-176">Opérateurs suffixés d’incrémentation `x++` et de décrémentation `x--`</span><span class="sxs-lookup"><span data-stu-id="7af48-176">Postfix increment `x++` and decrement `x--` operators</span></span>
- <span data-ttu-id="7af48-177">Opérateurs préfixés d’incrémentation `++x` et de décrémentation `--x` et opérateurs unaires `+` et `-`</span><span class="sxs-lookup"><span data-stu-id="7af48-177">Prefix increment `++x` and decrement `--x` and unary `+` and `-` operators</span></span>
- <span data-ttu-id="7af48-178">Opérateurs multiplicatifs `*`, `/` et `%`</span><span class="sxs-lookup"><span data-stu-id="7af48-178">Multiplicative `*`, `/`, and `%` operators</span></span>
- <span data-ttu-id="7af48-179">Opérateurs additifs `+` et `-`</span><span class="sxs-lookup"><span data-stu-id="7af48-179">Additive `+` and `-` operators</span></span>

<span data-ttu-id="7af48-180">Les opérateurs arithmétiques binaires sont associatifs sur leur gauche.</span><span class="sxs-lookup"><span data-stu-id="7af48-180">Binary arithmetic operators are left-associative.</span></span> <span data-ttu-id="7af48-181">Autrement dit, les opérateurs de même niveau de priorité sont évalués de gauche à droite.</span><span class="sxs-lookup"><span data-stu-id="7af48-181">That is, operators with the same precedence level are evaluated from left to right.</span></span>

<span data-ttu-id="7af48-182">Utilisez des parenthèses, `()`, pour modifier l’ordre d’évaluation imposé par la priorité et l’associativité de l’opérateur.</span><span class="sxs-lookup"><span data-stu-id="7af48-182">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence and associativity.</span></span>

[!code-csharp-interactive[precedence and associativity](snippets/ArithmeticOperators.cs#PrecedenceAndAssociativity)]

<span data-ttu-id="7af48-183">Pour la liste complète des opérateurs C’commandés par niveau de préséance, voir la section [De préséance de l’opérateur](index.md#operator-precedence) de [l’article des opérateurs C.](index.md)</span><span class="sxs-lookup"><span data-stu-id="7af48-183">For the complete list of C# operators ordered by precedence level, see the [Operator precedence](index.md#operator-precedence) section of the [C# operators](index.md) article.</span></span>

## <a name="arithmetic-overflow-and-division-by-zero"></a><span data-ttu-id="7af48-184">Débordement arithmétique et division par zéro</span><span class="sxs-lookup"><span data-stu-id="7af48-184">Arithmetic overflow and division by zero</span></span>

<span data-ttu-id="7af48-185">Quand le résultat d’une opération arithmétique n’est pas compris dans la plage de valeurs finies possibles du type numérique impliqué, le comportement d’un opérateur arithmétique varie selon le type de ses opérandes.</span><span class="sxs-lookup"><span data-stu-id="7af48-185">When the result of an arithmetic operation is outside the range of possible finite values of the involved numeric type, the behavior of an arithmetic operator depends on the type of its operands.</span></span>

### <a name="integer-arithmetic-overflow"></a><span data-ttu-id="7af48-186">Débordement arithmétique entier</span><span class="sxs-lookup"><span data-stu-id="7af48-186">Integer arithmetic overflow</span></span>

<span data-ttu-id="7af48-187">La division d'un entier par zéro lève toujours une exception <xref:System.DivideByZeroException>.</span><span class="sxs-lookup"><span data-stu-id="7af48-187">Integer division by zero always throws a <xref:System.DivideByZeroException>.</span></span>

<span data-ttu-id="7af48-188">En cas de débordement arithmétique entier, un contexte de vérification de débordement, qui peut être [vérifié ou non vérifié](../keywords/checked-and-unchecked.md), contrôle le comportement qui en résulte :</span><span class="sxs-lookup"><span data-stu-id="7af48-188">In case of integer arithmetic overflow, an overflow checking context, which can be [checked or unchecked](../keywords/checked-and-unchecked.md), controls the resulting behavior:</span></span>

- <span data-ttu-id="7af48-189">Dans un contexte vérifié, si le débordement se produit dans une expression constante, une erreur de compilation se produit.</span><span class="sxs-lookup"><span data-stu-id="7af48-189">In a checked context, if overflow happens in a constant expression, a compile-time error occurs.</span></span> <span data-ttu-id="7af48-190">Sinon, un <xref:System.OverflowException> est levé quand l’opération est effectuée au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="7af48-190">Otherwise, when the operation is performed at run time, an <xref:System.OverflowException> is thrown.</span></span>
- <span data-ttu-id="7af48-191">Dans un contexte non vérifié, le résultat est tronqué en supprimant tous les bits de poids fort qui ne tiennent pas dans le type destinataire.</span><span class="sxs-lookup"><span data-stu-id="7af48-191">In an unchecked context, the result is truncated by discarding any high-order bits that don't fit in the destination type.</span></span>

<span data-ttu-id="7af48-192">Avec les instructions [vérifiées et non vérifiées](../keywords/checked-and-unchecked.md), vous pouvez utiliser les opérateurs `checked` et `unchecked` pour contrôler le contexte de vérification de débordement, dans lequel une expression est évaluée :</span><span class="sxs-lookup"><span data-stu-id="7af48-192">Along with the [checked and unchecked](../keywords/checked-and-unchecked.md) statements, you can use the `checked` and `unchecked` operators to control the overflow checking context, in which an expression is evaluated:</span></span>

[!code-csharp-interactive[checked and unchecked](snippets/ArithmeticOperators.cs#CheckedUnchecked)]

<span data-ttu-id="7af48-193">Par défaut, les opérations arithmétiques se produisent dans un contexte *unchecked*.</span><span class="sxs-lookup"><span data-stu-id="7af48-193">By default, arithmetic operations occur in an *unchecked* context.</span></span>

### <a name="floating-point-arithmetic-overflow"></a><span data-ttu-id="7af48-194">Débordement arithmétique à virgule flottante</span><span class="sxs-lookup"><span data-stu-id="7af48-194">Floating-point arithmetic overflow</span></span>

<span data-ttu-id="7af48-195">Les opérations arithmétiques avec les types `float` et `double` ne lèvent jamais d’exceptions.</span><span class="sxs-lookup"><span data-stu-id="7af48-195">Arithmetic operations with the `float` and `double` types never throw an exception.</span></span> <span data-ttu-id="7af48-196">Le résultat des opérations arithmétiques avec ces types peut être une des valeurs spéciales qui représentent l’infini et non un nombre :</span><span class="sxs-lookup"><span data-stu-id="7af48-196">The result of arithmetic operations with those types can be one of special values that represent infinity and not-a-number:</span></span>

[!code-csharp-interactive[double non-finite values](snippets/ArithmeticOperators.cs#FloatingPointOverflow)]

<span data-ttu-id="7af48-197">Pour les opérandes du type `decimal`, le débordement arithmétique lève toujours un <xref:System.OverflowException> et la division par zéro lève toujours un <xref:System.DivideByZeroException>.</span><span class="sxs-lookup"><span data-stu-id="7af48-197">For the operands of the `decimal` type, arithmetic overflow always throws an <xref:System.OverflowException> and division by zero always throws a <xref:System.DivideByZeroException>.</span></span>

## <a name="round-off-errors"></a><span data-ttu-id="7af48-198">Erreurs d’arrondi</span><span class="sxs-lookup"><span data-stu-id="7af48-198">Round-off errors</span></span>

<span data-ttu-id="7af48-199">En raison des limites générales de la représentation des points flottants des nombres réels et de l’arithmétique à point flottant, des erreurs de ronde pourraient se produire dans les calculs avec des types de points flottants.</span><span class="sxs-lookup"><span data-stu-id="7af48-199">Because of general limitations of the floating-point representation of real numbers and floating-point arithmetic, round-off errors might occur in calculations with floating-point types.</span></span> <span data-ttu-id="7af48-200">Autrement dit, le résultat d’une expression peut différer du résultat mathématique attendu.</span><span class="sxs-lookup"><span data-stu-id="7af48-200">That is, the produced result of an expression might differ from the expected mathematical result.</span></span> <span data-ttu-id="7af48-201">L’exemple suivant illustre plusieurs cas de ce genre :</span><span class="sxs-lookup"><span data-stu-id="7af48-201">The following example demonstrates several such cases:</span></span>

[!code-csharp-interactive[round-off errors](snippets/ArithmeticOperators.cs#RoundOffErrors)]

<span data-ttu-id="7af48-202">Pour plus d’informations, voir remarques à [l’adresse System.Double](/dotnet/api/system.double#remarks), [System.Single](/dotnet/api/system.single#remarks), ou [System.Decimal](/dotnet/api/system.decimal#remarks) pages de référence.</span><span class="sxs-lookup"><span data-stu-id="7af48-202">For more information, see remarks at the [System.Double](/dotnet/api/system.double#remarks), [System.Single](/dotnet/api/system.single#remarks), or [System.Decimal](/dotnet/api/system.decimal#remarks) reference pages.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="7af48-203">Capacité de surcharge de l’opérateur</span><span class="sxs-lookup"><span data-stu-id="7af48-203">Operator overloadability</span></span>

<span data-ttu-id="7af48-204">Un type défini par l’utilisateur`++`peut `--` `+` [surcharger](operator-overloading.md) les opérateurs unary `+`( `-`, , et `-`) et binaires (`*` `/`, `%`, , et ) arithmétique.</span><span class="sxs-lookup"><span data-stu-id="7af48-204">A user-defined type can [overload](operator-overloading.md) the unary (`++`, `--`, `+`, and `-`) and binary (`*`, `/`, `%`, `+`, and `-`) arithmetic operators.</span></span> <span data-ttu-id="7af48-205">Quand un opérateur binaire est surchargé, l’opérateur d’assignation composée correspondant est aussi implicitement surchargé.</span><span class="sxs-lookup"><span data-stu-id="7af48-205">When a binary operator is overloaded, the corresponding compound assignment operator is also implicitly overloaded.</span></span> <span data-ttu-id="7af48-206">Un type défini par l’utilisateur ne peut pas surcharger explicitement un opérateur d’assignation composée.</span><span class="sxs-lookup"><span data-stu-id="7af48-206">A user-defined type cannot explicitly overload a compound assignment operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="7af48-207">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="7af48-207">C# language specification</span></span>

<span data-ttu-id="7af48-208">Pour plus d’informations, consultez les sections suivantes de la [spécification du langage C#](~/_csharplang/spec/introduction.md) :</span><span class="sxs-lookup"><span data-stu-id="7af48-208">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="7af48-209">Opérateurs suffixés d’incrémentation et de décrémentation</span><span class="sxs-lookup"><span data-stu-id="7af48-209">Postfix increment and decrement operators</span></span>](~/_csharplang/spec/expressions.md#postfix-increment-and-decrement-operators)
- [<span data-ttu-id="7af48-210">Opérateurs d’augmentation et de décroissement de Préfixe</span><span class="sxs-lookup"><span data-stu-id="7af48-210">Prefix increment and decrement operators</span></span>](~/_csharplang/spec/expressions.md#prefix-increment-and-decrement-operators)
- [<span data-ttu-id="7af48-211">Opérateur plus unaire</span><span class="sxs-lookup"><span data-stu-id="7af48-211">Unary plus operator</span></span>](~/_csharplang/spec/expressions.md#unary-plus-operator)
- [<span data-ttu-id="7af48-212">Opération moins unaire</span><span class="sxs-lookup"><span data-stu-id="7af48-212">Unary minus operator</span></span>](~/_csharplang/spec/expressions.md#unary-minus-operator)
- [<span data-ttu-id="7af48-213">Opérateur de multiplication</span><span class="sxs-lookup"><span data-stu-id="7af48-213">Multiplication operator</span></span>](~/_csharplang/spec/expressions.md#multiplication-operator)
- [<span data-ttu-id="7af48-214">Opérateur de division</span><span class="sxs-lookup"><span data-stu-id="7af48-214">Division operator</span></span>](~/_csharplang/spec/expressions.md#division-operator)
- [<span data-ttu-id="7af48-215">Opérateur restant</span><span class="sxs-lookup"><span data-stu-id="7af48-215">Remainder operator</span></span>](~/_csharplang/spec/expressions.md#remainder-operator)
- [<span data-ttu-id="7af48-216">Opérateur d’addition</span><span class="sxs-lookup"><span data-stu-id="7af48-216">Addition operator</span></span>](~/_csharplang/spec/expressions.md#addition-operator)
- [<span data-ttu-id="7af48-217">Opérateur de soustraction</span><span class="sxs-lookup"><span data-stu-id="7af48-217">Subtraction operator</span></span>](~/_csharplang/spec/expressions.md#subtraction-operator)
- [<span data-ttu-id="7af48-218">Assignation composée</span><span class="sxs-lookup"><span data-stu-id="7af48-218">Compound assignment</span></span>](~/_csharplang/spec/expressions.md#compound-assignment)
- [<span data-ttu-id="7af48-219">Opérateurs vérifiés et non vérifiés</span><span class="sxs-lookup"><span data-stu-id="7af48-219">The checked and unchecked operators</span></span>](~/_csharplang/spec/expressions.md#the-checked-and-unchecked-operators)
- [<span data-ttu-id="7af48-220">Promotions numériques</span><span class="sxs-lookup"><span data-stu-id="7af48-220">Numeric promotions</span></span>](~/_csharplang/spec/expressions.md#numeric-promotions)

## <a name="see-also"></a><span data-ttu-id="7af48-221">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7af48-221">See also</span></span>

- [<span data-ttu-id="7af48-222">Référence C#</span><span class="sxs-lookup"><span data-stu-id="7af48-222">C# reference</span></span>](../index.md)
- [<span data-ttu-id="7af48-223">Opérateurs CMD</span><span class="sxs-lookup"><span data-stu-id="7af48-223">C# operators</span></span>](index.md)
- <xref:System.Math?displayProperty=nameWithType>
- <xref:System.MathF?displayProperty=nameWithType>
- [<span data-ttu-id="7af48-224">Valeurs numériques dans .NET</span><span class="sxs-lookup"><span data-stu-id="7af48-224">Numerics in .NET</span></span>](../../../standard/numerics.md)
