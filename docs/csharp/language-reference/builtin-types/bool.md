---
title: type de seins - référence C
ms.date: 11/26/2019
f1_keywords:
- bool
- bool_CSharpKeyword
helpviewer_keywords:
- bool data type [C#]
- Boolean [C#]
ms.assetid: 551cfe35-2632-4343-af49-33ad12da08e2
ms.openlocfilehash: 2ba2e54a6b0f24402fc3728dfe19b548a2368830
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78846443"
---
# <a name="bool-c-reference"></a><span data-ttu-id="7a6d7-102">bool (référence C)</span><span class="sxs-lookup"><span data-stu-id="7a6d7-102">bool (C# reference)</span></span>

<span data-ttu-id="7a6d7-103">Le `bool` mot clé de type <xref:System.Boolean?displayProperty=nameWithType> est un alias pour le type de `true` `false`structure .NET qui représente une valeur Boolean, qui peut être soit ou .</span><span class="sxs-lookup"><span data-stu-id="7a6d7-103">The `bool` type keyword is an alias for the .NET <xref:System.Boolean?displayProperty=nameWithType> structure type that represents a Boolean value, which can be either `true` or `false`.</span></span>

<span data-ttu-id="7a6d7-104">Pour effectuer des opérations `bool` logiques avec des valeurs du type, utilisez [boolean](../operators/boolean-logical-operators.md) opérateurs logiques.</span><span class="sxs-lookup"><span data-stu-id="7a6d7-104">To perform logical operations with values of the `bool` type, use [Boolean logical](../operators/boolean-logical-operators.md) operators.</span></span> <span data-ttu-id="7a6d7-105">Le `bool` type est le type de résultat des opérateurs de [comparaison](../operators/comparison-operators.md) et [d’égalité.](../operators/equality-operators.md)</span><span class="sxs-lookup"><span data-stu-id="7a6d7-105">The `bool` type is the result type of [comparison](../operators/comparison-operators.md) and [equality](../operators/equality-operators.md) operators.</span></span> <span data-ttu-id="7a6d7-106">Une `bool` expression peut être une expression conditionnelle de contrôle dans le [si,](../keywords/if-else.md) [faire](../keywords/do.md), [tandis que](../keywords/while.md), et [pour](../keywords/for.md) les déclarations et dans l’opérateur [ `?:`conditionnel ](../operators/conditional-operator.md).</span><span class="sxs-lookup"><span data-stu-id="7a6d7-106">A `bool` expression can be a controlling conditional expression in the [if](../keywords/if-else.md), [do](../keywords/do.md), [while](../keywords/while.md), and [for](../keywords/for.md) statements and in the [conditional operator `?:`](../operators/conditional-operator.md).</span></span>

<span data-ttu-id="7a6d7-107">La valeur par `bool` défaut `false`du type est .</span><span class="sxs-lookup"><span data-stu-id="7a6d7-107">The default value of the `bool` type is `false`.</span></span>

## <a name="literals"></a><span data-ttu-id="7a6d7-108">Littéraux</span><span class="sxs-lookup"><span data-stu-id="7a6d7-108">Literals</span></span>

<span data-ttu-id="7a6d7-109">Vous pouvez `true` utiliser `false` les et les `bool` littérals pour `bool` initialiser une variable ou pour passer une valeur :</span><span class="sxs-lookup"><span data-stu-id="7a6d7-109">You can use the `true` and `false` literals to initialize a `bool` variable or to pass a `bool` value:</span></span>

[!code-csharp-interactive[bool literals](snippets/BoolType.cs#Literals)]

## <a name="three-valued-boolean-logic"></a><span data-ttu-id="7a6d7-110">Logique Boolean à trois valeur</span><span class="sxs-lookup"><span data-stu-id="7a6d7-110">Three-valued Boolean logic</span></span>

<span data-ttu-id="7a6d7-111">Utilisez le `bool?` type infirmable, si vous devez prendre en charge la logique à trois valeur, par exemple, lorsque vous travaillez avec des bases de données qui prennent en charge un type Boolean de trois valeur.</span><span class="sxs-lookup"><span data-stu-id="7a6d7-111">Use the nullable `bool?` type, if you need to support the three-valued logic, for example, when you work with databases that support a three-valued Boolean type.</span></span> <span data-ttu-id="7a6d7-112">Dans le cas des opérandes `bool?`, les opérateurs prédéfinis `&` et `|` prennent en charge la logique à trois valeurs.</span><span class="sxs-lookup"><span data-stu-id="7a6d7-112">For the `bool?` operands, the predefined `&` and `|` operators support the three-valued logic.</span></span> <span data-ttu-id="7a6d7-113">Pour plus d’informations, voir la section [Opérateurs logiques booléens Nullable](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) de l’article [Opérateurs logiques booléens](../operators/boolean-logical-operators.md).</span><span class="sxs-lookup"><span data-stu-id="7a6d7-113">For more information, see the [Nullable Boolean logical operators](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) section of the [Boolean logical operators](../operators/boolean-logical-operators.md) article.</span></span>

<span data-ttu-id="7a6d7-114">Pour plus d’informations sur les types de valeur nulable, voir [les types de valeur nulable](nullable-value-types.md).</span><span class="sxs-lookup"><span data-stu-id="7a6d7-114">For more information about nullable value types, see [Nullable value types](nullable-value-types.md).</span></span>

## <a name="conversions"></a><span data-ttu-id="7a6d7-115">Conversions</span><span class="sxs-lookup"><span data-stu-id="7a6d7-115">Conversions</span></span>

<span data-ttu-id="7a6d7-116">C fournit seulement deux conversions `bool` qui impliquent le type.</span><span class="sxs-lookup"><span data-stu-id="7a6d7-116">C# provides only two conversions that involve the `bool` type.</span></span> <span data-ttu-id="7a6d7-117">Il s’agit d’une `bool?` conversion implicite au type `bool?` nul correspondant et d’une conversion explicite du type.</span><span class="sxs-lookup"><span data-stu-id="7a6d7-117">Those are an implicit conversion to the corresponding nullable `bool?` type and an explicit conversion from the `bool?` type.</span></span> <span data-ttu-id="7a6d7-118">Cependant, .NET fournit des méthodes supplémentaires que vous `bool` pouvez utiliser pour convertir vers ou à partir du type.</span><span class="sxs-lookup"><span data-stu-id="7a6d7-118">However, .NET provides additional methods that you can use to convert to or from the `bool` type.</span></span> <span data-ttu-id="7a6d7-119">Pour plus d’informations, consultez la section [Convertir les valeurs de Boolean à](/dotnet/api/system.boolean#converting-to-and-from-boolean-values) partir de la page de référence de l’API. <xref:System.Boolean?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="7a6d7-119">For more information, see the [Converting to and from Boolean values](/dotnet/api/system.boolean#converting-to-and-from-boolean-values) section of the <xref:System.Boolean?displayProperty=nameWithType> API reference page.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="7a6d7-120">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="7a6d7-120">C# language specification</span></span>

<span data-ttu-id="7a6d7-121">Pour plus d’informations, voir La section [du type bool](~/_csharplang/spec/types.md#the-bool-type) de la [spécification linguistique C](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="7a6d7-121">For more information, see [The bool type](~/_csharplang/spec/types.md#the-bool-type) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7a6d7-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7a6d7-122">See also</span></span>

- [<span data-ttu-id="7a6d7-123">Référence C#</span><span class="sxs-lookup"><span data-stu-id="7a6d7-123">C# reference</span></span>](../index.md)
- [<span data-ttu-id="7a6d7-124">Types de valeur</span><span class="sxs-lookup"><span data-stu-id="7a6d7-124">Value types</span></span>](value-types.md)
- [<span data-ttu-id="7a6d7-125">opérateurs true et false</span><span class="sxs-lookup"><span data-stu-id="7a6d7-125">true and false operators</span></span>](../operators/true-false-operators.md)
