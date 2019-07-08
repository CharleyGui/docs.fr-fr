---
title: '- et -=, opérateurs - Référence C#'
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
ms.openlocfilehash: 80603107beb708e76a2c7446f300d71ede411570
ms.sourcegitcommit: eaa6d5cd0f4e7189dbe0bd756e9f53508b01989e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2019
ms.locfileid: "67609854"
---
# <a name="--and---operators-c-reference"></a><span data-ttu-id="06e27-102">Opérateurs - et -=, opérateurs - (référence C#)</span><span class="sxs-lookup"><span data-stu-id="06e27-102">- and -= operators (C# reference)</span></span>

<span data-ttu-id="06e27-103">L’opérateur `-` est pris en charge par les types numériques intégrés et les types [délégués](../keywords/delegate.md).</span><span class="sxs-lookup"><span data-stu-id="06e27-103">The `-` operator is supported by the built-in numeric types and [delegate](../keywords/delegate.md) types.</span></span>

<span data-ttu-id="06e27-104">Pour plus d’informations sur l’opérateur arithmétique `-`, consultez les sections [Opérateurs plus et moins unaires](arithmetic-operators.md#unary-plus-and-minus-operators) et [Opérateur de soustraction -](arithmetic-operators.md#subtraction-operator--) de l’article [Opérateurs arithmétiques](arithmetic-operators.md).</span><span class="sxs-lookup"><span data-stu-id="06e27-104">For information about the arithmetic `-` operator, see the [Unary plus and minus operators](arithmetic-operators.md#unary-plus-and-minus-operators) and [Subtraction operator -](arithmetic-operators.md#subtraction-operator--) sections of the [Arithmetic operators](arithmetic-operators.md) article.</span></span>

## <a name="delegate-removal"></a><span data-ttu-id="06e27-105">Suppression de délégué</span><span class="sxs-lookup"><span data-stu-id="06e27-105">Delegate removal</span></span>

<span data-ttu-id="06e27-106">Pour les opérandes du même type [délégué](../keywords/delegate.md), l’opérateur `-` retourne une instance de délégué qui est calculée comme suit :</span><span class="sxs-lookup"><span data-stu-id="06e27-106">For operands of the same [delegate](../keywords/delegate.md) type, the `-` operator returns a delegate instance that is calculated as follows:</span></span>

- <span data-ttu-id="06e27-107">Si les deux opérandes ont des valeurs non Null et que la liste d’appel de l’opérande de partie droite est une sous-liste contiguë correcte de la liste d’appel de l’opérande de partie droite, le résultat de l’opération est une nouvelle liste d’appel obtenue en supprimant les entrées de l’opérande de partie droite à partir de la liste d’appel de l’opérande de gauche.</span><span class="sxs-lookup"><span data-stu-id="06e27-107">If both operands are non-null and the invocation list of the right-hand operand is a proper contiguous sublist of the invocation list of the left-hand operand, the result of the operation is a new invocation list that is obtained by removing the right-hand operand's entries from the invocation list of the left-hand operand.</span></span> <span data-ttu-id="06e27-108">Si la liste des opérandes de partie droite correspond à plusieurs sous-listes contiguës dans la liste des opérandes de partie gauche, seule la sous-liste correspondante la plus à droite est supprimée.</span><span class="sxs-lookup"><span data-stu-id="06e27-108">If the right-hand operand's list matches multiple contiguous sublists in the left-hand operand's list, only the right-most matching sublist is removed.</span></span> <span data-ttu-id="06e27-109">Si la suppression aboutit à une liste vide, le résultat est `null`.</span><span class="sxs-lookup"><span data-stu-id="06e27-109">If removal results in an empty list, the result is `null`.</span></span>

  [!code-csharp-interactive[delegate removal](~/samples/csharp/language-reference/operators/SubtractionOperator.cs#DelegateRemoval)]

- <span data-ttu-id="06e27-110">Si la liste d’appel de l’opérande de partie droite n’est pas une sous-liste contiguë correcte de la liste d’appel de l’opérande de partie gauche, le résultat de l’opération est l’opérande de partie gauche.</span><span class="sxs-lookup"><span data-stu-id="06e27-110">If the invocation list of the right-hand operand is not a proper contiguous sublist of the invocation list of the left-hand operand, the result of the operation is the left-hand operand.</span></span> <span data-ttu-id="06e27-111">Par exemple, la suppression d’un délégué qui ne fait pas partie du délégué multicast ne fait rien et génère un délégué multicast inchangé.</span><span class="sxs-lookup"><span data-stu-id="06e27-111">For example, removing a delegate that is not part of the multicast delegate does nothing and results in the unchanged multicast delegate.</span></span>

  [!code-csharp-interactive[delegate removal with no effect](~/samples/csharp/language-reference/operators/SubtractionOperator.cs#DelegateRemovalNoChange)]

  <span data-ttu-id="06e27-112">L’exemple précédent montre également que durant la suppression de délégué, les instances de délégués sont comparées.</span><span class="sxs-lookup"><span data-stu-id="06e27-112">The preceding example also demonstrates that during delegate removal delegate instances are compared.</span></span> <span data-ttu-id="06e27-113">Par exemple, les délégués qui sont produits à partir de l’évaluation d’[expressions lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md) identiques ne sont pas égaux.</span><span class="sxs-lookup"><span data-stu-id="06e27-113">For example, delegates that are produced from evaluation of identical [lambda expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md) are not equal.</span></span> <span data-ttu-id="06e27-114">Pour plus d’informations sur l’égalité des délégués, consultez la section [Opérateurs d’égalité de délégués](~/_csharplang/spec/expressions.md#delegate-equality-operators) de la [spécification du langage C#](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="06e27-114">For more information about delegate equality, see the [Delegate equality operators](~/_csharplang/spec/expressions.md#delegate-equality-operators) section of the [C# language specification](../language-specification/index.md).</span></span>

- <span data-ttu-id="06e27-115">Si l’opérande de partie gauche est `null`, le résultat de l’opération est `null`.</span><span class="sxs-lookup"><span data-stu-id="06e27-115">If the left-hand operand is `null`, the result of the operation is `null`.</span></span> <span data-ttu-id="06e27-116">Si l’opérande de partie droite est `null`, le résultat de l’opération est l’opérande de partie gauche.</span><span class="sxs-lookup"><span data-stu-id="06e27-116">If the right-hand operand is `null`, the result of the operation is the left-hand operand.</span></span>

  [!code-csharp-interactive[delegate removal and null](~/samples/csharp/language-reference/operators/SubtractionOperator.cs#DelegateRemovalAndNull)]

<span data-ttu-id="06e27-117">Pour combiner des délégués, utilisez l’[opérateur `+`](addition-operator.md#delegate-combination).</span><span class="sxs-lookup"><span data-stu-id="06e27-117">To combine delegates, use the [`+` operator](addition-operator.md#delegate-combination).</span></span>

<span data-ttu-id="06e27-118">Pour plus d'informations sur les types de délégués, consultez [Délégués](../../programming-guide/delegates/index.md).</span><span class="sxs-lookup"><span data-stu-id="06e27-118">For more information about delegate types, see [Delegates](../../programming-guide/delegates/index.md).</span></span>

## <a name="subtraction-assignment-operator--"></a><span data-ttu-id="06e27-119">Opérateur d’assignation de soustraction -=</span><span class="sxs-lookup"><span data-stu-id="06e27-119">Subtraction assignment operator -=</span></span>

<span data-ttu-id="06e27-120">Expression utilisant l’opérateur `-=`, par exemple</span><span class="sxs-lookup"><span data-stu-id="06e27-120">An expression using the `-=` operator, such as</span></span>

```csharp
x -= y
```

<span data-ttu-id="06e27-121">est équivalent à</span><span class="sxs-lookup"><span data-stu-id="06e27-121">is equivalent to</span></span>

```csharp
x = x - y
```

<span data-ttu-id="06e27-122">sauf que `x` n’est évalué qu’une seule fois.</span><span class="sxs-lookup"><span data-stu-id="06e27-122">except that `x` is only evaluated once.</span></span>
  
<span data-ttu-id="06e27-123">L’exemple suivant illustre l’utilisation de l’opérateur `-=` :</span><span class="sxs-lookup"><span data-stu-id="06e27-123">The following example demonstrates the usage of the `-=` operator:</span></span>

[!code-csharp-interactive[-= examples](~/samples/csharp/language-reference/operators/SubtractionOperator.cs#SubtractAndAssign)]

<span data-ttu-id="06e27-124">Vous utilisez également l’opérateur `-=` pour spécifier une méthode de gestionnaire d’événements à supprimer quand vous vous désabonnez d’un [événement](../keywords/event.md).</span><span class="sxs-lookup"><span data-stu-id="06e27-124">You also use the `-=` operator to specify an event handler method to remove when you unsubscribe from an [event](../keywords/event.md).</span></span> <span data-ttu-id="06e27-125">Pour plus d’informations, consultez [Guide pratique pour s’abonner et annuler l’abonnement à des événements](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="06e27-125">For more information, see [How to: subscribe to and unsubscribe from events](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="06e27-126">Capacité de surcharge de l’opérateur</span><span class="sxs-lookup"><span data-stu-id="06e27-126">Operator overloadability</span></span>

<span data-ttu-id="06e27-127">Un type défini par l’utilisateur peut [surcharger](operator-overloading.md) l’opérateur `-`.</span><span class="sxs-lookup"><span data-stu-id="06e27-127">A user-defined type can [overload](operator-overloading.md) the `-` operator.</span></span> <span data-ttu-id="06e27-128">Quand un opérateur binaire `-` est surchargé, l’opérateur `-=` est aussi implicitement surchargé.</span><span class="sxs-lookup"><span data-stu-id="06e27-128">When a binary `-` operator is overloaded, the `-=` operator is also implicitly overloaded.</span></span> <span data-ttu-id="06e27-129">Un type défini par l’utilisateur ne peut pas surcharger explicitement l’opérateur `-=`.</span><span class="sxs-lookup"><span data-stu-id="06e27-129">A user-defined type cannot explicitly overload the `-=` operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="06e27-130">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="06e27-130">C# language specification</span></span>

<span data-ttu-id="06e27-131">Pour plus d’informations, consultez les sections [Opérateur moins unaire](~/_csharplang/spec/expressions.md#unary-minus-operator) et [Opérateur de soustraction](~/_csharplang/spec/expressions.md#subtraction-operator) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="06e27-131">For more information, see the [Unary minus operator](~/_csharplang/spec/expressions.md#unary-minus-operator) and [Subtraction operator](~/_csharplang/spec/expressions.md#subtraction-operator) sections of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="06e27-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="06e27-132">See also</span></span>

- [<span data-ttu-id="06e27-133">Informations de référence sur C#</span><span class="sxs-lookup"><span data-stu-id="06e27-133">C# reference</span></span>](../index.md)
- [<span data-ttu-id="06e27-134">Opérateurs C#</span><span class="sxs-lookup"><span data-stu-id="06e27-134">C# operators</span></span>](index.md)
- [<span data-ttu-id="06e27-135">Délégués</span><span class="sxs-lookup"><span data-stu-id="06e27-135">Delegates</span></span>](../../programming-guide/delegates/index.md)
- [<span data-ttu-id="06e27-136">Événements</span><span class="sxs-lookup"><span data-stu-id="06e27-136">Events</span></span>](../../programming-guide/events/index.md)
- [<span data-ttu-id="06e27-137">Opérateurs arithmétiques</span><span class="sxs-lookup"><span data-stu-id="06e27-137">Arithmetic operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="06e27-138">+ et +=, opérateurs</span><span class="sxs-lookup"><span data-stu-id="06e27-138">+ and += operators</span></span>](addition-operator.md)
