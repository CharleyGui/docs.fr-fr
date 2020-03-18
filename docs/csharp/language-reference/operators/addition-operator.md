---
title: + et +=, opérateurs - Référence C#
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
ms.openlocfilehash: cafd07f4b4aefdcc4b43750d61c155fe3d65aa46
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399300"
---
# <a name="-and--operators-c-reference"></a><span data-ttu-id="d20d7-102">+ et +=, opérateurs (référence C#)</span><span class="sxs-lookup"><span data-stu-id="d20d7-102">+ and += operators (C# reference)</span></span>

<span data-ttu-id="d20d7-103">Les `+` `+=` opérateurs et les opérateurs sont pris en charge par les types [numériques intégrés](../builtin-types/integral-numeric-types.md) et [flottants,](../builtin-types/floating-point-numeric-types.md) le type [de chaîne](../builtin-types/reference-types.md#the-string-type) et les types [de délégués.](../builtin-types/reference-types.md#the-delegate-type)</span><span class="sxs-lookup"><span data-stu-id="d20d7-103">The `+` and `+=` operators are supported by the built-in [integral](../builtin-types/integral-numeric-types.md) and [floating-point](../builtin-types/floating-point-numeric-types.md) numeric types, the [string](../builtin-types/reference-types.md#the-string-type) type, and [delegate](../builtin-types/reference-types.md#the-delegate-type) types.</span></span>

<span data-ttu-id="d20d7-104">Pour plus d’informations sur l’opérateur arithmétique `+`, consultez les sections [Opérateurs plus et moins unaires](arithmetic-operators.md#unary-plus-and-minus-operators) et [Opérateur d’addition +](arithmetic-operators.md#addition-operator-) de l’article [Opérateurs arithmétiques](arithmetic-operators.md).</span><span class="sxs-lookup"><span data-stu-id="d20d7-104">For information about the arithmetic `+` operator, see the [Unary plus and minus operators](arithmetic-operators.md#unary-plus-and-minus-operators) and [Addition operator +](arithmetic-operators.md#addition-operator-) sections of the [Arithmetic operators](arithmetic-operators.md) article.</span></span>

## <a name="string-concatenation"></a><span data-ttu-id="d20d7-105">Concaténation de chaînes</span><span class="sxs-lookup"><span data-stu-id="d20d7-105">String concatenation</span></span>

<span data-ttu-id="d20d7-106">Quand les deux opérandes ou l’un d’entre eux sont de [type chaîne](../builtin-types/reference-types.md#the-string-type), l’opérateur `+` concatène les représentations sous forme de chaîne de ses opérandes :</span><span class="sxs-lookup"><span data-stu-id="d20d7-106">When one or both operands are of type [string](../builtin-types/reference-types.md#the-string-type), the `+` operator concatenates the string representations of its operands:</span></span>

[!code-csharp-interactive[string concatenation](snippets/AdditionOperator.cs#AddStrings)]

<span data-ttu-id="d20d7-107">En commençant par le C 6, [l’interpolation](../tokens/interpolated.md) des cordes offre un moyen plus pratique de formater les chaînes :</span><span class="sxs-lookup"><span data-stu-id="d20d7-107">Beginning with C# 6, [string interpolation](../tokens/interpolated.md) provides a more convenient way to format strings:</span></span>

[!code-csharp-interactive[string interpolation](snippets/AdditionOperator.cs#UseStringInterpolation)]

## <a name="delegate-combination"></a><span data-ttu-id="d20d7-108">Combinaison de délégués</span><span class="sxs-lookup"><span data-stu-id="d20d7-108">Delegate combination</span></span>

<span data-ttu-id="d20d7-109">Pour les opérandes du même type [délégué](../builtin-types/reference-types.md#the-delegate-type), l’opérateur `+` retourne une nouvelle instance de délégué qui, lorsqu’elle est appelée, appelle l’opérande de partie gauche, puis l’opérande de partie droite.</span><span class="sxs-lookup"><span data-stu-id="d20d7-109">For operands of the same [delegate](../builtin-types/reference-types.md#the-delegate-type) type, the `+` operator returns a new delegate instance that, when invoked, invokes the left-hand operand and then invokes the right-hand operand.</span></span> <span data-ttu-id="d20d7-110">Si un des opérandes est `null`, l’opérateur `+` retourne la valeur de l’autre opérande (qui peut également être `null`).</span><span class="sxs-lookup"><span data-stu-id="d20d7-110">If any of the operands is `null`, the `+` operator returns the value of another operand (which also might be `null`).</span></span> <span data-ttu-id="d20d7-111">L’exemple suivant montre comment les délégués peuvent être combinés avec l’opérateur `+` :</span><span class="sxs-lookup"><span data-stu-id="d20d7-111">The following example shows how delegates can be combined with the `+` operator:</span></span>

[!code-csharp-interactive[delegate combination](snippets/AdditionOperator.cs#AddDelegates)]

<span data-ttu-id="d20d7-112">Pour effectuer le retrait des délégués, utilisez [ `-` l’opérateur](subtraction-operator.md#delegate-removal).</span><span class="sxs-lookup"><span data-stu-id="d20d7-112">To perform delegate removal, use the [`-` operator](subtraction-operator.md#delegate-removal).</span></span>

<span data-ttu-id="d20d7-113">Pour plus d'informations sur les types de délégués, consultez [Délégués](../../programming-guide/delegates/index.md).</span><span class="sxs-lookup"><span data-stu-id="d20d7-113">For more information about delegate types, see [Delegates](../../programming-guide/delegates/index.md).</span></span>

## <a name="addition-assignment-operator-"></a><span data-ttu-id="d20d7-114">Opérateur d’assignation d’addition +=</span><span class="sxs-lookup"><span data-stu-id="d20d7-114">Addition assignment operator +=</span></span>

<span data-ttu-id="d20d7-115">Expression utilisant l’opérateur `+=`, par exemple</span><span class="sxs-lookup"><span data-stu-id="d20d7-115">An expression using the `+=` operator, such as</span></span>

```csharp
x += y
```

<span data-ttu-id="d20d7-116">équivaut à :</span><span class="sxs-lookup"><span data-stu-id="d20d7-116">is equivalent to</span></span>

```csharp
x = x + y
```

<span data-ttu-id="d20d7-117">sauf que `x` n’est évalué qu’une seule fois.</span><span class="sxs-lookup"><span data-stu-id="d20d7-117">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="d20d7-118">L’exemple suivant illustre l’utilisation de l’opérateur `+=` :</span><span class="sxs-lookup"><span data-stu-id="d20d7-118">The following example demonstrates the usage of the `+=` operator:</span></span>

[!code-csharp-interactive[+= examples](snippets/AdditionOperator.cs#AddAndAssign)]

<span data-ttu-id="d20d7-119">Vous utilisez également l’opérateur `+=` pour spécifier une méthode de gestionnaire d’événements lorsque vous vous abonnez à un [événement](../keywords/event.md).</span><span class="sxs-lookup"><span data-stu-id="d20d7-119">You also use the `+=` operator to specify an event handler method when you subscribe to an [event](../keywords/event.md).</span></span> <span data-ttu-id="d20d7-120">Pour plus d’informations, consultez [Guide pratique pour s’abonner et annuler l’abonnement à des événements](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="d20d7-120">For more information, see [How to: subscribe to and unsubscribe from events](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="d20d7-121">Capacité de surcharge de l’opérateur</span><span class="sxs-lookup"><span data-stu-id="d20d7-121">Operator overloadability</span></span>

<span data-ttu-id="d20d7-122">Un type défini par l’utilisateur peut [surcharger](operator-overloading.md) l’opérateur `+`.</span><span class="sxs-lookup"><span data-stu-id="d20d7-122">A user-defined type can [overload](operator-overloading.md) the `+` operator.</span></span> <span data-ttu-id="d20d7-123">Quand un opérateur binaire `+` est surchargé, l’opérateur `+=` est aussi implicitement surchargé.</span><span class="sxs-lookup"><span data-stu-id="d20d7-123">When a binary `+` operator is overloaded, the `+=` operator is also implicitly overloaded.</span></span> <span data-ttu-id="d20d7-124">Un type défini par l’utilisateur ne peut pas surcharger explicitement l’opérateur `+=`.</span><span class="sxs-lookup"><span data-stu-id="d20d7-124">A user-defined type cannot explicitly overload the `+=` operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="d20d7-125">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="d20d7-125">C# language specification</span></span>

<span data-ttu-id="d20d7-126">Pour plus d’informations, consultez les sections [Opérateur unaire plus](~/_csharplang/spec/expressions.md#unary-plus-operator) et [Opérateur d’addition](~/_csharplang/spec/expressions.md#addition-operator) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="d20d7-126">For more information, see the [Unary plus operator](~/_csharplang/spec/expressions.md#unary-plus-operator) and [Addition operator](~/_csharplang/spec/expressions.md#addition-operator) sections of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d20d7-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d20d7-127">See also</span></span>

- [<span data-ttu-id="d20d7-128">Référence C#</span><span class="sxs-lookup"><span data-stu-id="d20d7-128">C# reference</span></span>](../index.md)
- [<span data-ttu-id="d20d7-129">Opérateurs CMD</span><span class="sxs-lookup"><span data-stu-id="d20d7-129">C# operators</span></span>](index.md)
- [<span data-ttu-id="d20d7-130">Comment concatenate plusieurs cordes</span><span class="sxs-lookup"><span data-stu-id="d20d7-130">How to concatenate multiple strings</span></span>](../../how-to/concatenate-multiple-strings.md)
- [<span data-ttu-id="d20d7-131">Événements</span><span class="sxs-lookup"><span data-stu-id="d20d7-131">Events</span></span>](../../programming-guide/events/index.md)
- [<span data-ttu-id="d20d7-132">Opérateurs d’arithmétique</span><span class="sxs-lookup"><span data-stu-id="d20d7-132">Arithmetic operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="d20d7-133">- et -- opérateurs</span><span class="sxs-lookup"><span data-stu-id="d20d7-133">- and -= operators</span></span>](subtraction-operator.md)
