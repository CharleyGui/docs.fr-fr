---
title: Opérateurs d’égalité - Référence C#
description: En savoir plus sur les opérateurs de comparaison d’égalité C# et l’égalité de type C#.
ms.date: 06/26/2019
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
ms.openlocfilehash: 6771edcca8159b0805018c16167b25c287d3152c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743743"
---
# <a name="equality-operators-c-reference"></a><span data-ttu-id="367f1-103">Opérateurs d’égalité (référence C#)</span><span class="sxs-lookup"><span data-stu-id="367f1-103">Equality operators (C# reference)</span></span>

<span data-ttu-id="367f1-104">Les opérateurs [`==` (égalité)](#equality-operator-) et [`!=` (inégalité)](#inequality-operator-) vérifient si leurs opérandes sont égaux ou non.</span><span class="sxs-lookup"><span data-stu-id="367f1-104">The [`==` (equality)](#equality-operator-) and [`!=` (inequality)](#inequality-operator-) operators check if their operands are equal or not.</span></span>

## <a name="equality-operator-"></a><span data-ttu-id="367f1-105">Opérateur d’égalité ==</span><span class="sxs-lookup"><span data-stu-id="367f1-105">Equality operator ==</span></span>

<span data-ttu-id="367f1-106">L’opérateur d’égalité `==` retourne `true` si ses opérandes sont égaux, `false` dans le cas contraire.</span><span class="sxs-lookup"><span data-stu-id="367f1-106">The equality operator `==` returns `true` if its operands are equal, `false` otherwise.</span></span>

### <a name="value-types-equality"></a><span data-ttu-id="367f1-107">Égalité de types valeur</span><span class="sxs-lookup"><span data-stu-id="367f1-107">Value types equality</span></span>

<span data-ttu-id="367f1-108">Les opérandes des [types valeur intégrés](../builtin-types/value-types.md#built-in-value-types) sont égaux si leurs valeurs sont égales :</span><span class="sxs-lookup"><span data-stu-id="367f1-108">Operands of the [built-in value types](../builtin-types/value-types.md#built-in-value-types) are equal if their values are equal:</span></span>

[!code-csharp-interactive[value types equality](~/samples/csharp/language-reference/operators/EqualityOperators.cs#ValueTypesEquality)]

> [!NOTE]
> <span data-ttu-id="367f1-109">Pour les opérateurs `==`, [`<`, `>`, `<=` et `>=`](comparison-operators.md), si un des opérandes n’est pas un nombre (<xref:System.Double.NaN?displayProperty=nameWithType> ou <xref:System.Single.NaN?displayProperty=nameWithType>), le résultat de l’opération est `false`.</span><span class="sxs-lookup"><span data-stu-id="367f1-109">For the `==`, [`<`, `>`, `<=`, and `>=`](comparison-operators.md) operators, if any of the operands is not a number (<xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType>), the result of operation is `false`.</span></span> <span data-ttu-id="367f1-110">Cela signifie que la valeur `NaN` n’est ni supérieure à, ni inférieure à, ni égale à n’importe quelle autre valeur `double` (ou `float`), y compris `NaN`.</span><span class="sxs-lookup"><span data-stu-id="367f1-110">That means that the `NaN` value is neither greater than, less than, nor equal to any other `double` (or `float`) value, including `NaN`.</span></span> <span data-ttu-id="367f1-111">Pour plus d’informations et des exemples, consultez l’article de référence <xref:System.Double.NaN?displayProperty=nameWithType> ou <xref:System.Single.NaN?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="367f1-111">For more information and examples, see the <xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType> reference article.</span></span>

<span data-ttu-id="367f1-112">Deux opérandes du même type [enum](../builtin-types/enum.md) sont égaux si les valeurs correspondantes du type intégral sous-jacent sont égales.</span><span class="sxs-lookup"><span data-stu-id="367f1-112">Two operands of the same [enum](../builtin-types/enum.md) type are equal if the corresponding values of the underlying integral type are equal.</span></span>

<span data-ttu-id="367f1-113">Par défaut, les types [struct](../keywords/struct.md) définis par l’utilisateur ne prennent pas en charge l’opérateur `==`.</span><span class="sxs-lookup"><span data-stu-id="367f1-113">User-defined [struct](../keywords/struct.md) types don't support the `==` operator by default.</span></span> <span data-ttu-id="367f1-114">Pour prendre en charge l’opérateur `==`, un struct défini par l’utilisateur doit le [surcharger](operator-overloading.md).</span><span class="sxs-lookup"><span data-stu-id="367f1-114">To support the `==` operator, a user-defined struct must [overload](operator-overloading.md) it.</span></span>

<span data-ttu-id="367f1-115">À compter de C# 7.3, les opérateurs `==` et `!=` sont pris en charge par les [tuples](../../tuples.md) C#.</span><span class="sxs-lookup"><span data-stu-id="367f1-115">Beginning with C# 7.3, the `==` and `!=` operators are supported by C# [tuples](../../tuples.md).</span></span> <span data-ttu-id="367f1-116">Pour plus d’informations, consultez la section [Égalité et tuples](../../tuples.md#equality-and-tuples) de l’article [Types de tuple C#](../../tuples.md).</span><span class="sxs-lookup"><span data-stu-id="367f1-116">For more information, see the [Equality and tuples](../../tuples.md#equality-and-tuples) section of the [C# tuple types](../../tuples.md) article.</span></span>

### <a name="reference-types-equality"></a><span data-ttu-id="367f1-117">Égalité de types référence</span><span class="sxs-lookup"><span data-stu-id="367f1-117">Reference types equality</span></span>

<span data-ttu-id="367f1-118">Par défaut, deux opérandes de type référence sont égaux s’ils font référence au même objet :</span><span class="sxs-lookup"><span data-stu-id="367f1-118">By default, two reference-type operands are equal if they refer to the same object:</span></span>

[!code-csharp[reference type equality](~/samples/csharp/language-reference/operators/EqualityOperators.cs#ReferenceTypesEquality)]

<span data-ttu-id="367f1-119">Comme le montre l’exemple, les types référence définis par l’utilisateur prennent en charge l’opérateur `==` par défaut.</span><span class="sxs-lookup"><span data-stu-id="367f1-119">As the example shows, user-defined reference types support the `==` operator by default.</span></span> <span data-ttu-id="367f1-120">Un type référence peut toutefois surcharger l’opérateur `==`.</span><span class="sxs-lookup"><span data-stu-id="367f1-120">However, a reference type can overload the `==` operator.</span></span> <span data-ttu-id="367f1-121">Si un type référence surcharge l’opérateur `==`, utilisez la méthode <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> pour vérifier si deux références de ce type font référence au même objet.</span><span class="sxs-lookup"><span data-stu-id="367f1-121">If a reference type overloads the `==` operator, use the <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> method to check if two references of that type refer to the same object.</span></span>

### <a name="string-equality"></a><span data-ttu-id="367f1-122">Égalité de chaîne</span><span class="sxs-lookup"><span data-stu-id="367f1-122">String equality</span></span>

<span data-ttu-id="367f1-123">Deux opérandes [string](../builtin-types/reference-types.md#the-string-type) sont égaux lorsque les deux sont `null` ou lorsque les deux instances de chaîne sont de même longueur et ont des caractères identiques dans chaque position de caractère :</span><span class="sxs-lookup"><span data-stu-id="367f1-123">Two [string](../builtin-types/reference-types.md#the-string-type) operands are equal when both of them are `null` or both string instances are of the same length and have identical characters in each character position:</span></span>

[!code-csharp-interactive[string equality](~/samples/csharp/language-reference/operators/EqualityOperators.cs#StringEquality)]

<span data-ttu-id="367f1-124">Il s’agit d’une comparaison ordinale respectant la casse.</span><span class="sxs-lookup"><span data-stu-id="367f1-124">That is a case-sensitive ordinal comparison.</span></span> <span data-ttu-id="367f1-125">Pour plus d’informations sur la comparaison de chaînes, consultez [Comment comparer des chaînes en C#](../../how-to/compare-strings.md).</span><span class="sxs-lookup"><span data-stu-id="367f1-125">For more information about string comparison, see [How to compare strings in C#](../../how-to/compare-strings.md).</span></span>

### <a name="delegate-equality"></a><span data-ttu-id="367f1-126">Égalité de délégué</span><span class="sxs-lookup"><span data-stu-id="367f1-126">Delegate equality</span></span>

<span data-ttu-id="367f1-127">Deux opérandes de [délégué](../../programming-guide/delegates/index.md) du même type de runtime sont égaux si les deux sont `null` ou si leurs listes d’appel sont de même longueur et ont des entrées égales dans chaque position :</span><span class="sxs-lookup"><span data-stu-id="367f1-127">Two [delegate](../../programming-guide/delegates/index.md) operands of the same runtime type are equal when both of them are `null` or their invocation lists are of the same length and have equal entries in each position:</span></span>

[!code-csharp-interactive[delegate equality](~/samples/csharp/language-reference/operators/EqualityOperators.cs#DelegateEquality)]

<span data-ttu-id="367f1-128">Pour plus d’informations, consultez la section [Opérateurs d’égalité de délégué](~/_csharplang/spec/expressions.md#delegate-equality-operators) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="367f1-128">For more information, see the [Delegate equality operators](~/_csharplang/spec/expressions.md#delegate-equality-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="367f1-129">Les délégués qui sont produits à partir de l’évaluation d’[expressions lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md) identiques sémantiquement ne sont pas égaux, comme l’indique l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="367f1-129">Delegates that are produced from evaluation of semantically identical [lambda expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md) are not equal, as the following example shows:</span></span>

[!code-csharp-interactive[from identical lambdas](~/samples/csharp/language-reference/operators/EqualityOperators.cs#IdenticalLambdas)]

## <a name="inequality-operator-"></a><span data-ttu-id="367f1-130">Opérateur d’inégalité !=</span><span class="sxs-lookup"><span data-stu-id="367f1-130">Inequality operator !=</span></span>

<span data-ttu-id="367f1-131">L’opérateur d’inégalité `!=` retourne `true` si ses opérandes ne sont pas égaux, `false` dans le cas contraire.</span><span class="sxs-lookup"><span data-stu-id="367f1-131">The inequality operator `!=` returns `true` if its operands are not equal, `false` otherwise.</span></span> <span data-ttu-id="367f1-132">Pour les opérandes des [types intégrés](../keywords/built-in-types-table.md), l’expression `x != y` produit le même résultat que l’expression `!(x == y)`.</span><span class="sxs-lookup"><span data-stu-id="367f1-132">For the operands of the [built-in types](../keywords/built-in-types-table.md), the expression `x != y` produces the same result as the expression `!(x == y)`.</span></span> <span data-ttu-id="367f1-133">Pour plus d’informations sur l’égalité des types, consultez la section [Opérateur d’égalité](#equality-operator-).</span><span class="sxs-lookup"><span data-stu-id="367f1-133">For more information about type equality, see the [Equality operator](#equality-operator-) section.</span></span>

<span data-ttu-id="367f1-134">L’exemple suivant illustre l’utilisation de l’opérateur `!=` :</span><span class="sxs-lookup"><span data-stu-id="367f1-134">The following example demonstrates the usage of the `!=` operator:</span></span>

[!code-csharp-interactive[non-equality examples](~/samples/csharp/language-reference/operators/EqualityOperators.cs#NonEquality)]

## <a name="operator-overloadability"></a><span data-ttu-id="367f1-135">Capacité de surcharge de l’opérateur</span><span class="sxs-lookup"><span data-stu-id="367f1-135">Operator overloadability</span></span>

<span data-ttu-id="367f1-136">Un type défini par l’utilisateur peut [surcharger](operator-overloading.md) les opérateurs `==` et `!=`.</span><span class="sxs-lookup"><span data-stu-id="367f1-136">A user-defined type can [overload](operator-overloading.md) the `==` and `!=` operators.</span></span> <span data-ttu-id="367f1-137">Si un type surcharge un des deux opérateurs, il doit aussi en surcharger un autre.</span><span class="sxs-lookup"><span data-stu-id="367f1-137">If a type overloads one of the two operators, it must also overload another one.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="367f1-138">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="367f1-138">C# language specification</span></span>

<span data-ttu-id="367f1-139">Pour plus d’informations, consultez la section [Opérateurs relationnels et de test de type](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="367f1-139">For more information, see the [Relational and type-testing operators](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="367f1-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="367f1-140">See also</span></span>

- [<span data-ttu-id="367f1-141">Informations de référence sur C#</span><span class="sxs-lookup"><span data-stu-id="367f1-141">C# reference</span></span>](../index.md)
- [<span data-ttu-id="367f1-142">Opérateurs C#</span><span class="sxs-lookup"><span data-stu-id="367f1-142">C# operators</span></span>](index.md)
- <xref:System.IEquatable%601?displayProperty=nameWithType>
- <xref:System.Object.Equals%2A?displayProperty=nameWithType>
- <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType>
- [<span data-ttu-id="367f1-143">Comparaisons d’égalité</span><span class="sxs-lookup"><span data-stu-id="367f1-143">Equality comparisons</span></span>](../../programming-guide/statements-expressions-operators/equality-comparisons.md)
- [<span data-ttu-id="367f1-144">Opérateurs de comparaison</span><span class="sxs-lookup"><span data-stu-id="367f1-144">Comparison operators</span></span>](comparison-operators.md)
