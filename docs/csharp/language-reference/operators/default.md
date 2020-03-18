---
title: opérateur par défaut - référence C#
description: Utilisez l’opérateur par défaut pour produire la valeur par défaut d’un type
ms.date: 08/01/2019
helpviewer_keywords:
- default keyword [C#]
ms.openlocfilehash: 0d37fe952e71e74f014872231a2e58663dea9d18
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399482"
---
# <a name="default-operator-c-reference"></a><span data-ttu-id="9f67c-103">opérateur par défaut (référence C#)</span><span class="sxs-lookup"><span data-stu-id="9f67c-103">default operator (C# reference)</span></span>

<span data-ttu-id="9f67c-104">L’opérateur `default` produit la [valeur par défaut](../builtin-types/default-values.md) d’un type.</span><span class="sxs-lookup"><span data-stu-id="9f67c-104">The `default` operator produces the [default value](../builtin-types/default-values.md) of a type.</span></span> <span data-ttu-id="9f67c-105">L’argument de l’opérateur `default` doit avoir le nom d’un type ou d’un paramètre de type.</span><span class="sxs-lookup"><span data-stu-id="9f67c-105">The argument to the `default` operator must be the name of a type or a type parameter.</span></span>

<span data-ttu-id="9f67c-106">L’exemple suivant illustre l’utilisation de l’opérateur `default` :</span><span class="sxs-lookup"><span data-stu-id="9f67c-106">The following example shows the usage of the `default` operator:</span></span>

[!code-csharp-interactive[default of T](snippets/DefaultOperator.cs#WithOperand)]

<span data-ttu-id="9f67c-107">Vous utilisez `default` également le mot clé comme étiquette de cas par défaut dans une [ `switch` déclaration](../keywords/switch.md).</span><span class="sxs-lookup"><span data-stu-id="9f67c-107">You also use the `default` keyword as the default case label within a [`switch` statement](../keywords/switch.md).</span></span>

## <a name="default-literal"></a><span data-ttu-id="9f67c-108">littéral par défaut</span><span class="sxs-lookup"><span data-stu-id="9f67c-108">default literal</span></span>

<span data-ttu-id="9f67c-109">À partir de C# 7.1, vous pouvez utiliser le littéral `default` pour produire la valeur par défaut d'un type lorsque le compilateur peut déduire le type d'expression.</span><span class="sxs-lookup"><span data-stu-id="9f67c-109">Beginning with C# 7.1, you can use the `default` literal to produce the default value of a type when the compiler can infer the expression type.</span></span> <span data-ttu-id="9f67c-110">L’expression littérale `default` génère la même valeur que l’expression `default(T)`, où `T` est le type déduit.</span><span class="sxs-lookup"><span data-stu-id="9f67c-110">The `default` literal expression produces the same value as the `default(T)` expression where `T` is the inferred type.</span></span> <span data-ttu-id="9f67c-111">Vous pouvez utiliser le littéral `default` dans les cas suivants :</span><span class="sxs-lookup"><span data-stu-id="9f67c-111">You can use the `default` literal in any of the following cases:</span></span>

- <span data-ttu-id="9f67c-112">Dans l'affectation ou l'initialisation d'une variable.</span><span class="sxs-lookup"><span data-stu-id="9f67c-112">In the assignment or initialization of a variable.</span></span>
- <span data-ttu-id="9f67c-113">Dans la déclaration de la valeur par défaut pour un [paramètre de méthode facultatif](../../methods.md#optional-parameters-and-arguments).</span><span class="sxs-lookup"><span data-stu-id="9f67c-113">In the declaration of the default value for an [optional method parameter](../../methods.md#optional-parameters-and-arguments).</span></span>
- <span data-ttu-id="9f67c-114">Dans un appel de méthode pour fournir une valeur d'argument.</span><span class="sxs-lookup"><span data-stu-id="9f67c-114">In a method call to provide an argument value.</span></span>
- <span data-ttu-id="9f67c-115">Dans [ `return` ](../keywords/return.md) une déclaration ou comme une expression dans un [membre expression-corps](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span><span class="sxs-lookup"><span data-stu-id="9f67c-115">In a [`return` statement](../keywords/return.md) or as an expression in an [expression-bodied member](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span></span>

<span data-ttu-id="9f67c-116">L’exemple suivant illustre l’utilisation du littéral `default` :</span><span class="sxs-lookup"><span data-stu-id="9f67c-116">The following example shows the usage of the `default` literal:</span></span>

[!code-csharp-interactive[default literal](snippets/DefaultOperator.cs#DefaultLiteral)]

## <a name="c-language-specification"></a><span data-ttu-id="9f67c-117">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="9f67c-117">C# language specification</span></span>

<span data-ttu-id="9f67c-118">Pour plus d’informations, voir la section [Expressions de valeur par défaut](~/_csharplang/spec/expressions.md#default-value-expressions) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="9f67c-118">For more information, see the [Default value expressions](~/_csharplang/spec/expressions.md#default-value-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="9f67c-119">Pour plus d’informations sur le littéral `default`, voir la [proposition de fonctionnalité](~/_csharplang/proposals/csharp-7.1/target-typed-default.md).</span><span class="sxs-lookup"><span data-stu-id="9f67c-119">For more information about the `default` literal, see the [feature proposal note](~/_csharplang/proposals/csharp-7.1/target-typed-default.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9f67c-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9f67c-120">See also</span></span>

- [<span data-ttu-id="9f67c-121">Référence C#</span><span class="sxs-lookup"><span data-stu-id="9f67c-121">C# reference</span></span>](../index.md)
- [<span data-ttu-id="9f67c-122">Opérateurs CMD</span><span class="sxs-lookup"><span data-stu-id="9f67c-122">C# operators</span></span>](index.md)
- [<span data-ttu-id="9f67c-123">Valeurs par défaut des types C</span><span class="sxs-lookup"><span data-stu-id="9f67c-123">Default values of C# types</span></span>](../builtin-types/default-values.md)
- [<span data-ttu-id="9f67c-124">Génériques en .NET</span><span class="sxs-lookup"><span data-stu-id="9f67c-124">Generics in .NET</span></span>](../../../standard/generics/index.md)
