---
description: 'Opérateur ?: - Référence C#'
title: 'Opérateur ?: - Référence C#'
ms.date: 09/17/2020
f1_keywords:
- ?:_CSharpKeyword
- ?_CSharpKeyword
- :_CSharpKeyword
helpviewer_keywords:
- '?: operator [C#]'
- conditional operator (?:) [C#]
ms.assetid: e83a17f1-7500-48ba-8bee-2fbc4c847af4
ms.openlocfilehash: b6add045983619169bed0cd9f32eb27dba0a0338
ms.sourcegitcommit: a8730298170b8d96b4272e0c3dfc9819c606947b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90738877"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="7a854-103">Opérateur ?: (référence C#)</span><span class="sxs-lookup"><span data-stu-id="7a854-103">?: operator (C# reference)</span></span>

<span data-ttu-id="7a854-104">L’opérateur conditionnel `?:` , également appelé opérateur conditionnel ternaire, évalue une expression booléenne et retourne le résultat de l’une des deux expressions, selon que l’expression booléenne a pour valeur `true` ou `false` .</span><span class="sxs-lookup"><span data-stu-id="7a854-104">The conditional operator `?:`, also known as the ternary conditional operator, evaluates a Boolean expression and returns the result of one of the two expressions, depending on whether the Boolean expression evaluates to `true` or `false`.</span></span>

<span data-ttu-id="7a854-105">Voici la syntaxe de l'opérateur conditionnel :</span><span class="sxs-lookup"><span data-stu-id="7a854-105">The syntax for the conditional operator is as follows:</span></span>

```csharp
condition ? consequent : alternative
```

<span data-ttu-id="7a854-106">L'expression `condition` doit donner `true` ou `false`.</span><span class="sxs-lookup"><span data-stu-id="7a854-106">The `condition` expression must evaluate to `true` or `false`.</span></span> <span data-ttu-id="7a854-107">Si `condition` prend la valeur `true`, l’expression `consequent` est évaluée et son résultat devient le résultat de l’opération.</span><span class="sxs-lookup"><span data-stu-id="7a854-107">If `condition` evaluates to `true`, the `consequent` expression is evaluated, and its result becomes the result of the operation.</span></span> <span data-ttu-id="7a854-108">Si `condition` prend la valeur `false`, l’expression `alternative` est évaluée et son résultat devient le résultat de l’opération.</span><span class="sxs-lookup"><span data-stu-id="7a854-108">If `condition` evaluates to `false`, the `alternative` expression is evaluated, and its result becomes the result of the operation.</span></span> <span data-ttu-id="7a854-109">Soit `consequent`, soit `alternative` est évaluée.</span><span class="sxs-lookup"><span data-stu-id="7a854-109">Only `consequent` or `alternative` is evaluated.</span></span>

<span data-ttu-id="7a854-110">À compter de C# 9,0, les expressions conditionnelles sont de type cible.</span><span class="sxs-lookup"><span data-stu-id="7a854-110">Beginning with C# 9.0, conditional expressions are target-typed.</span></span> <span data-ttu-id="7a854-111">Autrement dit, si un type cible d’une expression conditionnelle est connu, les types de `consequent` et `alternative` doivent être implicitement convertibles en type cible, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="7a854-111">That is, if a target type of a conditional expression is known, the types of `consequent` and `alternative` must be implicitly convertible to the target type, as the following example shows:</span></span>

[!code-csharp[target-typed conditional](snippets/shared/ConditionalOperator.cs#TargetTyped)]

<span data-ttu-id="7a854-112">Si le type cible d’une expression conditionnelle est inconnu (par exemple, lorsque vous utilisez le [`var`](../keywords/var.md) mot clé) ou en C# 8,0 et les versions antérieures, le type de `consequent` et `alternative` doit être identique ou il doit y avoir une conversion implicite d’un type à l’autre :</span><span class="sxs-lookup"><span data-stu-id="7a854-112">If a target type of a conditional expression is unknown (for example, when you use the [`var`](../keywords/var.md) keyword) or in C# 8.0 and earlier, the type of `consequent` and `alternative` must be the same or there must be an implicit conversion from one type to the other:</span></span>

[!code-csharp[not target-typed conditional](snippets/shared/ConditionalOperator.cs#NotTargetTyped)]

<span data-ttu-id="7a854-113">L’opérateur conditionnel est associatif à droite ; autrement dit, une expression de la forme :</span><span class="sxs-lookup"><span data-stu-id="7a854-113">The conditional operator is right-associative, that is, an expression of the form</span></span>

```csharp
a ? b : c ? d : e
```

<span data-ttu-id="7a854-114">est évaluée comme étant</span><span class="sxs-lookup"><span data-stu-id="7a854-114">is evaluated as</span></span>

```csharp
a ? b : (c ? d : e)
```

> [!TIP]
> <span data-ttu-id="7a854-115">Vous pouvez utiliser l’appareil mnémonique suivant pour vous souvenir du mode d’évaluation de l’opérateur conditionnel :</span><span class="sxs-lookup"><span data-stu-id="7a854-115">You can use the following mnemonic device to remember how the conditional operator is evaluated:</span></span>
>
> ```text
> is this condition true ? yes : no
> ```

<span data-ttu-id="7a854-116">L’exemple suivant illustre l’utilisation de l’opérateur conditionnel :</span><span class="sxs-lookup"><span data-stu-id="7a854-116">The following example demonstrates the usage of the conditional operator:</span></span>

[!code-csharp-interactive[non ref conditional](snippets/shared/ConditionalOperator.cs#ConditionalValue)]

## <a name="conditional-ref-expression"></a><span data-ttu-id="7a854-117">Expression ref conditionnelle</span><span class="sxs-lookup"><span data-stu-id="7a854-117">Conditional ref expression</span></span>

<span data-ttu-id="7a854-118">À compter de C# 7,2, une variable locale Ref [locale](../keywords/ref.md#ref-locals) ou [ref ReadOnly](../keywords/ref.md#ref-readonly-locals) peut être assignée de manière conditionnelle avec une expression Ref conditionnelle.</span><span class="sxs-lookup"><span data-stu-id="7a854-118">Beginning with C# 7.2, a [ref local](../keywords/ref.md#ref-locals) or [ref readonly local](../keywords/ref.md#ref-readonly-locals) variable can be assigned conditionally with a conditional ref expression.</span></span> <span data-ttu-id="7a854-119">Vous pouvez également utiliser une expression Ref conditionnelle comme [valeur de retour de référence](../keywords/ref.md#reference-return-values) ou comme [ `ref` argument de méthode](../keywords/ref.md#passing-an-argument-by-reference).</span><span class="sxs-lookup"><span data-stu-id="7a854-119">You can also use a conditional ref expression as a [reference return value](../keywords/ref.md#reference-return-values) or as a [`ref` method argument](../keywords/ref.md#passing-an-argument-by-reference).</span></span>

<span data-ttu-id="7a854-120">La syntaxe d’une expression Ref conditionnelle est la suivante :</span><span class="sxs-lookup"><span data-stu-id="7a854-120">The syntax for a conditional ref expression is as follows:</span></span>

```csharp
condition ? ref consequent : ref alternative
```

<span data-ttu-id="7a854-121">À l’instar de l’opérateur conditionnel d’origine, une expression Ref conditionnelle évalue uniquement l’une des deux expressions : `consequent` ou `alternative` .</span><span class="sxs-lookup"><span data-stu-id="7a854-121">Like the original conditional operator, a conditional ref expression evaluates only one of the two expressions: either `consequent` or `alternative`.</span></span>

<span data-ttu-id="7a854-122">Dans le cas d’une expression Ref conditionnelle, le type de `consequent` et `alternative` doit être identique.</span><span class="sxs-lookup"><span data-stu-id="7a854-122">In the case of a conditional ref expression, the type of `consequent` and `alternative` must be the same.</span></span> <span data-ttu-id="7a854-123">Les expressions Ref conditionnelles ne sont pas de type cible.</span><span class="sxs-lookup"><span data-stu-id="7a854-123">Conditional ref expressions are not target-typed.</span></span>

<span data-ttu-id="7a854-124">L’exemple suivant illustre l’utilisation d’une expression Ref conditionnelle :</span><span class="sxs-lookup"><span data-stu-id="7a854-124">The following example demonstrates the usage of a conditional ref expression:</span></span>

[!code-csharp-interactive[conditional ref](snippets/shared/ConditionalOperator.cs#ConditionalRef)]

## <a name="conditional-operator-and-an-ifelse-statement"></a><span data-ttu-id="7a854-125">Opérateur conditionnel et instruction `if..else`</span><span class="sxs-lookup"><span data-stu-id="7a854-125">Conditional operator and an `if..else` statement</span></span>

<span data-ttu-id="7a854-126">L’utilisation de l’opérateur conditionnel au lieu d’une instruction [if-else](../keywords/if-else.md) peut entraîner un code plus concis dans les cas où vous avez besoin de calculer une valeur de manière conditionnelle.</span><span class="sxs-lookup"><span data-stu-id="7a854-126">Use of the conditional operator instead of an [if-else](../keywords/if-else.md) statement might result in more concise code in cases when you need conditionally to compute a value.</span></span> <span data-ttu-id="7a854-127">L’exemple suivant montre deux façons de classer un entier comme négatif ou non :</span><span class="sxs-lookup"><span data-stu-id="7a854-127">The following example demonstrates two ways to classify an integer as negative or nonnegative:</span></span>

[!code-csharp[conditional and if-else](snippets/shared/ConditionalOperator.cs#CompareWithIf)]

## <a name="operator-overloadability"></a><span data-ttu-id="7a854-128">Capacité de surcharge de l’opérateur</span><span class="sxs-lookup"><span data-stu-id="7a854-128">Operator overloadability</span></span>

<span data-ttu-id="7a854-129">Un type défini par l’utilisateur ne peut pas surcharger l’opérateur conditionnel.</span><span class="sxs-lookup"><span data-stu-id="7a854-129">A user-defined type cannot overload the conditional operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="7a854-130">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="7a854-130">C# language specification</span></span>

<span data-ttu-id="7a854-131">Pour plus d’informations, voir la section [Opérateur conditionnel](~/_csharplang/spec/expressions.md#conditional-operator) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="7a854-131">For more information, see the [Conditional operator](~/_csharplang/spec/expressions.md#conditional-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="7a854-132">Pour plus d’informations sur les fonctionnalités ajoutées dans C# 7,2 et versions ultérieures, consultez les notes de proposition de fonctionnalités suivantes :</span><span class="sxs-lookup"><span data-stu-id="7a854-132">For more information about features added in C# 7.2 and later, see the following feature proposal notes:</span></span>

- [<span data-ttu-id="7a854-133">Expressions Ref conditionnelles (C# 7,2)</span><span class="sxs-lookup"><span data-stu-id="7a854-133">Conditional ref expressions (C# 7.2)</span></span>](~/_csharplang/proposals/csharp-7.2/conditional-ref.md)
- [<span data-ttu-id="7a854-134">Expression conditionnelle typée cible (C# 9,0)</span><span class="sxs-lookup"><span data-stu-id="7a854-134">Target-typed conditional expression (C# 9.0)</span></span>](~/_csharplang/proposals/csharp-9.0/target-typed-conditional-expression.md)

## <a name="see-also"></a><span data-ttu-id="7a854-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7a854-135">See also</span></span>

- [<span data-ttu-id="7a854-136">Informations de référence sur C#</span><span class="sxs-lookup"><span data-stu-id="7a854-136">C# reference</span></span>](../index.md)
- [<span data-ttu-id="7a854-137">Opérateurs et expressions C#</span><span class="sxs-lookup"><span data-stu-id="7a854-137">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="7a854-138">if-else, instruction</span><span class="sxs-lookup"><span data-stu-id="7a854-138">if-else statement</span></span>](../keywords/if-else.md)
- <span data-ttu-id="7a854-139">[Opérateurs ?. et ?[]](member-access-operators.md#null-conditional-operators--and-)</span><span class="sxs-lookup"><span data-stu-id="7a854-139">[?. and ?[] operators](member-access-operators.md#null-conditional-operators--and-)</span></span>
- [<span data-ttu-id="7a854-140">?? et ?? =, opérateurs</span><span class="sxs-lookup"><span data-stu-id="7a854-140">?? and ??= operators</span></span>](null-coalescing-operator.md)
- [<span data-ttu-id="7a854-141">ref, mot clé</span><span class="sxs-lookup"><span data-stu-id="7a854-141">ref keyword</span></span>](../keywords/ref.md)
