---
title: + et +=, opérateurs - Référence C#
ms.date: 04/23/2020
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
ms.openlocfilehash: 18364d80b8117fd4074c2c4231eac07c76829bb3
ms.sourcegitcommit: 8b02d42f93adda304246a47f49f6449fc74a3af4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2020
ms.locfileid: "82135735"
---
# <a name="-and--operators-c-reference"></a><span data-ttu-id="102b4-102">+ et +=, opérateurs (référence C#)</span><span class="sxs-lookup"><span data-stu-id="102b4-102">+ and += operators (C# reference)</span></span>

<span data-ttu-id="102b4-103">Les `+` opérateurs `+=` et sont pris en charge par les types numériques [intégraux](../builtin-types/integral-numeric-types.md) et à [virgule flottante](../builtin-types/floating-point-numeric-types.md) intégrés, le type de [chaîne](../builtin-types/reference-types.md#the-string-type) et les types [délégués](../builtin-types/reference-types.md#the-delegate-type) .</span><span class="sxs-lookup"><span data-stu-id="102b4-103">The `+` and `+=` operators are supported by the built-in [integral](../builtin-types/integral-numeric-types.md) and [floating-point](../builtin-types/floating-point-numeric-types.md) numeric types, the [string](../builtin-types/reference-types.md#the-string-type) type, and [delegate](../builtin-types/reference-types.md#the-delegate-type) types.</span></span>

<span data-ttu-id="102b4-104">Pour plus d’informations sur l’opérateur arithmétique `+`, consultez les sections [Opérateurs plus et moins unaires](arithmetic-operators.md#unary-plus-and-minus-operators) et [Opérateur d’addition +](arithmetic-operators.md#addition-operator-) de l’article [Opérateurs arithmétiques](arithmetic-operators.md).</span><span class="sxs-lookup"><span data-stu-id="102b4-104">For information about the arithmetic `+` operator, see the [Unary plus and minus operators](arithmetic-operators.md#unary-plus-and-minus-operators) and [Addition operator +](arithmetic-operators.md#addition-operator-) sections of the [Arithmetic operators](arithmetic-operators.md) article.</span></span>

## <a name="string-concatenation"></a><span data-ttu-id="102b4-105">Concaténation de chaînes</span><span class="sxs-lookup"><span data-stu-id="102b4-105">String concatenation</span></span>

<span data-ttu-id="102b4-106">Quand l’un des opérandes ou les deux [string](../builtin-types/reference-types.md#the-string-type)sont de type `+` chaîne, l’opérateur concatène les représentations sous forme de chaîne de ses opérandes `null` (la représentation sous forme de chaîne de est une chaîne vide) :</span><span class="sxs-lookup"><span data-stu-id="102b4-106">When one or both operands are of type [string](../builtin-types/reference-types.md#the-string-type), the `+` operator concatenates the string representations of its operands (the string representation of `null` is an empty string):</span></span>

[!code-csharp-interactive[string concatenation](snippets/AdditionOperator.cs#AddStrings)]

<span data-ttu-id="102b4-107">À compter de C# 6, l' [interpolation de chaîne](../tokens/interpolated.md) offre un moyen plus pratique de mettre en forme les chaînes :</span><span class="sxs-lookup"><span data-stu-id="102b4-107">Beginning with C# 6, [string interpolation](../tokens/interpolated.md) provides a more convenient way to format strings:</span></span>

[!code-csharp-interactive[string interpolation](snippets/AdditionOperator.cs#UseStringInterpolation)]

## <a name="delegate-combination"></a><span data-ttu-id="102b4-108">Combinaison de délégués</span><span class="sxs-lookup"><span data-stu-id="102b4-108">Delegate combination</span></span>

<span data-ttu-id="102b4-109">Pour les opérandes du même type [délégué](../builtin-types/reference-types.md#the-delegate-type), l’opérateur `+` retourne une nouvelle instance de délégué qui, lorsqu’elle est appelée, appelle l’opérande de partie gauche, puis l’opérande de partie droite.</span><span class="sxs-lookup"><span data-stu-id="102b4-109">For operands of the same [delegate](../builtin-types/reference-types.md#the-delegate-type) type, the `+` operator returns a new delegate instance that, when invoked, invokes the left-hand operand and then invokes the right-hand operand.</span></span> <span data-ttu-id="102b4-110">Si un des opérandes est `null`, l’opérateur `+` retourne la valeur de l’autre opérande (qui peut également être `null`).</span><span class="sxs-lookup"><span data-stu-id="102b4-110">If any of the operands is `null`, the `+` operator returns the value of another operand (which also might be `null`).</span></span> <span data-ttu-id="102b4-111">L’exemple suivant montre comment les délégués peuvent être combinés avec l’opérateur `+` :</span><span class="sxs-lookup"><span data-stu-id="102b4-111">The following example shows how delegates can be combined with the `+` operator:</span></span>

[!code-csharp-interactive[delegate combination](snippets/AdditionOperator.cs#AddDelegates)]

<span data-ttu-id="102b4-112">Pour effectuer la suppression d’un délégué, utilisez l' [ `-` opérateur](subtraction-operator.md#delegate-removal).</span><span class="sxs-lookup"><span data-stu-id="102b4-112">To perform delegate removal, use the [`-` operator](subtraction-operator.md#delegate-removal).</span></span>

<span data-ttu-id="102b4-113">Pour plus d'informations sur les types de délégués, consultez [Délégués](../../programming-guide/delegates/index.md).</span><span class="sxs-lookup"><span data-stu-id="102b4-113">For more information about delegate types, see [Delegates](../../programming-guide/delegates/index.md).</span></span>

## <a name="addition-assignment-operator-"></a><span data-ttu-id="102b4-114">Opérateur d’assignation d’addition +=</span><span class="sxs-lookup"><span data-stu-id="102b4-114">Addition assignment operator +=</span></span>

<span data-ttu-id="102b4-115">Expression utilisant l’opérateur `+=`, par exemple</span><span class="sxs-lookup"><span data-stu-id="102b4-115">An expression using the `+=` operator, such as</span></span>

```csharp
x += y
```

<span data-ttu-id="102b4-116">équivaut à :</span><span class="sxs-lookup"><span data-stu-id="102b4-116">is equivalent to</span></span>

```csharp
x = x + y
```

<span data-ttu-id="102b4-117">sauf que `x` n’est évalué qu’une seule fois.</span><span class="sxs-lookup"><span data-stu-id="102b4-117">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="102b4-118">L’exemple suivant illustre l’utilisation de l’opérateur `+=` :</span><span class="sxs-lookup"><span data-stu-id="102b4-118">The following example demonstrates the usage of the `+=` operator:</span></span>

[!code-csharp-interactive[+= examples](snippets/AdditionOperator.cs#AddAndAssign)]

<span data-ttu-id="102b4-119">Vous utilisez également l’opérateur `+=` pour spécifier une méthode de gestionnaire d’événements lorsque vous vous abonnez à un [événement](../keywords/event.md).</span><span class="sxs-lookup"><span data-stu-id="102b4-119">You also use the `+=` operator to specify an event handler method when you subscribe to an [event](../keywords/event.md).</span></span> <span data-ttu-id="102b4-120">Pour plus d’informations, consultez [Guide pratique pour s’abonner et annuler l’abonnement à des événements](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="102b4-120">For more information, see [How to: subscribe to and unsubscribe from events](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="102b4-121">Capacité de surcharge de l’opérateur</span><span class="sxs-lookup"><span data-stu-id="102b4-121">Operator overloadability</span></span>

<span data-ttu-id="102b4-122">Un type défini par l’utilisateur peut [surcharger](operator-overloading.md) l’opérateur `+`.</span><span class="sxs-lookup"><span data-stu-id="102b4-122">A user-defined type can [overload](operator-overloading.md) the `+` operator.</span></span> <span data-ttu-id="102b4-123">Quand un opérateur binaire `+` est surchargé, l’opérateur `+=` est aussi implicitement surchargé.</span><span class="sxs-lookup"><span data-stu-id="102b4-123">When a binary `+` operator is overloaded, the `+=` operator is also implicitly overloaded.</span></span> <span data-ttu-id="102b4-124">Un type défini par l’utilisateur ne peut pas surcharger explicitement l’opérateur `+=`.</span><span class="sxs-lookup"><span data-stu-id="102b4-124">A user-defined type cannot explicitly overload the `+=` operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="102b4-125">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="102b4-125">C# language specification</span></span>

<span data-ttu-id="102b4-126">Pour plus d’informations, consultez les sections [Opérateur unaire plus](~/_csharplang/spec/expressions.md#unary-plus-operator) et [Opérateur d’addition](~/_csharplang/spec/expressions.md#addition-operator) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="102b4-126">For more information, see the [Unary plus operator](~/_csharplang/spec/expressions.md#unary-plus-operator) and [Addition operator](~/_csharplang/spec/expressions.md#addition-operator) sections of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="102b4-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="102b4-127">See also</span></span>

- [<span data-ttu-id="102b4-128">Référence C#</span><span class="sxs-lookup"><span data-stu-id="102b4-128">C# reference</span></span>](../index.md)
- [<span data-ttu-id="102b4-129">Opérateurs C#</span><span class="sxs-lookup"><span data-stu-id="102b4-129">C# operators</span></span>](index.md)
- [<span data-ttu-id="102b4-130">Concaténation de plusieurs chaînes</span><span class="sxs-lookup"><span data-stu-id="102b4-130">How to concatenate multiple strings</span></span>](../../how-to/concatenate-multiple-strings.md)
- [<span data-ttu-id="102b4-131">Événements</span><span class="sxs-lookup"><span data-stu-id="102b4-131">Events</span></span>](../../programming-guide/events/index.md)
- [<span data-ttu-id="102b4-132">Opérateurs arithmétiques</span><span class="sxs-lookup"><span data-stu-id="102b4-132">Arithmetic operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="102b4-133">opérateurs-and-=</span><span class="sxs-lookup"><span data-stu-id="102b4-133">- and -= operators</span></span>](subtraction-operator.md)
