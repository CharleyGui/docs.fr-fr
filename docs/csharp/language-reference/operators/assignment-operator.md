---
title: Opérateur >= - Référence C#
ms.custom: seodec18
ms.date: 09/10/2019
f1_keywords:
- =_CSharpKeyword
helpviewer_keywords:
- = operator [C#]
ms.assetid: d802a6d5-32f0-42b8-b180-12f5a081bfc1
ms.openlocfilehash: a450a55524f33f4f06ed077aba864e8f641a458d
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70924659"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="29e8c-102">Opérateur >= (référence C#)</span><span class="sxs-lookup"><span data-stu-id="29e8c-102">= operator (C# reference)</span></span>

<span data-ttu-id="29e8c-103">L’opérateur d’assignation `=` assigne la valeur de son opérande de droite à une variable, une [propriété](../../programming-guide/classes-and-structs/properties.md) ou un élément [d’indexeur](../../programming-guide/indexers/index.md) donné par son opérande de gauche.</span><span class="sxs-lookup"><span data-stu-id="29e8c-103">The assignment operator `=` assigns the value of its right-hand operand to a variable, a [property](../../programming-guide/classes-and-structs/properties.md), or an [indexer](../../programming-guide/indexers/index.md) element given by its left-hand operand.</span></span> <span data-ttu-id="29e8c-104">Le résultat d’une expression d’assignation est la valeur assignée à l’opérande de gauche.</span><span class="sxs-lookup"><span data-stu-id="29e8c-104">The result of an assignment expression is the value assigned to the left-hand operand.</span></span> <span data-ttu-id="29e8c-105">L’opérande de droite doit être du même type que l’opérande de gauche, ou implicitement convertible vers le type de l’opérande de gauche.</span><span class="sxs-lookup"><span data-stu-id="29e8c-105">The type of the right-hand operand must be the same as the type of the left-hand operand or implicitly convertible to it.</span></span>

<span data-ttu-id="29e8c-106">L’opérateur d’assignation est associatif à droite ; autrement dit, une expression de la forme :</span><span class="sxs-lookup"><span data-stu-id="29e8c-106">The assignment operator is right-associative, that is, an expression of the form</span></span>

```csharp
a = b = c
```

<span data-ttu-id="29e8c-107">est évaluée comme étant</span><span class="sxs-lookup"><span data-stu-id="29e8c-107">is evaluated as</span></span>

```csharp
a = (b = c)
```

<span data-ttu-id="29e8c-108">L’exemple suivant illustre l’utilisation de l’opérateur d’assignation avec une variable locale, une propriété et un élément d’indexeur comme opérande de gauche :</span><span class="sxs-lookup"><span data-stu-id="29e8c-108">The following example demonstrates the usage of the assignment operator with a local variable, a property, and an indexer element as its left-hand operand:</span></span>

[!code-csharp-interactive[simple assignment](~/samples/csharp/language-reference/operators/AssignmentOperator.cs#Simple)]

## <a name="ref-assignment-operator"></a><span data-ttu-id="29e8c-109">Opérateur d'assignation ref</span><span class="sxs-lookup"><span data-stu-id="29e8c-109">ref assignment operator</span></span>

<span data-ttu-id="29e8c-110">À partir de C# 7.3, vous pouvez utiliser l’opérateur d’assignation ref `= ref` pour réaffecter une variable [locale ref](../keywords/ref.md#ref-locals) ou une variable [locale ref readonly](../keywords/ref.md#ref-readonly-locals).</span><span class="sxs-lookup"><span data-stu-id="29e8c-110">Beginning with C# 7.3, you can use the ref assignment operator `= ref` to reassign a [ref local](../keywords/ref.md#ref-locals) or [ref readonly local](../keywords/ref.md#ref-readonly-locals) variable.</span></span> <span data-ttu-id="29e8c-111">L’exemple suivant illustre l’utilisation de l’opérateur d’assignation ref :</span><span class="sxs-lookup"><span data-stu-id="29e8c-111">The following example demonstrates the usage of the ref assignment operator:</span></span>

[!code-csharp[ref assignment operator](~/samples/csharp/language-reference/operators/AssignmentOperator.cs#RefAssignment)]

<span data-ttu-id="29e8c-112">Dans le cas de l’opérateur d’assignation ref, les deux opérandes doivent être du même type.</span><span class="sxs-lookup"><span data-stu-id="29e8c-112">In the case of the ref assignment operator, the type of both its operands must be the same.</span></span>

<span data-ttu-id="29e8c-113">Pour plus d’informations, voir la [proposition de fonctionnalité](~/_csharplang/proposals/csharp-7.3/ref-local-reassignment.md).</span><span class="sxs-lookup"><span data-stu-id="29e8c-113">For more information, see the [feature proposal note](~/_csharplang/proposals/csharp-7.3/ref-local-reassignment.md).</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="29e8c-114">Assignation composée</span><span class="sxs-lookup"><span data-stu-id="29e8c-114">Compound assignment</span></span>

<span data-ttu-id="29e8c-115">Pour un opérateur binaire `op`, une expression d’assignation composée du formulaire</span><span class="sxs-lookup"><span data-stu-id="29e8c-115">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="29e8c-116">est équivalent à</span><span class="sxs-lookup"><span data-stu-id="29e8c-116">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="29e8c-117">sauf que `x` n’est évalué qu’une seule fois.</span><span class="sxs-lookup"><span data-stu-id="29e8c-117">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="29e8c-118">L’assignation composée est prise en charge par les opérateurs [arithmétiques](arithmetic-operators.md#compound-assignment), [logiques booléens](boolean-logical-operators.md#compound-assignment) et [logiques au niveau du bit et du décalage](bitwise-and-shift-operators.md#compound-assignment).</span><span class="sxs-lookup"><span data-stu-id="29e8c-118">Compound assignment is supported by [arithmetic](arithmetic-operators.md#compound-assignment), [Boolean logical](boolean-logical-operators.md#compound-assignment), and [bitwise logical and shift](bitwise-and-shift-operators.md#compound-assignment) operators.</span></span>

## <a name="null-coalescing-assignment"></a><span data-ttu-id="29e8c-119">Assignation de fusion Null</span><span class="sxs-lookup"><span data-stu-id="29e8c-119">Null-coalescing assignment</span></span>

<span data-ttu-id="29e8c-120">À partir C# de 8,0, vous pouvez utiliser l’opérateur `??=` d’assignation de fusion Null pour assigner la valeur de son opérande droit à son opérande gauche uniquement si l’opérande de gauche est évalué à. `null`</span><span class="sxs-lookup"><span data-stu-id="29e8c-120">Beginning with C# 8.0, you can use the null-coalescing assignment operator `??=` to assign the value of its right-hand operand to its left-hand operand only if the left-hand operand evaluates to `null`.</span></span> <span data-ttu-id="29e8c-121">Pour plus d’informations, consultez [les = l’article Operators](null-coalescing-operator.md) .</span><span class="sxs-lookup"><span data-stu-id="29e8c-121">For more information, see the [?? and ??= operators](null-coalescing-operator.md) article.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="29e8c-122">Capacité de surcharge de l’opérateur</span><span class="sxs-lookup"><span data-stu-id="29e8c-122">Operator overloadability</span></span>

<span data-ttu-id="29e8c-123">Un type défini par l’utilisateur ne peut pas surcharger l’opérateur d’assignation.</span><span class="sxs-lookup"><span data-stu-id="29e8c-123">A user-defined type cannot overload the assignment operator.</span></span> <span data-ttu-id="29e8c-124">Toutefois, il peut définir une conversion implicite vers un autre type.</span><span class="sxs-lookup"><span data-stu-id="29e8c-124">However, a user-defined type can define an implicit conversion to another type.</span></span> <span data-ttu-id="29e8c-125">Ainsi, la valeur d’un type défini par l’utilisateur peut être assignée à une variable, une propriété ou un élément d’indexeur d’un autre type.</span><span class="sxs-lookup"><span data-stu-id="29e8c-125">That way, the value of a user-defined type can be assigned to a variable, a property, or an indexer element of another type.</span></span> <span data-ttu-id="29e8c-126">Pour plus d’informations, consultez [Opérateurs de conversion définie par l’utilisateur](user-defined-conversion-operators.md).</span><span class="sxs-lookup"><span data-stu-id="29e8c-126">For more information, see [User-defined conversion operators](user-defined-conversion-operators.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="29e8c-127">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="29e8c-127">C# language specification</span></span>

<span data-ttu-id="29e8c-128">Pour plus d’informations, voir la section [Opérateurs d’assignation](~/_csharplang/spec/expressions.md#assignment-operators) de la [spécification du langage C#](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="29e8c-128">For more information, see the [Assignment operators](~/_csharplang/spec/expressions.md#assignment-operators) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="29e8c-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="29e8c-129">See also</span></span>

- [<span data-ttu-id="29e8c-130">Informations de référence sur C#</span><span class="sxs-lookup"><span data-stu-id="29e8c-130">C# reference</span></span>](../index.md)
- [<span data-ttu-id="29e8c-131">Opérateurs C#</span><span class="sxs-lookup"><span data-stu-id="29e8c-131">C# operators</span></span>](index.md)
- [<span data-ttu-id="29e8c-132">ref, mot clé</span><span class="sxs-lookup"><span data-stu-id="29e8c-132">ref keyword</span></span>](../keywords/ref.md)
