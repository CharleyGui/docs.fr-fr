---
title: + + et +=, opérateurs - Référence C#
ms.custom: seodec18
ms.date: 05/24/2019
f1_keywords:
- +_CSharpKeyword
- +=_CSharpKeyword
helpviewer_keywords:
- addition operator [C#]
- concatenation operator [C#]
- delegate combination [C#]
- + operator [C#]
- addition assignment operator [C#]
- event subscription [C#]
- += operator [C#]
ms.assetid: 93e56486-bb42-43c1-bd43-60af11e64e67
ms.openlocfilehash: d03743bad47c60925462d027d18445047ebc0fc9
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66300113"
---
# <a name="-and--operators-c-reference"></a><span data-ttu-id="956e1-102">+ et +=, opérateurs (référence C#)</span><span class="sxs-lookup"><span data-stu-id="956e1-102">+ and += operators (C# Reference)</span></span>

<span data-ttu-id="956e1-103">L’opérateur `+` est pris en charge par les types numériques intégrés, le type [chaîne](../keywords/string.md) et les types [délégués](../keywords/delegate.md).</span><span class="sxs-lookup"><span data-stu-id="956e1-103">The `+` operator is supported by the built-in numeric types, [string](../keywords/string.md) type, and [delegate](../keywords/delegate.md) types.</span></span>

<span data-ttu-id="956e1-104">Pour plus d’informations sur l’opérateur arithmétique `+`, consultez les sections [Opérateurs plus et moins unaires](arithmetic-operators.md#unary-plus-and-minus-operators) et [Opérateur d’addition +](arithmetic-operators.md#addition-operator-) de l’article [Opérateurs arithmétiques](arithmetic-operators.md).</span><span class="sxs-lookup"><span data-stu-id="956e1-104">For information about the arithmetic `+` operator, see the [Unary plus and minus operators](arithmetic-operators.md#unary-plus-and-minus-operators) and [Addition operator +](arithmetic-operators.md#addition-operator-) sections of the [Arithmetic operators](arithmetic-operators.md) article.</span></span>

## <a name="string-concatenation"></a><span data-ttu-id="956e1-105">Concaténation de chaînes</span><span class="sxs-lookup"><span data-stu-id="956e1-105">String concatenation</span></span>

<span data-ttu-id="956e1-106">Quand les deux opérandes ou l’un d’entre eux sont de [type chaîne](../keywords/string.md), l’opérateur `+` concatène les représentations sous forme de chaîne de ses opérandes :</span><span class="sxs-lookup"><span data-stu-id="956e1-106">When one or both operands are of type [string](../keywords/string.md), the `+` operator concatenates the string representations of its operands:</span></span>

[!code-csharp-interactive[string concatenation](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#AddStrings)]

<span data-ttu-id="956e1-107">À partir de C# 6, l’[interpolation de chaîne](../tokens/interpolated.md) fournit un moyen plus pratique de mettre en format les chaînes :</span><span class="sxs-lookup"><span data-stu-id="956e1-107">Starting with C# 6, [string interpolation](../tokens/interpolated.md) provides a more convenient way to format strings:</span></span>

[!code-csharp-interactive[string interpolation](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#UseStringInterpolation)]

## <a name="delegate-combination"></a><span data-ttu-id="956e1-108">Combinaison de délégués</span><span class="sxs-lookup"><span data-stu-id="956e1-108">Delegate combination</span></span>

<span data-ttu-id="956e1-109">Pour les opérandes du même type [délégué](../keywords/delegate.md), l’opérateur `+` retourne une nouvelle instance de délégué qui, lorsqu’elle est appelée, appelle le premier opérande, puis le second opérande.</span><span class="sxs-lookup"><span data-stu-id="956e1-109">For operands of the same [delegate](../keywords/delegate.md) type, the `+` operator returns a new delegate instance that, when invoked, invokes the first operand and then invokes the second operand.</span></span> <span data-ttu-id="956e1-110">Si un des opérandes est `null`, l’opérateur `+` retourne la valeur de l’autre opérande (qui peut également être `null`).</span><span class="sxs-lookup"><span data-stu-id="956e1-110">If any of the operands is `null`, the `+` operator returns the value of another operand (which also might be `null`).</span></span> <span data-ttu-id="956e1-111">L’exemple suivant montre comment les délégués peuvent être combinés avec l’opérateur `+` :</span><span class="sxs-lookup"><span data-stu-id="956e1-111">The following example shows how delegates can be combined with the `+` operator:</span></span>

[!code-csharp-interactive[delegate combination](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#AddDelegates)]

<span data-ttu-id="956e1-112">Pour plus d'informations sur les types de délégués, consultez [Délégués](../../programming-guide/delegates/index.md).</span><span class="sxs-lookup"><span data-stu-id="956e1-112">For more information about delegate types, see [Delegates](../../programming-guide/delegates/index.md).</span></span>

## <a name="addition-assignment-operator-"></a><span data-ttu-id="956e1-113">Opérateur d’assignation d’addition +=</span><span class="sxs-lookup"><span data-stu-id="956e1-113">Addition assignment operator +=</span></span>

<span data-ttu-id="956e1-114">Expression utilisant l’opérateur `+=`, par exemple</span><span class="sxs-lookup"><span data-stu-id="956e1-114">An expression using the `+=` operator, such as</span></span>

```csharp
x += y
```

<span data-ttu-id="956e1-115">est équivalent à</span><span class="sxs-lookup"><span data-stu-id="956e1-115">is equivalent to</span></span>

```csharp
x = x + y
```

<span data-ttu-id="956e1-116">sauf que `x` n’est évalué qu’une seule fois.</span><span class="sxs-lookup"><span data-stu-id="956e1-116">except that `x` is only evaluated once.</span></span>
  
<span data-ttu-id="956e1-117">L’exemple suivant illustre l’utilisation de l’opérateur `+=` :</span><span class="sxs-lookup"><span data-stu-id="956e1-117">The following example demonstrates the usage of the `+=` operator:</span></span>

[!code-csharp-interactive[+= examples](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#AddAndAssign)]

<span data-ttu-id="956e1-118">Vous utilisez également l’opérateur `+=` pour spécifier une méthode de gestionnaire d’événements lorsque vous vous abonnez à un [événement](../keywords/event.md).</span><span class="sxs-lookup"><span data-stu-id="956e1-118">You also use the `+=` operator to specify an event handler method when you subscribe to an [event](../keywords/event.md).</span></span> <span data-ttu-id="956e1-119">Pour plus d’informations, consultez [Guide pratique pour s’abonner et annuler l’abonnement à des événements](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="956e1-119">For more information, see [How to: subscribe to and unsubscribe from events](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="956e1-120">Capacité de surcharge de l’opérateur</span><span class="sxs-lookup"><span data-stu-id="956e1-120">Operator overloadability</span></span>

<span data-ttu-id="956e1-121">Un type défini par l’utilisateur peut [surcharger](../keywords/operator.md) l’opérateur `+`.</span><span class="sxs-lookup"><span data-stu-id="956e1-121">A user-defined type can [overload](../keywords/operator.md) the `+` operator.</span></span> <span data-ttu-id="956e1-122">Quand un opérateur binaire `+` est surchargé, l’opérateur `+=` est aussi implicitement surchargé.</span><span class="sxs-lookup"><span data-stu-id="956e1-122">When a binary `+` operator is overloaded, the `+=` operator is also implicitly overloaded.</span></span> <span data-ttu-id="956e1-123">Un type défini par l’utilisateur ne peut pas surcharger explicitement l’opérateur `+=`.</span><span class="sxs-lookup"><span data-stu-id="956e1-123">A user-defined type cannot explicitly overload the `+=` operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="956e1-124">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="956e1-124">C# language specification</span></span>

<span data-ttu-id="956e1-125">Pour plus d’informations, consultez les sections [Opérateur unaire plus](~/_csharplang/spec/expressions.md#unary-plus-operator) et [Opérateur d’addition](~/_csharplang/spec/expressions.md#addition-operator) de la [spécification du langage C#](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="956e1-125">For more information, see the [Unary plus operator](~/_csharplang/spec/expressions.md#unary-plus-operator) and [Addition operator](~/_csharplang/spec/expressions.md#addition-operator) sections of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="956e1-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="956e1-126">See also</span></span>

- [<span data-ttu-id="956e1-127">Référence C#</span><span class="sxs-lookup"><span data-stu-id="956e1-127">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="956e1-128">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="956e1-128">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="956e1-129">Opérateurs C#</span><span class="sxs-lookup"><span data-stu-id="956e1-129">C# Operators</span></span>](index.md)
- [<span data-ttu-id="956e1-130">Interpolation de chaîne</span><span class="sxs-lookup"><span data-stu-id="956e1-130">String interpolation</span></span>](../tokens/interpolated.md)
- [<span data-ttu-id="956e1-131">Guide pratique pour concaténer plusieurs chaînes</span><span class="sxs-lookup"><span data-stu-id="956e1-131">How to: concatenate multiple strings</span></span>](../../how-to/concatenate-multiple-strings.md)
- [<span data-ttu-id="956e1-132">Délégués</span><span class="sxs-lookup"><span data-stu-id="956e1-132">Delegates</span></span>](../../programming-guide/delegates/index.md)
- [<span data-ttu-id="956e1-133">Événements</span><span class="sxs-lookup"><span data-stu-id="956e1-133">Events</span></span>](../../programming-guide/events/index.md)
- [<span data-ttu-id="956e1-134">Checked et unchecked</span><span class="sxs-lookup"><span data-stu-id="956e1-134">Checked and unchecked</span></span>](../keywords/checked-and-unchecked.md)
- [<span data-ttu-id="956e1-135">Opérateurs arithmétiques</span><span class="sxs-lookup"><span data-stu-id="956e1-135">Arithmetic operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="956e1-136">- et -=, opérateurs</span><span class="sxs-lookup"><span data-stu-id="956e1-136">- and -= operators</span></span>](subtraction-operator.md)
