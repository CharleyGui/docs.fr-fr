---
title: expressions de valeur par défaut-référence C#
description: Utiliser les expressions de valeur par défaut pour obtenir la valeur par défaut d’un type
ms.date: 03/13/2020
f1_keywords:
- default_CSharpKeyword
- default
helpviewer_keywords:
- default keyword [C#]
ms.openlocfilehash: c07eb8e50dc2ec3413882fa841d2f896b28d2e8d
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556707"
---
# <a name="default-value-expressions-c-reference"></a><span data-ttu-id="472c7-103">expressions de valeur par défaut (référence C#)</span><span class="sxs-lookup"><span data-stu-id="472c7-103">default value expressions (C# reference)</span></span>

<span data-ttu-id="472c7-104">Une expression de valeur par défaut produit la [valeur par défaut](../builtin-types/default-values.md) d’un type.</span><span class="sxs-lookup"><span data-stu-id="472c7-104">A default value expression produces the [default value](../builtin-types/default-values.md) of a type.</span></span> <span data-ttu-id="472c7-105">Il existe deux types d’expressions de valeur par défaut : l’appel d' [opérateur par défaut](#default-operator) et un [littéral par défaut](#default-literal).</span><span class="sxs-lookup"><span data-stu-id="472c7-105">There are two kinds of default value expressions: the [default operator](#default-operator) call and a [default literal](#default-literal).</span></span>

<span data-ttu-id="472c7-106">Vous utilisez également le `default` mot clé comme étiquette de cas par défaut dans une [ `switch` instruction](../keywords/switch.md).</span><span class="sxs-lookup"><span data-stu-id="472c7-106">You also use the `default` keyword as the default case label within a [`switch` statement](../keywords/switch.md).</span></span>

## <a name="default-operator"></a><span data-ttu-id="472c7-107">Opérateur default</span><span class="sxs-lookup"><span data-stu-id="472c7-107">default operator</span></span>

<span data-ttu-id="472c7-108">L’argument de l’opérateur `default` doit avoir le nom d’un type ou d’un paramètre de type, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="472c7-108">The argument to the `default` operator must be the name of a type or a type parameter, as the following example shows:</span></span>

[!code-csharp-interactive[default of T](snippets/DefaultOperator.cs#WithOperand)]

## <a name="default-literal"></a><span data-ttu-id="472c7-109">littéral par défaut</span><span class="sxs-lookup"><span data-stu-id="472c7-109">default literal</span></span>

<span data-ttu-id="472c7-110">À partir de C# 7.1, vous pouvez utiliser le littéral `default` pour produire la valeur par défaut d'un type lorsque le compilateur peut déduire le type d'expression.</span><span class="sxs-lookup"><span data-stu-id="472c7-110">Beginning with C# 7.1, you can use the `default` literal to produce the default value of a type when the compiler can infer the expression type.</span></span> <span data-ttu-id="472c7-111">L’expression littérale `default` génère la même valeur que l’expression `default(T)`, où `T` est le type déduit.</span><span class="sxs-lookup"><span data-stu-id="472c7-111">The `default` literal expression produces the same value as the `default(T)` expression where `T` is the inferred type.</span></span> <span data-ttu-id="472c7-112">Vous pouvez utiliser le littéral `default` dans les cas suivants :</span><span class="sxs-lookup"><span data-stu-id="472c7-112">You can use the `default` literal in any of the following cases:</span></span>

- <span data-ttu-id="472c7-113">Dans l'affectation ou l'initialisation d'une variable.</span><span class="sxs-lookup"><span data-stu-id="472c7-113">In the assignment or initialization of a variable.</span></span>
- <span data-ttu-id="472c7-114">Dans la déclaration de la valeur par défaut d’un [paramètre de méthode facultatif](../../methods.md#optional-parameters-and-arguments).</span><span class="sxs-lookup"><span data-stu-id="472c7-114">In the declaration of the default value for an [optional method parameter](../../methods.md#optional-parameters-and-arguments).</span></span>
- <span data-ttu-id="472c7-115">Dans un appel de méthode pour fournir une valeur d'argument.</span><span class="sxs-lookup"><span data-stu-id="472c7-115">In a method call to provide an argument value.</span></span>
- <span data-ttu-id="472c7-116">Dans une [ `return` instruction](../keywords/return.md) ou en tant qu’expression dans un [membre d’expression](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span><span class="sxs-lookup"><span data-stu-id="472c7-116">In a [`return` statement](../keywords/return.md) or as an expression in an [expression-bodied member](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span></span>

<span data-ttu-id="472c7-117">L’exemple suivant illustre l’utilisation du littéral `default` :</span><span class="sxs-lookup"><span data-stu-id="472c7-117">The following example shows the usage of the `default` literal:</span></span>

[!code-csharp-interactive[default literal](snippets/DefaultOperator.cs#DefaultLiteral)]

## <a name="c-language-specification"></a><span data-ttu-id="472c7-118">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="472c7-118">C# language specification</span></span>

<span data-ttu-id="472c7-119">Pour plus d’informations, voir la section [Expressions de valeur par défaut](~/_csharplang/spec/expressions.md#default-value-expressions) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="472c7-119">For more information, see the [Default value expressions](~/_csharplang/spec/expressions.md#default-value-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="472c7-120">Pour plus d’informations sur le littéral `default`, voir la [proposition de fonctionnalité](~/_csharplang/proposals/csharp-7.1/target-typed-default.md).</span><span class="sxs-lookup"><span data-stu-id="472c7-120">For more information about the `default` literal, see the [feature proposal note](~/_csharplang/proposals/csharp-7.1/target-typed-default.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="472c7-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="472c7-121">See also</span></span>

- [<span data-ttu-id="472c7-122">Informations de référence sur C#</span><span class="sxs-lookup"><span data-stu-id="472c7-122">C# reference</span></span>](../index.md)
- [<span data-ttu-id="472c7-123">Opérateurs et expressions C#</span><span class="sxs-lookup"><span data-stu-id="472c7-123">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="472c7-124">Valeurs par défaut des types C#</span><span class="sxs-lookup"><span data-stu-id="472c7-124">Default values of C# types</span></span>](../builtin-types/default-values.md)
- [<span data-ttu-id="472c7-125">Génériques en .NET</span><span class="sxs-lookup"><span data-stu-id="472c7-125">Generics in .NET</span></span>](../../../standard/generics/index.md)
