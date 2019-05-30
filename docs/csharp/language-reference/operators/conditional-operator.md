---
title: '?: , opérateur - Référence C#'
ms.custom: seodec18
ms.date: 11/20/2018
f1_keywords:
- ?:_CSharpKeyword
- ?_CSharpKeyword
- :_CSharpKeyword
helpviewer_keywords:
- '?: operator [C#]'
- conditional operator (?:) [C#]
ms.assetid: e83a17f1-7500-48ba-8bee-2fbc4c847af4
ms.openlocfilehash: 58317c26f87034991c817d0d7221d810657ca332
ms.sourcegitcommit: 11deacc8ec9f229ab8ee3cd537515d4c2826515f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2019
ms.locfileid: "66003710"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="3c240-102">?: Opérateur (référence C#)</span><span class="sxs-lookup"><span data-stu-id="3c240-102">?: Operator (C# Reference)</span></span>

<span data-ttu-id="3c240-103">L’opérateur conditionnel `?:`, souvent appelé opérateur conditionnel ternaire, évalue une expression booléenne et retourne le résultat de l’évaluation d’une des deux expressions, selon que l’expression booléenne donne `true` ou `false`.</span><span class="sxs-lookup"><span data-stu-id="3c240-103">The conditional operator `?:`, commonly known as the ternary conditional operator, evaluates a Boolean expression, and returns the result of evaluating one of two expressions, depending on whether the Boolean expression evaluates to `true` or `false`.</span></span> <span data-ttu-id="3c240-104">À partir de C# 7.2, [l’expression ref conditionnelle](#conditional-ref-expression) retourne la référence au résultat d’une des deux expressions.</span><span class="sxs-lookup"><span data-stu-id="3c240-104">Beginning with C# 7.2, the [conditional ref expression](#conditional-ref-expression) returns the reference to the result of one of the two expressions.</span></span>

<span data-ttu-id="3c240-105">Voici la syntaxe de l'opérateur conditionnel :</span><span class="sxs-lookup"><span data-stu-id="3c240-105">The syntax for the conditional operator is as follows:</span></span>

```csharp
condition ? consequent : alternative
```

<span data-ttu-id="3c240-106">L'expression `condition` doit donner `true` ou `false`.</span><span class="sxs-lookup"><span data-stu-id="3c240-106">The `condition` expression must evaluate to `true` or `false`.</span></span> <span data-ttu-id="3c240-107">Si `condition` prend la valeur `true`, l’expression `consequent` est évaluée et son résultat devient le résultat de l’opération.</span><span class="sxs-lookup"><span data-stu-id="3c240-107">If `condition` evaluates to `true`, the `consequent` expression is evaluated, and its result becomes the result of the operation.</span></span> <span data-ttu-id="3c240-108">Si `condition` prend la valeur `false`, l’expression `alternative` est évaluée et son résultat devient le résultat de l’opération.</span><span class="sxs-lookup"><span data-stu-id="3c240-108">If `condition` evaluates to `false`, the `alternative` expression is evaluated, and its result becomes the result of the operation.</span></span> <span data-ttu-id="3c240-109">Soit `consequent`, soit `alternative` est évaluée.</span><span class="sxs-lookup"><span data-stu-id="3c240-109">Only `consequent` or `alternative` is evaluated.</span></span>

<span data-ttu-id="3c240-110">Il faut que `consequent` et `alternative` soient du même type ou bien qu’une conversion implicite existe d’un type à l’autre.</span><span class="sxs-lookup"><span data-stu-id="3c240-110">The type of `consequent` and `alternative` must be the same, or there must be an implicit conversion from one type to the other.</span></span>

<span data-ttu-id="3c240-111">L’opérateur conditionnel est associatif à droite ; autrement dit, une expression de la forme :</span><span class="sxs-lookup"><span data-stu-id="3c240-111">The conditional operator is right-associative, that is, an expression of the form</span></span>

```csharp
a ? b : c ? d : e
```

<span data-ttu-id="3c240-112">est évaluée comme étant</span><span class="sxs-lookup"><span data-stu-id="3c240-112">is evaluated as</span></span>

```csharp
a ? b : (c ? d : e)
```

> [!TIP]
> <span data-ttu-id="3c240-113">Vous pouvez utiliser l’appareil mnémonique suivant pour vous souvenir du mode d’évaluation de l’opérateur conditionnel :</span><span class="sxs-lookup"><span data-stu-id="3c240-113">You can use the following mnemonic device to remember how the conditional operator is evaluated:</span></span>
>
> ```text
> is this condition true ? yes : no
> ```

<span data-ttu-id="3c240-114">L’exemple suivant illustre l’utilisation de l’opérateur conditionnel :</span><span class="sxs-lookup"><span data-stu-id="3c240-114">The following example demonstrates the usage of the conditional operator:</span></span>

[!code-csharp[non ref conditional](~/samples/snippets/csharp/language-reference/operators/ConditionalExamples.cs#ConditionalValue)]

## <a name="conditional-ref-expression"></a><span data-ttu-id="3c240-115">Expression ref conditionnelle</span><span class="sxs-lookup"><span data-stu-id="3c240-115">Conditional ref expression</span></span>

<span data-ttu-id="3c240-116">À partir de C# 7.2, il est possible d’utiliser l’expression ref conditionnelle pour retourner la référence au résultat d’une des deux expressions.</span><span class="sxs-lookup"><span data-stu-id="3c240-116">Beginning with C# 7.2, you can use the conditional ref expression to return the reference to the result of one of the two expressions.</span></span> <span data-ttu-id="3c240-117">Vous pouvez affecter cette référence à une variable [locale ref](../keywords/ref.md#ref-locals) ou [locale ref readonly](../keywords/ref.md#ref-readonly-locals), ou l’utiliser comme [valeur de retour de référence](../keywords/ref.md#reference-return-values) ou comme [paramètre de méthode `ref`](../keywords/ref.md#passing-an-argument-by-reference).</span><span class="sxs-lookup"><span data-stu-id="3c240-117">You can assign that reference to a [ref local](../keywords/ref.md#ref-locals) or [ref readonly local](../keywords/ref.md#ref-readonly-locals) variable, or use it as a [reference return value](../keywords/ref.md#reference-return-values) or as a [`ref` method parameter](../keywords/ref.md#passing-an-argument-by-reference).</span></span>

<span data-ttu-id="3c240-118">Voici la syntaxe de l'expression ref conditionnelle :</span><span class="sxs-lookup"><span data-stu-id="3c240-118">The syntax for the conditional ref expression is as follows:</span></span>

```csharp
condition ? ref consequent : ref alternative
```

<span data-ttu-id="3c240-119">Comme l’opérateur conditionnel d’origine, l’expression ref conditionnelle n’évalue qu’une des deux expressions : soit `consequent`, soit `alternative`.</span><span class="sxs-lookup"><span data-stu-id="3c240-119">Like the original conditional operator, the conditional ref expression evaluates only one of the two expressions: either `consequent` or `alternative`.</span></span>

<span data-ttu-id="3c240-120">Dans le cas de l’expression ref conditionnelle, `consequent` et `alternative` doivent être du même type.</span><span class="sxs-lookup"><span data-stu-id="3c240-120">In the case of the conditional ref expression, the type of `consequent` and `alternative` must be the same.</span></span>

<span data-ttu-id="3c240-121">L’exemple suivant illustre l’utilisation de l’expression ref conditionnelle :</span><span class="sxs-lookup"><span data-stu-id="3c240-121">The following example demonstrates the usage of the conditional ref expression:</span></span>

[!code-csharp[conditional ref](~/samples/snippets/csharp/language-reference/operators/ConditionalExamples.cs#ConditionalRef)]

<span data-ttu-id="3c240-122">Pour plus d’informations, voir la [proposition de fonctionnalité](../../../../_csharplang/proposals/csharp-7.2/conditional-ref.md).</span><span class="sxs-lookup"><span data-stu-id="3c240-122">For more information, see the [feature proposal note](../../../../_csharplang/proposals/csharp-7.2/conditional-ref.md).</span></span>

## <a name="conditional-operator-and-an-ifelse-statement"></a><span data-ttu-id="3c240-123">Opérateur conditionnel et instruction `if..else`</span><span class="sxs-lookup"><span data-stu-id="3c240-123">Conditional operator and an `if..else` statement</span></span>

<span data-ttu-id="3c240-124">Sur une instruction [if-else](../keywords/if-else.md), l’opérateur conditionnel permet de rester concis dans l’écriture du code lorsque l’objectif est de calculer une valeur sous condition.</span><span class="sxs-lookup"><span data-stu-id="3c240-124">Use of the conditional operator over an [if-else](../keywords/if-else.md) statement might result in more concise code in cases when you need conditionally to compute a value.</span></span> <span data-ttu-id="3c240-125">L’exemple suivant montre deux façons de classer un entier comme négatif ou non :</span><span class="sxs-lookup"><span data-stu-id="3c240-125">The following example demonstrates two ways to classify an integer as negative or nonnegative:</span></span>

[!code-csharp[conditional and if-else](~/samples/snippets/csharp/language-reference/operators/ConditionalExamples.cs#CompareWithIf)]

## <a name="operator-overloadability"></a><span data-ttu-id="3c240-126">Capacité de surcharge de l’opérateur</span><span class="sxs-lookup"><span data-stu-id="3c240-126">Operator overloadability</span></span>

<span data-ttu-id="3c240-127">L'opérateur conditionnel ne peut pas être surchargé.</span><span class="sxs-lookup"><span data-stu-id="3c240-127">The conditional operator cannot be overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="3c240-128">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="3c240-128">C# language specification</span></span>

<span data-ttu-id="3c240-129">Pour plus d’informations, voir la section [Opérateur conditionnel](~/_csharplang/spec/expressions.md#conditional-operator) de la [spécification du langage C#](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="3c240-129">For more information, see the [Conditional operator](~/_csharplang/spec/expressions.md#conditional-operator) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3c240-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3c240-130">See also</span></span>

- [<span data-ttu-id="3c240-131">Référence C#</span><span class="sxs-lookup"><span data-stu-id="3c240-131">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="3c240-132">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="3c240-132">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="3c240-133">Opérateurs C#</span><span class="sxs-lookup"><span data-stu-id="3c240-133">C# Operators</span></span>](index.md)
- [<span data-ttu-id="3c240-134">Instruction if-else</span><span class="sxs-lookup"><span data-stu-id="3c240-134">if-else statement</span></span>](../keywords/if-else.md)
- <span data-ttu-id="3c240-135">[Opérateurs ?. et ?[]](member-access-operators.md#null-conditional-operators--and-)</span><span class="sxs-lookup"><span data-stu-id="3c240-135">[?. and ?[] Operators](member-access-operators.md#null-conditional-operators--and-)</span></span>
- [<span data-ttu-id="3c240-136">?? Opérateur</span><span class="sxs-lookup"><span data-stu-id="3c240-136">?? Operator</span></span>](null-coalescing-operator.md)
- [<span data-ttu-id="3c240-137">ref, mot clé</span><span class="sxs-lookup"><span data-stu-id="3c240-137">ref keyword</span></span>](../keywords/ref.md)
