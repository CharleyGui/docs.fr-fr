---
title: 'Opérateur ?: - Référence C#'
ms.date: 11/20/2018
f1_keywords:
- ?:_CSharpKeyword
- ?_CSharpKeyword
- :_CSharpKeyword
helpviewer_keywords:
- '?: operator [C#]'
- conditional operator (?:) [C#]
ms.assetid: e83a17f1-7500-48ba-8bee-2fbc4c847af4
ms.openlocfilehash: 6e8fde8c210b2c33cc514167be7face657cbb618
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/03/2020
ms.locfileid: "78239377"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="aea41-102">Opérateur ?: (référence C#)</span><span class="sxs-lookup"><span data-stu-id="aea41-102">?: operator (C# reference)</span></span>

<span data-ttu-id="aea41-103">L’opérateur conditionnel `?:`, également appelé opérateur conditionnel ternaire, évalue une expression booléenne et retourne le résultat de l’une des deux expressions, selon que l’expression booléenne a la valeur `true` ou `false`.</span><span class="sxs-lookup"><span data-stu-id="aea41-103">The conditional operator `?:`, also known as the ternary conditional operator, evaluates a Boolean expression and returns the result of one of the two expressions, depending on whether the Boolean expression evaluates to `true` or `false`.</span></span> <span data-ttu-id="aea41-104">À partir de C# 7.2, [l’expression ref conditionnelle](#conditional-ref-expression) retourne la référence au résultat d’une des deux expressions.</span><span class="sxs-lookup"><span data-stu-id="aea41-104">Beginning with C# 7.2, the [conditional ref expression](#conditional-ref-expression) returns the reference to the result of one of the two expressions.</span></span>

<span data-ttu-id="aea41-105">Voici la syntaxe de l'opérateur conditionnel :</span><span class="sxs-lookup"><span data-stu-id="aea41-105">The syntax for the conditional operator is as follows:</span></span>

```csharp
condition ? consequent : alternative
```

<span data-ttu-id="aea41-106">L'expression `condition` doit donner `true` ou `false`.</span><span class="sxs-lookup"><span data-stu-id="aea41-106">The `condition` expression must evaluate to `true` or `false`.</span></span> <span data-ttu-id="aea41-107">Si `condition` prend la valeur `true`, l’expression `consequent` est évaluée et son résultat devient le résultat de l’opération.</span><span class="sxs-lookup"><span data-stu-id="aea41-107">If `condition` evaluates to `true`, the `consequent` expression is evaluated, and its result becomes the result of the operation.</span></span> <span data-ttu-id="aea41-108">Si `condition` prend la valeur `false`, l’expression `alternative` est évaluée et son résultat devient le résultat de l’opération.</span><span class="sxs-lookup"><span data-stu-id="aea41-108">If `condition` evaluates to `false`, the `alternative` expression is evaluated, and its result becomes the result of the operation.</span></span> <span data-ttu-id="aea41-109">Soit `consequent`, soit `alternative` est évaluée.</span><span class="sxs-lookup"><span data-stu-id="aea41-109">Only `consequent` or `alternative` is evaluated.</span></span>

<span data-ttu-id="aea41-110">Il faut que `consequent` et `alternative` soient du même type ou bien qu’une conversion implicite existe d’un type à l’autre.</span><span class="sxs-lookup"><span data-stu-id="aea41-110">The type of `consequent` and `alternative` must be the same, or there must be an implicit conversion from one type to the other.</span></span>

<span data-ttu-id="aea41-111">L’opérateur conditionnel est associatif à droite ; autrement dit, une expression de la forme :</span><span class="sxs-lookup"><span data-stu-id="aea41-111">The conditional operator is right-associative, that is, an expression of the form</span></span>

```csharp
a ? b : c ? d : e
```

<span data-ttu-id="aea41-112">est évaluée comme</span><span class="sxs-lookup"><span data-stu-id="aea41-112">is evaluated as</span></span>

```csharp
a ? b : (c ? d : e)
```

> [!TIP]
> <span data-ttu-id="aea41-113">Vous pouvez utiliser l’appareil mnémonique suivant pour vous souvenir du mode d’évaluation de l’opérateur conditionnel :</span><span class="sxs-lookup"><span data-stu-id="aea41-113">You can use the following mnemonic device to remember how the conditional operator is evaluated:</span></span>
>
> ```text
> is this condition true ? yes : no
> ```

<span data-ttu-id="aea41-114">L’exemple suivant illustre l’utilisation de l’opérateur conditionnel :</span><span class="sxs-lookup"><span data-stu-id="aea41-114">The following example demonstrates the usage of the conditional operator:</span></span>

[!code-csharp-interactive[non ref conditional](~/samples/snippets/csharp/language-reference/operators/ConditionalOperator.cs#ConditionalValue)]

## <a name="conditional-ref-expression"></a><span data-ttu-id="aea41-115">Expression ref conditionnelle</span><span class="sxs-lookup"><span data-stu-id="aea41-115">Conditional ref expression</span></span>

<span data-ttu-id="aea41-116">À partir de C# 7.2, il est possible d’utiliser l’expression ref conditionnelle pour retourner la référence au résultat d’une des deux expressions.</span><span class="sxs-lookup"><span data-stu-id="aea41-116">Beginning with C# 7.2, you can use the conditional ref expression to return the reference to the result of one of the two expressions.</span></span> <span data-ttu-id="aea41-117">Vous pouvez affecter cette référence à une variable [locale ref](../keywords/ref.md#ref-locals) ou [locale ref readonly](../keywords/ref.md#ref-readonly-locals), ou l’utiliser comme [valeur de retour de référence](../keywords/ref.md#reference-return-values) ou comme [paramètre de méthode `ref`](../keywords/ref.md#passing-an-argument-by-reference).</span><span class="sxs-lookup"><span data-stu-id="aea41-117">You can assign that reference to a [ref local](../keywords/ref.md#ref-locals) or [ref readonly local](../keywords/ref.md#ref-readonly-locals) variable, or use it as a [reference return value](../keywords/ref.md#reference-return-values) or as a [`ref` method parameter](../keywords/ref.md#passing-an-argument-by-reference).</span></span>

<span data-ttu-id="aea41-118">Voici la syntaxe de l'expression ref conditionnelle :</span><span class="sxs-lookup"><span data-stu-id="aea41-118">The syntax for the conditional ref expression is as follows:</span></span>

```csharp
condition ? ref consequent : ref alternative
```

<span data-ttu-id="aea41-119">Comme l’opérateur conditionnel d’origine, l’expression ref conditionnelle n’évalue qu’une des deux expressions : soit `consequent`, soit `alternative`.</span><span class="sxs-lookup"><span data-stu-id="aea41-119">Like the original conditional operator, the conditional ref expression evaluates only one of the two expressions: either `consequent` or `alternative`.</span></span>

<span data-ttu-id="aea41-120">Dans le cas de l’expression ref conditionnelle, `consequent` et `alternative` doivent être du même type.</span><span class="sxs-lookup"><span data-stu-id="aea41-120">In the case of the conditional ref expression, the type of `consequent` and `alternative` must be the same.</span></span>

<span data-ttu-id="aea41-121">L’exemple suivant illustre l’utilisation de l’expression ref conditionnelle :</span><span class="sxs-lookup"><span data-stu-id="aea41-121">The following example demonstrates the usage of the conditional ref expression:</span></span>

[!code-csharp-interactive[conditional ref](~/samples/snippets/csharp/language-reference/operators/ConditionalOperator.cs#ConditionalRef)]

## <a name="conditional-operator-and-an-ifelse-statement"></a><span data-ttu-id="aea41-122">Opérateur conditionnel et instruction `if..else`</span><span class="sxs-lookup"><span data-stu-id="aea41-122">Conditional operator and an `if..else` statement</span></span>

<span data-ttu-id="aea41-123">L’utilisation de l’opérateur conditionnel au lieu d’une instruction [if-else](../keywords/if-else.md) peut entraîner un code plus concis dans les cas où vous avez besoin de calculer une valeur de manière conditionnelle.</span><span class="sxs-lookup"><span data-stu-id="aea41-123">Use of the conditional operator instead of an [if-else](../keywords/if-else.md) statement might result in more concise code in cases when you need conditionally to compute a value.</span></span> <span data-ttu-id="aea41-124">L’exemple suivant montre deux façons de classer un entier comme négatif ou non :</span><span class="sxs-lookup"><span data-stu-id="aea41-124">The following example demonstrates two ways to classify an integer as negative or nonnegative:</span></span>

[!code-csharp[conditional and if-else](~/samples/snippets/csharp/language-reference/operators/ConditionalOperator.cs#CompareWithIf)]

## <a name="operator-overloadability"></a><span data-ttu-id="aea41-125">Capacité de surcharge de l’opérateur</span><span class="sxs-lookup"><span data-stu-id="aea41-125">Operator overloadability</span></span>

<span data-ttu-id="aea41-126">Un type défini par l’utilisateur ne peut pas surcharger l’opérateur conditionnel.</span><span class="sxs-lookup"><span data-stu-id="aea41-126">A user-defined type cannot overload the conditional operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="aea41-127">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="aea41-127">C# language specification</span></span>

<span data-ttu-id="aea41-128">Pour plus d’informations, voir la section [Opérateur conditionnel](~/_csharplang/spec/expressions.md#conditional-operator) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="aea41-128">For more information, see the [Conditional operator](~/_csharplang/spec/expressions.md#conditional-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="aea41-129">Pour plus d’informations sur l’expression Ref conditionnelle, consultez la [Remarque relative](~/_csharplang/proposals/csharp-7.2/conditional-ref.md)à la proposition de fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="aea41-129">For more information about the conditional ref expression, see the [feature proposal note](~/_csharplang/proposals/csharp-7.2/conditional-ref.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="aea41-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aea41-130">See also</span></span>

- [<span data-ttu-id="aea41-131">Informations de référence sur C#</span><span class="sxs-lookup"><span data-stu-id="aea41-131">C# reference</span></span>](../index.md)
- [<span data-ttu-id="aea41-132">Opérateurs C#</span><span class="sxs-lookup"><span data-stu-id="aea41-132">C# operators</span></span>](index.md)
- [<span data-ttu-id="aea41-133">Instruction if-else</span><span class="sxs-lookup"><span data-stu-id="aea41-133">if-else statement</span></span>](../keywords/if-else.md)
- <span data-ttu-id="aea41-134">[Opérateurs ?. et ?[]](member-access-operators.md#null-conditional-operators--and-)</span><span class="sxs-lookup"><span data-stu-id="aea41-134">[?. and ?[] operators](member-access-operators.md#null-conditional-operators--and-)</span></span>
- [<span data-ttu-id="aea41-135">?? et ?? =, opérateurs</span><span class="sxs-lookup"><span data-stu-id="aea41-135">?? and ??= operators</span></span>](null-coalescing-operator.md)
- [<span data-ttu-id="aea41-136">ref, mot clé</span><span class="sxs-lookup"><span data-stu-id="aea41-136">ref keyword</span></span>](../keywords/ref.md)
