---
title: Opérateur >= - Référence C#
ms.custom: seodec18
ms.date: 06/21/2019
f1_keywords:
- =_CSharpKeyword
helpviewer_keywords:
- = operator [C#]
ms.assetid: d802a6d5-32f0-42b8-b180-12f5a081bfc1
ms.openlocfilehash: ef9c9bab5c1cebb06edf934254507180e2197349
ms.sourcegitcommit: a970268118ea61ce14207e0916e17243546a491f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/21/2019
ms.locfileid: "67306565"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="d28dc-102">Opérateur >= (référence C#)</span><span class="sxs-lookup"><span data-stu-id="d28dc-102">= operator (C# reference)</span></span>

<span data-ttu-id="d28dc-103">L’opérateur d’assignation `=` assigne la valeur de son opérande de droite à une variable, une [propriété](../../programming-guide/classes-and-structs/properties.md) ou un élément [d’indexeur](../../../csharp/programming-guide/indexers/index.md) donné par son opérande de gauche.</span><span class="sxs-lookup"><span data-stu-id="d28dc-103">The assignment operator `=` assigns the value of its right-hand operand to a variable, a [property](../../programming-guide/classes-and-structs/properties.md), or an [indexer](../../../csharp/programming-guide/indexers/index.md) element given by its left-hand operand.</span></span> <span data-ttu-id="d28dc-104">Le résultat d’une expression d’assignation est la valeur assignée à l’opérande de gauche.</span><span class="sxs-lookup"><span data-stu-id="d28dc-104">The result of an assignment expression is the value assigned to the left-hand operand.</span></span> <span data-ttu-id="d28dc-105">L’opérande de droite doit être du même type que l’opérande de gauche, ou implicitement convertible vers le type de l’opérande de gauche.</span><span class="sxs-lookup"><span data-stu-id="d28dc-105">The type of the right-hand operand must be the same as the type of the left-hand operand or implicitly convertible to it.</span></span>

<span data-ttu-id="d28dc-106">L’opérateur d’assignation est associatif à droite ; autrement dit, une expression de la forme :</span><span class="sxs-lookup"><span data-stu-id="d28dc-106">The assignment operator is right-associative, that is, an expression of the form</span></span>

```csharp
a = b = c
```

<span data-ttu-id="d28dc-107">est évaluée comme étant</span><span class="sxs-lookup"><span data-stu-id="d28dc-107">is evaluated as</span></span>

```csharp
a = (b = c)
```

<span data-ttu-id="d28dc-108">L’exemple suivant illustre l’utilisation de l’opérateur d’assignation avec une variable locale, une propriété et un élément d’indexeur comme opérande de gauche :</span><span class="sxs-lookup"><span data-stu-id="d28dc-108">The following example demonstrates the usage of the assignment operator with a local variable, a property, and an indexer element as its left-hand operand:</span></span>

[!code-csharp-interactive[simple assignment](~/samples/csharp/language-reference/operators/AssignmentOperator.cs#Simple)]

## <a name="ref-assignment-operator"></a><span data-ttu-id="d28dc-109">Opérateur d'assignation ref</span><span class="sxs-lookup"><span data-stu-id="d28dc-109">ref assignment operator</span></span>

<span data-ttu-id="d28dc-110">À partir de C# 7.3, vous pouvez utiliser l’opérateur d’assignation ref `= ref` pour réaffecter une variable [locale ref](../keywords/ref.md#ref-locals) ou une variable [locale ref readonly](../keywords/ref.md#ref-readonly-locals).</span><span class="sxs-lookup"><span data-stu-id="d28dc-110">Beginning with C# 7.3, you can use the ref assignment operator `= ref` to reassign a [ref local](../keywords/ref.md#ref-locals) or [ref readonly local](../keywords/ref.md#ref-readonly-locals) variable.</span></span> <span data-ttu-id="d28dc-111">L’exemple suivant illustre l’utilisation de l’opérateur d’assignation ref :</span><span class="sxs-lookup"><span data-stu-id="d28dc-111">The following example demonstrates the usage of the ref assignment operator:</span></span>

[!code-csharp[ref assignment operator](~/samples/csharp/language-reference/operators/AssignmentOperator.cs#RefAssignment)]

<span data-ttu-id="d28dc-112">Dans le cas de l’opérateur d’assignation ref, les deux opérandes doivent être du même type.</span><span class="sxs-lookup"><span data-stu-id="d28dc-112">In the case of the ref assignment operator, the type of both its operands must be the same.</span></span>

<span data-ttu-id="d28dc-113">Pour plus d’informations, voir la [proposition de fonctionnalité](~/_csharplang/proposals/csharp-7.3/ref-local-reassignment.md).</span><span class="sxs-lookup"><span data-stu-id="d28dc-113">For more information, see the [feature proposal note](~/_csharplang/proposals/csharp-7.3/ref-local-reassignment.md).</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="d28dc-114">Assignation composée</span><span class="sxs-lookup"><span data-stu-id="d28dc-114">Compound assignment</span></span>

<span data-ttu-id="d28dc-115">Pour un opérateur binaire `op`, une expression d’assignation composée du formulaire</span><span class="sxs-lookup"><span data-stu-id="d28dc-115">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="d28dc-116">est équivalent à</span><span class="sxs-lookup"><span data-stu-id="d28dc-116">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="d28dc-117">sauf que `x` n’est évalué qu’une seule fois.</span><span class="sxs-lookup"><span data-stu-id="d28dc-117">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="d28dc-118">L’assignation composée est prise en charge par les opérateurs [arithmétiques](arithmetic-operators.md#compound-assignment), [logiques booléens](boolean-logical-operators.md#compound-assignment) et [logiques au niveau du bit et du décalage](bitwise-and-shift-operators.md#compound-assignment).</span><span class="sxs-lookup"><span data-stu-id="d28dc-118">Compound assignment is supported by [arithmetic](arithmetic-operators.md#compound-assignment), [Boolean logical](boolean-logical-operators.md#compound-assignment), and [bitwise logical and shift](bitwise-and-shift-operators.md#compound-assignment) operators.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="d28dc-119">Capacité de surcharge de l’opérateur</span><span class="sxs-lookup"><span data-stu-id="d28dc-119">Operator overloadability</span></span>

<span data-ttu-id="d28dc-120">Un type défini par l’utilisateur ne peut pas surcharger l’opérateur d’assignation.</span><span class="sxs-lookup"><span data-stu-id="d28dc-120">A user-defined type cannot overload the assignment operator.</span></span> <span data-ttu-id="d28dc-121">Toutefois, il peut définir une conversion implicite vers un autre type.</span><span class="sxs-lookup"><span data-stu-id="d28dc-121">However, a user-defined type can define an implicit conversion to another type.</span></span> <span data-ttu-id="d28dc-122">Ainsi, la valeur d’un type défini par l’utilisateur peut être assignée à une variable, une propriété ou un élément d’indexeur d’un autre type.</span><span class="sxs-lookup"><span data-stu-id="d28dc-122">That way, the value of a user-defined type can be assigned to a variable, a property, or an indexer element of another type.</span></span> <span data-ttu-id="d28dc-123">Pour plus d'informations, voir l’article [implicit, mot clé](../keywords/implicit.md).</span><span class="sxs-lookup"><span data-stu-id="d28dc-123">For more information, see the [implicit](../keywords/implicit.md) keyword article.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="d28dc-124">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="d28dc-124">C# language specification</span></span>

<span data-ttu-id="d28dc-125">Pour plus d’informations, voir la section [Opérateurs d’assignation](~/_csharplang/spec/expressions.md#assignment-operators) de la [spécification du langage C#](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="d28dc-125">For more information, see the [Assignment operators](~/_csharplang/spec/expressions.md#assignment-operators) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d28dc-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d28dc-126">See also</span></span>

- [<span data-ttu-id="d28dc-127">Informations de référence sur C#</span><span class="sxs-lookup"><span data-stu-id="d28dc-127">C# reference</span></span>](../index.md)
- [<span data-ttu-id="d28dc-128">Opérateurs C#</span><span class="sxs-lookup"><span data-stu-id="d28dc-128">C# operators</span></span>](index.md)
- [<span data-ttu-id="d28dc-129">ref, mot clé</span><span class="sxs-lookup"><span data-stu-id="d28dc-129">ref keyword</span></span>](../keywords/ref.md)
