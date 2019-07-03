---
title: Opérateurs d’égalité - Référence C#
description: Découvrez les opérateurs de comparaison d’égalité C#.
ms.date: 03/28/2019
author: pkulikov
f1_keywords:
- ==_CSharpKeyword
- '!=_CSharpKeyword'
helpviewer_keywords:
- comparison operators [C#]
- relational operators [C#]
- equality operator [C#]
- equals operator [C#]
- == operator [C#]
- inequality operator [C#]
- not equals operator [C#]
- '!= operator [C#]'
ms.openlocfilehash: f60d62d1823a8bd06b0417638719a81e95d7438b
ms.sourcegitcommit: 4c41ec195caf03d98b7900007c3c8e24eba20d34
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/20/2019
ms.locfileid: "67267699"
---
# <a name="equality-operators-c-reference"></a><span data-ttu-id="df6cd-103">Opérateurs d’égalité (référence C#)</span><span class="sxs-lookup"><span data-stu-id="df6cd-103">Equality operators (C# reference)</span></span>

<span data-ttu-id="df6cd-104">Les opérateurs [`==` (égalité)](#equality-operator-) et [`!=` (inégalité)](#inequality-operator-) vérifient si leurs opérandes sont égaux ou non.</span><span class="sxs-lookup"><span data-stu-id="df6cd-104">The [`==` (equality)](#equality-operator-) and [`!=` (inequality)](#inequality-operator-) operators check if their operands are equal or not.</span></span>

## <a name="equality-operator-"></a><span data-ttu-id="df6cd-105">Opérateur d’égalité ==</span><span class="sxs-lookup"><span data-stu-id="df6cd-105">Equality operator ==</span></span>

<span data-ttu-id="df6cd-106">L’opérateur d’égalité `==` retourne `true` si ses opérandes sont égaux, `false` dans le cas contraire.</span><span class="sxs-lookup"><span data-stu-id="df6cd-106">The equality operator `==` returns `true` if its operands are equal, `false` otherwise.</span></span>

### <a name="value-types-equality"></a><span data-ttu-id="df6cd-107">Égalité de types valeur</span><span class="sxs-lookup"><span data-stu-id="df6cd-107">Value types equality</span></span>

<span data-ttu-id="df6cd-108">Les opérandes des [types valeur intégrés](../keywords/value-types-table.md) sont égaux si leurs valeurs sont égales :</span><span class="sxs-lookup"><span data-stu-id="df6cd-108">Operands of the [built-in value types](../keywords/value-types-table.md) are equal if their values are equal:</span></span>

[!code-csharp-interactive[value types equality](~/samples/csharp/language-reference/operators/EqualityOperators.cs#ValueTypesEquality)]

> [!NOTE]
> <span data-ttu-id="df6cd-109">Pour les opérateurs `==`, [`<`, `>`, `<=` et `>=`](comparison-operators.md), si un des opérandes n’est pas un nombre (<xref:System.Double.NaN?displayProperty=nameWithType> ou <xref:System.Single.NaN?displayProperty=nameWithType>), le résultat de l’opération est `false`.</span><span class="sxs-lookup"><span data-stu-id="df6cd-109">For the `==`, [`<`, `>`, `<=`, and `>=`](comparison-operators.md) operators, if any of the operands is not a number (<xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType>), the result of operation is `false`.</span></span> <span data-ttu-id="df6cd-110">Cela signifie que la valeur `NaN` n’est ni supérieure à, ni inférieure à, ni égale à n’importe quelle autre valeur `double` (ou `float`), y compris `NaN`.</span><span class="sxs-lookup"><span data-stu-id="df6cd-110">That means that the `NaN` value is neither greater than, less than, nor equal to any other `double` (or `float`) value, including `NaN`.</span></span> <span data-ttu-id="df6cd-111">Pour plus d’informations et des exemples, consultez l’article de référence <xref:System.Double.NaN?displayProperty=nameWithType> ou <xref:System.Single.NaN?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="df6cd-111">For more information and examples, see the <xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType> reference article.</span></span>

<span data-ttu-id="df6cd-112">Deux opérandes du même type [enum](../keywords/enum.md) sont égaux si les valeurs correspondantes du type intégral sous-jacent sont égales.</span><span class="sxs-lookup"><span data-stu-id="df6cd-112">Two operands of the same [enum](../keywords/enum.md) type are equal if the corresponding values of the underlying integral type are equal.</span></span>

<span data-ttu-id="df6cd-113">Par défaut, les types [struct](../keywords/struct.md) définis par l’utilisateur ne prennent pas en charge l’opérateur `==`.</span><span class="sxs-lookup"><span data-stu-id="df6cd-113">User-defined [struct](../keywords/struct.md) types don't support the `==` operator by default.</span></span> <span data-ttu-id="df6cd-114">Pour prendre en charge l’opérateur `==`, un struct défini par l’utilisateur doit le [surcharger](#operator-overloadability).</span><span class="sxs-lookup"><span data-stu-id="df6cd-114">To support the `==` operator, a user-defined struct must [overload](#operator-overloadability) it.</span></span>

<span data-ttu-id="df6cd-115">À compter de C# 7.3, les opérateurs `==` et `!=` sont pris en charge par les [tuples](../../tuples.md) C#.</span><span class="sxs-lookup"><span data-stu-id="df6cd-115">Beginning with C# 7.3, the `==` and `!=` operators are supported by C# [tuples](../../tuples.md).</span></span> <span data-ttu-id="df6cd-116">Pour plus d’informations, consultez la section [Égalité et tuples](../../tuples.md#equality-and-tuples) de l’article [Types de tuple C#](../../tuples.md).</span><span class="sxs-lookup"><span data-stu-id="df6cd-116">For more information, see the [Equality and tuples](../../tuples.md#equality-and-tuples) section of the [C# tuple types](../../tuples.md) article.</span></span>

### <a name="string-equality"></a><span data-ttu-id="df6cd-117">Égalité de chaîne</span><span class="sxs-lookup"><span data-stu-id="df6cd-117">String equality</span></span>

<span data-ttu-id="df6cd-118">Deux opérandes [string](../keywords/string.md) sont égaux lorsque les deux sont `null` ou lorsque les deux instances de chaîne sont de même longueur et ont des caractères identiques dans chaque position de caractère :</span><span class="sxs-lookup"><span data-stu-id="df6cd-118">Two [string](../keywords/string.md) operands are equal when both of them are `null` or both string instances are of the same length and have identical characters in each character position:</span></span>

[!code-csharp-interactive[string equality](~/samples/csharp/language-reference/operators/EqualityOperators.cs#StringEquality)]

<span data-ttu-id="df6cd-119">Il s’agit d’une comparaison ordinale respectant la casse.</span><span class="sxs-lookup"><span data-stu-id="df6cd-119">That is case-sensitive ordinal comparison.</span></span> <span data-ttu-id="df6cd-120">Pour plus d’informations sur la comparaison de chaînes, consultez [Comment comparer des chaînes en C#](../../how-to/compare-strings.md).</span><span class="sxs-lookup"><span data-stu-id="df6cd-120">For more information about string comparison, see [How to compare strings in C#](../../how-to/compare-strings.md).</span></span>

### <a name="reference-types-equality"></a><span data-ttu-id="df6cd-121">Égalité de types référence</span><span class="sxs-lookup"><span data-stu-id="df6cd-121">Reference types equality</span></span>

<span data-ttu-id="df6cd-122">Deux opérandes de type référence autres que `string` sont égaux lorsqu’ils font référence au même objet :</span><span class="sxs-lookup"><span data-stu-id="df6cd-122">Two other than `string` reference type operands are equal when they refer to the same object:</span></span>

[!code-csharp[reference type equality](~/samples/csharp/language-reference/operators/EqualityOperators.cs#ReferenceTypesEquality)]

<span data-ttu-id="df6cd-123">Comme le montre l’exemple, les types référence définis par l’utilisateur prennent en charge l’opérateur `==` par défaut.</span><span class="sxs-lookup"><span data-stu-id="df6cd-123">As the example shows, user-defined reference types support the `==` operator by default.</span></span> <span data-ttu-id="df6cd-124">Un type référence défini par l’utilisateur peut toutefois surcharger l’opérateur `==`.</span><span class="sxs-lookup"><span data-stu-id="df6cd-124">However, a user-defined reference type can overload the `==` operator.</span></span> <span data-ttu-id="df6cd-125">Si un type référence surcharge l’opérateur `==`, utilisez la méthode <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> pour vérifier si deux références de ce type font référence au même objet.</span><span class="sxs-lookup"><span data-stu-id="df6cd-125">If a reference type overloads the `==` operator, use the <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> method to check if two references of that type refer to the same object.</span></span>

## <a name="inequality-operator-"></a><span data-ttu-id="df6cd-126">Opérateur d’inégalité !=</span><span class="sxs-lookup"><span data-stu-id="df6cd-126">Inequality operator !=</span></span>

<span data-ttu-id="df6cd-127">L’opérateur d’inégalité `!=` retourne `true` si ses opérandes ne sont pas égaux, `false` dans le cas contraire.</span><span class="sxs-lookup"><span data-stu-id="df6cd-127">The inequality operator `!=` returns `true` if its operands are not equal, `false` otherwise.</span></span> <span data-ttu-id="df6cd-128">Pour les opérandes des [types intégrés](../keywords/built-in-types-table.md), l’expression `x != y` produit le même résultat que l’expression `!(x == y)`.</span><span class="sxs-lookup"><span data-stu-id="df6cd-128">For the operands of the [built-in types](../keywords/built-in-types-table.md), the expression `x != y` produces the same result as the expression `!(x == y)`.</span></span> <span data-ttu-id="df6cd-129">Pour plus d’informations sur l’égalité des types, consultez la section [Opérateur d’égalité](#equality-operator-).</span><span class="sxs-lookup"><span data-stu-id="df6cd-129">For more information about type equality, see the [Equality operator](#equality-operator-) section.</span></span>

<span data-ttu-id="df6cd-130">L’exemple suivant illustre l’utilisation de l’opérateur `!=` :</span><span class="sxs-lookup"><span data-stu-id="df6cd-130">The following example demonstrates the usage of the `!=` operator:</span></span>

[!code-csharp-interactive[non-equality examples](~/samples/csharp/language-reference/operators/EqualityOperators.cs#NonEquality)]

## <a name="operator-overloadability"></a><span data-ttu-id="df6cd-131">Capacité de surcharge de l’opérateur</span><span class="sxs-lookup"><span data-stu-id="df6cd-131">Operator overloadability</span></span>

<span data-ttu-id="df6cd-132">Un type défini par l’utilisateur peut [surcharger](../keywords/operator.md) les opérateurs `==` et `!=`.</span><span class="sxs-lookup"><span data-stu-id="df6cd-132">A user-defined type can [overload](../keywords/operator.md) the `==` and `!=` operators.</span></span> <span data-ttu-id="df6cd-133">Si un type surcharge un des deux opérateurs, il doit aussi en surcharger un autre.</span><span class="sxs-lookup"><span data-stu-id="df6cd-133">If a type overloads one of the two operators, it must also overload another one.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="df6cd-134">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="df6cd-134">C# language specification</span></span>

<span data-ttu-id="df6cd-135">Pour plus d’informations, consultez la section [Opérateurs relationnels et de test de type](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="df6cd-135">For more information, see the [Relational and type-testing operators](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="df6cd-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="df6cd-136">See also</span></span>

- [<span data-ttu-id="df6cd-137">Informations de référence sur C#</span><span class="sxs-lookup"><span data-stu-id="df6cd-137">C# reference</span></span>](../index.md)
- [<span data-ttu-id="df6cd-138">Opérateurs C#</span><span class="sxs-lookup"><span data-stu-id="df6cd-138">C# operators</span></span>](index.md)
- <xref:System.IEquatable%601?displayProperty=nameWithType>
- <xref:System.Object.Equals%2A?displayProperty=nameWithType>
- <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType>
- [<span data-ttu-id="df6cd-139">Comparaisons d’égalité</span><span class="sxs-lookup"><span data-stu-id="df6cd-139">Equality comparisons</span></span>](../../programming-guide/statements-expressions-operators/equality-comparisons.md)
- [<span data-ttu-id="df6cd-140">Opérateurs de comparaison</span><span class="sxs-lookup"><span data-stu-id="df6cd-140">Comparison operators</span></span>](comparison-operators.md)
