---
title: Opérateurs de comparaison - Référence C#
description: Découvrez les opérateurs de comparaison C# que vous pouvez utiliser pour vérifier l’ordre des valeurs numériques.
ms.date: 05/11/2020
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
ms.openlocfilehash: 9fa739d8b5461d4043f3ae51f5d14949a95c68e5
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2020
ms.locfileid: "87916875"
---
# <a name="comparison-operators-c-reference"></a><span data-ttu-id="3fa96-103">Opérateurs de comparaison (référence C#)</span><span class="sxs-lookup"><span data-stu-id="3fa96-103">Comparison operators (C# reference)</span></span>

<span data-ttu-id="3fa96-104">Les opérateurs [ `<` (inférieur à)](#less-than-operator-), [ `>` (supérieur](#greater-than-operator-)à), [ `<=` (inférieur ou égal à)](#less-than-or-equal-operator-)et [ `>=` (supérieur ou égal à)](#greater-than-or-equal-operator-) , également connus sous le nom d’opérateurs relationnels, comparent leurs opérandes.</span><span class="sxs-lookup"><span data-stu-id="3fa96-104">The [`<` (less than)](#less-than-operator-), [`>` (greater than)](#greater-than-operator-), [`<=` (less than or equal)](#less-than-or-equal-operator-), and [`>=` (greater than or equal)](#greater-than-or-equal-operator-) comparison, also known as relational, operators compare their operands.</span></span> <span data-ttu-id="3fa96-105">Ces opérateurs sont pris en charge par tous les types numériques [intégraux](../builtin-types/integral-numeric-types.md) et [à virgule flottante](../builtin-types/floating-point-numeric-types.md) .</span><span class="sxs-lookup"><span data-stu-id="3fa96-105">Those operators are supported by all [integral](../builtin-types/integral-numeric-types.md) and [floating-point](../builtin-types/floating-point-numeric-types.md) numeric types.</span></span>

> [!NOTE]
> <span data-ttu-id="3fa96-106">Pour les opérateurs `==`, `<`, `>`, `<=` et `>=`, si un des opérandes n’est pas un nombre (<xref:System.Double.NaN?displayProperty=nameWithType> ou <xref:System.Single.NaN?displayProperty=nameWithType>), le résultat de l’opération est `false`.</span><span class="sxs-lookup"><span data-stu-id="3fa96-106">For the `==`, `<`, `>`, `<=`, and `>=` operators, if any of the operands is not a number (<xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType>), the result of operation is `false`.</span></span> <span data-ttu-id="3fa96-107">Cela signifie que la valeur `NaN` n’est ni supérieure à, ni inférieure à, ni égale à n’importe quelle autre valeur `double` (ou `float`), y compris `NaN`.</span><span class="sxs-lookup"><span data-stu-id="3fa96-107">That means that the `NaN` value is neither greater than, less than, nor equal to any other `double` (or `float`) value, including `NaN`.</span></span> <span data-ttu-id="3fa96-108">Pour plus d’informations et des exemples, consultez l’article de référence <xref:System.Double.NaN?displayProperty=nameWithType> ou <xref:System.Single.NaN?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3fa96-108">For more information and examples, see the <xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType> reference article.</span></span>

<span data-ttu-id="3fa96-109">Le type [char](../builtin-types/char.md) prend également en charge les opérateurs de comparaison.</span><span class="sxs-lookup"><span data-stu-id="3fa96-109">The [char](../builtin-types/char.md) type also supports comparison operators.</span></span> <span data-ttu-id="3fa96-110">Dans le cas des `char` opérandes, les codes de caractère correspondants sont comparés.</span><span class="sxs-lookup"><span data-stu-id="3fa96-110">In the case of `char` operands, the corresponding character codes are compared.</span></span>

<span data-ttu-id="3fa96-111">Les types d’énumération prennent également en charge les opérateurs de comparaison.</span><span class="sxs-lookup"><span data-stu-id="3fa96-111">Enumeration types also support comparison operators.</span></span> <span data-ttu-id="3fa96-112">Pour les opérandes du même type [enum](../builtin-types/enum.md), les valeurs correspondantes du type intégral sous-jacent sont comparées.</span><span class="sxs-lookup"><span data-stu-id="3fa96-112">For operands of the same [enum](../builtin-types/enum.md) type, the corresponding values of the underlying integral type are compared.</span></span>

<span data-ttu-id="3fa96-113">Les [ `==` `!=` opérateurs et](equality-operators.md) vérifient si leurs opérandes sont égaux ou non.</span><span class="sxs-lookup"><span data-stu-id="3fa96-113">The [`==` and `!=` operators](equality-operators.md) check if their operands are equal or not.</span></span>

## <a name="less-than-operator-"></a><span data-ttu-id="3fa96-114">Opérateur Inférieur à \<</span><span class="sxs-lookup"><span data-stu-id="3fa96-114">Less than operator \<</span></span>

<span data-ttu-id="3fa96-115">L’opérateur `<` retourne `true` si son opérande de partie gauche est inférieur à son opérande de partie droite, `false` dans le cas contraire :</span><span class="sxs-lookup"><span data-stu-id="3fa96-115">The `<` operator returns `true` if its left-hand operand is less than its right-hand operand, `false` otherwise:</span></span>

[!code-csharp-interactive[less than example](snippets/shared/ComparisonOperators.cs#Less)]

## <a name="greater-than-operator-"></a><span data-ttu-id="3fa96-116">Opérateur Supérieur à ></span><span class="sxs-lookup"><span data-stu-id="3fa96-116">Greater than operator ></span></span>

<span data-ttu-id="3fa96-117">L’opérateur `>` retourne `true` si son opérande de partie gauche est supérieur à son opérande de partie droite, `false` dans le cas contraire :</span><span class="sxs-lookup"><span data-stu-id="3fa96-117">The `>` operator returns `true` if its left-hand operand is greater than its right-hand operand, `false` otherwise:</span></span>

[!code-csharp-interactive[greater than example](snippets/shared/ComparisonOperators.cs#Greater)]

## <a name="less-than-or-equal-operator-"></a><span data-ttu-id="3fa96-118">Opérateur Inférieur ou égal à \<=</span><span class="sxs-lookup"><span data-stu-id="3fa96-118">Less than or equal operator \<=</span></span>

<span data-ttu-id="3fa96-119">L’opérateur `<=` retourne `true` si son opérande de partie gauche est inférieur ou égal à son opérande de partie droite, `false` dans le cas contraire :</span><span class="sxs-lookup"><span data-stu-id="3fa96-119">The `<=` operator returns `true` if its left-hand operand is less than or equal to its right-hand operand, `false` otherwise:</span></span>

[!code-csharp-interactive[less than or equal example](snippets/shared/ComparisonOperators.cs#LessOrEqual)]

## <a name="greater-than-or-equal-operator-"></a><span data-ttu-id="3fa96-120">Opérateur Supérieur ou égal à >=</span><span class="sxs-lookup"><span data-stu-id="3fa96-120">Greater than or equal operator >=</span></span>

<span data-ttu-id="3fa96-121">L’opérateur `>=` retourne `true` si son opérande de partie gauche est supérieur ou égal à son opérande de partie droite, `false` dans le cas contraire :</span><span class="sxs-lookup"><span data-stu-id="3fa96-121">The `>=` operator returns `true` if its left-hand operand is greater than or equal to its right-hand operand, `false` otherwise:</span></span>

[!code-csharp-interactive[greater than or equal example](snippets/shared/ComparisonOperators.cs#GreaterOrEqual)]

## <a name="operator-overloadability"></a><span data-ttu-id="3fa96-122">Capacité de surcharge de l’opérateur</span><span class="sxs-lookup"><span data-stu-id="3fa96-122">Operator overloadability</span></span>

<span data-ttu-id="3fa96-123">Un type défini par l’utilisateur peut [surcharger](operator-overloading.md) les `<` opérateurs,, `>` `<=` et `>=` .</span><span class="sxs-lookup"><span data-stu-id="3fa96-123">A user-defined type can [overload](operator-overloading.md) the `<`, `>`, `<=`, and `>=` operators.</span></span>

<span data-ttu-id="3fa96-124">Si un type surcharge un des opérateurs `<` ou `>`, il doit surcharger à la fois `<` et `>`.</span><span class="sxs-lookup"><span data-stu-id="3fa96-124">If a type overloads one of the `<` or `>` operators, it must overload both `<` and `>`.</span></span> <span data-ttu-id="3fa96-125">Si un type surcharge un des opérateurs `<=` ou `>=`, il doit surcharger à la fois `<=` et `>=`.</span><span class="sxs-lookup"><span data-stu-id="3fa96-125">If a type overloads one of the `<=` or `>=` operators, it must overload both `<=` and `>=`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="3fa96-126">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="3fa96-126">C# language specification</span></span>

<span data-ttu-id="3fa96-127">Pour plus d’informations, consultez la section [Opérateurs relationnels et de test de type](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="3fa96-127">For more information, see the [Relational and type-testing operators](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3fa96-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3fa96-128">See also</span></span>

- [<span data-ttu-id="3fa96-129">Informations de référence sur C#</span><span class="sxs-lookup"><span data-stu-id="3fa96-129">C# reference</span></span>](../index.md)
- [<span data-ttu-id="3fa96-130">Opérateurs et expressions C#</span><span class="sxs-lookup"><span data-stu-id="3fa96-130">C# operators and expressions</span></span>](index.md)
- <xref:System.IComparable%601?displayProperty=nameWithType>
- [<span data-ttu-id="3fa96-131">Opérateurs d'égalité</span><span class="sxs-lookup"><span data-stu-id="3fa96-131">Equality operators</span></span>](equality-operators.md)
