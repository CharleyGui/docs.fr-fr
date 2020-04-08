---
title: Types de valeur nuls - Référence C
description: Renseignez-vous sur les types de valeur nulS de C et sur la façon de les utiliser
ms.date: 11/04/2019
helpviewer_keywords:
- nullable value types [C#]
ms.openlocfilehash: c13ef6a091ec6aebd4608c5ed8d2c03b067c7312
ms.sourcegitcommit: 2b3b2d684259463ddfc76ad680e5e09fdc1984d2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80888070"
---
# <a name="nullable-value-types-c-reference"></a><span data-ttu-id="648f6-103">Types de valeur nuls (référence C)</span><span class="sxs-lookup"><span data-stu-id="648f6-103">Nullable value types (C# reference)</span></span>

<span data-ttu-id="648f6-104">Un *type* `T?` de valeur in nullable représente toutes les valeurs de son type `T` de [valeur](value-types.md) sous-jacente et une valeur [nulle](../keywords/null.md) supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="648f6-104">A *nullable value type* `T?` represents all values of its underlying [value type](value-types.md) `T` and an additional [null](../keywords/null.md) value.</span></span> <span data-ttu-id="648f6-105">Par exemple, vous pouvez attribuer l’une `bool?` des `true` `false`trois `null`valeurs suivantes à une variable : , , ou .</span><span class="sxs-lookup"><span data-stu-id="648f6-105">For example, you can assign any of the following three values to a `bool?` variable: `true`, `false`, or `null`.</span></span> <span data-ttu-id="648f6-106">Un type `T` de valeur sous-jacent ne peut pas être un type de valeur nul lui-même.</span><span class="sxs-lookup"><span data-stu-id="648f6-106">An underlying value type `T` cannot be a nullable value type itself.</span></span>

> [!NOTE]
> <span data-ttu-id="648f6-107">C 8.0 introduit la fonction de type de référence nul.</span><span class="sxs-lookup"><span data-stu-id="648f6-107">C# 8.0 introduces the nullable reference types feature.</span></span> <span data-ttu-id="648f6-108">Pour plus d’informations, voir [Les types de référence Nullable](nullable-reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="648f6-108">For more information, see [Nullable reference types](nullable-reference-types.md).</span></span> <span data-ttu-id="648f6-109">Les types de valeur nulles sont disponibles à partir de C 2.</span><span class="sxs-lookup"><span data-stu-id="648f6-109">The nullable value types are available beginning with C# 2.</span></span>

<span data-ttu-id="648f6-110">Tout type de valeur in nullable est un exemple de la structure générique. <xref:System.Nullable%601?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="648f6-110">Any nullable value type is an instance of the generic <xref:System.Nullable%601?displayProperty=nameWithType> structure.</span></span> <span data-ttu-id="648f6-111">Vous pouvez vous référer à un type `T` de valeur nul avec `Nullable<T>` un `T?`type sous-jacent dans l’un des formulaires interchangeables suivants : ou .</span><span class="sxs-lookup"><span data-stu-id="648f6-111">You can refer to a nullable value type with an underlying type `T` in any of the following interchangeable forms: `Nullable<T>` or `T?`.</span></span>

<span data-ttu-id="648f6-112">Vous utilisez généralement un type de valeur inquérable lorsque vous devez représenter la valeur indéfinie d’un type de valeur sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="648f6-112">You typically use a nullable value type when you need to represent the undefined value of an underlying value type.</span></span> <span data-ttu-id="648f6-113">Par exemple, un Boolean, ou `bool`, `true` `false`variable ne peut être soit ou .</span><span class="sxs-lookup"><span data-stu-id="648f6-113">For example, a Boolean, or `bool`, variable can only be either `true` or `false`.</span></span> <span data-ttu-id="648f6-114">Toutefois, dans certaines applications, une valeur variable peut être indéfinie ou manquante.</span><span class="sxs-lookup"><span data-stu-id="648f6-114">However, in some applications a variable value can be undefined or missing.</span></span> <span data-ttu-id="648f6-115">Par exemple, un champ `true` `false`de base de données peut contenir ou, ou il peut ne contenir aucune valeur du tout, c’est-à-dire, `NULL`.</span><span class="sxs-lookup"><span data-stu-id="648f6-115">For example, a database field may contain `true` or `false`, or it may contain no value at all, that is, `NULL`.</span></span> <span data-ttu-id="648f6-116">Vous pouvez `bool?` utiliser le type dans ce scénario.</span><span class="sxs-lookup"><span data-stu-id="648f6-116">You can use the `bool?` type in that scenario.</span></span>

## <a name="declaration-and-assignment"></a><span data-ttu-id="648f6-117">Déclaration et affectation</span><span class="sxs-lookup"><span data-stu-id="648f6-117">Declaration and assignment</span></span>

<span data-ttu-id="648f6-118">Comme un type de valeur est implicitement convertible au type de valeur nullable correspondant, vous pouvez attribuer une valeur à une variable d’un type de valeur nul, comme vous le feriez pour son type de valeur sous-jacente.</span><span class="sxs-lookup"><span data-stu-id="648f6-118">As a value type is implicitly convertible to the corresponding nullable value type, you can assign a value to a variable of a nullable value type as you would do that for its underlying value type.</span></span> <span data-ttu-id="648f6-119">Vous pouvez également affecter la valeur `null`.</span><span class="sxs-lookup"><span data-stu-id="648f6-119">You also can assign the `null` value.</span></span> <span data-ttu-id="648f6-120">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="648f6-120">For example:</span></span>

[!code-csharp[declare and assign](snippets/NullableValueTypes.cs#Declaration)]

<span data-ttu-id="648f6-121">La valeur par défaut d’un type de valeur nul représente, `null`c’est-à-dire, c’est une instance dont <xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> la propriété retourne `false`.</span><span class="sxs-lookup"><span data-stu-id="648f6-121">The default value of a nullable value type represents `null`, that is, it's an instance whose <xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> property returns `false`.</span></span>

## <a name="examination-of-an-instance-of-a-nullable-value-type"></a><span data-ttu-id="648f6-122">Examen d’un cas de type de valeur nul</span><span class="sxs-lookup"><span data-stu-id="648f6-122">Examination of an instance of a nullable value type</span></span>

<span data-ttu-id="648f6-123">En commençant par le C 7.0, vous pouvez utiliser [ `is` l’opérateur avec un](../operators/type-testing-and-cast.md#type-testing-with-pattern-matching) `null` modèle de type pour examiner à la fois une instance d’un type de valeur nul pour et récupérer une valeur d’un type sous-jacent :</span><span class="sxs-lookup"><span data-stu-id="648f6-123">Beginning with C# 7.0, you can use the [`is` operator with a type pattern](../operators/type-testing-and-cast.md#type-testing-with-pattern-matching) to both examine an instance of a nullable value type for `null` and retrieve a value of an underlying type:</span></span>

[!code-csharp-interactive[use pattern matching](snippets/NullableValueTypes.cs#PatternMatching)]

<span data-ttu-id="648f6-124">Vous pouvez toujours utiliser les propriétés suivantes pour examiner et obtenir une valeur d’une variable de type valeur nulle :</span><span class="sxs-lookup"><span data-stu-id="648f6-124">You always can use the following read-only properties to examine and get a value of a nullable value type variable:</span></span>

- <span data-ttu-id="648f6-125"><xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType>indique si un cas de type de valeur nulle a une valeur de son type sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="648f6-125"><xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> indicates whether an instance of a nullable value type has a value of its underlying type.</span></span>

- <span data-ttu-id="648f6-126"><xref:System.Nullable%601.Value%2A?displayProperty=nameWithType> obtient la valeur d’un type sous-jacent si <xref:System.Nullable%601.HasValue%2A> est `true`.</span><span class="sxs-lookup"><span data-stu-id="648f6-126"><xref:System.Nullable%601.Value%2A?displayProperty=nameWithType> gets the value of an underlying type if <xref:System.Nullable%601.HasValue%2A> is `true`.</span></span> <span data-ttu-id="648f6-127">Si <xref:System.Nullable%601.HasValue%2A> est `false`, la propriété <xref:System.Nullable%601.Value%2A> lève une <xref:System.InvalidOperationException>.</span><span class="sxs-lookup"><span data-stu-id="648f6-127">If <xref:System.Nullable%601.HasValue%2A> is `false`, the <xref:System.Nullable%601.Value%2A> property throws an <xref:System.InvalidOperationException>.</span></span>

<span data-ttu-id="648f6-128">L’exemple suivant `HasValue` utilise la propriété pour vérifier si la variable contient une valeur avant de l’afficher :</span><span class="sxs-lookup"><span data-stu-id="648f6-128">The following example uses the `HasValue` property to test whether the variable contains a value before displaying it:</span></span>

[!code-csharp-interactive[use HasValue](snippets/NullableValueTypes.cs#HasValue)]

<span data-ttu-id="648f6-129">Vous pouvez également comparer une variable d’un type de valeur nul avec `null` au lieu d’utiliser la `HasValue` propriété, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="648f6-129">You also can compare a variable of a nullable value type with `null` instead of using the `HasValue` property, as the following example shows:</span></span>

[!code-csharp-interactive[use comparison with null](snippets/NullableValueTypes.cs#CompareWithNull)]

## <a name="conversion-from-a-nullable-value-type-to-an-underlying-type"></a><span data-ttu-id="648f6-130">Conversion d’un type de valeur in nullable à un type sous-jacent</span><span class="sxs-lookup"><span data-stu-id="648f6-130">Conversion from a nullable value type to an underlying type</span></span>

<span data-ttu-id="648f6-131">Si vous souhaitez attribuer une valeur d’un type de valeur nul à une variable de type valeur `null`non annulable, vous devrez peut-être spécifier la valeur à attribuer à la place de .</span><span class="sxs-lookup"><span data-stu-id="648f6-131">If you want to assign a value of a nullable value type to a non-nullable value type variable, you might need to specify the value to be assigned in place of `null`.</span></span> <span data-ttu-id="648f6-132">Utilisez [l’opérateur `??` de fusion nulle](../operators/null-coalescing-operator.md) pour le faire <xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType> (vous pouvez également utiliser la méthode dans le même but):</span><span class="sxs-lookup"><span data-stu-id="648f6-132">Use the [null-coalescing operator `??`](../operators/null-coalescing-operator.md) to do that (you also can use the <xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType> method for the same purpose):</span></span>

[!code-csharp-interactive[?? operator](snippets/NullableValueTypes.cs#NullCoalescing)]

<span data-ttu-id="648f6-133">Si vous souhaitez utiliser la valeur [par défaut](default-values.md) `null`du type <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> de valeur sous-jacente à la place de , utilisez la méthode.</span><span class="sxs-lookup"><span data-stu-id="648f6-133">If you want to use the [default](default-values.md) value of the underlying value type in place of `null`, use the <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="648f6-134">Vous pouvez également lancer explicitement un type de valeur nul à un type non annulable, comme l’exemple suivant le montre :</span><span class="sxs-lookup"><span data-stu-id="648f6-134">You also can explicitly cast a nullable value type to a non-nullable type, as the following example shows:</span></span>

[!code-csharp[explicit cast](snippets/NullableValueTypes.cs#Cast)]

<span data-ttu-id="648f6-135">Au moment de l’exécution, si la `null`valeur d’un <xref:System.InvalidOperationException>type de valeur nul est , le casting explicite jette un .</span><span class="sxs-lookup"><span data-stu-id="648f6-135">At run time, if the value of a nullable value type is `null`, the explicit cast throws an <xref:System.InvalidOperationException>.</span></span>

<span data-ttu-id="648f6-136">Un type `T` de valeur non annulable est implicitement `T?`convertible au type de valeur nullable correspondant .</span><span class="sxs-lookup"><span data-stu-id="648f6-136">A non-nullable value type `T` is implicitly convertible to the corresponding nullable value type `T?`.</span></span>

## <a name="lifted-operators"></a><span data-ttu-id="648f6-137">Opérateurs levés</span><span class="sxs-lookup"><span data-stu-id="648f6-137">Lifted operators</span></span>

<span data-ttu-id="648f6-138">Les opérateurs prédéfinis non classés et [binaires](../operators/index.md) ou tout `T` opérateur surchargé qui sont pris `T?`en charge par un type de valeur sont également pris en charge par le type de valeur nulle correspondant .</span><span class="sxs-lookup"><span data-stu-id="648f6-138">The predefined unary and binary [operators](../operators/index.md) or any overloaded operators that are supported by a value type `T` are also supported by the corresponding nullable value type `T?`.</span></span> <span data-ttu-id="648f6-139">Ces opérateurs, également connus sous `null` le nom `null` *d’opérateurs levés,* produisent si l’un ou les deux opérands sont ; autrement, l’opérateur utilise les valeurs contenues de ses opérandes pour calculer le résultat.</span><span class="sxs-lookup"><span data-stu-id="648f6-139">These operators, also known as *lifted operators*, produce `null` if one or both operands are `null`; otherwise, the operator uses the contained values of its operands to calculate the result.</span></span> <span data-ttu-id="648f6-140">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="648f6-140">For example:</span></span>

[!code-csharp[lifted operators](snippets/NullableValueTypes.cs#LiftedOperator)]

> [!NOTE]
> <span data-ttu-id="648f6-141">Pour `bool?` le type, les `&` prédéfinis et `|` les opérateurs ne suivent pas les règles décrites dans cette section: le `null`résultat d’une évaluation de l’opérateur peut être non-null même si l’un des opérands est .</span><span class="sxs-lookup"><span data-stu-id="648f6-141">For the `bool?` type, the predefined `&` and `|` operators don't follow the rules described in this section: the result of an operator evaluation can be non-null even if one of the operands is `null`.</span></span> <span data-ttu-id="648f6-142">Pour plus d’informations, voir la section [Opérateurs logiques booléens Nullable](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) de l’article [Opérateurs logiques booléens](../operators/boolean-logical-operators.md).</span><span class="sxs-lookup"><span data-stu-id="648f6-142">For more information, see the [Nullable Boolean logical operators](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) section of the [Boolean logical operators](../operators/boolean-logical-operators.md) article.</span></span>

<span data-ttu-id="648f6-143">Pour [comparison operators](../operators/comparison-operators.md) `<`les opérateurs `>` `<=`de `>=`comparaison , , , et `null`, si `false`l’un ou les deux opérands sont , le résultat est; autrement, les valeurs contenues des opérandes sont comparées.</span><span class="sxs-lookup"><span data-stu-id="648f6-143">For the [comparison operators](../operators/comparison-operators.md) `<`, `>`, `<=`, and `>=`, if one or both operands are `null`, the result is `false`; otherwise, the contained values of operands are compared.</span></span> <span data-ttu-id="648f6-144">Ne partez pas du principe que parce qu’une comparaison spécifique (par exemple `<=`) retourne `false`, la comparaison opposée (`>`) retourne `true`.</span><span class="sxs-lookup"><span data-stu-id="648f6-144">Do not assume that because a particular comparison (for example, `<=`) returns `false`, the opposite comparison (`>`) returns `true`.</span></span> <span data-ttu-id="648f6-145">L’exemple suivant montre que 10 n’est</span><span class="sxs-lookup"><span data-stu-id="648f6-145">The following example shows that 10 is</span></span>

- <span data-ttu-id="648f6-146">ni plus grand ni égal à`null`</span><span class="sxs-lookup"><span data-stu-id="648f6-146">neither greater than or equal to `null`</span></span>
- <span data-ttu-id="648f6-147">ni moins que`null`</span><span class="sxs-lookup"><span data-stu-id="648f6-147">nor less than `null`</span></span>

[!code-csharp-interactive[relational and equality operators](snippets/NullableValueTypes.cs#ComparisonOperators)]

<span data-ttu-id="648f6-148">Pour [l’opérateur](../operators/equality-operators.md#equality-operator-) `==`de l’égalité `null`, si `true`les deux opérandes sont `null`, le `false`résultat est , si un seul des opérands est , le résultat est; autrement, les valeurs contenues des opérandes sont comparées.</span><span class="sxs-lookup"><span data-stu-id="648f6-148">For the [equality operator](../operators/equality-operators.md#equality-operator-) `==`, if both operands are `null`, the result is `true`, if only one of the operands is `null`, the result is `false`; otherwise, the contained values of operands are compared.</span></span>

<span data-ttu-id="648f6-149">Pour [l’opérateur](../operators/equality-operators.md#inequality-operator-) `!=`d’inégalité , `null`si les `false`deux opérandes sont , `null`le résultat `true`est , si un seul des opérands est , le résultat est ; autrement, les valeurs contenues des opérandes sont comparées.</span><span class="sxs-lookup"><span data-stu-id="648f6-149">For the [inequality operator](../operators/equality-operators.md#inequality-operator-) `!=`, if both operands are `null`, the result is `false`, if only one of the operands is `null`, the result is `true`; otherwise, the contained values of operands are compared.</span></span>

<span data-ttu-id="648f6-150">S’il existe une [conversion définie par l’utilisateur](../operators/user-defined-conversion-operators.md) entre deux types de valeurs, la même conversion peut également être utilisée entre les types de valeur nuls correspondants.</span><span class="sxs-lookup"><span data-stu-id="648f6-150">If there exists a [user-defined conversion](../operators/user-defined-conversion-operators.md) between two value types, the same conversion can also be used between the corresponding nullable value types.</span></span>

## <a name="boxing-and-unboxing"></a><span data-ttu-id="648f6-151">Boxing et unboxing</span><span class="sxs-lookup"><span data-stu-id="648f6-151">Boxing and unboxing</span></span>

<span data-ttu-id="648f6-152">Une instance d’un `T?` type de valeur nulle est [boxée](../../programming-guide/types/boxing-and-unboxing.md) comme suit :</span><span class="sxs-lookup"><span data-stu-id="648f6-152">An instance of a nullable value type `T?` is [boxed](../../programming-guide/types/boxing-and-unboxing.md) as follows:</span></span>

- <span data-ttu-id="648f6-153">Si <xref:System.Nullable%601.HasValue%2A> retourne `false`, la référence null est générée.</span><span class="sxs-lookup"><span data-stu-id="648f6-153">If <xref:System.Nullable%601.HasValue%2A> returns `false`, the null reference is produced.</span></span>
- <span data-ttu-id="648f6-154">Si <xref:System.Nullable%601.HasValue%2A> `true`les rendements , la `T` valeur correspondante du type <xref:System.Nullable%601>de valeur sous-jacente est en boîte, et non l’exemple de .</span><span class="sxs-lookup"><span data-stu-id="648f6-154">If <xref:System.Nullable%601.HasValue%2A> returns `true`, the corresponding value of the underlying value type `T` is boxed, not the instance of <xref:System.Nullable%601>.</span></span>

<span data-ttu-id="648f6-155">Vous pouvez déballer une valeur `T` en boîte d’un `T?`type de valeur au type de valeur nullable correspondant, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="648f6-155">You can unbox a boxed value of a value type `T` to the corresponding nullable value type `T?`, as the following example shows:</span></span>

[!code-csharp-interactive[boxing and unboxing](snippets/NullableValueTypes.cs#Boxing)]

## <a name="how-to-identify-a-nullable-value-type"></a><span data-ttu-id="648f6-156">Comment identifier un type de valeur nul</span><span class="sxs-lookup"><span data-stu-id="648f6-156">How to identify a nullable value type</span></span>

<span data-ttu-id="648f6-157">L’exemple suivant montre comment <xref:System.Type?displayProperty=nameWithType> déterminer si une instance représente un <xref:System.Nullable%601?displayProperty=nameWithType> type de valeur `T`nulle construit, c’est-à-dire le type avec un paramètre de type spécifié :</span><span class="sxs-lookup"><span data-stu-id="648f6-157">The following example shows how to determine whether a <xref:System.Type?displayProperty=nameWithType> instance represents a constructed nullable value type, that is, the <xref:System.Nullable%601?displayProperty=nameWithType> type with a specified type parameter `T`:</span></span>

[!code-csharp-interactive[whether Type is nullable](snippets/NullableValueTypes.cs#IsTypeNullable)]

<span data-ttu-id="648f6-158">Comme l’exemple le montre, vous utilisez <xref:System.Type?displayProperty=nameWithType> le [type d’opérateur](../operators/type-testing-and-cast.md#typeof-operator) pour créer une instance.</span><span class="sxs-lookup"><span data-stu-id="648f6-158">As the example shows, you use the [typeof](../operators/type-testing-and-cast.md#typeof-operator) operator to create a <xref:System.Type?displayProperty=nameWithType> instance.</span></span>

<span data-ttu-id="648f6-159">Si vous souhaitez déterminer si une instance est d’un type <xref:System.Object.GetType%2A?displayProperty=nameWithType> de valeur <xref:System.Type> nulle, n’utilisez pas la méthode pour obtenir une instance à tester avec le code précédent.</span><span class="sxs-lookup"><span data-stu-id="648f6-159">If you want to determine whether an instance is of a nullable value type, don't use the <xref:System.Object.GetType%2A?displayProperty=nameWithType> method to get a <xref:System.Type> instance to be tested with the preceding code.</span></span> <span data-ttu-id="648f6-160">Lorsque vous <xref:System.Object.GetType%2A?displayProperty=nameWithType> appelez la méthode sur une instance d’un type <xref:System.Object>de valeur nulle, l’instance est en [boîte](#boxing-and-unboxing) à .</span><span class="sxs-lookup"><span data-stu-id="648f6-160">When you call the <xref:System.Object.GetType%2A?displayProperty=nameWithType> method on an instance of a nullable value type, the instance is [boxed](#boxing-and-unboxing) to <xref:System.Object>.</span></span> <span data-ttu-id="648f6-161">Comme la boxe d’un cas non nul d’un type de valeur <xref:System.Object.GetType%2A> nulle <xref:System.Type> équivaut à la boxe d’une valeur du type sous-jacent, renvoie une instance qui représente le type sous-jacent d’un type de valeur nul:</span><span class="sxs-lookup"><span data-stu-id="648f6-161">As boxing of a non-null instance of a nullable value type is equivalent to boxing of a value of the underlying type, <xref:System.Object.GetType%2A> returns a <xref:System.Type> instance that represents the underlying type of a nullable value type:</span></span>

[!code-csharp-interactive[GetType example](snippets/NullableValueTypes.cs#GetType)]

<span data-ttu-id="648f6-162">En outre, ne pas utiliser [l’opérateur est](../operators/type-testing-and-cast.md#is-operator) pour déterminer si une instance est d’un type de valeur nulle.</span><span class="sxs-lookup"><span data-stu-id="648f6-162">Also, don't use the [is](../operators/type-testing-and-cast.md#is-operator) operator to determine whether an instance is of a nullable value type.</span></span> <span data-ttu-id="648f6-163">Comme l’indique l’exemple suivant, vous ne pouvez pas distinguer les `is` types d’instance de type valeur nul et son exemple de type sous-jacent avec l’opérateur :</span><span class="sxs-lookup"><span data-stu-id="648f6-163">As the following example shows, you cannot distinguish types of a nullable value type instance and its underlying type instance with the `is` operator:</span></span>

[!code-csharp-interactive[is operator example](snippets/NullableValueTypes.cs#IsOperator)]

<span data-ttu-id="648f6-164">Vous pouvez utiliser le code présenté dans l’exemple suivant pour déterminer si une instance est d’un type de valeur nul :</span><span class="sxs-lookup"><span data-stu-id="648f6-164">You can use the code presented in the following example to determine whether an instance is of a nullable value type:</span></span>

[!code-csharp-interactive[whether an instance is of a nullable type](snippets/NullableValueTypes.cs#IsInstanceNullable)]

> [!NOTE]
> <span data-ttu-id="648f6-165">Les méthodes décrites dans cet article ne s’appliquent pas dans le cas des types de [référence nuls](nullable-reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="648f6-165">The methods described in this section are not applicable in the case of [nullable reference types](nullable-reference-types.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="648f6-166">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="648f6-166">C# language specification</span></span>

<span data-ttu-id="648f6-167">Pour plus d’informations, consultez les sections suivantes de la [spécification du langage C#](~/_csharplang/spec/introduction.md) :</span><span class="sxs-lookup"><span data-stu-id="648f6-167">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="648f6-168">Types Nullable</span><span class="sxs-lookup"><span data-stu-id="648f6-168">Nullable types</span></span>](~/_csharplang/spec/types.md#nullable-types)
- [<span data-ttu-id="648f6-169">Opérateurs levés</span><span class="sxs-lookup"><span data-stu-id="648f6-169">Lifted operators</span></span>](~/_csharplang/spec/expressions.md#lifted-operators)
- [<span data-ttu-id="648f6-170">Conversions implicites annulables</span><span class="sxs-lookup"><span data-stu-id="648f6-170">Implicit nullable conversions</span></span>](~/_csharplang/spec/conversions.md#implicit-nullable-conversions)
- [<span data-ttu-id="648f6-171">Conversions annulées explicites</span><span class="sxs-lookup"><span data-stu-id="648f6-171">Explicit nullable conversions</span></span>](~/_csharplang/spec/conversions.md#explicit-nullable-conversions)
- [<span data-ttu-id="648f6-172">Opérateurs de conversion levés</span><span class="sxs-lookup"><span data-stu-id="648f6-172">Lifted conversion operators</span></span>](~/_csharplang/spec/conversions.md#lifted-conversion-operators)

## <a name="see-also"></a><span data-ttu-id="648f6-173">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="648f6-173">See also</span></span>

- [<span data-ttu-id="648f6-174">Référence C#</span><span class="sxs-lookup"><span data-stu-id="648f6-174">C# reference</span></span>](../index.md)
- [<span data-ttu-id="648f6-175">Que signifie réellement « lifted » ?</span><span class="sxs-lookup"><span data-stu-id="648f6-175">What exactly does 'lifted' mean?</span></span>](https://docs.microsoft.com/archive/blogs/ericlippert/what-exactly-does-lifted-mean)
- <xref:System.Nullable%601?displayProperty=nameWithType>
- <xref:System.Nullable?displayProperty=nameWithType>
- <xref:System.Nullable.GetUnderlyingType%2A?displayProperty=nameWithType>
- [<span data-ttu-id="648f6-176">Types références Nullables</span><span class="sxs-lookup"><span data-stu-id="648f6-176">Nullable reference types</span></span>](nullable-reference-types.md)
