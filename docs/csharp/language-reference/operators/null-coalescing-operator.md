---
title: ?? opérateur - Référence C#
ms.custom: seodec18
ms.date: 06/07/2019
f1_keywords:
- ??_CSharpKeyword
helpviewer_keywords:
- null-coalescing operator [C#]
- ?? operator [C#]
ms.assetid: 088b1f0d-c1af-4fe1-b4b8-196fd5ea9132
ms.openlocfilehash: 8ca97261b348b7813ab179abbc1f2c5f535966a1
ms.sourcegitcommit: 5ae6affa0b171be3bb5f4729fb68ea4fe799f959
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/10/2019
ms.locfileid: "66816009"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="aa007-103">??</span><span class="sxs-lookup"><span data-stu-id="aa007-103">??</span></span> <span data-ttu-id="aa007-104">operator (référence C#)</span><span class="sxs-lookup"><span data-stu-id="aa007-104">operator (C# Reference)</span></span>

<span data-ttu-id="aa007-105">L’opérateur de fusion null `??` retourne la valeur de l’opérande de gauche si elle n’est pas `null`; sinon, elle évalue l’opérande de droite et retourne son résultat.</span><span class="sxs-lookup"><span data-stu-id="aa007-105">The null-coalescing operator `??` returns the value of its left-hand operand if it isn't `null`; otherwise, it evaluates the right-hand operand and returns its result.</span></span> <span data-ttu-id="aa007-106">Le `??` opérateur n’évalue pas son opérande de droite si l’opérande de gauche a la valeur non null.</span><span class="sxs-lookup"><span data-stu-id="aa007-106">The `??` operator doesn't evaluate its right-hand operand if the left-hand operand evaluates to non-null.</span></span>

<span data-ttu-id="aa007-107">L’opérateur de fusion null est associatif à droite, autrement dit, une expression sous la forme</span><span class="sxs-lookup"><span data-stu-id="aa007-107">The null-coalescing operator is right-associative, that is, an expression of the form</span></span>

```csharp
a ?? b ?? c
```

<span data-ttu-id="aa007-108">est évaluée comme étant</span><span class="sxs-lookup"><span data-stu-id="aa007-108">is evaluated as</span></span>

```csharp
a ?? (b ?? c)
```

<span data-ttu-id="aa007-109">Le `??` opérateur peut être utile dans les scénarios suivants :</span><span class="sxs-lookup"><span data-stu-id="aa007-109">The `??` operator can be useful in the following scenarios:</span></span>

- <span data-ttu-id="aa007-110">Dans les expressions avec la [opérateurs conditionnels null ?. et ?] ](member-access-operators.md#null-conditional-operators--and-), vous pouvez utiliser l’opérateur de fusion null pour fournir une autre expression à évaluer au cas où le résultat de l’expression avec les opérations de condition null est `null`:</span><span class="sxs-lookup"><span data-stu-id="aa007-110">In expressions with the [null-conditional operators ?. and ?[]](member-access-operators.md#null-conditional-operators--and-), you can use the null-coalescing operator to provide an alternative expression to evaluate in case the result of the expression with null-conditional operations is `null`:</span></span>

  [!code-csharp-interactive[with null-conditional](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#WithNullConditional)]

- <span data-ttu-id="aa007-111">Lorsque vous travaillez avec [types valeur nullable](../../programming-guide/nullable-types/index.md) et devez fournir une valeur d’un type valeur sous-jacent, utilisez l’opérateur de fusion null pour spécifier la valeur à fournir au cas où une valeur de type nullable est `null`:</span><span class="sxs-lookup"><span data-stu-id="aa007-111">When you work with [nullable value types](../../programming-guide/nullable-types/index.md) and need to provide a value of an underlying value type, use the null-coalescing operator to specify the value to provide in case a nullable type value is `null`:</span></span>

  [!code-csharp-interactive[with nullable types](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#WithNullableTypes)]

  <span data-ttu-id="aa007-112">Utilisez le <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> méthode si la valeur à utiliser lorsqu’une valeur de type nullable est `null` doit avoir la valeur par défaut du type valeur sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="aa007-112">Use the <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> method if the value to be used when a nullable type value is `null` should be the default value of the underlying value type.</span></span>

- <span data-ttu-id="aa007-113">En commençant par C# 7.0, vous pouvez utiliser un [ `throw` expression](../keywords/throw.md#the-throw-expression) comme opérande droit de l’opérateur de fusion null pour rendre le code de vérification d’argument plus concis :</span><span class="sxs-lookup"><span data-stu-id="aa007-113">Starting with C# 7.0, you can use a [`throw` expression](../keywords/throw.md#the-throw-expression) as the right-hand operand of the null-coalescing operator to make the argument-checking code more concise:</span></span>

  [!code-csharp[with throw expression](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#WithThrowExpression)]

  <span data-ttu-id="aa007-114">L’exemple précédent montre également comment utiliser [membres expression-bodied](../../programming-guide/statements-expressions-operators/expression-bodied-members.md) pour définir une propriété.</span><span class="sxs-lookup"><span data-stu-id="aa007-114">The preceding example also demonstrates how to use [expression-bodied members](../../programming-guide/statements-expressions-operators/expression-bodied-members.md) to define a property.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="aa007-115">Capacité de surcharge de l’opérateur</span><span class="sxs-lookup"><span data-stu-id="aa007-115">Operator overloadability</span></span>

<span data-ttu-id="aa007-116">L’opérateur de fusion null ne peut pas être surchargé.</span><span class="sxs-lookup"><span data-stu-id="aa007-116">The null-coalescing operator cannot be overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="aa007-117">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="aa007-117">C# language specification</span></span>

<span data-ttu-id="aa007-118">Pour plus d’informations, consultez [l’opérateur de fusion null](~/_csharplang/spec/expressions.md#the-null-coalescing-operator) section de la [ C# spécification du langage](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="aa007-118">For more information, see [The null coalescing operator](~/_csharplang/spec/expressions.md#the-null-coalescing-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="aa007-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aa007-119">See also</span></span>

- [<span data-ttu-id="aa007-120">Référence C#</span><span class="sxs-lookup"><span data-stu-id="aa007-120">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="aa007-121">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="aa007-121">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="aa007-122">Opérateurs C#</span><span class="sxs-lookup"><span data-stu-id="aa007-122">C# operators</span></span>](index.md)
- <span data-ttu-id="aa007-123">[Opérateurs ?. et ?[]](member-access-operators.md#null-conditional-operators--and-)</span><span class="sxs-lookup"><span data-stu-id="aa007-123">[?. and ?[] operators](member-access-operators.md#null-conditional-operators--and-)</span></span>
- [<span data-ttu-id="aa007-124">?:, opérateur</span><span class="sxs-lookup"><span data-stu-id="aa007-124">?: operator</span></span>](conditional-operator.md)
