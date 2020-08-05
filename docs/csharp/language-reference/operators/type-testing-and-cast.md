---
title: Opérateurs de test de type et expression de cast-référence C#
description: Découvrez les opérateurs C# que vous pouvez utiliser pour vérifier le type de résultat d’une expression et le convertir en un autre type si nécessaire.
ms.date: 06/21/2019
author: pkulikov
f1_keywords:
- is_CSharpKeyword
- as_CSharpKeyword
- ()_CSharpKeyword
- typeof_CSharpKeyword
helpviewer_keywords:
- type-testing operators [C#]
- conversion operators [C#]
- type conversion [C#]
- is operator [C#]
- as operator [C#]
- cast operator [C#]
- cast expression [C#]
- () operator [C#]
- typeof operator [C#]
ms.openlocfilehash: 7c1c65c61a2214792dcd26efd4be1a9d7f2c07ca
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87555498"
---
# <a name="type-testing-operators-and-cast-expression-c-reference"></a><span data-ttu-id="efa42-103">Opérateurs de test de type et expression de cast (référence C#)</span><span class="sxs-lookup"><span data-stu-id="efa42-103">Type-testing operators and cast expression (C# reference)</span></span>

<span data-ttu-id="efa42-104">Vous pouvez utiliser les opérateurs et expressions suivants pour effectuer une vérification de type ou une conversion de type :</span><span class="sxs-lookup"><span data-stu-id="efa42-104">You can use the following operators and expressions to perform type checking or type conversion:</span></span>

- <span data-ttu-id="efa42-105">[Opérateur is](#is-operator) : pour vérifier si le type de runtime d’une expression est compatible avec un type donné</span><span class="sxs-lookup"><span data-stu-id="efa42-105">[is operator](#is-operator): to check if the runtime type of an expression is compatible with a given type</span></span>
- <span data-ttu-id="efa42-106">[Opérateur as](#as-operator) : pour convertir explicitement une expression en un type donné si son type de runtime est compatible avec ce type</span><span class="sxs-lookup"><span data-stu-id="efa42-106">[as operator](#as-operator): to explicitly convert an expression to a given type if its runtime type is compatible with that type</span></span>
- <span data-ttu-id="efa42-107">[expression de cast](#cast-expression): pour effectuer une conversion explicite</span><span class="sxs-lookup"><span data-stu-id="efa42-107">[cast expression](#cast-expression): to perform an explicit conversion</span></span>
- <span data-ttu-id="efa42-108">[Opérateur typeof](#typeof-operator) : pour obtenir l’instance de <xref:System.Type?displayProperty=nameWithType> pour un type</span><span class="sxs-lookup"><span data-stu-id="efa42-108">[typeof operator](#typeof-operator): to obtain the <xref:System.Type?displayProperty=nameWithType> instance for a type</span></span>

## <a name="is-operator"></a><span data-ttu-id="efa42-109">Opérateur is</span><span class="sxs-lookup"><span data-stu-id="efa42-109">is operator</span></span>

<span data-ttu-id="efa42-110">L’opérateur `is` vérifie si le type de runtime du résultat d’une expression est compatible avec un type donné.</span><span class="sxs-lookup"><span data-stu-id="efa42-110">The `is` operator checks if the runtime type of an expression result is compatible with a given type.</span></span> <span data-ttu-id="efa42-111">À compter de C# 7,0, l' `is` opérateur teste également un résultat d’expression par rapport à un modèle.</span><span class="sxs-lookup"><span data-stu-id="efa42-111">Beginning with C# 7.0, the `is` operator also tests an expression result against a pattern.</span></span>

<span data-ttu-id="efa42-112">L’expression avec l’opérateur de test de type `is` a la forme suivante</span><span class="sxs-lookup"><span data-stu-id="efa42-112">The expression with the type-testing `is` operator has the following form</span></span>

```csharp
E is T
```

<span data-ttu-id="efa42-113">où `E` est une expression qui retourne une valeur et `T` est le nom d’un type ou un d’un paramètre de type.</span><span class="sxs-lookup"><span data-stu-id="efa42-113">where `E` is an expression that returns a value and `T` is the name of a type or a type parameter.</span></span> <span data-ttu-id="efa42-114">`E` ne peut pas être une méthode anonyme ou une expression lambda.</span><span class="sxs-lookup"><span data-stu-id="efa42-114">`E` cannot be an anonymous method or a lambda expression.</span></span>

<span data-ttu-id="efa42-115">L’expression `E is T` retourne `true` si le résultat de `E` n’est pas null et peut être converti en type `T` par une conversion de référence, une conversion boxing ou une conversion unboxing ; sinon, elle retourne `false`.</span><span class="sxs-lookup"><span data-stu-id="efa42-115">The `E is T` expression returns `true` if the result of `E` is non-null and can be converted to type `T` by a reference conversion, a boxing conversion, or an unboxing conversion; otherwise, it returns `false`.</span></span> <span data-ttu-id="efa42-116">L’opérateur `is` ne considère pas les conversions définies par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="efa42-116">The `is` operator doesn't consider user-defined conversions.</span></span>

<span data-ttu-id="efa42-117">L’exemple suivant montre que l’opérateur `is` retourne `true` si le type de runtime d’une expression dérive d’un type donné, autrement dit, s’il existe une conversion de référence entre les types :</span><span class="sxs-lookup"><span data-stu-id="efa42-117">The following example demonstrates that the `is` operator returns `true` if the runtime type of an expression result derives from a given type, that is, there exists a reference conversion between types:</span></span>

[!code-csharp[is with reference conversion](snippets/TypeTestingAndConversionOperators.cs#IsWithReferenceConversion)]

<span data-ttu-id="efa42-118">L’exemple suivant montre que l' `is` opérateur prend en compte les conversions boxing et unboxing, mais ne prend pas en compte les [conversions numériques](../builtin-types/numeric-conversions.md):</span><span class="sxs-lookup"><span data-stu-id="efa42-118">The next example shows that the `is` operator takes into account boxing and unboxing conversions but doesn't consider [numeric conversions](../builtin-types/numeric-conversions.md):</span></span>

[!code-csharp-interactive[is with int](snippets/TypeTestingAndConversionOperators.cs#IsWithInt)]

<span data-ttu-id="efa42-119">Pour plus d’informations sur les conversions C#, consultez le chapitre [Conversions](~/_csharplang/spec/conversions.md) de la [Spécification du langage C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="efa42-119">For information about C# conversions, see the [Conversions](~/_csharplang/spec/conversions.md) chapter of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

### <a name="type-testing-with-pattern-matching"></a><span data-ttu-id="efa42-120">Test de type avec des critères spéciaux</span><span class="sxs-lookup"><span data-stu-id="efa42-120">Type testing with pattern matching</span></span>

<span data-ttu-id="efa42-121">À compter de C# 7,0, l' `is` opérateur teste également un résultat d’expression par rapport à un modèle.</span><span class="sxs-lookup"><span data-stu-id="efa42-121">Beginning with C# 7.0, the `is` operator also tests an expression result against a pattern.</span></span> <span data-ttu-id="efa42-122">En particulier, il prend en charge le modèle de type sous la forme suivante :</span><span class="sxs-lookup"><span data-stu-id="efa42-122">In particular, it supports the type pattern in the following form:</span></span>

```csharp
E is T v
```

<span data-ttu-id="efa42-123">où `E` est une expression qui retourne une valeur, `T` est le nom d’un type ou un d’un paramètre de type et `v` est une nouvelle variable locale de type `T`.</span><span class="sxs-lookup"><span data-stu-id="efa42-123">where `E` is an expression that returns a value, `T` is the name of a type or a type parameter, and `v` is a new local variable of type `T`.</span></span> <span data-ttu-id="efa42-124">Si le résultat de `E` n’est pas null et peut être converti en `T` par conversion de référence, boxing ou unboxing, l’expression `E is T v` retourne `true` et la valeur convertie du résultat de `E` est affectée à la variable `v`.</span><span class="sxs-lookup"><span data-stu-id="efa42-124">If the result of `E` is non-null and can be converted to `T` by a reference, boxing, or unboxing conversion, the `E is T v` expression returns `true` and the converted value of the result of `E` is assigned to variable `v`.</span></span>

<span data-ttu-id="efa42-125">L’exemple suivant illustre l’utilisation de l’opérateur `is` avec le modèle de type :</span><span class="sxs-lookup"><span data-stu-id="efa42-125">The following example demonstrates the usage of the `is` operator with the type pattern:</span></span>

[!code-csharp-interactive[is with type pattern](snippets/TypeTestingAndConversionOperators.cs#IsTypePattern)]

<span data-ttu-id="efa42-126">Pour plus d’informations sur le modèle de type et les autres modèles pris en charge, consultez [Critères spéciaux avec is](../keywords/is.md#pattern-matching-with-is).</span><span class="sxs-lookup"><span data-stu-id="efa42-126">For more information about the type pattern and other supported patterns, see [Pattern matching with is](../keywords/is.md#pattern-matching-with-is).</span></span>

## <a name="as-operator"></a><span data-ttu-id="efa42-127">opérateur as</span><span class="sxs-lookup"><span data-stu-id="efa42-127">as operator</span></span>

<span data-ttu-id="efa42-128">L’opérateur `as` convertit explicitement le résultat d’une expression en un type de valeur de référence ou nullable.</span><span class="sxs-lookup"><span data-stu-id="efa42-128">The `as` operator explicitly converts the result of an expression to a given reference or nullable value type.</span></span> <span data-ttu-id="efa42-129">Si la conversion n’est pas possible, l’opérateur `as` retourne `null`.</span><span class="sxs-lookup"><span data-stu-id="efa42-129">If the conversion is not possible, the `as` operator returns `null`.</span></span> <span data-ttu-id="efa42-130">Contrairement à une [expression de cast](#cast-expression), l' `as` opérateur ne lève jamais d’exception.</span><span class="sxs-lookup"><span data-stu-id="efa42-130">Unlike a [cast expression](#cast-expression), the `as` operator never throws an exception.</span></span>

<span data-ttu-id="efa42-131">L’expression de la forme</span><span class="sxs-lookup"><span data-stu-id="efa42-131">The expression of the form</span></span>

```csharp
E as T
```

<span data-ttu-id="efa42-132">où `E` est une expression qui retourne une valeur et `T` est le nom d’un type ou un d’un paramètre de type, avec le même résultat que</span><span class="sxs-lookup"><span data-stu-id="efa42-132">where `E` is an expression that returns a value and `T` is the name of a type or a type parameter, produces the same result as</span></span>

```csharp
E is T ? (T)(E) : (T)null
```

<span data-ttu-id="efa42-133">sauf que `E` n’est évalué qu’une seule fois.</span><span class="sxs-lookup"><span data-stu-id="efa42-133">except that `E` is only evaluated once.</span></span>

<span data-ttu-id="efa42-134">L’opérateur `as` envisage uniquement les conversions de référence, nullable, boxing et unboxing.</span><span class="sxs-lookup"><span data-stu-id="efa42-134">The `as` operator considers only reference, nullable, boxing, and unboxing conversions.</span></span> <span data-ttu-id="efa42-135">Vous ne pouvez pas utiliser l’opérateur `as` pour effectuer une conversion définie par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="efa42-135">You cannot use the `as` operator to perform a user-defined conversion.</span></span> <span data-ttu-id="efa42-136">Pour ce faire, utilisez une [expression de cast](#cast-expression).</span><span class="sxs-lookup"><span data-stu-id="efa42-136">To do that, use a [cast expression](#cast-expression).</span></span>

<span data-ttu-id="efa42-137">L’exemple suivant illustre l’utilisation de l’opérateur `as` :</span><span class="sxs-lookup"><span data-stu-id="efa42-137">The following example demonstrates the usage of the `as` operator:</span></span>

[!code-csharp-interactive[as operator](snippets/TypeTestingAndConversionOperators.cs#AsOperator)]

> [!NOTE]
> <span data-ttu-id="efa42-138">Comme le montre l’exemple précédent, vous devez comparer le résultat de l’expression `as` avec `null` pour vérifier si la conversion a réussi.</span><span class="sxs-lookup"><span data-stu-id="efa42-138">As the preceding example shows, you need to compare the result of the `as` expression with `null` to check if the conversion is successful.</span></span> <span data-ttu-id="efa42-139">À compter de C# 7,0, vous pouvez utiliser l' [opérateur is](#type-testing-with-pattern-matching) pour tester si la conversion aboutit et, si elle aboutit, assigner son résultat à une nouvelle variable.</span><span class="sxs-lookup"><span data-stu-id="efa42-139">Beginning with C# 7.0, you can use the [is operator](#type-testing-with-pattern-matching) both to test if the conversion succeeds and, if it succeeds, assign its result to a new variable.</span></span>

## <a name="cast-expression"></a><span data-ttu-id="efa42-140">Expression Cast</span><span class="sxs-lookup"><span data-stu-id="efa42-140">Cast expression</span></span>

<span data-ttu-id="efa42-141">Une expression cast de la forme `(T)E` effectue une conversion explicite du résultat de l’expression `E` en type `T`.</span><span class="sxs-lookup"><span data-stu-id="efa42-141">A cast expression of the form `(T)E` performs an explicit conversion of the result of expression `E` to type `T`.</span></span> <span data-ttu-id="efa42-142">S’il n’existe aucune conversion explicite du type de `E` en type `T`, une erreur de compilation se produit.</span><span class="sxs-lookup"><span data-stu-id="efa42-142">If no explicit conversion exists from the type of `E` to type `T`, a compile-time error occurs.</span></span> <span data-ttu-id="efa42-143">Au moment de l’exécution, une conversion explicite peut ne pas réussir, et une expression cast peut lever une exception.</span><span class="sxs-lookup"><span data-stu-id="efa42-143">At run time, an explicit conversion might not succeed and a cast expression might throw an exception.</span></span>

<span data-ttu-id="efa42-144">L’exemple suivant montre des conversions numériques et de référence explicites :</span><span class="sxs-lookup"><span data-stu-id="efa42-144">The following example demonstrates explicit numeric and reference conversions:</span></span>

[!code-csharp-interactive[cast expression](snippets/TypeTestingAndConversionOperators.cs#Cast)]

<span data-ttu-id="efa42-145">Pour plus d’informations sur les conversions explicites prises en charge, consultez la section [Conversions explicites](~/_csharplang/spec/conversions.md#explicit-conversions) de la [Spécification du langage C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="efa42-145">For information about supported explicit conversions, see the [Explicit conversions](~/_csharplang/spec/conversions.md#explicit-conversions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span> <span data-ttu-id="efa42-146">Pour plus d’informations sur la façon de définir une conversion de type explicite ou implicite personnalisée, consultez [Opérateurs de conversion définie par l’utilisateur](user-defined-conversion-operators.md).</span><span class="sxs-lookup"><span data-stu-id="efa42-146">For information about how to define a custom explicit or implicit type conversion, see [User-defined conversion operators](user-defined-conversion-operators.md).</span></span>

### <a name="other-usages-of-"></a><span data-ttu-id="efa42-147">Autres utilisations de ()</span><span class="sxs-lookup"><span data-stu-id="efa42-147">Other usages of ()</span></span>

<span data-ttu-id="efa42-148">Vous pouvez aussi utiliser des parenthèses pour [appeler une méthode ou un délégué](member-access-operators.md#invocation-expression-).</span><span class="sxs-lookup"><span data-stu-id="efa42-148">You also use parentheses to [call a method or invoke a delegate](member-access-operators.md#invocation-expression-).</span></span>

<span data-ttu-id="efa42-149">Une autre utilisation des parenthèses est d’ajuster l’ordre dans lequel évaluer les opérations dans une expression.</span><span class="sxs-lookup"><span data-stu-id="efa42-149">Other use of parentheses is to adjust the order in which to evaluate operations in an expression.</span></span> <span data-ttu-id="efa42-150">Pour plus d’informations, consultez [Opérateurs C#](index.md).</span><span class="sxs-lookup"><span data-stu-id="efa42-150">For more information, see [C# operators](index.md).</span></span>

## <a name="typeof-operator"></a><span data-ttu-id="efa42-151">Opérateur typeof</span><span class="sxs-lookup"><span data-stu-id="efa42-151">typeof operator</span></span>

<span data-ttu-id="efa42-152">L’opérateur `typeof` obtient l’instance <xref:System.Type?displayProperty=nameWithType> pour un type.</span><span class="sxs-lookup"><span data-stu-id="efa42-152">The `typeof` operator obtains the <xref:System.Type?displayProperty=nameWithType> instance for a type.</span></span> <span data-ttu-id="efa42-153">L’argument de l’opérateur `typeof` doit avoir le nom d’un type ou d’un paramètre de type, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="efa42-153">The argument to the `typeof` operator must be the name of a type or a type parameter, as the following example shows:</span></span>

[!code-csharp-interactive[typeof operator](snippets/TypeTestingAndConversionOperators.cs#TypeOf)]

<span data-ttu-id="efa42-154">Vous pouvez également utiliser l' `typeof` opérateur avec des types génériques indépendants.</span><span class="sxs-lookup"><span data-stu-id="efa42-154">You can also use the `typeof` operator with unbound generic types.</span></span> <span data-ttu-id="efa42-155">Le nom d’un type générique indépendant doit contenir le nombre approprié de virgules, à savoir une de moins que le nombre de paramètres de type.</span><span class="sxs-lookup"><span data-stu-id="efa42-155">The name of an unbound generic type must contain the appropriate number of commas, which is one less than the number of type parameters.</span></span> <span data-ttu-id="efa42-156">L’exemple suivant illustre l’utilisation de l’opérateur `typeof` avec un type générique indépendant :</span><span class="sxs-lookup"><span data-stu-id="efa42-156">The following example shows the usage of the `typeof` operator with an unbound generic type:</span></span>

[!code-csharp-interactive[typeof unbound generic](snippets/TypeTestingAndConversionOperators.cs#TypeOfUnboundGeneric)]

<span data-ttu-id="efa42-157">Une expression ne peut pas être un argument de l’opérateur `typeof`.</span><span class="sxs-lookup"><span data-stu-id="efa42-157">An expression cannot be an argument of the `typeof` operator.</span></span> <span data-ttu-id="efa42-158">Pour obtenir l' <xref:System.Type?displayProperty=nameWithType> instance du type au moment de l’exécution d’un résultat d’expression, utilisez la <xref:System.Object.GetType%2A?displayProperty=nameWithType> méthode.</span><span class="sxs-lookup"><span data-stu-id="efa42-158">To get the <xref:System.Type?displayProperty=nameWithType> instance for the runtime type of an expression result, use the <xref:System.Object.GetType%2A?displayProperty=nameWithType> method.</span></span>

### <a name="type-testing-with-the-typeof-operator"></a><span data-ttu-id="efa42-159">Test de type avec l’opérateur `typeof`</span><span class="sxs-lookup"><span data-stu-id="efa42-159">Type testing with the `typeof` operator</span></span>

<span data-ttu-id="efa42-160">Utilisez l’opérateur `typeof` pour vérifier si le type de runtime du résultat de l’expression correspond exactement à un type donné.</span><span class="sxs-lookup"><span data-stu-id="efa42-160">Use the `typeof` operator to check if the runtime type of the expression result exactly matches a given type.</span></span> <span data-ttu-id="efa42-161">L’exemple suivant illustre la différence entre la vérification des types effectuée avec l’opérateur `typeof`[l’opérateur is](#is-operator) :</span><span class="sxs-lookup"><span data-stu-id="efa42-161">The following example demonstrates the difference between type checking performed with the `typeof` operator and the [is operator](#is-operator):</span></span>

[!code-csharp[typeof vs is](snippets/TypeTestingAndConversionOperators.cs#TypeCheckWithTypeOf)]

## <a name="operator-overloadability"></a><span data-ttu-id="efa42-162">Capacité de surcharge de l’opérateur</span><span class="sxs-lookup"><span data-stu-id="efa42-162">Operator overloadability</span></span>

<span data-ttu-id="efa42-163">Les `is` `as` opérateurs, et `typeof` ne peuvent pas être surchargés.</span><span class="sxs-lookup"><span data-stu-id="efa42-163">The `is`, `as`, and `typeof` operators cannot be overloaded.</span></span>

<span data-ttu-id="efa42-164">Un type défini par l’utilisateur ne peut pas surcharger l’opérateur `()`, mais vous pouvez définir des conversions de type personnalisées qui peuvent être effectuées par une expression cast.</span><span class="sxs-lookup"><span data-stu-id="efa42-164">A user-defined type cannot overload the `()` operator, but can define custom type conversions that can be performed by a cast expression.</span></span> <span data-ttu-id="efa42-165">Pour plus d’informations, consultez [Opérateurs de conversion définie par l’utilisateur](user-defined-conversion-operators.md).</span><span class="sxs-lookup"><span data-stu-id="efa42-165">For more information, see [User-defined conversion operators](user-defined-conversion-operators.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="efa42-166">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="efa42-166">C# language specification</span></span>

<span data-ttu-id="efa42-167">Pour plus d’informations, consultez les sections suivantes de la [spécification du langage C#](~/_csharplang/spec/introduction.md) :</span><span class="sxs-lookup"><span data-stu-id="efa42-167">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="efa42-168">L’opérateur is</span><span class="sxs-lookup"><span data-stu-id="efa42-168">The is operator</span></span>](~/_csharplang/spec/expressions.md#the-is-operator)
- [<span data-ttu-id="efa42-169">L’opérateur as</span><span class="sxs-lookup"><span data-stu-id="efa42-169">The as operator</span></span>](~/_csharplang/spec/expressions.md#the-as-operator)
- [<span data-ttu-id="efa42-170">Expressions cast</span><span class="sxs-lookup"><span data-stu-id="efa42-170">Cast expressions</span></span>](~/_csharplang/spec/expressions.md#cast-expressions)
- [<span data-ttu-id="efa42-171">Opérateur typeof</span><span class="sxs-lookup"><span data-stu-id="efa42-171">The typeof operator</span></span>](~/_csharplang/spec/expressions.md#the-typeof-operator)

## <a name="see-also"></a><span data-ttu-id="efa42-172">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="efa42-172">See also</span></span>

- [<span data-ttu-id="efa42-173">Informations de référence sur C#</span><span class="sxs-lookup"><span data-stu-id="efa42-173">C# reference</span></span>](../index.md)
- [<span data-ttu-id="efa42-174">Opérateurs et expressions C#</span><span class="sxs-lookup"><span data-stu-id="efa42-174">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="efa42-175">Comment effectuer un cast en toute sécurité à l’aide de critères spéciaux et des opérateurs is et As</span><span class="sxs-lookup"><span data-stu-id="efa42-175">How to safely cast by using pattern matching and the is and as operators</span></span>](../../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md)
- [<span data-ttu-id="efa42-176">Génériques en .NET</span><span class="sxs-lookup"><span data-stu-id="efa42-176">Generics in .NET</span></span>](../../../standard/generics/index.md)
