---
title: 'Opérateur ?: - Référence C#'
ms.date: 03/06/2020
f1_keywords:
- ?:_CSharpKeyword
- ?_CSharpKeyword
- :_CSharpKeyword
helpviewer_keywords:
- '?: operator [C#]'
- conditional operator (?:) [C#]
ms.assetid: e83a17f1-7500-48ba-8bee-2fbc4c847af4
ms.openlocfilehash: 1a17ba092d4228ba909c8774a2f7e15c2c50cfdc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399517"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="e56f5-102">Opérateur ?: (référence C#)</span><span class="sxs-lookup"><span data-stu-id="e56f5-102">?: operator (C# reference)</span></span>

<span data-ttu-id="e56f5-103">L’opérateur `?:`conditionnel , également connu sous le nom d’opérateur conditionnel ternaire, évalue une expression Boolean et `true` renvoie le résultat de l’une des deux expressions, selon que l’expression Boolean évalue ou `false`.</span><span class="sxs-lookup"><span data-stu-id="e56f5-103">The conditional operator `?:`, also known as the ternary conditional operator, evaluates a Boolean expression and returns the result of one of the two expressions, depending on whether the Boolean expression evaluates to `true` or `false`.</span></span>

<span data-ttu-id="e56f5-104">Voici la syntaxe de l'opérateur conditionnel :</span><span class="sxs-lookup"><span data-stu-id="e56f5-104">The syntax for the conditional operator is as follows:</span></span>

```csharp
condition ? consequent : alternative
```

<span data-ttu-id="e56f5-105">L'expression `condition` doit donner `true` ou `false`.</span><span class="sxs-lookup"><span data-stu-id="e56f5-105">The `condition` expression must evaluate to `true` or `false`.</span></span> <span data-ttu-id="e56f5-106">Si `condition` prend la valeur `true`, l’expression `consequent` est évaluée et son résultat devient le résultat de l’opération.</span><span class="sxs-lookup"><span data-stu-id="e56f5-106">If `condition` evaluates to `true`, the `consequent` expression is evaluated, and its result becomes the result of the operation.</span></span> <span data-ttu-id="e56f5-107">Si `condition` prend la valeur `false`, l’expression `alternative` est évaluée et son résultat devient le résultat de l’opération.</span><span class="sxs-lookup"><span data-stu-id="e56f5-107">If `condition` evaluates to `false`, the `alternative` expression is evaluated, and its result becomes the result of the operation.</span></span> <span data-ttu-id="e56f5-108">Soit `consequent`, soit `alternative` est évaluée.</span><span class="sxs-lookup"><span data-stu-id="e56f5-108">Only `consequent` or `alternative` is evaluated.</span></span>

<span data-ttu-id="e56f5-109">Il faut que `consequent` et `alternative` soient du même type ou bien qu’une conversion implicite existe d’un type à l’autre.</span><span class="sxs-lookup"><span data-stu-id="e56f5-109">The type of `consequent` and `alternative` must be the same, or there must be an implicit conversion from one type to the other.</span></span>

<span data-ttu-id="e56f5-110">L’opérateur conditionnel est associatif à droite ; autrement dit, une expression de la forme :</span><span class="sxs-lookup"><span data-stu-id="e56f5-110">The conditional operator is right-associative, that is, an expression of the form</span></span>

```csharp
a ? b : c ? d : e
```

<span data-ttu-id="e56f5-111">est évaluée comme étant</span><span class="sxs-lookup"><span data-stu-id="e56f5-111">is evaluated as</span></span>

```csharp
a ? b : (c ? d : e)
```

> [!TIP]
> <span data-ttu-id="e56f5-112">Vous pouvez utiliser l’appareil mnémonique suivant pour vous souvenir du mode d’évaluation de l’opérateur conditionnel :</span><span class="sxs-lookup"><span data-stu-id="e56f5-112">You can use the following mnemonic device to remember how the conditional operator is evaluated:</span></span>
>
> ```text
> is this condition true ? yes : no
> ```

<span data-ttu-id="e56f5-113">L’exemple suivant illustre l’utilisation de l’opérateur conditionnel :</span><span class="sxs-lookup"><span data-stu-id="e56f5-113">The following example demonstrates the usage of the conditional operator:</span></span>

[!code-csharp-interactive[non ref conditional](snippets/ConditionalOperator.cs#ConditionalValue)]

## <a name="conditional-ref-expression"></a><span data-ttu-id="e56f5-114">Expression ref conditionnelle</span><span class="sxs-lookup"><span data-stu-id="e56f5-114">Conditional ref expression</span></span>

<span data-ttu-id="e56f5-115">Commençant par C 7.2, une variable [locale ou réadsible d’arbitre](../keywords/ref.md#ref-locals) peut être assignée [conditionnellement](../keywords/ref.md#ref-readonly-locals) avec l’expression conditionnelle de l’arbitre.</span><span class="sxs-lookup"><span data-stu-id="e56f5-115">Beginning with C# 7.2, a [ref local](../keywords/ref.md#ref-locals) or [ref readonly local](../keywords/ref.md#ref-readonly-locals) variable can be assigned conditionally with the conditional ref expression.</span></span> <span data-ttu-id="e56f5-116">Vous pouvez également utiliser l’expression conditionnelle de ref comme valeur [de retour de référence](../keywords/ref.md#reference-return-values) ou comme argument [ `ref` de méthode.](../keywords/ref.md#passing-an-argument-by-reference)</span><span class="sxs-lookup"><span data-stu-id="e56f5-116">You can also use the conditional ref expression as a [reference return value](../keywords/ref.md#reference-return-values) or as a [`ref` method argument](../keywords/ref.md#passing-an-argument-by-reference).</span></span>

<span data-ttu-id="e56f5-117">Voici la syntaxe de l'expression ref conditionnelle :</span><span class="sxs-lookup"><span data-stu-id="e56f5-117">The syntax for the conditional ref expression is as follows:</span></span>

```csharp
condition ? ref consequent : ref alternative
```

<span data-ttu-id="e56f5-118">Comme l’opérateur conditionnel d’origine, l’expression ref conditionnelle n’évalue qu’une des deux expressions : soit `consequent`, soit `alternative`.</span><span class="sxs-lookup"><span data-stu-id="e56f5-118">Like the original conditional operator, the conditional ref expression evaluates only one of the two expressions: either `consequent` or `alternative`.</span></span>

<span data-ttu-id="e56f5-119">Dans le cas de l’expression ref conditionnelle, `consequent` et `alternative` doivent être du même type.</span><span class="sxs-lookup"><span data-stu-id="e56f5-119">In the case of the conditional ref expression, the type of `consequent` and `alternative` must be the same.</span></span>

<span data-ttu-id="e56f5-120">L’exemple suivant illustre l’utilisation de l’expression ref conditionnelle :</span><span class="sxs-lookup"><span data-stu-id="e56f5-120">The following example demonstrates the usage of the conditional ref expression:</span></span>

[!code-csharp-interactive[conditional ref](snippets/ConditionalOperator.cs#ConditionalRef)]

## <a name="conditional-operator-and-an-ifelse-statement"></a><span data-ttu-id="e56f5-121">Opérateur conditionnel et instruction `if..else`</span><span class="sxs-lookup"><span data-stu-id="e56f5-121">Conditional operator and an `if..else` statement</span></span>

<span data-ttu-id="e56f5-122">L’utilisation de l’opérateur conditionnel au lieu d’une déclaration [if-else](../keywords/if-else.md) peut entraîner un code plus concis dans les cas où vous avez besoin conditionnellement pour calculer une valeur.</span><span class="sxs-lookup"><span data-stu-id="e56f5-122">Use of the conditional operator instead of an [if-else](../keywords/if-else.md) statement might result in more concise code in cases when you need conditionally to compute a value.</span></span> <span data-ttu-id="e56f5-123">L’exemple suivant montre deux façons de classer un entier comme négatif ou non :</span><span class="sxs-lookup"><span data-stu-id="e56f5-123">The following example demonstrates two ways to classify an integer as negative or nonnegative:</span></span>

[!code-csharp[conditional and if-else](snippets/ConditionalOperator.cs#CompareWithIf)]

## <a name="operator-overloadability"></a><span data-ttu-id="e56f5-124">Capacité de surcharge de l’opérateur</span><span class="sxs-lookup"><span data-stu-id="e56f5-124">Operator overloadability</span></span>

<span data-ttu-id="e56f5-125">Un type défini par l’utilisateur ne peut pas surcharger l’opérateur conditionnel.</span><span class="sxs-lookup"><span data-stu-id="e56f5-125">A user-defined type cannot overload the conditional operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="e56f5-126">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="e56f5-126">C# language specification</span></span>

<span data-ttu-id="e56f5-127">Pour plus d’informations, voir la section [Opérateur conditionnel](~/_csharplang/spec/expressions.md#conditional-operator) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="e56f5-127">For more information, see the [Conditional operator](~/_csharplang/spec/expressions.md#conditional-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="e56f5-128">Pour plus d’informations sur l’expression de l’arbitre conditionnel, voir la [note de proposition de fonctionnalité](~/_csharplang/proposals/csharp-7.2/conditional-ref.md).</span><span class="sxs-lookup"><span data-stu-id="e56f5-128">For more information about the conditional ref expression, see the [feature proposal note](~/_csharplang/proposals/csharp-7.2/conditional-ref.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e56f5-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e56f5-129">See also</span></span>

- [<span data-ttu-id="e56f5-130">Référence C#</span><span class="sxs-lookup"><span data-stu-id="e56f5-130">C# reference</span></span>](../index.md)
- [<span data-ttu-id="e56f5-131">Opérateurs CMD</span><span class="sxs-lookup"><span data-stu-id="e56f5-131">C# operators</span></span>](index.md)
- [<span data-ttu-id="e56f5-132">if-else, instruction</span><span class="sxs-lookup"><span data-stu-id="e56f5-132">if-else statement</span></span>](../keywords/if-else.md)
- <span data-ttu-id="e56f5-133">[Opérateurs ?. et ?[]](member-access-operators.md#null-conditional-operators--and-)</span><span class="sxs-lookup"><span data-stu-id="e56f5-133">[?. and ?[] operators](member-access-operators.md#null-conditional-operators--and-)</span></span>
- [<span data-ttu-id="e56f5-134">?? Et?? - opérateurs</span><span class="sxs-lookup"><span data-stu-id="e56f5-134">?? and ??= operators</span></span>](null-coalescing-operator.md)
- [<span data-ttu-id="e56f5-135">ref, mot clé</span><span class="sxs-lookup"><span data-stu-id="e56f5-135">ref keyword</span></span>](../keywords/ref.md)
