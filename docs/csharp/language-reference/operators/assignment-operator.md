---
title: Opérateurs d’assignation-référence C#
ms.date: 09/10/2019
f1_keywords:
- =_CSharpKeyword
helpviewer_keywords:
- = operator [C#]
ms.assetid: d802a6d5-32f0-42b8-b180-12f5a081bfc1
ms.openlocfilehash: 7b4f3b3f4d6b697903461f08435552f2df36bfe4
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2020
ms.locfileid: "87916938"
---
# <a name="assignment-operators-c-reference"></a><span data-ttu-id="a6903-102">Opérateurs d’assignation (référence C#)</span><span class="sxs-lookup"><span data-stu-id="a6903-102">Assignment operators (C# reference)</span></span>

<span data-ttu-id="a6903-103">L’opérateur d’assignation `=` assigne la valeur de son opérande de droite à une variable, une [propriété](../../programming-guide/classes-and-structs/properties.md) ou un élément [d’indexeur](../../programming-guide/indexers/index.md) donné par son opérande de gauche.</span><span class="sxs-lookup"><span data-stu-id="a6903-103">The assignment operator `=` assigns the value of its right-hand operand to a variable, a [property](../../programming-guide/classes-and-structs/properties.md), or an [indexer](../../programming-guide/indexers/index.md) element given by its left-hand operand.</span></span> <span data-ttu-id="a6903-104">Le résultat d’une expression d’assignation est la valeur assignée à l’opérande de gauche.</span><span class="sxs-lookup"><span data-stu-id="a6903-104">The result of an assignment expression is the value assigned to the left-hand operand.</span></span> <span data-ttu-id="a6903-105">L’opérande de droite doit être du même type que l’opérande de gauche, ou implicitement convertible vers le type de l’opérande de gauche.</span><span class="sxs-lookup"><span data-stu-id="a6903-105">The type of the right-hand operand must be the same as the type of the left-hand operand or implicitly convertible to it.</span></span>

<span data-ttu-id="a6903-106">L’opérateur `=` d’assignation est associatif à droite, autrement dit, une expression de la forme</span><span class="sxs-lookup"><span data-stu-id="a6903-106">The assignment operator `=` is right-associative, that is, an expression of the form</span></span>

```csharp
a = b = c
```

<span data-ttu-id="a6903-107">est évaluée comme étant</span><span class="sxs-lookup"><span data-stu-id="a6903-107">is evaluated as</span></span>

```csharp
a = (b = c)
```

<span data-ttu-id="a6903-108">L’exemple suivant illustre l’utilisation de l’opérateur d’assignation avec une variable locale, une propriété et un élément d’indexeur comme opérande de gauche :</span><span class="sxs-lookup"><span data-stu-id="a6903-108">The following example demonstrates the usage of the assignment operator with a local variable, a property, and an indexer element as its left-hand operand:</span></span>

[!code-csharp-interactive[simple assignment](snippets/shared/AssignmentOperator.cs#Simple)]

## <a name="ref-assignment-operator"></a><span data-ttu-id="a6903-109">Opérateur d'assignation ref</span><span class="sxs-lookup"><span data-stu-id="a6903-109">ref assignment operator</span></span>

<span data-ttu-id="a6903-110">À partir de C# 7.3, vous pouvez utiliser l’opérateur d’assignation ref `= ref` pour réaffecter une variable [locale ref](../keywords/ref.md#ref-locals) ou une variable [locale ref readonly](../keywords/ref.md#ref-readonly-locals).</span><span class="sxs-lookup"><span data-stu-id="a6903-110">Beginning with C# 7.3, you can use the ref assignment operator `= ref` to reassign a [ref local](../keywords/ref.md#ref-locals) or [ref readonly local](../keywords/ref.md#ref-readonly-locals) variable.</span></span> <span data-ttu-id="a6903-111">L’exemple suivant illustre l’utilisation de l’opérateur d’assignation ref :</span><span class="sxs-lookup"><span data-stu-id="a6903-111">The following example demonstrates the usage of the ref assignment operator:</span></span>

[!code-csharp[ref assignment operator](snippets/shared/AssignmentOperator.cs#RefAssignment)]

<span data-ttu-id="a6903-112">Dans le cas de l’opérateur d’assignation de référence, les deux opérandes doivent être du même type.</span><span class="sxs-lookup"><span data-stu-id="a6903-112">In the case of the ref assignment operator, the both of its operands must be of the same type.</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="a6903-113">Assignation composée</span><span class="sxs-lookup"><span data-stu-id="a6903-113">Compound assignment</span></span>

<span data-ttu-id="a6903-114">Pour un opérateur binaire `op`, une expression d’assignation composée du formulaire</span><span class="sxs-lookup"><span data-stu-id="a6903-114">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="a6903-115">équivaut à :</span><span class="sxs-lookup"><span data-stu-id="a6903-115">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="a6903-116">sauf que `x` n’est évalué qu’une seule fois.</span><span class="sxs-lookup"><span data-stu-id="a6903-116">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="a6903-117">L’assignation composée est prise en charge par les opérateurs [arithmétiques](arithmetic-operators.md#compound-assignment), [logiques booléens](boolean-logical-operators.md#compound-assignment) et [logiques au niveau du bit et du décalage](bitwise-and-shift-operators.md#compound-assignment).</span><span class="sxs-lookup"><span data-stu-id="a6903-117">Compound assignment is supported by [arithmetic](arithmetic-operators.md#compound-assignment), [Boolean logical](boolean-logical-operators.md#compound-assignment), and [bitwise logical and shift](bitwise-and-shift-operators.md#compound-assignment) operators.</span></span>

## <a name="null-coalescing-assignment"></a><span data-ttu-id="a6903-118">Assignation de fusion Null</span><span class="sxs-lookup"><span data-stu-id="a6903-118">Null-coalescing assignment</span></span>

<span data-ttu-id="a6903-119">À compter de C# 8,0, vous pouvez utiliser l’opérateur d’assignation de fusion Null `??=` pour assigner la valeur de son opérande droit à son opérande de gauche uniquement si l’opérande de gauche prend la valeur `null` .</span><span class="sxs-lookup"><span data-stu-id="a6903-119">Beginning with C# 8.0, you can use the null-coalescing assignment operator `??=` to assign the value of its right-hand operand to its left-hand operand only if the left-hand operand evaluates to `null`.</span></span> <span data-ttu-id="a6903-120">Pour plus d’informations, consultez [les = l’article Operators](null-coalescing-operator.md) .</span><span class="sxs-lookup"><span data-stu-id="a6903-120">For more information, see the [?? and ??= operators](null-coalescing-operator.md) article.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="a6903-121">Capacité de surcharge de l’opérateur</span><span class="sxs-lookup"><span data-stu-id="a6903-121">Operator overloadability</span></span>

<span data-ttu-id="a6903-122">Un type défini par l’utilisateur ne peut pas [surcharger](operator-overloading.md) l’opérateur d’assignation.</span><span class="sxs-lookup"><span data-stu-id="a6903-122">A user-defined type cannot [overload](operator-overloading.md) the assignment operator.</span></span> <span data-ttu-id="a6903-123">Toutefois, il peut définir une conversion implicite vers un autre type.</span><span class="sxs-lookup"><span data-stu-id="a6903-123">However, a user-defined type can define an implicit conversion to another type.</span></span> <span data-ttu-id="a6903-124">Ainsi, la valeur d’un type défini par l’utilisateur peut être assignée à une variable, une propriété ou un élément d’indexeur d’un autre type.</span><span class="sxs-lookup"><span data-stu-id="a6903-124">That way, the value of a user-defined type can be assigned to a variable, a property, or an indexer element of another type.</span></span> <span data-ttu-id="a6903-125">Pour plus d’informations, consultez [Opérateurs de conversion définie par l’utilisateur](user-defined-conversion-operators.md).</span><span class="sxs-lookup"><span data-stu-id="a6903-125">For more information, see [User-defined conversion operators](user-defined-conversion-operators.md).</span></span>

<span data-ttu-id="a6903-126">Un type défini par l’utilisateur ne peut pas surcharger explicitement un opérateur d’assignation composée.</span><span class="sxs-lookup"><span data-stu-id="a6903-126">A user-defined type cannot explicitly overload a compound assignment operator.</span></span> <span data-ttu-id="a6903-127">Toutefois, si un type défini par l’utilisateur surcharge un opérateur binaire `op` , l' `op=` opérateur, s’il existe, est également implicitement surchargé.</span><span class="sxs-lookup"><span data-stu-id="a6903-127">However, if a user-defined type overloads a binary operator `op`, the `op=` operator, if it exists, is also implicitly overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="a6903-128">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="a6903-128">C# language specification</span></span>

<span data-ttu-id="a6903-129">Pour plus d’informations, voir la section [Opérateurs d’assignation](~/_csharplang/spec/expressions.md#assignment-operators) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="a6903-129">For more information, see the [Assignment operators](~/_csharplang/spec/expressions.md#assignment-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="a6903-130">Pour plus d’informations sur l’opérateur d’assignation de référence `= ref` , consultez la [Remarque relative](~/_csharplang/proposals/csharp-7.3/ref-local-reassignment.md)à la proposition de fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="a6903-130">For more information about the ref assignment operator `= ref`, see the [feature proposal note](~/_csharplang/proposals/csharp-7.3/ref-local-reassignment.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a6903-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a6903-131">See also</span></span>

- [<span data-ttu-id="a6903-132">Informations de référence sur C#</span><span class="sxs-lookup"><span data-stu-id="a6903-132">C# reference</span></span>](../index.md)
- [<span data-ttu-id="a6903-133">Opérateurs et expressions C#</span><span class="sxs-lookup"><span data-stu-id="a6903-133">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="a6903-134">ref, mot clé</span><span class="sxs-lookup"><span data-stu-id="a6903-134">ref keyword</span></span>](../keywords/ref.md)
