---
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
ms.openlocfilehash: 4623dc7d6c8c6c437c78aee45f0eeee8a92e3200
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2020
ms.locfileid: "87854878"
---
# <a name="bool-c-reference"></a><span data-ttu-id="c7714-102">bool (référence C#)</span><span class="sxs-lookup"><span data-stu-id="c7714-102">bool (C# reference)</span></span>

<span data-ttu-id="c7714-103">Le `bool` mot clé type est un alias pour le <xref:System.Boolean?displayProperty=nameWithType> type de structure .net qui représente une valeur booléenne, qui peut être `true` ou `false` .</span><span class="sxs-lookup"><span data-stu-id="c7714-103">The `bool` type keyword is an alias for the .NET <xref:System.Boolean?displayProperty=nameWithType> structure type that represents a Boolean value, which can be either `true` or `false`.</span></span>

<span data-ttu-id="c7714-104">Pour effectuer des opérations logiques avec des valeurs de `bool` type, utilisez des opérateurs [logiques booléens](../operators/boolean-logical-operators.md) .</span><span class="sxs-lookup"><span data-stu-id="c7714-104">To perform logical operations with values of the `bool` type, use [Boolean logical](../operators/boolean-logical-operators.md) operators.</span></span> <span data-ttu-id="c7714-105">Le `bool` type est le type de résultat des opérateurs de [comparaison](../operators/comparison-operators.md) et d' [égalité](../operators/equality-operators.md) .</span><span class="sxs-lookup"><span data-stu-id="c7714-105">The `bool` type is the result type of [comparison](../operators/comparison-operators.md) and [equality](../operators/equality-operators.md) operators.</span></span> <span data-ttu-id="c7714-106">Une `bool` expression peut être une expression conditionnelle de contrôle dans les instructions [If](../keywords/if-else.md), [do](../keywords/do.md), [while](../keywords/while.md)et [for](../keywords/for.md) et dans l' [opérateur `?:` conditionnel ](../operators/conditional-operator.md).</span><span class="sxs-lookup"><span data-stu-id="c7714-106">A `bool` expression can be a controlling conditional expression in the [if](../keywords/if-else.md), [do](../keywords/do.md), [while](../keywords/while.md), and [for](../keywords/for.md) statements and in the [conditional operator `?:`](../operators/conditional-operator.md).</span></span>

<span data-ttu-id="c7714-107">La valeur par défaut du `bool` type est `false` .</span><span class="sxs-lookup"><span data-stu-id="c7714-107">The default value of the `bool` type is `false`.</span></span>

## <a name="literals"></a><span data-ttu-id="c7714-108">Littéraux</span><span class="sxs-lookup"><span data-stu-id="c7714-108">Literals</span></span>

<span data-ttu-id="c7714-109">Vous pouvez utiliser les `true` `false` littéraux et pour initialiser une `bool` variable ou pour passer une `bool` valeur :</span><span class="sxs-lookup"><span data-stu-id="c7714-109">You can use the `true` and `false` literals to initialize a `bool` variable or to pass a `bool` value:</span></span>

[!code-csharp-interactive[bool literals](snippets/BoolType.cs#Literals)]

## <a name="three-valued-boolean-logic"></a><span data-ttu-id="c7714-110">Logique booléenne à trois valeurs</span><span class="sxs-lookup"><span data-stu-id="c7714-110">Three-valued Boolean logic</span></span>

<span data-ttu-id="c7714-111">Utilisez le `bool?` type Nullable, si vous avez besoin de prendre en charge la logique à trois valeurs, par exemple, lorsque vous utilisez des bases de données qui prennent en charge un type booléen à trois valeurs.</span><span class="sxs-lookup"><span data-stu-id="c7714-111">Use the nullable `bool?` type, if you need to support the three-valued logic, for example, when you work with databases that support a three-valued Boolean type.</span></span> <span data-ttu-id="c7714-112">Dans le cas des opérandes `bool?`, les opérateurs prédéfinis `&` et `|` prennent en charge la logique à trois valeurs.</span><span class="sxs-lookup"><span data-stu-id="c7714-112">For the `bool?` operands, the predefined `&` and `|` operators support the three-valued logic.</span></span> <span data-ttu-id="c7714-113">Pour plus d’informations, voir la section [Opérateurs logiques booléens Nullable](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) de l’article [Opérateurs logiques booléens](../operators/boolean-logical-operators.md).</span><span class="sxs-lookup"><span data-stu-id="c7714-113">For more information, see the [Nullable Boolean logical operators](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) section of the [Boolean logical operators](../operators/boolean-logical-operators.md) article.</span></span>

<span data-ttu-id="c7714-114">Pour plus d’informations sur les types valeur Nullable, consultez [types valeur Nullable](nullable-value-types.md).</span><span class="sxs-lookup"><span data-stu-id="c7714-114">For more information about nullable value types, see [Nullable value types](nullable-value-types.md).</span></span>

## <a name="conversions"></a><span data-ttu-id="c7714-115">Conversions</span><span class="sxs-lookup"><span data-stu-id="c7714-115">Conversions</span></span>

<span data-ttu-id="c7714-116">C# fournit uniquement deux conversions qui impliquent le `bool` type.</span><span class="sxs-lookup"><span data-stu-id="c7714-116">C# provides only two conversions that involve the `bool` type.</span></span> <span data-ttu-id="c7714-117">Il s’agit d’une conversion implicite vers le type Nullable correspondant `bool?` et d’une conversion explicite du `bool?` type.</span><span class="sxs-lookup"><span data-stu-id="c7714-117">Those are an implicit conversion to the corresponding nullable `bool?` type and an explicit conversion from the `bool?` type.</span></span> <span data-ttu-id="c7714-118">Toutefois, .NET fournit des méthodes supplémentaires que vous pouvez utiliser pour convertir vers ou à partir du `bool` type.</span><span class="sxs-lookup"><span data-stu-id="c7714-118">However, .NET provides additional methods that you can use to convert to or from the `bool` type.</span></span> <span data-ttu-id="c7714-119">Pour plus d’informations, consultez la section [conversion de valeurs booléennes en et à partir](/dotnet/api/system.boolean#converting-to-and-from-boolean-values) de la <xref:System.Boolean?displayProperty=nameWithType> page de référence des API.</span><span class="sxs-lookup"><span data-stu-id="c7714-119">For more information, see the [Converting to and from Boolean values](/dotnet/api/system.boolean#converting-to-and-from-boolean-values) section of the <xref:System.Boolean?displayProperty=nameWithType> API reference page.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="c7714-120">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="c7714-120">C# language specification</span></span>

<span data-ttu-id="c7714-121">Pour plus d’informations, consultez [la section type bool](~/_csharplang/spec/types.md#the-bool-type) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="c7714-121">For more information, see [The bool type](~/_csharplang/spec/types.md#the-bool-type) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c7714-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c7714-122">See also</span></span>

- [<span data-ttu-id="c7714-123">Informations de référence sur C#</span><span class="sxs-lookup"><span data-stu-id="c7714-123">C# reference</span></span>](../index.md)
- [<span data-ttu-id="c7714-124">Types de valeur</span><span class="sxs-lookup"><span data-stu-id="c7714-124">Value types</span></span>](value-types.md)
- [<span data-ttu-id="c7714-125">opérateurs true et false</span><span class="sxs-lookup"><span data-stu-id="c7714-125">true and false operators</span></span>](../operators/true-false-operators.md)
