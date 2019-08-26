---
title: Utilisation de types Nullable - Guide de programmation C#
ms.custom: seodec18
description: Découvrez comment utiliser les types Nullable C#.
ms.date: 08/02/2018
helpviewer_keywords:
- nullable types [C#], about nullable types
ms.assetid: 0bacbe72-ce15-4b14-83e1-9c14e6380c28
ms.openlocfilehash: 75b8889f5f1f1b0dab4aa365daa34ef5ae226b02
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69588836"
---
# <a name="using-nullable-types-c-programming-guide"></a><span data-ttu-id="5925a-103">Utilisation de types Nullable (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="5925a-103">Using nullable types (C# Programming Guide)</span></span>

<span data-ttu-id="5925a-104">Les types Nullable sont des types qui représentent toutes les valeurs d’un type sous-jacent `T` ainsi qu’une autre valeur [null](../../language-reference/keywords/null.md).</span><span class="sxs-lookup"><span data-stu-id="5925a-104">Nullable types are types that represent all the values of an underlying value type `T`, and an additional [null](../../language-reference/keywords/null.md) value.</span></span> <span data-ttu-id="5925a-105">Pour plus d’informations, consultez la rubrique [Types Nullable](index.md).</span><span class="sxs-lookup"><span data-stu-id="5925a-105">For more information, see the [Nullable types](index.md) topic.</span></span>

<span data-ttu-id="5925a-106">Vous pouvez faire référence à un type Nullable dans l’un des formats suivants : `Nullable<T>` ou `T?`.</span><span class="sxs-lookup"><span data-stu-id="5925a-106">You can refer to a nullable type in any of the following forms: `Nullable<T>` or `T?`.</span></span> <span data-ttu-id="5925a-107">Ces deux formats sont interchangeables.</span><span class="sxs-lookup"><span data-stu-id="5925a-107">These two forms are interchangeable.</span></span>  
  
## <a name="declaration-and-assignment"></a><span data-ttu-id="5925a-108">Déclaration et affectation</span><span class="sxs-lookup"><span data-stu-id="5925a-108">Declaration and assignment</span></span>

<span data-ttu-id="5925a-109">Comme un type valeur peut être converti implicitement en type Nullable correspondant, vous affectez une valeur à un type Nullable comme vous le feriez pour son type valeur sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="5925a-109">As a value type can be implicitly converted to the corresponding nullable type, you assign a value to a nullable type as you would for its underlying value type.</span></span> <span data-ttu-id="5925a-110">Vous pouvez également affecter la valeur `null`.</span><span class="sxs-lookup"><span data-stu-id="5925a-110">You also can assign the `null` value.</span></span>  <span data-ttu-id="5925a-111">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="5925a-111">For example:</span></span>
  
[!code-csharp[declare and assign](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#1)]

## <a name="examination-of-a-nullable-type-value"></a><span data-ttu-id="5925a-112">Examen d’une valeur de type Nullable</span><span class="sxs-lookup"><span data-stu-id="5925a-112">Examination of a nullable type value</span></span>

<span data-ttu-id="5925a-113">Pour examiner une instance d’un type Nullable à la recherche de la valeur null et récupérer une valeur d’un type sous-jacent, utilisez les propriétés en lecture seule suivantes :</span><span class="sxs-lookup"><span data-stu-id="5925a-113">Use the following readonly properties to examine an instance of a nullable type for null and retrieve a value of an underlying type:</span></span>  
  
- <span data-ttu-id="5925a-114"><xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> indique si une instance d’un type Nullable a une valeur de son type sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="5925a-114"><xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> indicates whether an instance of a nullable type has a value of its underlying type.</span></span>
  
- <span data-ttu-id="5925a-115"><xref:System.Nullable%601.Value%2A?displayProperty=nameWithType> obtient la valeur d’un type sous-jacent si <xref:System.Nullable%601.HasValue%2A> est `true`.</span><span class="sxs-lookup"><span data-stu-id="5925a-115"><xref:System.Nullable%601.Value%2A?displayProperty=nameWithType> gets the value of an underlying type if <xref:System.Nullable%601.HasValue%2A> is `true`.</span></span> <span data-ttu-id="5925a-116">Si <xref:System.Nullable%601.HasValue%2A> est `false`, la propriété <xref:System.Nullable%601.Value%2A> lève une <xref:System.InvalidOperationException>.</span><span class="sxs-lookup"><span data-stu-id="5925a-116">If <xref:System.Nullable%601.HasValue%2A> is `false`, the <xref:System.Nullable%601.Value%2A> property throws an <xref:System.InvalidOperationException>.</span></span>
  
<span data-ttu-id="5925a-117">Le code dans l’exemple suivant utilise la propriété `HasValue` pour tester si la variable contient une valeur avant de l’afficher :</span><span class="sxs-lookup"><span data-stu-id="5925a-117">The code in the following example uses the `HasValue` property to test whether the variable contains a value before displaying it:</span></span>
  
[!code-csharp-interactive[use HasValue](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#2)]
  
<span data-ttu-id="5925a-118">Vous pouvez également comparer une variable de type Nullable avec `null` au lieu d’utiliser la propriété `HasValue`, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="5925a-118">You also can compare a nullable type variable with `null` instead of using the `HasValue` property, as the following example shows:</span></span>  
  
[!code-csharp-interactive[use comparison with null](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#3)]

<span data-ttu-id="5925a-119">À compter de C# 7.0, vous pouvez utiliser les [critères spéciaux](../../pattern-matching.md) pour examiner et obtenir une valeur d’un type Nullable :</span><span class="sxs-lookup"><span data-stu-id="5925a-119">Beginning with C# 7.0, you can use [pattern matching](../../pattern-matching.md) to both examine and get a value of a nullable type:</span></span>

[!code-csharp-interactive[use pattern matching](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#4)]

## <a name="conversion-from-a-nullable-type-to-an-underlying-type"></a><span data-ttu-id="5925a-120">Conversion d’un type Nullable en type sous-jacent</span><span class="sxs-lookup"><span data-stu-id="5925a-120">Conversion from a nullable type to an underlying type</span></span>

<span data-ttu-id="5925a-121">Si vous devez affecter une valeur de type Nullable à un type non Nullable, utilisez l’[opérateur de fusion null `??`](../../language-reference/operators/null-coalescing-operator.md) pour spécifier la valeur à affecter si une valeur de type Nullable est null (vous pouvez également utiliser pour cela la méthode <xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType>) :</span><span class="sxs-lookup"><span data-stu-id="5925a-121">If you need to assign a nullable type value to a non-nullable type, use the [null-coalescing operator `??`](../../language-reference/operators/null-coalescing-operator.md) to specify the value to be assigned if a nullable type value is null (you also can use the <xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType> method to do that):</span></span>
  
[!code-csharp-interactive[?? operator](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#5)]

<span data-ttu-id="5925a-122">Utilisez la méthode <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> si la valeur à utiliser quand une valeur de type Nullable est null doit être la valeur par défaut du type valeur sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="5925a-122">Use the <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> method if the value to be used when a nullable type value is null should be the default value of the underlying value type.</span></span>
  
<span data-ttu-id="5925a-123">Vous pouvez convertir explicitement un type Nullable en un type non Nullable.</span><span class="sxs-lookup"><span data-stu-id="5925a-123">You can explicitly cast a nullable type to a non-nullable type.</span></span> <span data-ttu-id="5925a-124">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="5925a-124">For example:</span></span>  
  
[!code-csharp[explicit cast](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#6)]

<span data-ttu-id="5925a-125">Au moment de l’exécution, si la valeur d’un type Nullable est null, le cast explicite lève une <xref:System.InvalidOperationException>.</span><span class="sxs-lookup"><span data-stu-id="5925a-125">At run time, if the value of a nullable type is null, the explicit cast throws an <xref:System.InvalidOperationException>.</span></span>

<span data-ttu-id="5925a-126">Un type valeur non Nullable est implicitement converti en type Nullable correspondant.</span><span class="sxs-lookup"><span data-stu-id="5925a-126">A non-nullable value type is implicitly converted to the corresponding nullable type.</span></span>
  
## <a name="operators"></a><span data-ttu-id="5925a-127">Opérateurs</span><span class="sxs-lookup"><span data-stu-id="5925a-127">Operators</span></span>

<span data-ttu-id="5925a-128">Les opérateurs unaire et binaire prédéfinis et tous les opérateurs définis par l’utilisateur existant pour les types valeur peuvent également être utilisés par les types Nullable.</span><span class="sxs-lookup"><span data-stu-id="5925a-128">The predefined unary and binary operators and any user-defined operators that exist for value types may also be used by nullable types.</span></span> <span data-ttu-id="5925a-129">Ces opérateurs produisent une valeur null si l’un des opérandes ou les deux sont null ; sinon, l’opérateur utilise les valeurs contenues pour calculer le résultat.</span><span class="sxs-lookup"><span data-stu-id="5925a-129">These operators produce a null value if one or both operands are null; otherwise, the operator uses the contained values to calculate the result.</span></span> <span data-ttu-id="5925a-130">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="5925a-130">For example:</span></span>  
  
[!code-csharp[operators](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#7)]

> [!NOTE]
> <span data-ttu-id="5925a-131">Pour le type `bool?`, les opérateurs `&` et `|` prédéfinis ne suivent pas les règles décrites dans cette section : le résultat d’une évaluation peut être non Null, même si l’un des opérandes est Null.</span><span class="sxs-lookup"><span data-stu-id="5925a-131">For the `bool?` type, the predefined `&` and `|` operators don't follow the rules described in this section: the result of an operator evaluation can be non-null even if one of the operands is null.</span></span> <span data-ttu-id="5925a-132">Pour plus d’informations, voir la section [Opérateurs logiques booléens Nullable](../../language-reference/operators/boolean-logical-operators.md#nullable-boolean-logical-operators) de l’article [Opérateurs logiques booléens](../../language-reference/operators/boolean-logical-operators.md).</span><span class="sxs-lookup"><span data-stu-id="5925a-132">For more information, see the [Nullable Boolean logical operators](../../language-reference/operators/boolean-logical-operators.md#nullable-boolean-logical-operators) section of the [Boolean logical operators](../../language-reference/operators/boolean-logical-operators.md) article.</span></span>
  
<span data-ttu-id="5925a-133">Pour les opérateurs relationnels (`<`, `>`, `<=`, `>=`), si l’un des opérandes ou les deux sont null, le résultat est `false`.</span><span class="sxs-lookup"><span data-stu-id="5925a-133">For the relational operators (`<`, `>`, `<=`, `>=`), if one or both operands are null, the result is `false`.</span></span> <span data-ttu-id="5925a-134">Ne partez pas du principe que parce qu’une comparaison spécifique (par exemple `<=`) retourne `false`, la comparaison opposée (`>`) retourne `true`.</span><span class="sxs-lookup"><span data-stu-id="5925a-134">Do not assume that because a particular comparison (for example, `<=`) returns `false`, the opposite comparison (`>`) returns `true`.</span></span> <span data-ttu-id="5925a-135">L’exemple suivant montre que 10 n’est</span><span class="sxs-lookup"><span data-stu-id="5925a-135">The following example shows that 10 is</span></span>

- <span data-ttu-id="5925a-136">ni supérieur ou égal à null,</span><span class="sxs-lookup"><span data-stu-id="5925a-136">neither greater than or equal to null,</span></span>
- <span data-ttu-id="5925a-137">ni inférieur à null.</span><span class="sxs-lookup"><span data-stu-id="5925a-137">nor less than null.</span></span>
  
[!code-csharp-interactive[relational and equality operators](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#8)]
  
<span data-ttu-id="5925a-138">L’exemple ci-dessus montre également qu’une comparaison d’égalité de deux types Nullable tous deux null donne la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="5925a-138">The above example also shows that an equality comparison of two nullable types that are both null evaluates to `true`.</span></span>

<span data-ttu-id="5925a-139">Pour plus d’informations, voir la section [Opérateurs lifted](~/_csharplang/spec/expressions.md#lifted-operators) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="5925a-139">For more information, see the [Lifted operators](~/_csharplang/spec/expressions.md#lifted-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="boxing-and-unboxing"></a><span data-ttu-id="5925a-140">Boxing et unboxing</span><span class="sxs-lookup"><span data-stu-id="5925a-140">Boxing and unboxing</span></span>

<span data-ttu-id="5925a-141">Un type valeur Nullable est [boxed](../types/boxing-and-unboxing.md) d’après les règles suivantes :</span><span class="sxs-lookup"><span data-stu-id="5925a-141">A nullable value type is [boxed](../types/boxing-and-unboxing.md) by the following rules:</span></span>

- <span data-ttu-id="5925a-142">Si <xref:System.Nullable%601.HasValue%2A> retourne `false`, la référence null est générée.</span><span class="sxs-lookup"><span data-stu-id="5925a-142">If <xref:System.Nullable%601.HasValue%2A> returns `false`, the null reference is produced.</span></span>  
- <span data-ttu-id="5925a-143">Si <xref:System.Nullable%601.HasValue%2A> retourne `true`, une valeur du type valeur sous-jacent `T` est boxed, pas l’instance de <xref:System.Nullable%601>.</span><span class="sxs-lookup"><span data-stu-id="5925a-143">If <xref:System.Nullable%601.HasValue%2A> returns `true`, a value of the underlying value type `T` is boxed, not the instance of <xref:System.Nullable%601>.</span></span>

<span data-ttu-id="5925a-144">Vous pouvez effectuer l’unboxing du type valeur boxed vers le type Nullable correspondant, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="5925a-144">You can unbox the boxed value type to the corresponding nullable type, as the following example shows:</span></span>

[!code-csharp-interactive[boxing and unboxing](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#9)]

## <a name="see-also"></a><span data-ttu-id="5925a-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5925a-145">See also</span></span>

- [<span data-ttu-id="5925a-146">Types Nullable</span><span class="sxs-lookup"><span data-stu-id="5925a-146">Nullable types</span></span>](index.md)
- [<span data-ttu-id="5925a-147">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="5925a-147">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="5925a-148">Que signifie réellement « Lifted » ?</span><span class="sxs-lookup"><span data-stu-id="5925a-148">What exactly does 'lifted' mean?</span></span>](https://blogs.msdn.microsoft.com/ericlippert/2007/06/27/what-exactly-does-lifted-mean/)
