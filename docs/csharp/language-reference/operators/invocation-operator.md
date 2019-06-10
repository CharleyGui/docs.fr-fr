---
title: (), opérateur - Référence C#
ms.custom: seodec18
ms.date: 01/15/2019
f1_keywords:
- ()_CSharpKeyword
helpviewer_keywords:
- type conversion [C#], () operator
- cast operator [C#]
- () operator [C#]
ms.assetid: 846e1f94-8a8c-42fc-a42c-fbd38e70d8cc
ms.openlocfilehash: 8f7382a49c81b6fd8e104b864ffc2f70db7fe4a6
ms.sourcegitcommit: 904b98d8d706f0e2d5ceaa00ce17ffbd92adfb88
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66758109"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="565ea-102">(), opérateur (référence C#)</span><span class="sxs-lookup"><span data-stu-id="565ea-102">() operator (C# Reference)</span></span>

<span data-ttu-id="565ea-103">Les parenthèses, `()`, sont généralement utilisées pour l’appel de méthode ou de délégué, ou dans les expressions Cast.</span><span class="sxs-lookup"><span data-stu-id="565ea-103">Parentheses, `()`, are typically used for method or delegate invocation or in cast expressions.</span></span>

<span data-ttu-id="565ea-104">Vous utilisez également des parenthèses pour spécifier l’ordre dans lequel évaluer les opérations dans une expression.</span><span class="sxs-lookup"><span data-stu-id="565ea-104">You also use parentheses to specify the order in which to evaluate operations in an expression.</span></span> <span data-ttu-id="565ea-105">Pour plus d’informations, consultez la section [Ajout de parenthèses](../../programming-guide/statements-expressions-operators/operators.md#adding-parentheses) de l’article [Opérateurs](../../programming-guide/statements-expressions-operators/operators.md).</span><span class="sxs-lookup"><span data-stu-id="565ea-105">For more information, see the [Adding parentheses](../../programming-guide/statements-expressions-operators/operators.md#adding-parentheses) section of the [Operators](../../programming-guide/statements-expressions-operators/operators.md) article.</span></span> <span data-ttu-id="565ea-106">Pour obtenir la liste des opérateurs classés par niveau de priorité, consultez [Opérateurs C#](index.md).</span><span class="sxs-lookup"><span data-stu-id="565ea-106">For the list of operators ordered by precedence level, see [C# operators](index.md).</span></span>

## <a name="method-invocation"></a><span data-ttu-id="565ea-107">Appel de méthode</span><span class="sxs-lookup"><span data-stu-id="565ea-107">Method invocation</span></span>

<span data-ttu-id="565ea-108">L’exemple suivant montre comment appeler une méthode, avec ou sans arguments, et un délégué :</span><span class="sxs-lookup"><span data-stu-id="565ea-108">The following example demonstrates how to invoke a method, with or without arguments, and a delegate:</span></span>

[!code-csharp-interactive[use for invocation](~/samples/csharp/language-reference/operators/InvocationOperatorExamples.cs#Invocation)]

<span data-ttu-id="565ea-109">Vous utilisez également des parenthèses quand vous appelez un [constructeur](../../programming-guide/classes-and-structs/constructors.md) avec un opérateur [`new`](../keywords/new-operator.md).</span><span class="sxs-lookup"><span data-stu-id="565ea-109">You also use parentheses when you invoke a [constructor](../../programming-guide/classes-and-structs/constructors.md) with a [`new`](../keywords/new-operator.md) operator.</span></span>

<span data-ttu-id="565ea-110">Pour plus d’informations sur les méthodes, consultez [Méthodes](../../programming-guide/classes-and-structs/methods.md).</span><span class="sxs-lookup"><span data-stu-id="565ea-110">For more information about methods, see [Methods](../../programming-guide/classes-and-structs/methods.md).</span></span> <span data-ttu-id="565ea-111">Pour plus d’informations sur les délégués, consultez [Délégués](../../programming-guide/delegates/index.md).</span><span class="sxs-lookup"><span data-stu-id="565ea-111">For more information about delegates, see [Delegates](../../programming-guide/delegates/index.md).</span></span>

## <a name="cast-expression"></a><span data-ttu-id="565ea-112">Expression Cast</span><span class="sxs-lookup"><span data-stu-id="565ea-112">Cast expression</span></span>

<span data-ttu-id="565ea-113">Une expression Cast de la forme `(T)E` appelle un opérateur de conversion pour convertir la valeur d’expression `E` en type `T`.</span><span class="sxs-lookup"><span data-stu-id="565ea-113">A cast expression of the form `(T)E` invokes a conversion operator to convert the value of expression `E` to type `T`.</span></span> <span data-ttu-id="565ea-114">S’il n’existe aucune conversion explicite du type de `E` en type `T`, une erreur de compilation se produit.</span><span class="sxs-lookup"><span data-stu-id="565ea-114">If no explicit conversion exists from the type of `E` to type `T`, a compile-time error occurs.</span></span> <span data-ttu-id="565ea-115">Pour plus d’informations sur la définition d’un opérateur de conversion, consultez les articles sur les mots clés [explicit](../keywords/explicit.md) et [implicit](../keywords/implicit.md).</span><span class="sxs-lookup"><span data-stu-id="565ea-115">For information about how to define a conversion operator, see the [explicit](../keywords/explicit.md) and [implicit](../keywords/implicit.md) keyword articles.</span></span>

<span data-ttu-id="565ea-116">L’exemple suivant illustre la conversion de type entre des types numériques :</span><span class="sxs-lookup"><span data-stu-id="565ea-116">The following example demonstrates type conversion between numeric types:</span></span>

[!code-csharp-interactive[use for cast](~/samples/csharp/language-reference/operators/InvocationOperatorExamples.cs#Cast)]

<span data-ttu-id="565ea-117">Pour plus d’informations sur les conversions explicites prédéfinies entre des types numériques, consultez [Tableau des conversions numériques explicites](../keywords/explicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="565ea-117">For more information about predefined explicit conversions between numeric types, see [Explicit numeric conversions table](../keywords/explicit-numeric-conversions-table.md).</span></span>

<span data-ttu-id="565ea-118">Pour plus d’informations, consultez [Cast et conversions de types](../../programming-guide/types/casting-and-type-conversions.md) et [Opérateurs de conversion](../../programming-guide/statements-expressions-operators/conversion-operators.md).</span><span class="sxs-lookup"><span data-stu-id="565ea-118">For more information, see [Casting and type conversions](../../programming-guide/types/casting-and-type-conversions.md) and [Conversion operators](../../programming-guide/statements-expressions-operators/conversion-operators.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="565ea-119">Capacité de surcharge de l’opérateur</span><span class="sxs-lookup"><span data-stu-id="565ea-119">Operator overloadability</span></span>

<span data-ttu-id="565ea-120">L’opérateur `()` ne peut pas être surchargé.</span><span class="sxs-lookup"><span data-stu-id="565ea-120">The operator `()` cannot be overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="565ea-121">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="565ea-121">C# language specification</span></span>

<span data-ttu-id="565ea-122">Pour plus d’informations, consultez les sections [Expressions d’appel](~/_csharplang/spec/expressions.md#invocation-expressions) et [Expressions Cast](~/_csharplang/spec/expressions.md#cast-expressions) de la [spécification du langage C#](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="565ea-122">For more information, see the [Invocation expressions](~/_csharplang/spec/expressions.md#invocation-expressions) and [Cast expressions](~/_csharplang/spec/expressions.md#cast-expressions) sections of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="565ea-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="565ea-123">See also</span></span>

- [<span data-ttu-id="565ea-124">Référence C#</span><span class="sxs-lookup"><span data-stu-id="565ea-124">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="565ea-125">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="565ea-125">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="565ea-126">Opérateurs C#</span><span class="sxs-lookup"><span data-stu-id="565ea-126">C# Operators</span></span>](index.md)
