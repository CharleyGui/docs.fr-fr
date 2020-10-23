---
title: Types valeur Nullable-référence C#
description: En savoir plus sur les types valeur Nullable C# et leur utilisation
ms.date: 11/04/2019
helpviewer_keywords:
- nullable value types [C#]
ms.openlocfilehash: 3ab2dff6b7399b0458a69d4498b2ebda24f6c5cc
ms.sourcegitcommit: 870bc4b4087510f6fba3c7b1c0d391f02bcc1f3e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2020
ms.locfileid: "92471833"
---
# <a name="nullable-value-types-c-reference"></a><span data-ttu-id="e3b3a-103">Types valeur Nullable (référence C#)</span><span class="sxs-lookup"><span data-stu-id="e3b3a-103">Nullable value types (C# reference)</span></span>

<span data-ttu-id="e3b3a-104">Un *type valeur Nullable* `T?` représente toutes les valeurs de son [type valeur](value-types.md) sous-jacent `T` et une valeur [null](../keywords/null.md) supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="e3b3a-104">A *nullable value type* `T?` represents all values of its underlying [value type](value-types.md) `T` and an additional [null](../keywords/null.md) value.</span></span> <span data-ttu-id="e3b3a-105">Par exemple, vous pouvez assigner l’une des trois valeurs suivantes à une `bool?` variable : `true` , `false` ou `null` .</span><span class="sxs-lookup"><span data-stu-id="e3b3a-105">For example, you can assign any of the following three values to a `bool?` variable: `true`, `false`, or `null`.</span></span> <span data-ttu-id="e3b3a-106">Un type valeur sous-jacent `T` ne peut pas être un type valeur Nullable lui-même.</span><span class="sxs-lookup"><span data-stu-id="e3b3a-106">An underlying value type `T` cannot be a nullable value type itself.</span></span>

> [!NOTE]
> <span data-ttu-id="e3b3a-107">C# 8,0 introduit la fonctionnalité de types référence Nullable.</span><span class="sxs-lookup"><span data-stu-id="e3b3a-107">C# 8.0 introduces the nullable reference types feature.</span></span> <span data-ttu-id="e3b3a-108">Pour plus d’informations, consultez [types de référence Nullable](nullable-reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="e3b3a-108">For more information, see [Nullable reference types](nullable-reference-types.md).</span></span> <span data-ttu-id="e3b3a-109">Les types valeur Nullable sont disponibles à partir de C# 2.</span><span class="sxs-lookup"><span data-stu-id="e3b3a-109">The nullable value types are available beginning with C# 2.</span></span>

<span data-ttu-id="e3b3a-110">Tout type valeur Nullable est une instance de la <xref:System.Nullable%601?displayProperty=nameWithType> structure générique.</span><span class="sxs-lookup"><span data-stu-id="e3b3a-110">Any nullable value type is an instance of the generic <xref:System.Nullable%601?displayProperty=nameWithType> structure.</span></span> <span data-ttu-id="e3b3a-111">Vous pouvez faire référence à un type valeur Nullable avec un type sous-jacent `T` dans l’un des formulaires interchangeables suivants : `Nullable<T>` ou `T?` .</span><span class="sxs-lookup"><span data-stu-id="e3b3a-111">You can refer to a nullable value type with an underlying type `T` in any of the following interchangeable forms: `Nullable<T>` or `T?`.</span></span>

<span data-ttu-id="e3b3a-112">En général, vous utilisez un type valeur Nullable lorsque vous devez représenter la valeur indéfinie d’un type valeur sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="e3b3a-112">You typically use a nullable value type when you need to represent the undefined value of an underlying value type.</span></span> <span data-ttu-id="e3b3a-113">Par exemple, une variable booléenne, ou `bool` , ne peut être que `true` ou `false` .</span><span class="sxs-lookup"><span data-stu-id="e3b3a-113">For example, a Boolean, or `bool`, variable can only be either `true` or `false`.</span></span> <span data-ttu-id="e3b3a-114">Toutefois, dans certaines applications, une valeur de variable peut être indéfinie ou manquante.</span><span class="sxs-lookup"><span data-stu-id="e3b3a-114">However, in some applications a variable value can be undefined or missing.</span></span> <span data-ttu-id="e3b3a-115">Par exemple, un champ de base de données peut contenir `true` ou `false` , ou il ne peut contenir aucune valeur, autrement dit, `NULL` .</span><span class="sxs-lookup"><span data-stu-id="e3b3a-115">For example, a database field may contain `true` or `false`, or it may contain no value at all, that is, `NULL`.</span></span> <span data-ttu-id="e3b3a-116">Vous pouvez utiliser le `bool?` type dans ce scénario.</span><span class="sxs-lookup"><span data-stu-id="e3b3a-116">You can use the `bool?` type in that scenario.</span></span>

## <a name="declaration-and-assignment"></a><span data-ttu-id="e3b3a-117">Déclaration et affectation</span><span class="sxs-lookup"><span data-stu-id="e3b3a-117">Declaration and assignment</span></span>

<span data-ttu-id="e3b3a-118">Comme un type valeur est implicitement convertible en type valeur Nullable correspondant, vous pouvez assigner une valeur à une variable d’un type valeur Nullable comme vous le feriez pour son type valeur sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="e3b3a-118">As a value type is implicitly convertible to the corresponding nullable value type, you can assign a value to a variable of a nullable value type as you would do that for its underlying value type.</span></span> <span data-ttu-id="e3b3a-119">Vous pouvez également affecter la `null` valeur.</span><span class="sxs-lookup"><span data-stu-id="e3b3a-119">You can also assign the `null` value.</span></span> <span data-ttu-id="e3b3a-120">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="e3b3a-120">For example:</span></span>

[!code-csharp[declare and assign](snippets/shared/NullableValueTypes.cs#Declaration)]

<span data-ttu-id="e3b3a-121">La valeur par défaut d’un type valeur Nullable représente `null` , autrement dit, une instance dont la <xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> propriété retourne `false` .</span><span class="sxs-lookup"><span data-stu-id="e3b3a-121">The default value of a nullable value type represents `null`, that is, it's an instance whose <xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> property returns `false`.</span></span>

## <a name="examination-of-an-instance-of-a-nullable-value-type"></a><span data-ttu-id="e3b3a-122">Examen d’une instance d’un type valeur Nullable</span><span class="sxs-lookup"><span data-stu-id="e3b3a-122">Examination of an instance of a nullable value type</span></span>

<span data-ttu-id="e3b3a-123">À compter de C# 7,0, vous pouvez utiliser l' [ `is` opérateur avec un modèle de type](../operators/type-testing-and-cast.md#type-testing-with-pattern-matching) pour examiner à la fois une instance d’un type de valeur Nullable pour `null` et récupérer une valeur d’un type sous-jacent :</span><span class="sxs-lookup"><span data-stu-id="e3b3a-123">Beginning with C# 7.0, you can use the [`is` operator with a type pattern](../operators/type-testing-and-cast.md#type-testing-with-pattern-matching) to both examine an instance of a nullable value type for `null` and retrieve a value of an underlying type:</span></span>

[!code-csharp-interactive[use pattern matching](snippets/shared/NullableValueTypes.cs#PatternMatching)]

<span data-ttu-id="e3b3a-124">Vous pouvez toujours utiliser les propriétés en lecture seule suivantes pour examiner et obtenir la valeur d’une variable de type valeur Nullable :</span><span class="sxs-lookup"><span data-stu-id="e3b3a-124">You always can use the following read-only properties to examine and get a value of a nullable value type variable:</span></span>

- <span data-ttu-id="e3b3a-125"><xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> indique si une instance d’un type valeur Nullable a une valeur de son type sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="e3b3a-125"><xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> indicates whether an instance of a nullable value type has a value of its underlying type.</span></span>

- <span data-ttu-id="e3b3a-126"><xref:System.Nullable%601.Value%2A?displayProperty=nameWithType> obtient la valeur d’un type sous-jacent si <xref:System.Nullable%601.HasValue%2A> est `true`.</span><span class="sxs-lookup"><span data-stu-id="e3b3a-126"><xref:System.Nullable%601.Value%2A?displayProperty=nameWithType> gets the value of an underlying type if <xref:System.Nullable%601.HasValue%2A> is `true`.</span></span> <span data-ttu-id="e3b3a-127">Si <xref:System.Nullable%601.HasValue%2A> est `false`, la propriété <xref:System.Nullable%601.Value%2A> lève une <xref:System.InvalidOperationException>.</span><span class="sxs-lookup"><span data-stu-id="e3b3a-127">If <xref:System.Nullable%601.HasValue%2A> is `false`, the <xref:System.Nullable%601.Value%2A> property throws an <xref:System.InvalidOperationException>.</span></span>

<span data-ttu-id="e3b3a-128">L’exemple suivant utilise la `HasValue` propriété pour déterminer si la variable contient une valeur avant de l’afficher :</span><span class="sxs-lookup"><span data-stu-id="e3b3a-128">The following example uses the `HasValue` property to test whether the variable contains a value before displaying it:</span></span>

[!code-csharp-interactive[use HasValue](snippets/shared/NullableValueTypes.cs#HasValue)]

<span data-ttu-id="e3b3a-129">Vous pouvez également comparer une variable d’un type valeur Nullable avec `null` au lieu d’utiliser la `HasValue` propriété, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="e3b3a-129">You can also compare a variable of a nullable value type with `null` instead of using the `HasValue` property, as the following example shows:</span></span>

[!code-csharp-interactive[use comparison with null](snippets/shared/NullableValueTypes.cs#CompareWithNull)]

## <a name="conversion-from-a-nullable-value-type-to-an-underlying-type"></a><span data-ttu-id="e3b3a-130">Conversion d’un type valeur Nullable en un type sous-jacent</span><span class="sxs-lookup"><span data-stu-id="e3b3a-130">Conversion from a nullable value type to an underlying type</span></span>

<span data-ttu-id="e3b3a-131">Si vous souhaitez assigner une valeur d’un type valeur Nullable à une variable de type valeur n’acceptant pas les valeurs NULL, vous devrez peut-être spécifier la valeur à assigner à la place de `null` .</span><span class="sxs-lookup"><span data-stu-id="e3b3a-131">If you want to assign a value of a nullable value type to a non-nullable value type variable, you might need to specify the value to be assigned in place of `null`.</span></span> <span data-ttu-id="e3b3a-132">Utilisez l' [opérateur `??` de fusion Null](../operators/null-coalescing-operator.md) pour effectuer cette opération (vous pouvez également utiliser la <xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType> méthode dans le même but) :</span><span class="sxs-lookup"><span data-stu-id="e3b3a-132">Use the [null-coalescing operator `??`](../operators/null-coalescing-operator.md) to do that (you can also use the <xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType> method for the same purpose):</span></span>

[!code-csharp-interactive[?? operator](snippets/shared/NullableValueTypes.cs#NullCoalescing)]

<span data-ttu-id="e3b3a-133">Si vous souhaitez utiliser la valeur [par défaut](default-values.md) du type valeur sous-jacent à la place de `null` , utilisez la <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> méthode.</span><span class="sxs-lookup"><span data-stu-id="e3b3a-133">If you want to use the [default](default-values.md) value of the underlying value type in place of `null`, use the <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="e3b3a-134">Vous pouvez également effectuer un cast explicite d’un type valeur Nullable vers un type non Nullable, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="e3b3a-134">You can also explicitly cast a nullable value type to a non-nullable type, as the following example shows:</span></span>

[!code-csharp[explicit cast](snippets/shared/NullableValueTypes.cs#Cast)]

<span data-ttu-id="e3b3a-135">Au moment de l’exécution, si la valeur d’un type valeur Nullable est `null` , le cast explicite lève une <xref:System.InvalidOperationException> .</span><span class="sxs-lookup"><span data-stu-id="e3b3a-135">At run time, if the value of a nullable value type is `null`, the explicit cast throws an <xref:System.InvalidOperationException>.</span></span>

<span data-ttu-id="e3b3a-136">Un type valeur n’acceptant pas les valeurs null `T` est implicitement convertible en type valeur Nullable correspondant `T?` .</span><span class="sxs-lookup"><span data-stu-id="e3b3a-136">A non-nullable value type `T` is implicitly convertible to the corresponding nullable value type `T?`.</span></span>

## <a name="lifted-operators"></a><span data-ttu-id="e3b3a-137">Opérateurs levés</span><span class="sxs-lookup"><span data-stu-id="e3b3a-137">Lifted operators</span></span>

<span data-ttu-id="e3b3a-138">Les [opérateurs](../operators/index.md) unaires et binaires prédéfinis ou tous les opérateurs surchargés pris en charge par un type valeur `T` sont également pris en charge par le type valeur Nullable correspondant `T?` .</span><span class="sxs-lookup"><span data-stu-id="e3b3a-138">The predefined unary and binary [operators](../operators/index.md) or any overloaded operators that are supported by a value type `T` are also supported by the corresponding nullable value type `T?`.</span></span> <span data-ttu-id="e3b3a-139">Ces opérateurs, également appelés *opérateurs levés*, produisent `null` si l’un des opérandes ou les deux sont `null` ; sinon, l’opérateur utilise les valeurs contenues de ses opérandes pour calculer le résultat.</span><span class="sxs-lookup"><span data-stu-id="e3b3a-139">These operators, also known as *lifted operators*, produce `null` if one or both operands are `null`; otherwise, the operator uses the contained values of its operands to calculate the result.</span></span> <span data-ttu-id="e3b3a-140">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="e3b3a-140">For example:</span></span>

[!code-csharp[lifted operators](snippets/shared/NullableValueTypes.cs#LiftedOperator)]

> [!NOTE]
> <span data-ttu-id="e3b3a-141">Pour le `bool?` type, les opérateurs prédéfinis `&` et `|` ne suivent pas les règles décrites dans cette section : le résultat d’une évaluation d’opérateur peut être non null, même si l’un des opérandes est `null` .</span><span class="sxs-lookup"><span data-stu-id="e3b3a-141">For the `bool?` type, the predefined `&` and `|` operators don't follow the rules described in this section: the result of an operator evaluation can be non-null even if one of the operands is `null`.</span></span> <span data-ttu-id="e3b3a-142">Pour plus d’informations, voir la section [Opérateurs logiques booléens Nullable](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) de l’article [Opérateurs logiques booléens](../operators/boolean-logical-operators.md).</span><span class="sxs-lookup"><span data-stu-id="e3b3a-142">For more information, see the [Nullable Boolean logical operators](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) section of the [Boolean logical operators](../operators/boolean-logical-operators.md) article.</span></span>

<span data-ttu-id="e3b3a-143">Pour les [opérateurs de comparaison](../operators/comparison-operators.md) `<` , `>` , `<=` et `>=` , si l’un des opérandes ou les deux sont `null` , le résultat est `false` ; sinon, les valeurs contenues des opérandes sont comparées.</span><span class="sxs-lookup"><span data-stu-id="e3b3a-143">For the [comparison operators](../operators/comparison-operators.md) `<`, `>`, `<=`, and `>=`, if one or both operands are `null`, the result is `false`; otherwise, the contained values of operands are compared.</span></span> <span data-ttu-id="e3b3a-144">Ne partez pas du principe que parce qu’une comparaison spécifique (par exemple `<=`) retourne `false`, la comparaison opposée (`>`) retourne `true`.</span><span class="sxs-lookup"><span data-stu-id="e3b3a-144">Do not assume that because a particular comparison (for example, `<=`) returns `false`, the opposite comparison (`>`) returns `true`.</span></span> <span data-ttu-id="e3b3a-145">L’exemple suivant montre que 10 n’est</span><span class="sxs-lookup"><span data-stu-id="e3b3a-145">The following example shows that 10 is</span></span>

- <span data-ttu-id="e3b3a-146">ni supérieur ou égal à `null`</span><span class="sxs-lookup"><span data-stu-id="e3b3a-146">neither greater than or equal to `null`</span></span>
- <span data-ttu-id="e3b3a-147">ni inférieur à `null`</span><span class="sxs-lookup"><span data-stu-id="e3b3a-147">nor less than `null`</span></span>

[!code-csharp-interactive[relational and equality operators](snippets/shared/NullableValueTypes.cs#ComparisonOperators)]

<span data-ttu-id="e3b3a-148">Pour l' [opérateur d’égalité](../operators/equality-operators.md#equality-operator-) `==` , si les deux opérandes sont `null` , le résultat est `true` , si un seul des opérandes est `null` , le résultat est `false` ; sinon, les valeurs contenues des opérandes sont comparées.</span><span class="sxs-lookup"><span data-stu-id="e3b3a-148">For the [equality operator](../operators/equality-operators.md#equality-operator-) `==`, if both operands are `null`, the result is `true`, if only one of the operands is `null`, the result is `false`; otherwise, the contained values of operands are compared.</span></span>

<span data-ttu-id="e3b3a-149">Pour l' [opérateur d’inégalité](../operators/equality-operators.md#inequality-operator-) `!=` , si les deux opérandes sont `null` , le résultat est `false` , si un seul des opérandes est `null` , le résultat est `true` ; sinon, les valeurs contenues des opérandes sont comparées.</span><span class="sxs-lookup"><span data-stu-id="e3b3a-149">For the [inequality operator](../operators/equality-operators.md#inequality-operator-) `!=`, if both operands are `null`, the result is `false`, if only one of the operands is `null`, the result is `true`; otherwise, the contained values of operands are compared.</span></span>

<span data-ttu-id="e3b3a-150">S’il existe une [conversion définie par l’utilisateur](../operators/user-defined-conversion-operators.md) entre deux types valeur, la même conversion peut également être utilisée entre les types valeur Nullable correspondants.</span><span class="sxs-lookup"><span data-stu-id="e3b3a-150">If there exists a [user-defined conversion](../operators/user-defined-conversion-operators.md) between two value types, the same conversion can also be used between the corresponding nullable value types.</span></span>

## <a name="boxing-and-unboxing"></a><span data-ttu-id="e3b3a-151">Boxing et unboxing</span><span class="sxs-lookup"><span data-stu-id="e3b3a-151">Boxing and unboxing</span></span>

<span data-ttu-id="e3b3a-152">Une instance d’un type valeur Nullable `T?` est [convertie](../../programming-guide/types/boxing-and-unboxing.md) comme suit :</span><span class="sxs-lookup"><span data-stu-id="e3b3a-152">An instance of a nullable value type `T?` is [boxed](../../programming-guide/types/boxing-and-unboxing.md) as follows:</span></span>

- <span data-ttu-id="e3b3a-153">Si <xref:System.Nullable%601.HasValue%2A> retourne `false`, la référence null est générée.</span><span class="sxs-lookup"><span data-stu-id="e3b3a-153">If <xref:System.Nullable%601.HasValue%2A> returns `false`, the null reference is produced.</span></span>
- <span data-ttu-id="e3b3a-154">Si <xref:System.Nullable%601.HasValue%2A> retourne `true` , la valeur correspondante du type valeur sous-jacent `T` est boxed, et non l’instance de <xref:System.Nullable%601> .</span><span class="sxs-lookup"><span data-stu-id="e3b3a-154">If <xref:System.Nullable%601.HasValue%2A> returns `true`, the corresponding value of the underlying value type `T` is boxed, not the instance of <xref:System.Nullable%601>.</span></span>

<span data-ttu-id="e3b3a-155">Vous pouvez convertir une valeur boxed d’un type valeur `T` en type valeur Nullable correspondant `T?` , comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="e3b3a-155">You can unbox a boxed value of a value type `T` to the corresponding nullable value type `T?`, as the following example shows:</span></span>

[!code-csharp-interactive[boxing and unboxing](snippets/shared/NullableValueTypes.cs#Boxing)]

## <a name="how-to-identify-a-nullable-value-type"></a><span data-ttu-id="e3b3a-156">Comment identifier un type valeur Nullable</span><span class="sxs-lookup"><span data-stu-id="e3b3a-156">How to identify a nullable value type</span></span>

<span data-ttu-id="e3b3a-157">L’exemple suivant montre comment déterminer si une <xref:System.Type?displayProperty=nameWithType> instance représente un type valeur Nullable construit, autrement dit, le <xref:System.Nullable%601?displayProperty=nameWithType> type avec un paramètre de type spécifié `T` :</span><span class="sxs-lookup"><span data-stu-id="e3b3a-157">The following example shows how to determine whether a <xref:System.Type?displayProperty=nameWithType> instance represents a constructed nullable value type, that is, the <xref:System.Nullable%601?displayProperty=nameWithType> type with a specified type parameter `T`:</span></span>

[!code-csharp-interactive[whether Type is nullable](snippets/shared/NullableValueTypes.cs#IsTypeNullable)]

<span data-ttu-id="e3b3a-158">Comme le montre l’exemple, vous utilisez l’opérateur [typeof](../operators/type-testing-and-cast.md#typeof-operator) pour créer une <xref:System.Type?displayProperty=nameWithType> instance.</span><span class="sxs-lookup"><span data-stu-id="e3b3a-158">As the example shows, you use the [typeof](../operators/type-testing-and-cast.md#typeof-operator) operator to create a <xref:System.Type?displayProperty=nameWithType> instance.</span></span>

<span data-ttu-id="e3b3a-159">Si vous souhaitez déterminer si une instance est d’un type valeur Nullable, n’utilisez pas la <xref:System.Object.GetType%2A?displayProperty=nameWithType> méthode pour obtenir une <xref:System.Type> instance à tester avec le code précédent.</span><span class="sxs-lookup"><span data-stu-id="e3b3a-159">If you want to determine whether an instance is of a nullable value type, don't use the <xref:System.Object.GetType%2A?displayProperty=nameWithType> method to get a <xref:System.Type> instance to be tested with the preceding code.</span></span> <span data-ttu-id="e3b3a-160">Quand vous appelez la <xref:System.Object.GetType%2A?displayProperty=nameWithType> méthode sur une instance d’un type valeur Nullable, l’instance est [convertie](#boxing-and-unboxing) en <xref:System.Object> .</span><span class="sxs-lookup"><span data-stu-id="e3b3a-160">When you call the <xref:System.Object.GetType%2A?displayProperty=nameWithType> method on an instance of a nullable value type, the instance is [boxed](#boxing-and-unboxing) to <xref:System.Object>.</span></span> <span data-ttu-id="e3b3a-161">La conversion boxing d’une instance non null d’un type valeur Nullable équivaut au boxing d’une valeur du type sous-jacent, <xref:System.Object.GetType%2A> retourne une <xref:System.Type> instance qui représente le type sous-jacent d’un type valeur Nullable :</span><span class="sxs-lookup"><span data-stu-id="e3b3a-161">As boxing of a non-null instance of a nullable value type is equivalent to boxing of a value of the underlying type, <xref:System.Object.GetType%2A> returns a <xref:System.Type> instance that represents the underlying type of a nullable value type:</span></span>

[!code-csharp-interactive[GetType example](snippets/shared/NullableValueTypes.cs#GetType)]

<span data-ttu-id="e3b3a-162">En outre, n’utilisez pas l’opérateur [is](../operators/type-testing-and-cast.md#is-operator) pour déterminer si une instance est d’un type valeur Nullable.</span><span class="sxs-lookup"><span data-stu-id="e3b3a-162">Also, don't use the [is](../operators/type-testing-and-cast.md#is-operator) operator to determine whether an instance is of a nullable value type.</span></span> <span data-ttu-id="e3b3a-163">Comme le montre l’exemple suivant, vous ne pouvez pas distinguer les types d’une instance de type valeur Nullable et son instance de type sous-jacent avec l' `is` opérateur :</span><span class="sxs-lookup"><span data-stu-id="e3b3a-163">As the following example shows, you cannot distinguish types of a nullable value type instance and its underlying type instance with the `is` operator:</span></span>

[!code-csharp-interactive[is operator example](snippets/shared/NullableValueTypes.cs#IsOperator)]

<span data-ttu-id="e3b3a-164">Vous pouvez utiliser le code présenté dans l’exemple suivant pour déterminer si une instance est d’un type valeur Nullable :</span><span class="sxs-lookup"><span data-stu-id="e3b3a-164">You can use the code presented in the following example to determine whether an instance is of a nullable value type:</span></span>

[!code-csharp-interactive[whether an instance is of a nullable type](snippets/shared/NullableValueTypes.cs#IsInstanceNullable)]

> [!NOTE]
> <span data-ttu-id="e3b3a-165">Les méthodes décrites dans cette section ne sont pas applicables dans le cas des [types référence Nullable](nullable-reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="e3b3a-165">The methods described in this section are not applicable in the case of [nullable reference types](nullable-reference-types.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="e3b3a-166">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="e3b3a-166">C# language specification</span></span>

<span data-ttu-id="e3b3a-167">Pour plus d’informations, consultez les sections suivantes de la [spécification du langage C#](~/_csharplang/spec/introduction.md) :</span><span class="sxs-lookup"><span data-stu-id="e3b3a-167">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="e3b3a-168">Types Nullable</span><span class="sxs-lookup"><span data-stu-id="e3b3a-168">Nullable types</span></span>](~/_csharplang/spec/types.md#nullable-types)
- [<span data-ttu-id="e3b3a-169">Opérateurs levés</span><span class="sxs-lookup"><span data-stu-id="e3b3a-169">Lifted operators</span></span>](~/_csharplang/spec/expressions.md#lifted-operators)
- [<span data-ttu-id="e3b3a-170">Conversions Nullable implicites</span><span class="sxs-lookup"><span data-stu-id="e3b3a-170">Implicit nullable conversions</span></span>](~/_csharplang/spec/conversions.md#implicit-nullable-conversions)
- [<span data-ttu-id="e3b3a-171">Conversions Nullable explicites</span><span class="sxs-lookup"><span data-stu-id="e3b3a-171">Explicit nullable conversions</span></span>](~/_csharplang/spec/conversions.md#explicit-nullable-conversions)
- [<span data-ttu-id="e3b3a-172">Opérateurs de conversion levés</span><span class="sxs-lookup"><span data-stu-id="e3b3a-172">Lifted conversion operators</span></span>](~/_csharplang/spec/conversions.md#lifted-conversion-operators)

## <a name="see-also"></a><span data-ttu-id="e3b3a-173">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e3b3a-173">See also</span></span>

- [<span data-ttu-id="e3b3a-174">Informations de référence sur C#</span><span class="sxs-lookup"><span data-stu-id="e3b3a-174">C# reference</span></span>](../index.md)
- [<span data-ttu-id="e3b3a-175">Que signifie réellement « lifted » ?</span><span class="sxs-lookup"><span data-stu-id="e3b3a-175">What exactly does 'lifted' mean?</span></span>](/archive/blogs/ericlippert/what-exactly-does-lifted-mean)
- <xref:System.Nullable%601?displayProperty=nameWithType>
- <xref:System.Nullable?displayProperty=nameWithType>
- <xref:System.Nullable.GetUnderlyingType%2A?displayProperty=nameWithType>
- [<span data-ttu-id="e3b3a-176">Types références Nullables</span><span class="sxs-lookup"><span data-stu-id="e3b3a-176">Nullable reference types</span></span>](nullable-reference-types.md)
