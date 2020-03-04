---
title: opérateur par défaut - référence C#
description: Utiliser l’opérateur par défaut pour produire la valeur par défaut d’un type
ms.date: 08/01/2019
helpviewer_keywords:
- default keyword [C#]
ms.openlocfilehash: ba4c02caa53a9d532be4012a4543a25cd41b6023
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/03/2020
ms.locfileid: "78239311"
---
# <a name="default-operator-c-reference"></a><span data-ttu-id="77048-103">opérateur par défaut (référence C#)</span><span class="sxs-lookup"><span data-stu-id="77048-103">default operator (C# reference)</span></span>

<span data-ttu-id="77048-104">L’opérateur `default` produit la [valeur par défaut](../builtin-types/default-values.md) d’un type.</span><span class="sxs-lookup"><span data-stu-id="77048-104">The `default` operator produces the [default value](../builtin-types/default-values.md) of a type.</span></span> <span data-ttu-id="77048-105">L’argument de l’opérateur `default` doit avoir le nom d’un type ou d’un paramètre de type.</span><span class="sxs-lookup"><span data-stu-id="77048-105">The argument to the `default` operator must be the name of a type or a type parameter.</span></span>

<span data-ttu-id="77048-106">L’exemple suivant illustre l’utilisation de l’opérateur `default` :</span><span class="sxs-lookup"><span data-stu-id="77048-106">The following example shows the usage of the `default` operator:</span></span>

[!code-csharp-interactive[default of T](~/samples/snippets/csharp/language-reference/operators/DefaultOperator.cs#WithOperand)]

<span data-ttu-id="77048-107">Vous utilisez également le mot clé `default` comme étiquette de cas par défaut dans une [instruction`switch`](../keywords/switch.md).</span><span class="sxs-lookup"><span data-stu-id="77048-107">You also use the `default` keyword as the default case label within a [`switch` statement](../keywords/switch.md).</span></span>

## <a name="default-literal"></a><span data-ttu-id="77048-108">littéral par défaut</span><span class="sxs-lookup"><span data-stu-id="77048-108">default literal</span></span>

<span data-ttu-id="77048-109">À partir de C# 7.1, vous pouvez utiliser le littéral `default` pour produire la valeur par défaut d'un type lorsque le compilateur peut déduire le type d'expression.</span><span class="sxs-lookup"><span data-stu-id="77048-109">Beginning with C# 7.1, you can use the `default` literal to produce the default value of a type when the compiler can infer the expression type.</span></span> <span data-ttu-id="77048-110">L’expression littérale `default` génère la même valeur que l’expression `default(T)`, où `T` est le type déduit.</span><span class="sxs-lookup"><span data-stu-id="77048-110">The `default` literal expression produces the same value as the `default(T)` expression where `T` is the inferred type.</span></span> <span data-ttu-id="77048-111">Vous pouvez utiliser le littéral `default` dans les cas suivants :</span><span class="sxs-lookup"><span data-stu-id="77048-111">You can use the `default` literal in any of the following cases:</span></span>

- <span data-ttu-id="77048-112">Dans l'affectation ou l'initialisation d'une variable.</span><span class="sxs-lookup"><span data-stu-id="77048-112">In the assignment or initialization of a variable.</span></span>
- <span data-ttu-id="77048-113">Dans la déclaration de la valeur par défaut d’un [paramètre de méthode facultatif](../../methods.md#optional-parameters-and-arguments).</span><span class="sxs-lookup"><span data-stu-id="77048-113">In the declaration of the default value for an [optional method parameter](../../methods.md#optional-parameters-and-arguments).</span></span>
- <span data-ttu-id="77048-114">Dans un appel de méthode pour fournir une valeur d'argument.</span><span class="sxs-lookup"><span data-stu-id="77048-114">In a method call to provide an argument value.</span></span>
- <span data-ttu-id="77048-115">Dans une [instruction`return`](../keywords/return.md) ou en tant qu’expression dans un [membre d’expression](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span><span class="sxs-lookup"><span data-stu-id="77048-115">In a [`return` statement](../keywords/return.md) or as an expression in an [expression-bodied member](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span></span>

<span data-ttu-id="77048-116">L’exemple suivant illustre l’utilisation du littéral `default` :</span><span class="sxs-lookup"><span data-stu-id="77048-116">The following example shows the usage of the `default` literal:</span></span>

[!code-csharp-interactive[default literal](~/samples/snippets/csharp/language-reference/operators/DefaultOperator.cs#DefaultLiteral)]

## <a name="c-language-specification"></a><span data-ttu-id="77048-117">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="77048-117">C# language specification</span></span>

<span data-ttu-id="77048-118">Pour plus d’informations, voir la section [Expressions de valeur par défaut](~/_csharplang/spec/expressions.md#default-value-expressions) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="77048-118">For more information, see the [Default value expressions](~/_csharplang/spec/expressions.md#default-value-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="77048-119">Pour plus d’informations sur le littéral `default`, voir la [proposition de fonctionnalité](~/_csharplang/proposals/csharp-7.1/target-typed-default.md).</span><span class="sxs-lookup"><span data-stu-id="77048-119">For more information about the `default` literal, see the [feature proposal note](~/_csharplang/proposals/csharp-7.1/target-typed-default.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="77048-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="77048-120">See also</span></span>

- [<span data-ttu-id="77048-121">Informations de référence sur C#</span><span class="sxs-lookup"><span data-stu-id="77048-121">C# reference</span></span>](../index.md)
- [<span data-ttu-id="77048-122">Opérateurs C#</span><span class="sxs-lookup"><span data-stu-id="77048-122">C# operators</span></span>](index.md)
- [<span data-ttu-id="77048-123">Valeurs par défaut C# des types</span><span class="sxs-lookup"><span data-stu-id="77048-123">Default values of C# types</span></span>](../builtin-types/default-values.md)
- [<span data-ttu-id="77048-124">Génériques en .NET</span><span class="sxs-lookup"><span data-stu-id="77048-124">Generics in .NET</span></span>](../../../standard/generics/index.md)
