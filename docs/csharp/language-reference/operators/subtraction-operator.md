---
title: '- - et -=, opérateurs - Référence C#'
ms.custom: seodec18
ms.date: 05/27/2019
f1_keywords:
- -_CSharpKeyword
- -=_CSharpKeyword
helpviewer_keywords:
- subtraction operator [C#]
- delegate removal [C#]
- '- operator [C#]'
- subtraction assignment operator [C#]
- event unsubscription [C#]
- -= operator [C#]
ms.assetid: 4de7a4fa-c69d-48e6-aff1-3130af970b2d
ms.openlocfilehash: aae10f8b03a16e55f0b26981f17585c8790e00c1
ms.sourcegitcommit: 5ae6affa0b171be3bb5f4729fb68ea4fe799f959
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/10/2019
ms.locfileid: "66816074"
---
# <a name="--and---operators-c-reference"></a><span data-ttu-id="c34e7-102">- et -=, opérateurs (référence C#)</span><span class="sxs-lookup"><span data-stu-id="c34e7-102">- and -= operators (C# Reference)</span></span>

<span data-ttu-id="c34e7-103">L’opérateur `-` est pris en charge par les types numériques intégrés et les types [délégués](../keywords/delegate.md).</span><span class="sxs-lookup"><span data-stu-id="c34e7-103">The `-` operator is supported by the built-in numeric types and [delegate](../keywords/delegate.md) types.</span></span>

<span data-ttu-id="c34e7-104">Pour plus d’informations sur l’opérateur arithmétique `-`, consultez les sections [Opérateurs plus et moins unaires](arithmetic-operators.md#unary-plus-and-minus-operators) et [Opérateur de soustraction -](arithmetic-operators.md#subtraction-operator--) de l’article [Opérateurs arithmétiques](arithmetic-operators.md).</span><span class="sxs-lookup"><span data-stu-id="c34e7-104">For information about the arithmetic `-` operator, see the [Unary plus and minus operators](arithmetic-operators.md#unary-plus-and-minus-operators) and [Subtraction operator -](arithmetic-operators.md#subtraction-operator--) sections of the [Arithmetic operators](arithmetic-operators.md) article.</span></span>

## <a name="delegate-removal"></a><span data-ttu-id="c34e7-105">Suppression de délégué</span><span class="sxs-lookup"><span data-stu-id="c34e7-105">Delegate removal</span></span>

<span data-ttu-id="c34e7-106">Pour les opérandes du même type [délégué](../keywords/delegate.md), l’opérateur `-` retourne une instance de délégué qui est calculée comme suit :</span><span class="sxs-lookup"><span data-stu-id="c34e7-106">For operands of the same [delegate](../keywords/delegate.md) type, the `-` operator returns a delegate instance that is calculated as follows:</span></span>

- <span data-ttu-id="c34e7-107">Si les deux opérandes ont des valeurs non Null et que la liste d’appel du deuxième opérande est une sous-liste contiguë correcte de la liste d’appel du premier opérande, le résultat de l’opération est une nouvelle liste d’appel qui est obtenue en supprimant les entrées du deuxième opérande à partir de la liste d’appel du premier opérande.</span><span class="sxs-lookup"><span data-stu-id="c34e7-107">If both operands are non-null and the invocation list of the second operand is a proper contiguous sublist of the invocation list of the first operand, the result of the operation is a new invocation list that is obtained by removing the second operand's entries from the invocation list of the first operand.</span></span> <span data-ttu-id="c34e7-108">Si la liste du deuxième opérande correspond à plusieurs sous-listes contiguës dans la liste du premier opérande, seule la sous-liste correspondante la plus à droite est supprimée.</span><span class="sxs-lookup"><span data-stu-id="c34e7-108">If the second operand's list matches multiple contiguous sublists in the first operand's list, only the right-most matching sublist is removed.</span></span> <span data-ttu-id="c34e7-109">Si la suppression aboutit à une liste vide, le résultat est `null`.</span><span class="sxs-lookup"><span data-stu-id="c34e7-109">If removal results in an empty list, the result is `null`.</span></span>

  [!code-csharp-interactive[delegate removal](~/samples/csharp/language-reference/operators/SubtractionOperator.cs#DelegateRemoval)]

- <span data-ttu-id="c34e7-110">Si la liste d’appel du second opérande n’est pas une sous-liste contiguë correcte de la liste d’appel du premier opérande, le résultat de l’opération est le premier opérande.</span><span class="sxs-lookup"><span data-stu-id="c34e7-110">If the invocation list of the second operand is not a proper contiguous sublist of the invocation list of the first operand, the result of the operation is the first operand.</span></span> <span data-ttu-id="c34e7-111">Par exemple, la suppression d’un délégué qui ne fait pas partie du délégué multicast ne fait rien et entraîne le délégué multicast inchangé.</span><span class="sxs-lookup"><span data-stu-id="c34e7-111">For example, removing a delegate that is not part of the multicast delegate does nothing and results in the unchanged multicast delegate.</span></span>

  [!code-csharp-interactive[delegate removal with no effect](~/samples/csharp/language-reference/operators/SubtractionOperator.cs#DelegateRemovalNoChange)]

  <span data-ttu-id="c34e7-112">L’exemple précédent montre également que les instances de délégué de suppression sont comparés au cours de délégué.</span><span class="sxs-lookup"><span data-stu-id="c34e7-112">The preceding example also demonstrates that during delegate removal delegate instances are compared.</span></span> <span data-ttu-id="c34e7-113">Par exemple, les délégués qui sont produites à partir de la version d’évaluation d’identiques [expressions lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md) ne sont pas égaux.</span><span class="sxs-lookup"><span data-stu-id="c34e7-113">For example, delegates that are produced from evaluation of identical [lambda expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md) are not equal.</span></span> <span data-ttu-id="c34e7-114">Pour plus d’informations sur l’égalité de délégué, consultez le [déléguer des opérateurs d’égalité](~/_csharplang/spec/expressions.md#delegate-equality-operators) section de la [ C# spécification du langage](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="c34e7-114">For more information about delegate equality, see the [Delegate equality operators](~/_csharplang/spec/expressions.md#delegate-equality-operators) section of the [C# language specification](../language-specification/index.md).</span></span>

- <span data-ttu-id="c34e7-115">Si le premier opérande a la valeur `null`, le résultat de l’opération est `null`.</span><span class="sxs-lookup"><span data-stu-id="c34e7-115">If the first operand is `null`, the result of the operation is `null`.</span></span> <span data-ttu-id="c34e7-116">Si le second opérande a la valeur `null`, le résultat de l’opération est le premier opérande.</span><span class="sxs-lookup"><span data-stu-id="c34e7-116">If the second operand is `null`, the result of the operation is the first operand.</span></span>

  [!code-csharp-interactive[delegate removal and null](~/samples/csharp/language-reference/operators/SubtractionOperator.cs#DelegateRemovalAndNull)]

<span data-ttu-id="c34e7-117">Pour combiner des délégués, utilisez le [ `+` opérateur](addition-operator.md#delegate-combination).</span><span class="sxs-lookup"><span data-stu-id="c34e7-117">To combine delegates, use the [`+` operator](addition-operator.md#delegate-combination).</span></span>

<span data-ttu-id="c34e7-118">Pour plus d'informations sur les types de délégués, consultez [Délégués](../../programming-guide/delegates/index.md).</span><span class="sxs-lookup"><span data-stu-id="c34e7-118">For more information about delegate types, see [Delegates](../../programming-guide/delegates/index.md).</span></span>

## <a name="subtraction-assignment-operator--"></a><span data-ttu-id="c34e7-119">Opérateur d’assignation de soustraction -=</span><span class="sxs-lookup"><span data-stu-id="c34e7-119">Subtraction assignment operator -=</span></span>

<span data-ttu-id="c34e7-120">Expression utilisant l’opérateur `-=`, par exemple</span><span class="sxs-lookup"><span data-stu-id="c34e7-120">An expression using the `-=` operator, such as</span></span>

```csharp
x -= y
```

<span data-ttu-id="c34e7-121">est équivalent à</span><span class="sxs-lookup"><span data-stu-id="c34e7-121">is equivalent to</span></span>

```csharp
x = x - y
```

<span data-ttu-id="c34e7-122">sauf que `x` n’est évalué qu’une seule fois.</span><span class="sxs-lookup"><span data-stu-id="c34e7-122">except that `x` is only evaluated once.</span></span>
  
<span data-ttu-id="c34e7-123">L’exemple suivant illustre l’utilisation de l’opérateur `-=` :</span><span class="sxs-lookup"><span data-stu-id="c34e7-123">The following example demonstrates the usage of the `-=` operator:</span></span>

[!code-csharp-interactive[-= examples](~/samples/csharp/language-reference/operators/SubtractionOperator.cs#SubtractAndAssign)]

<span data-ttu-id="c34e7-124">Vous utilisez également l’opérateur `-=` pour spécifier une méthode de gestionnaire d’événements à supprimer quand vous vous désabonnez d’un [événement](../keywords/event.md).</span><span class="sxs-lookup"><span data-stu-id="c34e7-124">You also use the `-=` operator to specify an event handler method to remove when you unsubscribe from an [event](../keywords/event.md).</span></span> <span data-ttu-id="c34e7-125">Pour plus d’informations, consultez [Guide pratique pour s’abonner et annuler l’abonnement à des événements](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="c34e7-125">For more information, see [How to: subscribe to and unsubscribe from events](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="c34e7-126">Capacité de surcharge de l’opérateur</span><span class="sxs-lookup"><span data-stu-id="c34e7-126">Operator overloadability</span></span>

<span data-ttu-id="c34e7-127">Un type défini par l’utilisateur peut [surcharger](../keywords/operator.md) l’opérateur `-`.</span><span class="sxs-lookup"><span data-stu-id="c34e7-127">A user-defined type can [overload](../keywords/operator.md) the `-` operator.</span></span> <span data-ttu-id="c34e7-128">Quand un opérateur binaire `-` est surchargé, l’opérateur `-=` est aussi implicitement surchargé.</span><span class="sxs-lookup"><span data-stu-id="c34e7-128">When a binary `-` operator is overloaded, the `-=` operator is also implicitly overloaded.</span></span> <span data-ttu-id="c34e7-129">Un type défini par l’utilisateur ne peut pas surcharger explicitement l’opérateur `-=`.</span><span class="sxs-lookup"><span data-stu-id="c34e7-129">A user-defined type cannot explicitly overload the `-=` operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="c34e7-130">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="c34e7-130">C# language specification</span></span>

<span data-ttu-id="c34e7-131">Pour plus d’informations, consultez les sections [Opérateur moins unaire](~/_csharplang/spec/expressions.md#unary-minus-operator) et [Opérateur de soustraction](~/_csharplang/spec/expressions.md#subtraction-operator) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="c34e7-131">For more information, see the [Unary minus operator](~/_csharplang/spec/expressions.md#unary-minus-operator) and [Subtraction operator](~/_csharplang/spec/expressions.md#subtraction-operator) sections of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c34e7-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c34e7-132">See also</span></span>

- [<span data-ttu-id="c34e7-133">Référence C#</span><span class="sxs-lookup"><span data-stu-id="c34e7-133">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="c34e7-134">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="c34e7-134">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="c34e7-135">Opérateurs C#</span><span class="sxs-lookup"><span data-stu-id="c34e7-135">C# Operators</span></span>](index.md)
- [<span data-ttu-id="c34e7-136">Délégués</span><span class="sxs-lookup"><span data-stu-id="c34e7-136">Delegates</span></span>](../../programming-guide/delegates/index.md)
- [<span data-ttu-id="c34e7-137">Événements</span><span class="sxs-lookup"><span data-stu-id="c34e7-137">Events</span></span>](../../programming-guide/events/index.md)
- [<span data-ttu-id="c34e7-138">Checked et unchecked</span><span class="sxs-lookup"><span data-stu-id="c34e7-138">Checked and unchecked</span></span>](../keywords/checked-and-unchecked.md)
- [<span data-ttu-id="c34e7-139">Opérateurs arithmétiques</span><span class="sxs-lookup"><span data-stu-id="c34e7-139">Arithmetic operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="c34e7-140">+ et +=, opérateurs</span><span class="sxs-lookup"><span data-stu-id="c34e7-140">+ and += operators</span></span>](addition-operator.md)
