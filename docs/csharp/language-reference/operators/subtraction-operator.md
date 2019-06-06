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
ms.openlocfilehash: 9f43a863de69122e251204668af2ea989fcc993c
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66300091"
---
# <a name="--and---operators-c-reference"></a><span data-ttu-id="bc537-102">- et -=, opérateurs (référence C#)</span><span class="sxs-lookup"><span data-stu-id="bc537-102">- and -= operators (C# Reference)</span></span>

<span data-ttu-id="bc537-103">L’opérateur `-` est pris en charge par les types numériques intégrés et les types [délégués](../keywords/delegate.md).</span><span class="sxs-lookup"><span data-stu-id="bc537-103">The `-` operator is supported by the built-in numeric types and [delegate](../keywords/delegate.md) types.</span></span>

<span data-ttu-id="bc537-104">Pour plus d’informations sur l’opérateur arithmétique `-`, consultez les sections [Opérateurs plus et moins unaires](arithmetic-operators.md#unary-plus-and-minus-operators) et [Opérateur de soustraction -](arithmetic-operators.md#subtraction-operator--) de l’article [Opérateurs arithmétiques](arithmetic-operators.md).</span><span class="sxs-lookup"><span data-stu-id="bc537-104">For information about the arithmetic `-` operator, see the [Unary plus and minus operators](arithmetic-operators.md#unary-plus-and-minus-operators) and [Subtraction operator -](arithmetic-operators.md#subtraction-operator--) sections of the [Arithmetic operators](arithmetic-operators.md) article.</span></span>

## <a name="delegate-removal"></a><span data-ttu-id="bc537-105">Suppression de délégué</span><span class="sxs-lookup"><span data-stu-id="bc537-105">Delegate removal</span></span>

<span data-ttu-id="bc537-106">Pour les opérandes du même type [délégué](../keywords/delegate.md), l’opérateur `-` retourne une instance de délégué qui est calculée comme suit :</span><span class="sxs-lookup"><span data-stu-id="bc537-106">For operands of the same [delegate](../keywords/delegate.md) type, the `-` operator returns a delegate instance that is calculated as follows:</span></span>

- <span data-ttu-id="bc537-107">Si les deux opérandes ont des valeurs non Null et que la liste d’appel du deuxième opérande est une sous-liste contiguë correcte de la liste d’appel du premier opérande, le résultat de l’opération est une nouvelle liste d’appel qui est obtenue en supprimant les entrées du deuxième opérande à partir de la liste d’appel du premier opérande.</span><span class="sxs-lookup"><span data-stu-id="bc537-107">If both operands are non-null and the invocation list of the second operand is a proper contiguous sublist of the invocation list of the first operand, the result of the operation is a new invocation list that is obtained by removing the second operand's entries from the invocation list of the first operand.</span></span> <span data-ttu-id="bc537-108">Si la liste du deuxième opérande correspond à plusieurs sous-listes contiguës dans la liste du premier opérande, seule la sous-liste correspondante la plus à droite est supprimée.</span><span class="sxs-lookup"><span data-stu-id="bc537-108">If the second operand's list matches multiple contiguous sublists in the first operand's list, only the right-most matching sublist is removed.</span></span> <span data-ttu-id="bc537-109">Si la suppression aboutit à une liste vide, le résultat est `null`.</span><span class="sxs-lookup"><span data-stu-id="bc537-109">If removal results in an empty list, the result is `null`.</span></span>
- <span data-ttu-id="bc537-110">Si la liste d’appel du second opérande n’est pas une sous-liste contiguë correcte de la liste d’appel du premier opérande, le résultat de l’opération est le premier opérande.</span><span class="sxs-lookup"><span data-stu-id="bc537-110">If the invocation list of the second operand is not a proper contiguous sublist of the invocation list of the first operand, the result of the operation is the first operand.</span></span>
- <span data-ttu-id="bc537-111">Si le premier opérande a la valeur `null`, le résultat de l’opération est `null`.</span><span class="sxs-lookup"><span data-stu-id="bc537-111">If the first operand is `null`, the result of the operation is `null`.</span></span> <span data-ttu-id="bc537-112">Si le second opérande a la valeur `null`, le résultat de l’opération est le premier opérande.</span><span class="sxs-lookup"><span data-stu-id="bc537-112">If the second operand is `null`, the result of the operation is the first operand.</span></span>

<span data-ttu-id="bc537-113">L’exemple suivant montre comment l’opération `-` effectue la suppression de délégué :</span><span class="sxs-lookup"><span data-stu-id="bc537-113">The following example shows how the `-` operation performs delegate removal:</span></span>

[!code-csharp-interactive[delegate removal](~/samples/csharp/language-reference/operators/SubtractionOperator.cs#DelegateRemoval)]

## <a name="subtraction-assignment-operator--"></a><span data-ttu-id="bc537-114">Opérateur d’assignation de soustraction -=</span><span class="sxs-lookup"><span data-stu-id="bc537-114">Subtraction assignment operator -=</span></span>

<span data-ttu-id="bc537-115">Expression utilisant l’opérateur `-=`, par exemple</span><span class="sxs-lookup"><span data-stu-id="bc537-115">An expression using the `-=` operator, such as</span></span>

```csharp
x -= y
```

<span data-ttu-id="bc537-116">est équivalent à</span><span class="sxs-lookup"><span data-stu-id="bc537-116">is equivalent to</span></span>

```csharp
x = x - y
```

<span data-ttu-id="bc537-117">sauf que `x` n’est évalué qu’une seule fois.</span><span class="sxs-lookup"><span data-stu-id="bc537-117">except that `x` is only evaluated once.</span></span>
  
<span data-ttu-id="bc537-118">L’exemple suivant illustre l’utilisation de l’opérateur `-=` :</span><span class="sxs-lookup"><span data-stu-id="bc537-118">The following example demonstrates the usage of the `-=` operator:</span></span>

[!code-csharp-interactive[-= examples](~/samples/csharp/language-reference/operators/SubtractionOperator.cs#SubtractAndAssign)]

<span data-ttu-id="bc537-119">Vous utilisez également l’opérateur `-=` pour spécifier une méthode de gestionnaire d’événements à supprimer quand vous vous désabonnez d’un [événement](../keywords/event.md).</span><span class="sxs-lookup"><span data-stu-id="bc537-119">You also use the `-=` operator to specify an event handler method to remove when you unsubscribe from an [event](../keywords/event.md).</span></span> <span data-ttu-id="bc537-120">Pour plus d’informations, consultez [Guide pratique pour s’abonner et annuler l’abonnement à des événements](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="bc537-120">For more information, see [How to: subscribe to and unsubscribe from events](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="bc537-121">Capacité de surcharge de l’opérateur</span><span class="sxs-lookup"><span data-stu-id="bc537-121">Operator overloadability</span></span>

<span data-ttu-id="bc537-122">Un type défini par l’utilisateur peut [surcharger](../keywords/operator.md) l’opérateur `-`.</span><span class="sxs-lookup"><span data-stu-id="bc537-122">A user-defined type can [overload](../keywords/operator.md) the `-` operator.</span></span> <span data-ttu-id="bc537-123">Quand un opérateur binaire `-` est surchargé, l’opérateur `-=` est aussi implicitement surchargé.</span><span class="sxs-lookup"><span data-stu-id="bc537-123">When a binary `-` operator is overloaded, the `-=` operator is also implicitly overloaded.</span></span> <span data-ttu-id="bc537-124">Un type défini par l’utilisateur ne peut pas surcharger explicitement l’opérateur `-=`.</span><span class="sxs-lookup"><span data-stu-id="bc537-124">A user-defined type cannot explicitly overload the `-=` operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="bc537-125">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="bc537-125">C# language specification</span></span>

<span data-ttu-id="bc537-126">Pour plus d’informations, consultez les sections [Opérateur moins unaire](~/_csharplang/spec/expressions.md#unary-minus-operator) et [Opérateur de soustraction](~/_csharplang/spec/expressions.md#subtraction-operator) de la [spécification du langage C#](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="bc537-126">For more information, see the [Unary minus operator](~/_csharplang/spec/expressions.md#unary-minus-operator) and [Subtraction operator](~/_csharplang/spec/expressions.md#subtraction-operator) sections of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="bc537-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bc537-127">See also</span></span>

- [<span data-ttu-id="bc537-128">Référence C#</span><span class="sxs-lookup"><span data-stu-id="bc537-128">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="bc537-129">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="bc537-129">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="bc537-130">Opérateurs C#</span><span class="sxs-lookup"><span data-stu-id="bc537-130">C# Operators</span></span>](index.md)
- [<span data-ttu-id="bc537-131">Délégués</span><span class="sxs-lookup"><span data-stu-id="bc537-131">Delegates</span></span>](../../programming-guide/delegates/index.md)
- [<span data-ttu-id="bc537-132">Événements</span><span class="sxs-lookup"><span data-stu-id="bc537-132">Events</span></span>](../../programming-guide/events/index.md)
- [<span data-ttu-id="bc537-133">Checked et unchecked</span><span class="sxs-lookup"><span data-stu-id="bc537-133">Checked and unchecked</span></span>](../keywords/checked-and-unchecked.md)
- [<span data-ttu-id="bc537-134">Opérateurs arithmétiques</span><span class="sxs-lookup"><span data-stu-id="bc537-134">Arithmetic operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="bc537-135">+ et +=, opérateurs</span><span class="sxs-lookup"><span data-stu-id="bc537-135">+ and += operators</span></span>](addition-operator.md)
