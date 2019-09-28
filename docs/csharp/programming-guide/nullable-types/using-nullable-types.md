---
title: Utilisation des types valeur Nullable C# -Guide de programmation
ms.custom: seodec18
description: En savoir plus sur l' C# utilisation des types valeur Nullable
ms.date: 09/26/2019
helpviewer_keywords:
- nullable types [C#], about nullable types
ms.assetid: 0bacbe72-ce15-4b14-83e1-9c14e6380c28
ms.openlocfilehash: 65fc3b0ca94f9a41c9375e96000449b52cb7db26
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71396163"
---
# <a name="using-nullable-value-types-c-programming-guide"></a><span data-ttu-id="82514-103">Utilisation des types valeur NullableC# (Guide de programmation)</span><span class="sxs-lookup"><span data-stu-id="82514-103">Using nullable value types (C# Programming Guide)</span></span>

<span data-ttu-id="82514-104">Les types valeur Nullable sont des types qui représentent toutes les valeurs d’un type valeur sous-jacent `T`, et une valeur [null](../../language-reference/keywords/null.md) supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="82514-104">Nullable value types are types that represent all the values of an underlying value type `T`, and an additional [null](../../language-reference/keywords/null.md) value.</span></span> <span data-ttu-id="82514-105">Pour plus d’informations, consultez la rubrique [types valeur Nullable](index.md) .</span><span class="sxs-lookup"><span data-stu-id="82514-105">For more information, see the [Nullable value types](index.md) topic.</span></span>

> [!NOTE]
> <span data-ttu-id="82514-106">C#8,0 introduit la fonctionnalité de types référence Nullable.</span><span class="sxs-lookup"><span data-stu-id="82514-106">C# 8.0 introduces the nullable reference types feature.</span></span> <span data-ttu-id="82514-107">Pour plus d’informations, consultez [types de référence Nullable](../../nullable-references.md).</span><span class="sxs-lookup"><span data-stu-id="82514-107">For more information, see [Nullable reference types](../../nullable-references.md).</span></span> <span data-ttu-id="82514-108">Les types valeur Nullable sont disponibles à partir C# de 2.</span><span class="sxs-lookup"><span data-stu-id="82514-108">The nullable value types are available starting with C# 2.</span></span>

<span data-ttu-id="82514-109">Vous pouvez faire référence à un type valeur Nullable dans l’un des formulaires interchangeables suivants : `Nullable<T>` ou `T?`.</span><span class="sxs-lookup"><span data-stu-id="82514-109">You can refer to a nullable value type in any of the following interchangeable forms: `Nullable<T>` or `T?`.</span></span> <span data-ttu-id="82514-110">`T` doit être un type valeur.</span><span class="sxs-lookup"><span data-stu-id="82514-110">`T` must be a value type.</span></span>

## <a name="declaration-and-assignment"></a><span data-ttu-id="82514-111">Déclaration et affectation</span><span class="sxs-lookup"><span data-stu-id="82514-111">Declaration and assignment</span></span>

<span data-ttu-id="82514-112">Comme un type valeur peut être implicitement converti en type valeur Nullable correspondant, vous assignez une valeur à un type Nullable comme vous le feriez pour son type valeur sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="82514-112">As a value type can be implicitly converted to the corresponding nullable value type, you assign a value to a nullable type as you would for its underlying value type.</span></span> <span data-ttu-id="82514-113">Vous pouvez également affecter la valeur `null`.</span><span class="sxs-lookup"><span data-stu-id="82514-113">You also can assign the `null` value.</span></span> <span data-ttu-id="82514-114">Exemple :</span><span class="sxs-lookup"><span data-stu-id="82514-114">For example:</span></span>

[!code-csharp[declare and assign](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#1)]

## <a name="examination-of-a-nullable-type-value"></a><span data-ttu-id="82514-115">Examen d’une valeur de type Nullable</span><span class="sxs-lookup"><span data-stu-id="82514-115">Examination of a nullable type value</span></span>

<span data-ttu-id="82514-116">Utilisez les propriétés ReadOnly suivantes pour examiner une instance d’un type valeur Nullable pour null et pour récupérer une valeur d’un type sous-jacent :</span><span class="sxs-lookup"><span data-stu-id="82514-116">Use the following readonly properties to examine an instance of a nullable value type for null and retrieve a value of an underlying type:</span></span>

- <span data-ttu-id="82514-117"><xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> indique si une instance d’un type Nullable a une valeur de son type sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="82514-117"><xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> indicates whether an instance of a nullable type has a value of its underlying type.</span></span>

- <span data-ttu-id="82514-118"><xref:System.Nullable%601.Value%2A?displayProperty=nameWithType> obtient la valeur d’un type sous-jacent si <xref:System.Nullable%601.HasValue%2A> est `true`.</span><span class="sxs-lookup"><span data-stu-id="82514-118"><xref:System.Nullable%601.Value%2A?displayProperty=nameWithType> gets the value of an underlying type if <xref:System.Nullable%601.HasValue%2A> is `true`.</span></span> <span data-ttu-id="82514-119">Si <xref:System.Nullable%601.HasValue%2A> est `false`, la propriété <xref:System.Nullable%601.Value%2A> lève une <xref:System.InvalidOperationException>.</span><span class="sxs-lookup"><span data-stu-id="82514-119">If <xref:System.Nullable%601.HasValue%2A> is `false`, the <xref:System.Nullable%601.Value%2A> property throws an <xref:System.InvalidOperationException>.</span></span>

<span data-ttu-id="82514-120">Le code dans l’exemple suivant utilise la propriété `HasValue` pour tester si la variable contient une valeur avant de l’afficher :</span><span class="sxs-lookup"><span data-stu-id="82514-120">The code in the following example uses the `HasValue` property to test whether the variable contains a value before displaying it:</span></span>

[!code-csharp-interactive[use HasValue](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#2)]

<span data-ttu-id="82514-121">Vous pouvez également comparer une variable d’un type valeur Nullable avec `null` au lieu d’utiliser la propriété `HasValue`, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="82514-121">You also can compare a variable of a nullable value type with `null` instead of using the `HasValue` property, as the following example shows:</span></span>

[!code-csharp-interactive[use comparison with null](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#3)]

<span data-ttu-id="82514-122">À partir C# de 7,0, vous pouvez utiliser les [critères spéciaux](../../pattern-matching.md) pour examiner et obtenir une valeur d’un type valeur Nullable :</span><span class="sxs-lookup"><span data-stu-id="82514-122">Beginning with C# 7.0, you can use [pattern matching](../../pattern-matching.md) to both examine and get a value of a nullable value type:</span></span>

[!code-csharp-interactive[use pattern matching](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#4)]

## <a name="conversion-from-a-nullable-value-type-to-an-underlying-type"></a><span data-ttu-id="82514-123">Conversion d’un type valeur Nullable en un type sous-jacent</span><span class="sxs-lookup"><span data-stu-id="82514-123">Conversion from a nullable value type to an underlying type</span></span>

<span data-ttu-id="82514-124">Si vous devez assigner une valeur d’un type valeur Nullable à un type non Nullable, utilisez l' [opérateur de fusion null `??`](../../language-reference/operators/null-coalescing-operator.md) pour spécifier la valeur à assigner si une valeur d’un type valeur Nullable est null (vous pouvez également utiliser la méthode <xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType>) :</span><span class="sxs-lookup"><span data-stu-id="82514-124">If you need to assign a value of a nullable value type to a non-nullable type, use the [null-coalescing operator `??`](../../language-reference/operators/null-coalescing-operator.md) to specify the value to be assigned if a value of a nullable value type is null (you also can use the <xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType> method to do that):</span></span>

[!code-csharp-interactive[?? operator](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#5)]

<span data-ttu-id="82514-125">Utilisez la méthode <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> si la valeur à utiliser lorsqu’une valeur d’un type valeur Nullable est `null` doit être la valeur par défaut du type valeur sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="82514-125">Use the <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> method if the value to be used when a value of a nullable value type is `null` should be the default value of the underlying value type.</span></span>

<span data-ttu-id="82514-126">Vous pouvez effectuer un cast explicite d’un type valeur Nullable en un type non Nullable.</span><span class="sxs-lookup"><span data-stu-id="82514-126">You can explicitly cast a nullable value type to a non-nullable type.</span></span> <span data-ttu-id="82514-127">Exemple :</span><span class="sxs-lookup"><span data-stu-id="82514-127">For example:</span></span>

[!code-csharp[explicit cast](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#6)]

<span data-ttu-id="82514-128">Au moment de l’exécution, si la valeur d’un type valeur Nullable est `null`, le cast explicite lève une <xref:System.InvalidOperationException>.</span><span class="sxs-lookup"><span data-stu-id="82514-128">At run time, if the value of a nullable value type is `null`, the explicit cast throws an <xref:System.InvalidOperationException>.</span></span>

<span data-ttu-id="82514-129">Un type valeur non Nullable est implicitement converti en type Nullable correspondant.</span><span class="sxs-lookup"><span data-stu-id="82514-129">A non-nullable value type is implicitly converted to the corresponding nullable type.</span></span>

## <a name="operators"></a><span data-ttu-id="82514-130">Opérateurs</span><span class="sxs-lookup"><span data-stu-id="82514-130">Operators</span></span>

<span data-ttu-id="82514-131">Les opérateurs unaires et binaires prédéfinis et tous les opérateurs définis par l’utilisateur qui existent pour les types valeur peuvent également être utilisés par les types Nullable correspondants.</span><span class="sxs-lookup"><span data-stu-id="82514-131">The predefined unary and binary operators and any user-defined operators that exist for value types may also be used by corresponding nullable types.</span></span> <span data-ttu-id="82514-132">Ces opérateurs produisent `null` si un ou les deux opérandes sont `null` ; dans le cas contraire, l’opérateur utilise les valeurs contenues pour calculer le résultat.</span><span class="sxs-lookup"><span data-stu-id="82514-132">These operators produce `null` if one or both operands are `null`; otherwise, the operator uses the contained values to calculate the result.</span></span> <span data-ttu-id="82514-133">Exemple :</span><span class="sxs-lookup"><span data-stu-id="82514-133">For example:</span></span>

[!code-csharp[operators](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#7)]

> [!NOTE]
> <span data-ttu-id="82514-134">Pour le type `bool?`, les opérateurs prédéfinis `&` et `|` ne suivent pas les règles décrites dans cette section : le résultat d’une évaluation d’opérateur peut être non null, même si l’un des opérandes est `null`.</span><span class="sxs-lookup"><span data-stu-id="82514-134">For the `bool?` type, the predefined `&` and `|` operators don't follow the rules described in this section: the result of an operator evaluation can be non-null even if one of the operands is `null`.</span></span> <span data-ttu-id="82514-135">Pour plus d’informations, voir la section [Opérateurs logiques booléens Nullable](../../language-reference/operators/boolean-logical-operators.md#nullable-boolean-logical-operators) de l’article [Opérateurs logiques booléens](../../language-reference/operators/boolean-logical-operators.md).</span><span class="sxs-lookup"><span data-stu-id="82514-135">For more information, see the [Nullable Boolean logical operators](../../language-reference/operators/boolean-logical-operators.md#nullable-boolean-logical-operators) section of the [Boolean logical operators](../../language-reference/operators/boolean-logical-operators.md) article.</span></span>
  
<span data-ttu-id="82514-136">Pour les opérateurs relationnels (`<`, `>`, `<=`, `>=`), si l’un des opérandes ou les deux sont `null`, le résultat est `false`.</span><span class="sxs-lookup"><span data-stu-id="82514-136">For the relational operators (`<`, `>`, `<=`, `>=`), if one or both operands are `null`, the result is `false`.</span></span> <span data-ttu-id="82514-137">Ne partez pas du principe que parce qu’une comparaison spécifique (par exemple `<=`) retourne `false`, la comparaison opposée (`>`) retourne `true`.</span><span class="sxs-lookup"><span data-stu-id="82514-137">Do not assume that because a particular comparison (for example, `<=`) returns `false`, the opposite comparison (`>`) returns `true`.</span></span> <span data-ttu-id="82514-138">L’exemple suivant montre que 10 n’est</span><span class="sxs-lookup"><span data-stu-id="82514-138">The following example shows that 10 is</span></span>

- <span data-ttu-id="82514-139">ni supérieur ou égal à `null`,</span><span class="sxs-lookup"><span data-stu-id="82514-139">neither greater than or equal to `null`,</span></span>
- <span data-ttu-id="82514-140">ni inférieur à `null`.</span><span class="sxs-lookup"><span data-stu-id="82514-140">nor less than `null`.</span></span>

[!code-csharp-interactive[relational and equality operators](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#8)]

<span data-ttu-id="82514-141">L’exemple ci-dessus montre également qu’une comparaison d’égalité de deux types valeur Nullable à la fois null correspond à `true`.</span><span class="sxs-lookup"><span data-stu-id="82514-141">The above example also shows that an equality comparison of two nullable value types that are both null evaluates to `true`.</span></span>

<span data-ttu-id="82514-142">Pour plus d’informations, voir la section [Opérateurs lifted](~/_csharplang/spec/expressions.md#lifted-operators) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="82514-142">For more information, see the [Lifted operators](~/_csharplang/spec/expressions.md#lifted-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="boxing-and-unboxing"></a><span data-ttu-id="82514-143">Boxing et unboxing</span><span class="sxs-lookup"><span data-stu-id="82514-143">Boxing and unboxing</span></span>

<span data-ttu-id="82514-144">Un type valeur Nullable est [boxed](../types/boxing-and-unboxing.md) d’après les règles suivantes :</span><span class="sxs-lookup"><span data-stu-id="82514-144">A nullable value type is [boxed](../types/boxing-and-unboxing.md) by the following rules:</span></span>

- <span data-ttu-id="82514-145">Si <xref:System.Nullable%601.HasValue%2A> retourne `false`, la référence null est générée.</span><span class="sxs-lookup"><span data-stu-id="82514-145">If <xref:System.Nullable%601.HasValue%2A> returns `false`, the null reference is produced.</span></span>
- <span data-ttu-id="82514-146">Si <xref:System.Nullable%601.HasValue%2A> retourne `true`, une valeur du type valeur sous-jacent `T` est boxed, pas l’instance de <xref:System.Nullable%601>.</span><span class="sxs-lookup"><span data-stu-id="82514-146">If <xref:System.Nullable%601.HasValue%2A> returns `true`, a value of the underlying value type `T` is boxed, not the instance of <xref:System.Nullable%601>.</span></span>

<span data-ttu-id="82514-147">Vous pouvez effectuer l’unboxing du type valeur boxed vers le type Nullable correspondant, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="82514-147">You can unbox the boxed value type to the corresponding nullable type, as the following example shows:</span></span>

[!code-csharp-interactive[boxing and unboxing](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#9)]

## <a name="see-also"></a><span data-ttu-id="82514-148">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="82514-148">See also</span></span>

- [<span data-ttu-id="82514-149">Types valeur Nullable</span><span class="sxs-lookup"><span data-stu-id="82514-149">Nullable value types</span></span>](index.md)
- [<span data-ttu-id="82514-150">Que signifie réellement « Lifted » ?</span><span class="sxs-lookup"><span data-stu-id="82514-150">What exactly does 'lifted' mean?</span></span>](https://blogs.msdn.microsoft.com/ericlippert/2007/06/27/what-exactly-does-lifted-mean/)
