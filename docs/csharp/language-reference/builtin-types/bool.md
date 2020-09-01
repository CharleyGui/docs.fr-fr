---
description: 'En savoir plus sur le type booléen intégré en C #'
title: bool, type-référence C#
ms.date: 11/26/2019
f1_keywords:
- bool
- bool_CSharpKeyword
- "true"
- "false"
- true_CSharpKeyword
- false_CSharpKeyword
helpviewer_keywords:
- bool data type [C#]
- Boolean [C#]
ms.assetid: 551cfe35-2632-4343-af49-33ad12da08e2
ms.openlocfilehash: 23e5bc34f1751b0a706c20dae340920239fcda9d
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89126461"
---
# <a name="bool-c-reference"></a><span data-ttu-id="1c8ad-103">bool (référence C#)</span><span class="sxs-lookup"><span data-stu-id="1c8ad-103">bool (C# reference)</span></span>

<span data-ttu-id="1c8ad-104">Le `bool` mot clé type est un alias pour le <xref:System.Boolean?displayProperty=nameWithType> type de structure .net qui représente une valeur booléenne, qui peut être `true` ou `false` .</span><span class="sxs-lookup"><span data-stu-id="1c8ad-104">The `bool` type keyword is an alias for the .NET <xref:System.Boolean?displayProperty=nameWithType> structure type that represents a Boolean value, which can be either `true` or `false`.</span></span>

<span data-ttu-id="1c8ad-105">Pour effectuer des opérations logiques avec des valeurs de `bool` type, utilisez des opérateurs [logiques booléens](../operators/boolean-logical-operators.md) .</span><span class="sxs-lookup"><span data-stu-id="1c8ad-105">To perform logical operations with values of the `bool` type, use [Boolean logical](../operators/boolean-logical-operators.md) operators.</span></span> <span data-ttu-id="1c8ad-106">Le `bool` type est le type de résultat des opérateurs de [comparaison](../operators/comparison-operators.md) et d' [égalité](../operators/equality-operators.md) .</span><span class="sxs-lookup"><span data-stu-id="1c8ad-106">The `bool` type is the result type of [comparison](../operators/comparison-operators.md) and [equality](../operators/equality-operators.md) operators.</span></span> <span data-ttu-id="1c8ad-107">Une `bool` expression peut être une expression conditionnelle de contrôle dans les instructions [If](../keywords/if-else.md), [do](../keywords/do.md), [while](../keywords/while.md)et [for](../keywords/for.md) et dans l' [opérateur `?:` conditionnel ](../operators/conditional-operator.md).</span><span class="sxs-lookup"><span data-stu-id="1c8ad-107">A `bool` expression can be a controlling conditional expression in the [if](../keywords/if-else.md), [do](../keywords/do.md), [while](../keywords/while.md), and [for](../keywords/for.md) statements and in the [conditional operator `?:`](../operators/conditional-operator.md).</span></span>

<span data-ttu-id="1c8ad-108">La valeur par défaut du `bool` type est `false` .</span><span class="sxs-lookup"><span data-stu-id="1c8ad-108">The default value of the `bool` type is `false`.</span></span>

## <a name="literals"></a><span data-ttu-id="1c8ad-109">Littéraux</span><span class="sxs-lookup"><span data-stu-id="1c8ad-109">Literals</span></span>

<span data-ttu-id="1c8ad-110">Vous pouvez utiliser les `true` `false` littéraux et pour initialiser une `bool` variable ou pour passer une `bool` valeur :</span><span class="sxs-lookup"><span data-stu-id="1c8ad-110">You can use the `true` and `false` literals to initialize a `bool` variable or to pass a `bool` value:</span></span>

[!code-csharp-interactive[bool literals](snippets/BoolType.cs#Literals)]

## <a name="three-valued-boolean-logic"></a><span data-ttu-id="1c8ad-111">Logique booléenne à trois valeurs</span><span class="sxs-lookup"><span data-stu-id="1c8ad-111">Three-valued Boolean logic</span></span>

<span data-ttu-id="1c8ad-112">Utilisez le `bool?` type Nullable, si vous avez besoin de prendre en charge la logique à trois valeurs, par exemple, lorsque vous utilisez des bases de données qui prennent en charge un type booléen à trois valeurs.</span><span class="sxs-lookup"><span data-stu-id="1c8ad-112">Use the nullable `bool?` type, if you need to support the three-valued logic, for example, when you work with databases that support a three-valued Boolean type.</span></span> <span data-ttu-id="1c8ad-113">Dans le cas des opérandes `bool?`, les opérateurs prédéfinis `&` et `|` prennent en charge la logique à trois valeurs.</span><span class="sxs-lookup"><span data-stu-id="1c8ad-113">For the `bool?` operands, the predefined `&` and `|` operators support the three-valued logic.</span></span> <span data-ttu-id="1c8ad-114">Pour plus d’informations, voir la section [Opérateurs logiques booléens Nullable](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) de l’article [Opérateurs logiques booléens](../operators/boolean-logical-operators.md).</span><span class="sxs-lookup"><span data-stu-id="1c8ad-114">For more information, see the [Nullable Boolean logical operators](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) section of the [Boolean logical operators](../operators/boolean-logical-operators.md) article.</span></span>

<span data-ttu-id="1c8ad-115">Pour plus d’informations sur les types valeur Nullable, consultez [types valeur Nullable](nullable-value-types.md).</span><span class="sxs-lookup"><span data-stu-id="1c8ad-115">For more information about nullable value types, see [Nullable value types](nullable-value-types.md).</span></span>

## <a name="conversions"></a><span data-ttu-id="1c8ad-116">Conversions</span><span class="sxs-lookup"><span data-stu-id="1c8ad-116">Conversions</span></span>

<span data-ttu-id="1c8ad-117">C# fournit uniquement deux conversions qui impliquent le `bool` type.</span><span class="sxs-lookup"><span data-stu-id="1c8ad-117">C# provides only two conversions that involve the `bool` type.</span></span> <span data-ttu-id="1c8ad-118">Il s’agit d’une conversion implicite vers le type Nullable correspondant `bool?` et d’une conversion explicite du `bool?` type.</span><span class="sxs-lookup"><span data-stu-id="1c8ad-118">Those are an implicit conversion to the corresponding nullable `bool?` type and an explicit conversion from the `bool?` type.</span></span> <span data-ttu-id="1c8ad-119">Toutefois, .NET fournit des méthodes supplémentaires que vous pouvez utiliser pour convertir vers ou à partir du `bool` type.</span><span class="sxs-lookup"><span data-stu-id="1c8ad-119">However, .NET provides additional methods that you can use to convert to or from the `bool` type.</span></span> <span data-ttu-id="1c8ad-120">Pour plus d’informations, consultez la section [conversion de valeurs booléennes en et à partir](/dotnet/api/system.boolean#converting-to-and-from-boolean-values) de la <xref:System.Boolean?displayProperty=nameWithType> page de référence des API.</span><span class="sxs-lookup"><span data-stu-id="1c8ad-120">For more information, see the [Converting to and from Boolean values](/dotnet/api/system.boolean#converting-to-and-from-boolean-values) section of the <xref:System.Boolean?displayProperty=nameWithType> API reference page.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="1c8ad-121">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="1c8ad-121">C# language specification</span></span>

<span data-ttu-id="1c8ad-122">Pour plus d’informations, consultez [la section type bool](~/_csharplang/spec/types.md#the-bool-type) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="1c8ad-122">For more information, see [The bool type](~/_csharplang/spec/types.md#the-bool-type) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1c8ad-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1c8ad-123">See also</span></span>

- [<span data-ttu-id="1c8ad-124">Informations de référence sur C#</span><span class="sxs-lookup"><span data-stu-id="1c8ad-124">C# reference</span></span>](../index.md)
- [<span data-ttu-id="1c8ad-125">Types de valeur</span><span class="sxs-lookup"><span data-stu-id="1c8ad-125">Value types</span></span>](value-types.md)
- [<span data-ttu-id="1c8ad-126">opérateurs true et false</span><span class="sxs-lookup"><span data-stu-id="1c8ad-126">true and false operators</span></span>](../operators/true-false-operators.md)
