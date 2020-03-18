---
title: Opérateurs de comparaison - Référence C#
description: Découvrez les opérateurs de comparaison C# que vous pouvez utiliser pour vérifier l’ordre des valeurs numériques.
ms.date: 04/25/2019
author: pkulikov
f1_keywords:
- <_CSharpKeyword
- '>_CSharpKeyword'
- <=_CSharpKeyword
- '>=_CSharpKeyword'
helpviewer_keywords:
- comparison operators [C#]
- relational operators [C#]
- less than operator [C#]
- < operator [C#]
- greater than operator [C#]
- '> operator [C#]'
- less than or equal to operator [C#]
- <= operator [C#]
- greater than or equal to operator [C#]
- '>= operator [C#]'
ms.openlocfilehash: 68502205193a1fc8ab7410053e13274560ffffb0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399244"
---
# <a name="comparison-operators-c-reference"></a><span data-ttu-id="65a22-103">Opérateurs de comparaison (référence C#)</span><span class="sxs-lookup"><span data-stu-id="65a22-103">Comparison operators (C# reference)</span></span>

<span data-ttu-id="65a22-104">La [ `<` comparaison (moins de)](#less-than-operator-), [ `>` (plus grande que)](#greater-than-operator-) [ `<=` , (moins ou égale)](#less-than-or-equal-operator-), et [ `>=` (plus ou plus élevée),](#greater-than-or-equal-operator-) également connue sous le nom relationnel, les opérateurs comparent leurs opérands.</span><span class="sxs-lookup"><span data-stu-id="65a22-104">The [`<` (less than)](#less-than-operator-), [`>` (greater than)](#greater-than-operator-), [`<=` (less than or equal)](#less-than-or-equal-operator-), and [`>=` (greater than or equal)](#greater-than-or-equal-operator-) comparison, also known as relational, operators compare their operands.</span></span> <span data-ttu-id="65a22-105">Ces opérateurs sont soutenus par tous les types [numériques intégrals](../builtin-types/integral-numeric-types.md) et [à points flottants.](../builtin-types/floating-point-numeric-types.md)</span><span class="sxs-lookup"><span data-stu-id="65a22-105">Those operators are supported by all [integral](../builtin-types/integral-numeric-types.md) and [floating-point](../builtin-types/floating-point-numeric-types.md) numeric types.</span></span>

> [!NOTE]
> <span data-ttu-id="65a22-106">Pour les opérateurs `==`, `<`, `>`, `<=` et `>=`, si un des opérandes n’est pas un nombre (<xref:System.Double.NaN?displayProperty=nameWithType> ou <xref:System.Single.NaN?displayProperty=nameWithType>), le résultat de l’opération est `false`.</span><span class="sxs-lookup"><span data-stu-id="65a22-106">For the `==`, `<`, `>`, `<=`, and `>=` operators, if any of the operands is not a number (<xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType>), the result of operation is `false`.</span></span> <span data-ttu-id="65a22-107">Cela signifie que la valeur `NaN` n’est ni supérieure à, ni inférieure à, ni égale à n’importe quelle autre valeur `double` (ou `float`), y compris `NaN`.</span><span class="sxs-lookup"><span data-stu-id="65a22-107">That means that the `NaN` value is neither greater than, less than, nor equal to any other `double` (or `float`) value, including `NaN`.</span></span> <span data-ttu-id="65a22-108">Pour plus d’informations et des exemples, consultez l’article de référence <xref:System.Double.NaN?displayProperty=nameWithType> ou <xref:System.Single.NaN?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="65a22-108">For more information and examples, see the <xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType> reference article.</span></span>

<span data-ttu-id="65a22-109">Les types d’énumération prennent également en charge les opérateurs de comparaison.</span><span class="sxs-lookup"><span data-stu-id="65a22-109">Enumeration types also support comparison operators.</span></span> <span data-ttu-id="65a22-110">Pour les opérandes du même type [enum](../builtin-types/enum.md), les valeurs correspondantes du type intégral sous-jacent sont comparées.</span><span class="sxs-lookup"><span data-stu-id="65a22-110">For operands of the same [enum](../builtin-types/enum.md) type, the corresponding values of the underlying integral type are compared.</span></span>

<span data-ttu-id="65a22-111">Les [ `==` `!=` opérateurs et les opérateurs](equality-operators.md) vérifient si leurs opérands sont égaux ou non.</span><span class="sxs-lookup"><span data-stu-id="65a22-111">The [`==` and `!=` operators](equality-operators.md) check if their operands are equal or not.</span></span>

## <a name="less-than-operator-"></a><span data-ttu-id="65a22-112">Opérateur Inférieur à \<</span><span class="sxs-lookup"><span data-stu-id="65a22-112">Less than operator \<</span></span>

<span data-ttu-id="65a22-113">L’opérateur `<` retourne `true` si son opérande de partie gauche est inférieur à son opérande de partie droite, `false` dans le cas contraire :</span><span class="sxs-lookup"><span data-stu-id="65a22-113">The `<` operator returns `true` if its left-hand operand is less than its right-hand operand, `false` otherwise:</span></span>

[!code-csharp-interactive[less than example](snippets/ComparisonOperators.cs#Less)]

## <a name="greater-than-operator-"></a><span data-ttu-id="65a22-114">Opérateur Supérieur à ></span><span class="sxs-lookup"><span data-stu-id="65a22-114">Greater than operator ></span></span>

<span data-ttu-id="65a22-115">L’opérateur `>` retourne `true` si son opérande de partie gauche est supérieur à son opérande de partie droite, `false` dans le cas contraire :</span><span class="sxs-lookup"><span data-stu-id="65a22-115">The `>` operator returns `true` if its left-hand operand is greater than its right-hand operand, `false` otherwise:</span></span>

[!code-csharp-interactive[greater than example](snippets/ComparisonOperators.cs#Greater)]

## <a name="less-than-or-equal-operator-"></a><span data-ttu-id="65a22-116">Opérateur Inférieur ou égal à \<=</span><span class="sxs-lookup"><span data-stu-id="65a22-116">Less than or equal operator \<=</span></span>

<span data-ttu-id="65a22-117">L’opérateur `<=` retourne `true` si son opérande de partie gauche est inférieur ou égal à son opérande de partie droite, `false` dans le cas contraire :</span><span class="sxs-lookup"><span data-stu-id="65a22-117">The `<=` operator returns `true` if its left-hand operand is less than or equal to its right-hand operand, `false` otherwise:</span></span>

[!code-csharp-interactive[less than or equal example](snippets/ComparisonOperators.cs#LessOrEqual)]

## <a name="greater-than-or-equal-operator-"></a><span data-ttu-id="65a22-118">Opérateur Supérieur ou égal à >=</span><span class="sxs-lookup"><span data-stu-id="65a22-118">Greater than or equal operator >=</span></span>

<span data-ttu-id="65a22-119">L’opérateur `>=` retourne `true` si son opérande de partie gauche est supérieur ou égal à son opérande de partie droite, `false` dans le cas contraire :</span><span class="sxs-lookup"><span data-stu-id="65a22-119">The `>=` operator returns `true` if its left-hand operand is greater than or equal to its right-hand operand, `false` otherwise:</span></span>

[!code-csharp-interactive[greater than or equal example](snippets/ComparisonOperators.cs#GreaterOrEqual)]

## <a name="operator-overloadability"></a><span data-ttu-id="65a22-120">Capacité de surcharge de l’opérateur</span><span class="sxs-lookup"><span data-stu-id="65a22-120">Operator overloadability</span></span>

<span data-ttu-id="65a22-121">Un type défini par l’utilisateur `<=`peut `>=` [surcharger](operator-overloading.md) le `<`, `>`, et les opérateurs.</span><span class="sxs-lookup"><span data-stu-id="65a22-121">A user-defined type can [overload](operator-overloading.md) the `<`, `>`, `<=`, and `>=` operators.</span></span>

<span data-ttu-id="65a22-122">Si un type surcharge un des opérateurs `<` ou `>`, il doit surcharger à la fois `<` et `>`.</span><span class="sxs-lookup"><span data-stu-id="65a22-122">If a type overloads one of the `<` or `>` operators, it must overload both `<` and `>`.</span></span> <span data-ttu-id="65a22-123">Si un type surcharge un des opérateurs `<=` ou `>=`, il doit surcharger à la fois `<=` et `>=`.</span><span class="sxs-lookup"><span data-stu-id="65a22-123">If a type overloads one of the `<=` or `>=` operators, it must overload both `<=` and `>=`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="65a22-124">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="65a22-124">C# language specification</span></span>

<span data-ttu-id="65a22-125">Pour plus d’informations, consultez la section [Opérateurs relationnels et de test de type](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="65a22-125">For more information, see the [Relational and type-testing operators](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="65a22-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="65a22-126">See also</span></span>

- [<span data-ttu-id="65a22-127">Référence C#</span><span class="sxs-lookup"><span data-stu-id="65a22-127">C# reference</span></span>](../index.md)
- [<span data-ttu-id="65a22-128">Opérateurs CMD</span><span class="sxs-lookup"><span data-stu-id="65a22-128">C# operators</span></span>](index.md)
- <xref:System.IComparable%601?displayProperty=nameWithType>
- [<span data-ttu-id="65a22-129">Opérateurs d’égalité</span><span class="sxs-lookup"><span data-stu-id="65a22-129">Equality operators</span></span>](equality-operators.md)
