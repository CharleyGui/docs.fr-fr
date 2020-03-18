---
title: Opérateurs de test et de cast de type - Référence C#
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
ms.openlocfilehash: 037ddc8eeda418b2e4858ab98be6cd362ca0e1e2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399468"
---
# <a name="type-testing-and-cast-operators-c-reference"></a><span data-ttu-id="a072d-103">Opérateurs de test et de cast de type (Référence C#)</span><span class="sxs-lookup"><span data-stu-id="a072d-103">Type-testing and cast operators (C# reference)</span></span>

<span data-ttu-id="a072d-104">Vous pouvez utiliser les opérateurs suivants pour effectuer la vérification du type ou la conversion de type :</span><span class="sxs-lookup"><span data-stu-id="a072d-104">You can use the following operators to perform type checking or type conversion:</span></span>

- <span data-ttu-id="a072d-105">[Opérateur is](#is-operator) : pour vérifier si le type de runtime d’une expression est compatible avec un type donné</span><span class="sxs-lookup"><span data-stu-id="a072d-105">[is operator](#is-operator): to check if the runtime type of an expression is compatible with a given type</span></span>
- <span data-ttu-id="a072d-106">[Opérateur as](#as-operator) : pour convertir explicitement une expression en un type donné si son type de runtime est compatible avec ce type</span><span class="sxs-lookup"><span data-stu-id="a072d-106">[as operator](#as-operator): to explicitly convert an expression to a given type if its runtime type is compatible with that type</span></span>
- <span data-ttu-id="a072d-107">[Opérateur cast ()](#cast-operator-) : pour effectuer une conversion explicite</span><span class="sxs-lookup"><span data-stu-id="a072d-107">[cast operator ()](#cast-operator-): to perform an explicit conversion</span></span>
- <span data-ttu-id="a072d-108">[Opérateur typeof](#typeof-operator) : pour obtenir l’instance de <xref:System.Type?displayProperty=nameWithType> pour un type</span><span class="sxs-lookup"><span data-stu-id="a072d-108">[typeof operator](#typeof-operator): to obtain the <xref:System.Type?displayProperty=nameWithType> instance for a type</span></span>

## <a name="is-operator"></a><span data-ttu-id="a072d-109">Opérateur is</span><span class="sxs-lookup"><span data-stu-id="a072d-109">is operator</span></span>

<span data-ttu-id="a072d-110">L’opérateur `is` vérifie si le type de runtime du résultat d’une expression est compatible avec un type donné.</span><span class="sxs-lookup"><span data-stu-id="a072d-110">The `is` operator checks if the runtime type of an expression result is compatible with a given type.</span></span> <span data-ttu-id="a072d-111">En commençant par le C 7.0, l’opérateur `is` teste également un résultat d’expression par rapport à un modèle.</span><span class="sxs-lookup"><span data-stu-id="a072d-111">Beginning with C# 7.0, the `is` operator also tests an expression result against a pattern.</span></span>

<span data-ttu-id="a072d-112">L’expression avec l’opérateur de test de type `is` a la forme suivante</span><span class="sxs-lookup"><span data-stu-id="a072d-112">The expression with the type-testing `is` operator has the following form</span></span>

```csharp
E is T
```

<span data-ttu-id="a072d-113">où `E` est une expression qui retourne une valeur et `T` est le nom d’un type ou un d’un paramètre de type.</span><span class="sxs-lookup"><span data-stu-id="a072d-113">where `E` is an expression that returns a value and `T` is the name of a type or a type parameter.</span></span> <span data-ttu-id="a072d-114">`E` ne peut pas être une méthode anonyme ou une expression lambda.</span><span class="sxs-lookup"><span data-stu-id="a072d-114">`E` cannot be an anonymous method or a lambda expression.</span></span>

<span data-ttu-id="a072d-115">L’expression `E is T` retourne `true` si le résultat de `E` n’est pas null et peut être converti en type `T` par une conversion de référence, une conversion boxing ou une conversion unboxing ; sinon, elle retourne `false`.</span><span class="sxs-lookup"><span data-stu-id="a072d-115">The `E is T` expression returns `true` if the result of `E` is non-null and can be converted to type `T` by a reference conversion, a boxing conversion, or an unboxing conversion; otherwise, it returns `false`.</span></span> <span data-ttu-id="a072d-116">L’opérateur `is` ne considère pas les conversions définies par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="a072d-116">The `is` operator doesn't consider user-defined conversions.</span></span>

<span data-ttu-id="a072d-117">L’exemple suivant montre que l’opérateur `is` retourne `true` si le type de runtime d’une expression dérive d’un type donné, autrement dit, s’il existe une conversion de référence entre les types :</span><span class="sxs-lookup"><span data-stu-id="a072d-117">The following example demonstrates that the `is` operator returns `true` if the runtime type of an expression result derives from a given type, that is, there exists a reference conversion between types:</span></span>

[!code-csharp[is with reference conversion](snippets/TypeTestingAndConversionOperators.cs#IsWithReferenceConversion)]

<span data-ttu-id="a072d-118">L’exemple suivant `is` montre que l’opérateur prend en compte les conversions de boxe et de déballage mais ne considère pas les [conversions numériques](../builtin-types/numeric-conversions.md):</span><span class="sxs-lookup"><span data-stu-id="a072d-118">The next example shows that the `is` operator takes into account boxing and unboxing conversions but doesn't consider [numeric conversions](../builtin-types/numeric-conversions.md):</span></span>

[!code-csharp-interactive[is with int](snippets/TypeTestingAndConversionOperators.cs#IsWithInt)]

<span data-ttu-id="a072d-119">Pour plus d’informations sur les conversions C#, consultez le chapitre [Conversions](~/_csharplang/spec/conversions.md) de la [Spécification du langage C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="a072d-119">For information about C# conversions, see the [Conversions](~/_csharplang/spec/conversions.md) chapter of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

### <a name="type-testing-with-pattern-matching"></a><span data-ttu-id="a072d-120">Test de type avec des critères spéciaux</span><span class="sxs-lookup"><span data-stu-id="a072d-120">Type testing with pattern matching</span></span>

<span data-ttu-id="a072d-121">En commençant par le C 7.0, l’opérateur `is` teste également un résultat d’expression par rapport à un modèle.</span><span class="sxs-lookup"><span data-stu-id="a072d-121">Beginning with C# 7.0, the `is` operator also tests an expression result against a pattern.</span></span> <span data-ttu-id="a072d-122">En particulier, il prend en charge le modèle de type sous la forme suivante :</span><span class="sxs-lookup"><span data-stu-id="a072d-122">In particular, it supports the type pattern in the following form:</span></span>

```csharp
E is T v
```

<span data-ttu-id="a072d-123">où `E` est une expression qui retourne une valeur, `T` est le nom d’un type ou un d’un paramètre de type et `v` est une nouvelle variable locale de type `T`.</span><span class="sxs-lookup"><span data-stu-id="a072d-123">where `E` is an expression that returns a value, `T` is the name of a type or a type parameter, and `v` is a new local variable of type `T`.</span></span> <span data-ttu-id="a072d-124">Si le résultat de `E` n’est pas null et peut être converti en `T` par conversion de référence, boxing ou unboxing, l’expression `E is T v` retourne `true` et la valeur convertie du résultat de `E` est affectée à la variable `v`.</span><span class="sxs-lookup"><span data-stu-id="a072d-124">If the result of `E` is non-null and can be converted to `T` by a reference, boxing, or unboxing conversion, the `E is T v` expression returns `true` and the converted value of the result of `E` is assigned to variable `v`.</span></span>

<span data-ttu-id="a072d-125">L’exemple suivant illustre l’utilisation de l’opérateur `is` avec le modèle de type :</span><span class="sxs-lookup"><span data-stu-id="a072d-125">The following example demonstrates the usage of the `is` operator with the type pattern:</span></span>

[!code-csharp-interactive[is with type pattern](snippets/TypeTestingAndConversionOperators.cs#IsTypePattern)]

<span data-ttu-id="a072d-126">Pour plus d’informations sur le modèle de type et les autres modèles pris en charge, consultez [Critères spéciaux avec is](../keywords/is.md#pattern-matching-with-is).</span><span class="sxs-lookup"><span data-stu-id="a072d-126">For more information about the type pattern and other supported patterns, see [Pattern matching with is](../keywords/is.md#pattern-matching-with-is).</span></span>

## <a name="as-operator"></a><span data-ttu-id="a072d-127">opérateur as</span><span class="sxs-lookup"><span data-stu-id="a072d-127">as operator</span></span>

<span data-ttu-id="a072d-128">L’opérateur `as` convertit explicitement le résultat d’une expression en un type de valeur de référence ou nullable.</span><span class="sxs-lookup"><span data-stu-id="a072d-128">The `as` operator explicitly converts the result of an expression to a given reference or nullable value type.</span></span> <span data-ttu-id="a072d-129">Si la conversion n’est pas possible, l’opérateur `as` retourne `null`.</span><span class="sxs-lookup"><span data-stu-id="a072d-129">If the conversion is not possible, the `as` operator returns `null`.</span></span> <span data-ttu-id="a072d-130">Contrairement à [l’opérateur cast ()](#cast-operator-), l’opérateur `as` ne lève jamais d’exception.</span><span class="sxs-lookup"><span data-stu-id="a072d-130">Unlike the [cast operator ()](#cast-operator-), the `as` operator never throws an exception.</span></span>

<span data-ttu-id="a072d-131">L’expression de la forme</span><span class="sxs-lookup"><span data-stu-id="a072d-131">The expression of the form</span></span>

```csharp
E as T
```

<span data-ttu-id="a072d-132">où `E` est une expression qui retourne une valeur et `T` est le nom d’un type ou un d’un paramètre de type, avec le même résultat que</span><span class="sxs-lookup"><span data-stu-id="a072d-132">where `E` is an expression that returns a value and `T` is the name of a type or a type parameter, produces the same result as</span></span>

```csharp
E is T ? (T)(E) : (T)null
```

<span data-ttu-id="a072d-133">sauf que `E` n’est évalué qu’une seule fois.</span><span class="sxs-lookup"><span data-stu-id="a072d-133">except that `E` is only evaluated once.</span></span>

<span data-ttu-id="a072d-134">L’opérateur `as` envisage uniquement les conversions de référence, nullable, boxing et unboxing.</span><span class="sxs-lookup"><span data-stu-id="a072d-134">The `as` operator considers only reference, nullable, boxing, and unboxing conversions.</span></span> <span data-ttu-id="a072d-135">Vous ne pouvez pas utiliser l’opérateur `as` pour effectuer une conversion définie par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="a072d-135">You cannot use the `as` operator to perform a user-defined conversion.</span></span> <span data-ttu-id="a072d-136">Pour ce faire, utilisez [l’opérateur cast ()](#cast-operator-).</span><span class="sxs-lookup"><span data-stu-id="a072d-136">To do that, use the [cast operator ()](#cast-operator-).</span></span>

<span data-ttu-id="a072d-137">L’exemple suivant illustre l’utilisation de l’opérateur `as` :</span><span class="sxs-lookup"><span data-stu-id="a072d-137">The following example demonstrates the usage of the `as` operator:</span></span>

[!code-csharp-interactive[as operator](snippets/TypeTestingAndConversionOperators.cs#AsOperator)]

> [!NOTE]
> <span data-ttu-id="a072d-138">Comme le montre l’exemple précédent, vous devez comparer le résultat de l’expression `as` avec `null` pour vérifier si la conversion a réussi.</span><span class="sxs-lookup"><span data-stu-id="a072d-138">As the preceding example shows, you need to compare the result of the `as` expression with `null` to check if the conversion is successful.</span></span> <span data-ttu-id="a072d-139">En commençant par C 7.0, vous pouvez utiliser [l’opérateur de l’is](#type-testing-with-pattern-matching) à la fois pour tester si la conversion réussit et, si elle réussit, attribuer son résultat à une nouvelle variable.</span><span class="sxs-lookup"><span data-stu-id="a072d-139">Beginning with C# 7.0, you can use the [is operator](#type-testing-with-pattern-matching) both to test if the conversion succeeds and, if it succeeds, assign its result to a new variable.</span></span>

## <a name="cast-operator-"></a><span data-ttu-id="a072d-140">Opérateur de cast ()</span><span class="sxs-lookup"><span data-stu-id="a072d-140">Cast operator ()</span></span>

<span data-ttu-id="a072d-141">Une expression cast de la forme `(T)E` effectue une conversion explicite du résultat de l’expression `E` en type `T`.</span><span class="sxs-lookup"><span data-stu-id="a072d-141">A cast expression of the form `(T)E` performs an explicit conversion of the result of expression `E` to type `T`.</span></span> <span data-ttu-id="a072d-142">S’il n’existe aucune conversion explicite du type de `E` en type `T`, une erreur de compilation se produit.</span><span class="sxs-lookup"><span data-stu-id="a072d-142">If no explicit conversion exists from the type of `E` to type `T`, a compile-time error occurs.</span></span> <span data-ttu-id="a072d-143">Au moment de l’exécution, une conversion explicite peut ne pas réussir, et une expression cast peut lever une exception.</span><span class="sxs-lookup"><span data-stu-id="a072d-143">At run time, an explicit conversion might not succeed and a cast expression might throw an exception.</span></span>

<span data-ttu-id="a072d-144">L’exemple suivant montre des conversions numériques et de référence explicites :</span><span class="sxs-lookup"><span data-stu-id="a072d-144">The following example demonstrates explicit numeric and reference conversions:</span></span>

[!code-csharp-interactive[cast expression](snippets/TypeTestingAndConversionOperators.cs#Cast)]

<span data-ttu-id="a072d-145">Pour plus d’informations sur les conversions explicites prises en charge, consultez la section [Conversions explicites](~/_csharplang/spec/conversions.md#explicit-conversions) de la [Spécification du langage C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="a072d-145">For information about supported explicit conversions, see the [Explicit conversions](~/_csharplang/spec/conversions.md#explicit-conversions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span> <span data-ttu-id="a072d-146">Pour plus d’informations sur la façon de définir une conversion de type explicite ou implicite personnalisée, consultez [Opérateurs de conversion définie par l’utilisateur](user-defined-conversion-operators.md).</span><span class="sxs-lookup"><span data-stu-id="a072d-146">For information about how to define a custom explicit or implicit type conversion, see [User-defined conversion operators](user-defined-conversion-operators.md).</span></span>

### <a name="other-usages-of-"></a><span data-ttu-id="a072d-147">Autres utilisations de ()</span><span class="sxs-lookup"><span data-stu-id="a072d-147">Other usages of ()</span></span>

<span data-ttu-id="a072d-148">Vous pouvez aussi utiliser des parenthèses pour [appeler une méthode ou un délégué](member-access-operators.md#invocation-operator-).</span><span class="sxs-lookup"><span data-stu-id="a072d-148">You also use parentheses to [call a method or invoke a delegate](member-access-operators.md#invocation-operator-).</span></span>

<span data-ttu-id="a072d-149">Une autre utilisation des parenthèses est d’ajuster l’ordre dans lequel évaluer les opérations dans une expression.</span><span class="sxs-lookup"><span data-stu-id="a072d-149">Other use of parentheses is to adjust the order in which to evaluate operations in an expression.</span></span> <span data-ttu-id="a072d-150">Pour plus d’informations, consultez [Opérateurs C#](index.md).</span><span class="sxs-lookup"><span data-stu-id="a072d-150">For more information, see [C# operators](index.md).</span></span>

## <a name="typeof-operator"></a><span data-ttu-id="a072d-151">Opérateur typeof</span><span class="sxs-lookup"><span data-stu-id="a072d-151">typeof operator</span></span>

<span data-ttu-id="a072d-152">L’opérateur `typeof` obtient l’instance <xref:System.Type?displayProperty=nameWithType> pour un type.</span><span class="sxs-lookup"><span data-stu-id="a072d-152">The `typeof` operator obtains the <xref:System.Type?displayProperty=nameWithType> instance for a type.</span></span> <span data-ttu-id="a072d-153">L’argument de l’opérateur `typeof` doit avoir le nom d’un type ou d’un paramètre de type, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="a072d-153">The argument to the `typeof` operator must be the name of a type or a type parameter, as the following example shows:</span></span>

[!code-csharp-interactive[typeof operator](snippets/TypeTestingAndConversionOperators.cs#TypeOf)]

<span data-ttu-id="a072d-154">Vous pouvez également utiliser l’opérateur `typeof` avec les types génériques indépendants.</span><span class="sxs-lookup"><span data-stu-id="a072d-154">You also can use the `typeof` operator with unbound generic types.</span></span> <span data-ttu-id="a072d-155">Le nom d’un type générique indépendant doit contenir le nombre approprié de virgules, à savoir une de moins que le nombre de paramètres de type.</span><span class="sxs-lookup"><span data-stu-id="a072d-155">The name of an unbound generic type must contain the appropriate number of commas, which is one less than the number of type parameters.</span></span> <span data-ttu-id="a072d-156">L’exemple suivant illustre l’utilisation de l’opérateur `typeof` avec un type générique indépendant :</span><span class="sxs-lookup"><span data-stu-id="a072d-156">The following example shows the usage of the `typeof` operator with an unbound generic type:</span></span>

[!code-csharp-interactive[typeof unbound generic](snippets/TypeTestingAndConversionOperators.cs#TypeOfUnboundGeneric)]

<span data-ttu-id="a072d-157">Une expression ne peut pas être un argument de l’opérateur `typeof`.</span><span class="sxs-lookup"><span data-stu-id="a072d-157">An expression cannot be an argument of the `typeof` operator.</span></span> <span data-ttu-id="a072d-158">Pour obtenir <xref:System.Type?displayProperty=nameWithType> l’exemple pour le type de <xref:System.Object.GetType%2A?displayProperty=nameWithType> temps d’exécution d’un résultat d’expression, utilisez la méthode.</span><span class="sxs-lookup"><span data-stu-id="a072d-158">To get the <xref:System.Type?displayProperty=nameWithType> instance for the runtime type of an expression result, use the <xref:System.Object.GetType%2A?displayProperty=nameWithType> method.</span></span>

### <a name="type-testing-with-the-typeof-operator"></a><span data-ttu-id="a072d-159">Test de type avec l’opérateur `typeof`</span><span class="sxs-lookup"><span data-stu-id="a072d-159">Type testing with the `typeof` operator</span></span>

<span data-ttu-id="a072d-160">Utilisez l’opérateur `typeof` pour vérifier si le type de runtime du résultat de l’expression correspond exactement à un type donné.</span><span class="sxs-lookup"><span data-stu-id="a072d-160">Use the `typeof` operator to check if the runtime type of the expression result exactly matches a given type.</span></span> <span data-ttu-id="a072d-161">L’exemple suivant illustre la différence entre la vérification des types effectuée avec l’opérateur `typeof`[l’opérateur is](#is-operator) :</span><span class="sxs-lookup"><span data-stu-id="a072d-161">The following example demonstrates the difference between type checking performed with the `typeof` operator and the [is operator](#is-operator):</span></span>

[!code-csharp[typeof vs is](snippets/TypeTestingAndConversionOperators.cs#TypeCheckWithTypeOf)]

## <a name="operator-overloadability"></a><span data-ttu-id="a072d-162">Capacité de surcharge de l’opérateur</span><span class="sxs-lookup"><span data-stu-id="a072d-162">Operator overloadability</span></span>

<span data-ttu-id="a072d-163">Le `is` `as`, `typeof` , et les opérateurs ne peuvent pas être surchargés.</span><span class="sxs-lookup"><span data-stu-id="a072d-163">The `is`, `as`, and `typeof` operators cannot be overloaded.</span></span>

<span data-ttu-id="a072d-164">Un type défini par l’utilisateur ne peut pas surcharger l’opérateur `()`, mais vous pouvez définir des conversions de type personnalisées qui peuvent être effectuées par une expression cast.</span><span class="sxs-lookup"><span data-stu-id="a072d-164">A user-defined type cannot overload the `()` operator, but can define custom type conversions that can be performed by a cast expression.</span></span> <span data-ttu-id="a072d-165">Pour plus d’informations, consultez [Opérateurs de conversion définie par l’utilisateur](user-defined-conversion-operators.md).</span><span class="sxs-lookup"><span data-stu-id="a072d-165">For more information, see [User-defined conversion operators](user-defined-conversion-operators.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="a072d-166">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="a072d-166">C# language specification</span></span>

<span data-ttu-id="a072d-167">Pour plus d’informations, consultez les sections suivantes de la [spécification du langage C#](~/_csharplang/spec/introduction.md) :</span><span class="sxs-lookup"><span data-stu-id="a072d-167">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="a072d-168">L’opérateur is</span><span class="sxs-lookup"><span data-stu-id="a072d-168">The is operator</span></span>](~/_csharplang/spec/expressions.md#the-is-operator)
- [<span data-ttu-id="a072d-169">L’opérateur as</span><span class="sxs-lookup"><span data-stu-id="a072d-169">The as operator</span></span>](~/_csharplang/spec/expressions.md#the-as-operator)
- [<span data-ttu-id="a072d-170">Expressions cast</span><span class="sxs-lookup"><span data-stu-id="a072d-170">Cast expressions</span></span>](~/_csharplang/spec/expressions.md#cast-expressions)
- [<span data-ttu-id="a072d-171">L’opérateur typeof</span><span class="sxs-lookup"><span data-stu-id="a072d-171">The typeof operator</span></span>](~/_csharplang/spec/expressions.md#the-typeof-operator)

## <a name="see-also"></a><span data-ttu-id="a072d-172">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a072d-172">See also</span></span>

- [<span data-ttu-id="a072d-173">Référence C#</span><span class="sxs-lookup"><span data-stu-id="a072d-173">C# reference</span></span>](../index.md)
- [<span data-ttu-id="a072d-174">Opérateurs CMD</span><span class="sxs-lookup"><span data-stu-id="a072d-174">C# operators</span></span>](index.md)
- [<span data-ttu-id="a072d-175">Comment lancer en toute sécurité en utilisant l’appariement des motifs et l’est et en tant qu’opérateurs</span><span class="sxs-lookup"><span data-stu-id="a072d-175">How to safely cast by using pattern matching and the is and as operators</span></span>](../../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md)
- [<span data-ttu-id="a072d-176">Génériques en .NET</span><span class="sxs-lookup"><span data-stu-id="a072d-176">Generics in .NET</span></span>](../../../standard/generics/index.md)
