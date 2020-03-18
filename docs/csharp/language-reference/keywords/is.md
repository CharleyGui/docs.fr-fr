---
title: is - Référence C#
ms.date: 06/21/2019
f1_keywords:
- is_CSharpKeyword
- is
helpviewer_keywords:
- is keyword [C#]
ms.assetid: bc62316a-d41f-4f90-8300-c6f4f0556e43
ms.openlocfilehash: e64b690482419963a92764b2c97a42dbb231fbfc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399636"
---
# <a name="is-c-reference"></a><span data-ttu-id="1c57f-102">is (référence C#)</span><span class="sxs-lookup"><span data-stu-id="1c57f-102">is (C# Reference)</span></span>

<span data-ttu-id="1c57f-103">L’opérateur `is` vérifie si le résultat d’une expression est compatible avec un type donné, ou (à compter de C# 7.0) teste une expression par rapport à un modèle.</span><span class="sxs-lookup"><span data-stu-id="1c57f-103">The `is` operator checks if the result of an expression is compatible with a given type, or (starting with C# 7.0) tests an expression against a pattern.</span></span> <span data-ttu-id="1c57f-104">Pour plus d’informations sur l’opérateur de test de type `is`, consultez la section [Opérateur is](../operators/type-testing-and-cast.md#is-operator) de l’article [Opérateurs de test et de cast de type](../operators/type-testing-and-cast.md).</span><span class="sxs-lookup"><span data-stu-id="1c57f-104">For information about the type-testing `is` operator see the [is operator](../operators/type-testing-and-cast.md#is-operator) section of the [Type-testing and cast operators](../operators/type-testing-and-cast.md) article.</span></span>

## <a name="pattern-matching-with-is"></a><span data-ttu-id="1c57f-105">Utilisation des critères spéciaux avec `is`</span><span class="sxs-lookup"><span data-stu-id="1c57f-105">Pattern matching with `is`</span></span>

<span data-ttu-id="1c57f-106">À compter de C# 7.0, les instructions `is` et [switch](switch.md) prennent en charge les critères spéciaux.</span><span class="sxs-lookup"><span data-stu-id="1c57f-106">Starting with C# 7.0, the `is` and [switch](switch.md) statements support pattern matching.</span></span> <span data-ttu-id="1c57f-107">Le mot clé `is` prend en charge les modèles suivants :</span><span class="sxs-lookup"><span data-stu-id="1c57f-107">The `is` keyword supports the following patterns:</span></span>

- <span data-ttu-id="1c57f-108">[Modèle de type](#type-pattern), qui permet de tester si une expression peut être convertie en un type spécifié et, si tel est le cas, caste l’expression en une variable de ce type.</span><span class="sxs-lookup"><span data-stu-id="1c57f-108">[Type pattern](#type-pattern), which tests whether an expression can be converted to a specified type and, if it can be, casts it to a variable of that type.</span></span>

- <span data-ttu-id="1c57f-109">[Modèle de constante](#constant-pattern) : teste si une expression correspond à une valeur de constante spécifiée.</span><span class="sxs-lookup"><span data-stu-id="1c57f-109">[Constant pattern](#constant-pattern), which tests whether an expression evaluates to a specified constant value.</span></span>

- <span data-ttu-id="1c57f-110">[Modèle de variable](#var-pattern) : correspondance qui réussit toujours et lie la valeur d’une expression à une variable locale.</span><span class="sxs-lookup"><span data-stu-id="1c57f-110">[var pattern](#var-pattern), a match that always succeeds and binds the value of an expression to a new local variable.</span></span>

### <a name="type-pattern"></a><span data-ttu-id="1c57f-111">Modèle de type</span><span class="sxs-lookup"><span data-stu-id="1c57f-111">Type pattern</span></span>

<span data-ttu-id="1c57f-112">Lorsque vous utilisez le modèle de type pour rechercher des critères spéciaux, `is` permet de tester si une expression peut être convertie en un type spécifié et, si tel est le cas, effectuer un cast de l’expression en une variable de ce type.</span><span class="sxs-lookup"><span data-stu-id="1c57f-112">When using the type pattern to perform pattern matching, `is` tests whether an expression can be converted to a specified type and, if it can be, casts it to a variable of that type.</span></span> <span data-ttu-id="1c57f-113">Il s’agit d’une extension simple de l’instruction `is` qui permet une évaluation et une conversion de type concises.</span><span class="sxs-lookup"><span data-stu-id="1c57f-113">It's a straightforward extension of the `is` statement that enables concise type evaluation and conversion.</span></span> <span data-ttu-id="1c57f-114">La forme générale du modèle de type `is` est la suivante :</span><span class="sxs-lookup"><span data-stu-id="1c57f-114">The general form of the `is` type pattern is:</span></span>

```csharp
   expr is type varname
```

<span data-ttu-id="1c57f-115">Lorsque *l’expr* est une expression qui évalue à un exemple d’un certain type, le *type* est le nom du type auquel le résultat de *l’expr* doit être converti, et *varname* est l’objet auquel le résultat de l’expr est converti si le *expr* `is` test est `true`.</span><span class="sxs-lookup"><span data-stu-id="1c57f-115">Where *expr* is an expression that evaluates to an instance of some type, *type* is the name of the type to which the result of *expr* is to be converted, and *varname* is the object to which the result of *expr* is converted if the `is` test is `true`.</span></span>

<span data-ttu-id="1c57f-116">L’expression `is` est `true` si *expr* n’est pas `null` et que l’une des conditions suivantes est remplie :</span><span class="sxs-lookup"><span data-stu-id="1c57f-116">The `is` expression is `true` if *expr* isn't `null`, and any of the following is true:</span></span>

- <span data-ttu-id="1c57f-117">*expr* est une instance du même type que *type*.</span><span class="sxs-lookup"><span data-stu-id="1c57f-117">*expr* is an instance of the same type as *type*.</span></span>

- <span data-ttu-id="1c57f-118">*expr* est une instance d’un type qui dérive de *type*.</span><span class="sxs-lookup"><span data-stu-id="1c57f-118">*expr* is an instance of a type that derives from *type*.</span></span> <span data-ttu-id="1c57f-119">En d’autres termes, le résultat de *expr* peut être upcasté en une instance de *type*.</span><span class="sxs-lookup"><span data-stu-id="1c57f-119">In other words, the result of *expr* can be upcast to an instance of *type*.</span></span>

- <span data-ttu-id="1c57f-120">*expr* a un type au moment de la compilation qui est une classe de base de *type* et *expr* a un type au moment de l’exécution égal à *type* ou dérivé de *type*.</span><span class="sxs-lookup"><span data-stu-id="1c57f-120">*expr* has a compile-time type that is a base class of *type*, and *expr* has a runtime type that is *type* or is derived from *type*.</span></span> <span data-ttu-id="1c57f-121">Le *type au moment de la compilation* d’une variable est le type de la variable, tel qu’il est défini dans sa déclaration.</span><span class="sxs-lookup"><span data-stu-id="1c57f-121">The *compile-time type* of a variable is the variable's type as defined in its declaration.</span></span> <span data-ttu-id="1c57f-122">Le *type au moment de l’exécution* d’une variable est le type de l’instance qui est assignée à cette variable.</span><span class="sxs-lookup"><span data-stu-id="1c57f-122">The *runtime type* of a variable is the type of the instance that is assigned to that variable.</span></span>

- <span data-ttu-id="1c57f-123">*expr* est une instance d’un type qui implémente l’interface *type*.</span><span class="sxs-lookup"><span data-stu-id="1c57f-123">*expr* is an instance of a type that implements the *type* interface.</span></span>

<span data-ttu-id="1c57f-124">À compter de C# 7.1, *expr* peut avoir un type à la compilation défini par un paramètre de type générique et ses contraintes.</span><span class="sxs-lookup"><span data-stu-id="1c57f-124">Beginning with C# 7.1, *expr* may have a compile-time type defined by a generic type parameter and its constraints.</span></span>

<span data-ttu-id="1c57f-125">Si *exp* est `true` et que `is` est utilisé avec une instruction `if`, *varname* est assigné dans l’instruction `if` uniquement.</span><span class="sxs-lookup"><span data-stu-id="1c57f-125">If *expr* is `true` and `is` is used with an `if` statement, *varname* is assigned within the `if` statement only.</span></span> <span data-ttu-id="1c57f-126">La portée de *varname* provient de l’expression `is` à la fin du bloc englobant l’instruction `if`.</span><span class="sxs-lookup"><span data-stu-id="1c57f-126">The scope of *varname* is from the `is` expression to the end of the block enclosing the `if` statement.</span></span> <span data-ttu-id="1c57f-127">L’utilisation de *varname* à tout autre emplacement génère une erreur de compilation liée à l’utilisation d’une variable qui n’a pas été attribuée.</span><span class="sxs-lookup"><span data-stu-id="1c57f-127">Using *varname* in any other location generates a compile-time error for use of a variable that has not been assigned.</span></span>

<span data-ttu-id="1c57f-128">L’exemple suivant utilise le modèle de type `is` pour fournir l’implémentation de la méthode <xref:System.IComparable.CompareTo(System.Object)?displayProperty=nameWithType> d’un type.</span><span class="sxs-lookup"><span data-stu-id="1c57f-128">The following example uses the `is` type pattern to provide the implementation of a type's <xref:System.IComparable.CompareTo(System.Object)?displayProperty=nameWithType> method.</span></span>

[!code-csharp[is#5](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern5.cs#5)]

<span data-ttu-id="1c57f-129">Sans critères spéciaux, ce code peut être écrit comme suit.</span><span class="sxs-lookup"><span data-stu-id="1c57f-129">Without pattern matching, this code might be written as follows.</span></span> <span data-ttu-id="1c57f-130">L’utilisation de critères spéciaux de type génère un code lisible plus compact en éliminant la nécessité de tester si le résultat d’une conversion est un `null`.</span><span class="sxs-lookup"><span data-stu-id="1c57f-130">The use of type pattern matching produces more compact, readable code by eliminating the need to test whether the result of a conversion is a `null`.</span></span>  

[!code-csharp[is#6](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern6.cs#6)]

<span data-ttu-id="1c57f-131">Le modèle de type `is` génère également du code plus compact lorsqu’il détermine le type d’un type valeur.</span><span class="sxs-lookup"><span data-stu-id="1c57f-131">The `is` type pattern also produces more compact code when determining the type of a value type.</span></span> <span data-ttu-id="1c57f-132">L’exemple suivant utilise le modèle de type `is` pour déterminer si un objet est une instance `Person` ou `Dog` avant d’afficher la valeur d’une propriété appropriée.</span><span class="sxs-lookup"><span data-stu-id="1c57f-132">The following example uses the `is` type pattern to determine whether an object is a `Person` or a `Dog` instance before displaying the value of an appropriate property.</span></span>

[!code-csharp[is#9](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern9.cs#9)]

<span data-ttu-id="1c57f-133">Le code équivalent sans critères spéciaux nécessite une attribution distincte comprenant un cast explicite.</span><span class="sxs-lookup"><span data-stu-id="1c57f-133">The equivalent code without pattern matching requires a separate assignment that includes an explicit cast.</span></span>

[!code-csharp[is#10](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern10.cs#10)]

### <a name="constant-pattern"></a><span data-ttu-id="1c57f-134">Modèle de constante</span><span class="sxs-lookup"><span data-stu-id="1c57f-134">Constant pattern</span></span>

<span data-ttu-id="1c57f-135">Lorsque vous utilisez des critères spéciaux avec le modèle de constante, `is` teste si une expression est égale à une constante spécifiée.</span><span class="sxs-lookup"><span data-stu-id="1c57f-135">When performing pattern matching with the constant pattern, `is` tests whether an expression equals a specified constant.</span></span> <span data-ttu-id="1c57f-136">Avec C# 6 et les versions antérieures, le modèle de constante est pris en charge par l’instruction [switch](switch.md).</span><span class="sxs-lookup"><span data-stu-id="1c57f-136">In C# 6 and earlier versions, the constant pattern is supported by the [switch](switch.md) statement.</span></span> <span data-ttu-id="1c57f-137">À compter de C# 7.0, il est également pris en charge par l’instruction `is`.</span><span class="sxs-lookup"><span data-stu-id="1c57f-137">Starting with C# 7.0, it's supported by the `is` statement as well.</span></span> <span data-ttu-id="1c57f-138">Sa syntaxe est la suivante :</span><span class="sxs-lookup"><span data-stu-id="1c57f-138">Its syntax is:</span></span>

```csharp
   expr is constant
```

<span data-ttu-id="1c57f-139">où *expr* est l’expression à évaluer, et où *constant* est la valeur à tester.</span><span class="sxs-lookup"><span data-stu-id="1c57f-139">where *expr* is the expression to evaluate, and *constant* is the value to test for.</span></span> <span data-ttu-id="1c57f-140">*constant* peut correspondre à l’une des expressions constantes suivantes :</span><span class="sxs-lookup"><span data-stu-id="1c57f-140">*constant* can be any of the following constant expressions:</span></span>

- <span data-ttu-id="1c57f-141">Une valeur littérale</span><span class="sxs-lookup"><span data-stu-id="1c57f-141">A literal value.</span></span>

- <span data-ttu-id="1c57f-142">Le nom d’une variable `const` déclarée</span><span class="sxs-lookup"><span data-stu-id="1c57f-142">The name of a declared `const` variable.</span></span>

- <span data-ttu-id="1c57f-143">Une constante d’énumération</span><span class="sxs-lookup"><span data-stu-id="1c57f-143">An enumeration constant.</span></span>

<span data-ttu-id="1c57f-144">L’expression constante est évaluée de la manière suivante :</span><span class="sxs-lookup"><span data-stu-id="1c57f-144">The constant expression is evaluated as follows:</span></span>

- <span data-ttu-id="1c57f-145">Si *expr* et *constant* sont des types intégraux, l’opérateur d’égalité C# détermine si l’expression retourne `true` (autrement dit, si `expr == constant`).</span><span class="sxs-lookup"><span data-stu-id="1c57f-145">If *expr* and *constant* are integral types, the C# equality operator determines whether the expression returns `true` (that is, whether `expr == constant`).</span></span>

- <span data-ttu-id="1c57f-146">Sinon, la valeur de l’expression est déterminée par un appel à la méthode statique [Object.Equals(expr, constant)](xref:System.Object.Equals(System.Object,System.Object)).</span><span class="sxs-lookup"><span data-stu-id="1c57f-146">Otherwise, the value of the expression is determined by a call to the static [Object.Equals(expr, constant)](xref:System.Object.Equals(System.Object,System.Object)) method.</span></span>  

<span data-ttu-id="1c57f-147">L’exemple suivant combine le modèle de type et le modèle de constante pour tester si un objet est une instance `Dice` et, si c’est le cas, pour déterminer si la valeur obtenue après un lancer de dés est de 6.</span><span class="sxs-lookup"><span data-stu-id="1c57f-147">The following example combines the type and constant patterns to test whether an object is a `Dice` instance and, if it is, to determine whether the value of a dice roll is 6.</span></span>

[!code-csharp[is#7](../../../../samples/snippets/csharp/language-reference/keywords/is/is-const-pattern7.cs#7)]

<span data-ttu-id="1c57f-148">La vérification de `null` peut être effectuée à l’aide du modèle de constante.</span><span class="sxs-lookup"><span data-stu-id="1c57f-148">Checking for `null` can be performed using the constant pattern.</span></span> <span data-ttu-id="1c57f-149">Le mot clé `null` est pris en charge par l’instruction `is`.</span><span class="sxs-lookup"><span data-stu-id="1c57f-149">The `null` keyword is supported by the `is` statement.</span></span> <span data-ttu-id="1c57f-150">Sa syntaxe est la suivante :</span><span class="sxs-lookup"><span data-stu-id="1c57f-150">Its syntax is:</span></span>

```csharp
   expr is null
```

<span data-ttu-id="1c57f-151">L’exemple suivant illustre une comparaison des vérifications de `null` :</span><span class="sxs-lookup"><span data-stu-id="1c57f-151">The following example shows a comparison of `null` checks:</span></span>

[!code-csharp[is#11](../../../../samples/snippets/csharp/language-reference/keywords/is/is-const-pattern11.cs#11)]

### <a name="var-pattern"></a><span data-ttu-id="1c57f-152">Modèle de variable</span><span class="sxs-lookup"><span data-stu-id="1c57f-152">var pattern</span></span>

<span data-ttu-id="1c57f-153">Un modèle correspondant `var` au modèle réussit toujours.</span><span class="sxs-lookup"><span data-stu-id="1c57f-153">A pattern match with the `var` pattern always succeeds.</span></span> <span data-ttu-id="1c57f-154">Sa syntaxe est la suivante :</span><span class="sxs-lookup"><span data-stu-id="1c57f-154">Its syntax is:</span></span>

```csharp
   expr is var varname
```

<span data-ttu-id="1c57f-155">Lorsque la valeur de *l’expr* est toujours attribuée à une variable locale nommée *varname*.</span><span class="sxs-lookup"><span data-stu-id="1c57f-155">Where the value of *expr* is always assigned to a local variable named *varname*.</span></span> <span data-ttu-id="1c57f-156">*varname* est une variable du même type que le type de compilation-temps *d’expr*.</span><span class="sxs-lookup"><span data-stu-id="1c57f-156">*varname* is a variable of the same type as the compile-time type of *expr*.</span></span>

<span data-ttu-id="1c57f-157">Si *expr* évalue `null`à `is` , `true` l’expression produit et attribue `null` à *varname*.</span><span class="sxs-lookup"><span data-stu-id="1c57f-157">If *expr* evaluates to `null`, the `is` expression produces `true` and assigns `null` to *varname*.</span></span> <span data-ttu-id="1c57f-158">Le modèle var est l’une `true` des `null` rares utilisations de `is` celui produit pour une valeur.</span><span class="sxs-lookup"><span data-stu-id="1c57f-158">The var pattern is one of the few uses of `is` that produces `true` for a `null` value.</span></span>

<span data-ttu-id="1c57f-159">Vous pouvez `var` utiliser le modèle pour créer une variable temporaire dans une expression Boolean, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="1c57f-159">You can use the `var` pattern to create a temporary variable within a Boolean expression, as the following example shows:</span></span>

[!code-csharp[is#8](../../../../samples/snippets/csharp/language-reference/keywords/is/is-var-pattern8.cs#8)]

<span data-ttu-id="1c57f-160">Dans l’exemple précédent, la variable temporaire est utilisée pour stocker le résultat d’une opération coûteuse.</span><span class="sxs-lookup"><span data-stu-id="1c57f-160">In the preceding example, the temporary variable is used to store the result of an expensive operation.</span></span> <span data-ttu-id="1c57f-161">La variable peut ensuite être utilisée plusieurs fois.</span><span class="sxs-lookup"><span data-stu-id="1c57f-161">The variable can then be used multiple times.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="1c57f-162">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="1c57f-162">C# language specification</span></span>
  
<span data-ttu-id="1c57f-163">Pour plus d’informations, consultez la section [L’opérateur is](~/_csharplang/spec/expressions.md#the-is-operator) de la [Specification du langage C#](~/_csharplang/spec/introduction.md) et les propositions de langage C# suivantes :</span><span class="sxs-lookup"><span data-stu-id="1c57f-163">For more information, see [The is operator](~/_csharplang/spec/expressions.md#the-is-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md) and the following C# language proposals:</span></span>

- [<span data-ttu-id="1c57f-164">Critères spéciaux</span><span class="sxs-lookup"><span data-stu-id="1c57f-164">Pattern matching</span></span>](~/_csharplang/proposals/csharp-7.0/pattern-matching.md)
- [<span data-ttu-id="1c57f-165">Critères spéciaux avec génériques</span><span class="sxs-lookup"><span data-stu-id="1c57f-165">Pattern matching with generics</span></span>](~/_csharplang/proposals/csharp-7.1/generics-pattern-match.md)
  
## <a name="see-also"></a><span data-ttu-id="1c57f-166">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1c57f-166">See also</span></span>

- [<span data-ttu-id="1c57f-167">Référence C#</span><span class="sxs-lookup"><span data-stu-id="1c57f-167">C# reference</span></span>](../index.md)
- [<span data-ttu-id="1c57f-168">Mots-clés CMD</span><span class="sxs-lookup"><span data-stu-id="1c57f-168">C# keywords</span></span>](index.md)
- [<span data-ttu-id="1c57f-169">Opérateurs de conversion et de test de type</span><span class="sxs-lookup"><span data-stu-id="1c57f-169">Type-testing and cast operators</span></span>](../operators/type-testing-and-cast.md)
