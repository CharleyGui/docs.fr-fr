---
title: opérateur par défaut - référence C#
ms.custom: seodec18
description: Utiliser un opérateur par défaut pour produire la valeur par défaut d’un type
ms.date: 08/01/2019
helpviewer_keywords:
- default keyword [C#]
ms.openlocfilehash: 5623cb9dc3790b5bb99635c41cb3f122f4c71d8e
ms.sourcegitcommit: bbfcc913c275885381820be28f61efcf8e83eecc
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2019
ms.locfileid: "68796938"
---
# <a name="default-operator-c-reference"></a><span data-ttu-id="8de83-103">opérateur par défaut (référence C#)</span><span class="sxs-lookup"><span data-stu-id="8de83-103">default operator (C# reference)</span></span>

<span data-ttu-id="8de83-104">L’opérateur `default` produit la [valeur par défaut](../keywords/default-values-table.md) d’un type.</span><span class="sxs-lookup"><span data-stu-id="8de83-104">The `default` operator produces the [default value](../keywords/default-values-table.md) of a type.</span></span> <span data-ttu-id="8de83-105">L’argument de l’opérateur `default` doit avoir le nom d’un type ou d’un paramètre de type.</span><span class="sxs-lookup"><span data-stu-id="8de83-105">The argument to the `default` operator must be the name of a type or a type parameter.</span></span>

<span data-ttu-id="8de83-106">L’exemple suivant illustre l’utilisation de l’opérateur `default` :</span><span class="sxs-lookup"><span data-stu-id="8de83-106">The following example shows the usage of the `default` operator:</span></span>

[!code-csharp-interactive[default of T](~/samples/csharp/language-reference/operators/DefaultOperator.cs#WithOperand)]

<span data-ttu-id="8de83-107">Vous utilisez également le mot-clé `default` comme étiquette case par défaut dans l'[instruction `switch`](../keywords/switch.md).</span><span class="sxs-lookup"><span data-stu-id="8de83-107">You also use the `default` keyword as the default case label within the [`switch` statement](../keywords/switch.md).</span></span>

## <a name="default-literal"></a><span data-ttu-id="8de83-108">littéral par défaut</span><span class="sxs-lookup"><span data-stu-id="8de83-108">default literal</span></span>

<span data-ttu-id="8de83-109">À partir de C# 7.1, vous pouvez utiliser le littéral `default` pour produire la valeur par défaut d'un type lorsque le compilateur peut déduire le type d'expression.</span><span class="sxs-lookup"><span data-stu-id="8de83-109">Beginning with C# 7.1, you can use the `default` literal to produce the default value of a type when the compiler can infer the expression type.</span></span> <span data-ttu-id="8de83-110">L’expression littérale `default` génère la même valeur que l’expression `default(T)`, où `T` est le type déduit.</span><span class="sxs-lookup"><span data-stu-id="8de83-110">The `default` literal expression produces the same value as the `default(T)` expression where `T` is the inferred type.</span></span> <span data-ttu-id="8de83-111">Vous pouvez utiliser le littéral `default` dans les cas suivants :</span><span class="sxs-lookup"><span data-stu-id="8de83-111">You can use the `default` literal in any of the following cases:</span></span>

- <span data-ttu-id="8de83-112">Dans l'affectation ou l'initialisation d'une variable.</span><span class="sxs-lookup"><span data-stu-id="8de83-112">In the assignment or initialization of a variable.</span></span>
- <span data-ttu-id="8de83-113">Dans la déclaration de la valeur par défaut d'un paramètre de méthode facultatif.</span><span class="sxs-lookup"><span data-stu-id="8de83-113">In the declaration of the default value for an optional method parameter.</span></span>
- <span data-ttu-id="8de83-114">Dans un appel de méthode pour fournir une valeur d'argument.</span><span class="sxs-lookup"><span data-stu-id="8de83-114">In a method call to provide an argument value.</span></span>
- <span data-ttu-id="8de83-115">Dans une instruction `return` ou en tant qu’expression d’un membre expression-bodied.</span><span class="sxs-lookup"><span data-stu-id="8de83-115">In a `return` statement or as an expression in an expression-bodied member.</span></span>

<span data-ttu-id="8de83-116">L’exemple suivant illustre l’utilisation du littéral `default` :</span><span class="sxs-lookup"><span data-stu-id="8de83-116">The following example shows the usage of the `default` literal:</span></span>

[!code-csharp-interactive[default literal](~/samples/csharp/language-reference/operators/DefaultOperator.cs#DefaultLiteral)]

## <a name="c-language-specification"></a><span data-ttu-id="8de83-117">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="8de83-117">C# language specification</span></span>

<span data-ttu-id="8de83-118">Pour plus d’informations, voir la section [Expressions de valeur par défaut](~/_csharplang/spec/expressions.md#default-value-expressions) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="8de83-118">For more information, see the [Default value expressions](~/_csharplang/spec/expressions.md#default-value-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="8de83-119">Pour plus d’informations sur le littéral `default`, voir la [proposition de fonctionnalité](~/_csharplang/proposals/csharp-7.1/target-typed-default.md).</span><span class="sxs-lookup"><span data-stu-id="8de83-119">For more information about the `default` literal, see the [feature proposal note](~/_csharplang/proposals/csharp-7.1/target-typed-default.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8de83-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8de83-120">See also</span></span>

- [<span data-ttu-id="8de83-121">Informations de référence sur C#</span><span class="sxs-lookup"><span data-stu-id="8de83-121">C# reference</span></span>](../index.md)
- [<span data-ttu-id="8de83-122">Opérateurs C#</span><span class="sxs-lookup"><span data-stu-id="8de83-122">C# operators</span></span>](index.md)
- [<span data-ttu-id="8de83-123">Tableau des valeurs par défaut</span><span class="sxs-lookup"><span data-stu-id="8de83-123">Default values table</span></span>](../keywords/default-values-table.md)
