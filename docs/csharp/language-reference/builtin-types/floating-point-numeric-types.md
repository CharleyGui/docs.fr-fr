---
title: Types numériques à virgule flottante - Référence C#
description: Vue d’ensemble des types virgule flottante C# intégrés
ms.date: 10/22/2019
f1_keywords:
- float
- float_CSharpKeyword
- double
- double_CSharpKeyword
- decimal_CSharpKeyword
- decimal
helpviewer_keywords:
- floating-point numbers [C#]
- ranges of floating-point types [C#]
- size of floating-point types [C#]
- types [C#], floating-point types
- float keyword [C#]
- floating-point numbers [C#], float keyword
- double data type [C#]
- decimal keyword [C#]
ms.openlocfilehash: 9c8b11f9337ee9de90f2d4d96b5be162713bfcbd
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77093212"
---
# <a name="floating-point-numeric-types-c-reference"></a><span data-ttu-id="42013-103">Types numériques à virgule flottante (Référence C#)</span><span class="sxs-lookup"><span data-stu-id="42013-103">Floating-point numeric types (C# reference)</span></span>

<span data-ttu-id="42013-104">Les *types numériques à virgule flottante* représentent des nombres réels.</span><span class="sxs-lookup"><span data-stu-id="42013-104">The *floating-point numeric types* represent real numbers.</span></span> <span data-ttu-id="42013-105">Tous les types numériques à virgule flottante sont des [types valeur](value-types.md).</span><span class="sxs-lookup"><span data-stu-id="42013-105">All floating-point numeric types are [value types](value-types.md).</span></span> <span data-ttu-id="42013-106">Il s’agit également de [types simples](value-types.md#built-in-value-types) qui peuvent être initialisés avec des [littéraux](#real-literals).</span><span class="sxs-lookup"><span data-stu-id="42013-106">They are also [simple types](value-types.md#built-in-value-types) and can be initialized with [literals](#real-literals).</span></span> <span data-ttu-id="42013-107">Tous les types numériques à virgule flottante prennent en charge les opérateurs [arithmétiques](../operators/arithmetic-operators.md), de [comparaison](../operators/comparison-operators.md)et d' [égalité](../operators/equality-operators.md) .</span><span class="sxs-lookup"><span data-stu-id="42013-107">All floating-point numeric types support [arithmetic](../operators/arithmetic-operators.md), [comparison](../operators/comparison-operators.md), and [equality](../operators/equality-operators.md) operators.</span></span>

## <a name="characteristics-of-the-floating-point-types"></a><span data-ttu-id="42013-108">Caractéristiques des types à virgule flottante</span><span class="sxs-lookup"><span data-stu-id="42013-108">Characteristics of the floating-point types</span></span>

<span data-ttu-id="42013-109">C# prend en charge les types à virgule flottante prédéfinis suivants :</span><span class="sxs-lookup"><span data-stu-id="42013-109">C# supports the following predefined floating-point types:</span></span>
  
|<span data-ttu-id="42013-110">C# type/mot clé</span><span class="sxs-lookup"><span data-stu-id="42013-110">C# type/keyword</span></span>|<span data-ttu-id="42013-111">Plage approximative</span><span class="sxs-lookup"><span data-stu-id="42013-111">Approximate range</span></span>|<span data-ttu-id="42013-112">Precision</span><span class="sxs-lookup"><span data-stu-id="42013-112">Precision</span></span>|<span data-ttu-id="42013-113">Size</span><span class="sxs-lookup"><span data-stu-id="42013-113">Size</span></span>|<span data-ttu-id="42013-114">Type .NET</span><span class="sxs-lookup"><span data-stu-id="42013-114">.NET type</span></span>|
|----------|-----------------------|---------------|--------------|--------------|
|`float`|<span data-ttu-id="42013-115">±1,5 x 10<sup>−45</sup> à ±3,4 x 10<sup>38</sup></span><span class="sxs-lookup"><span data-stu-id="42013-115">±1.5 x 10<sup>−45</sup> to ±3.4 x 10<sup>38</sup></span></span>|<span data-ttu-id="42013-116">~6-9 chiffres</span><span class="sxs-lookup"><span data-stu-id="42013-116">~6-9 digits</span></span>|<span data-ttu-id="42013-117">4 octets</span><span class="sxs-lookup"><span data-stu-id="42013-117">4 bytes</span></span>|<xref:System.Single?displayProperty=nameWithType>|
|`double`|<span data-ttu-id="42013-118">De ±5,0 × 10<sup>−324</sup> à ±1,7 × 10<sup>308</sup></span><span class="sxs-lookup"><span data-stu-id="42013-118">±5.0 × 10<sup>−324</sup> to ±1.7 × 10<sup>308</sup></span></span>|<span data-ttu-id="42013-119">~15-17 chiffres</span><span class="sxs-lookup"><span data-stu-id="42013-119">~15-17 digits</span></span>|<span data-ttu-id="42013-120">8 octets</span><span class="sxs-lookup"><span data-stu-id="42013-120">8 bytes</span></span>|<xref:System.Double?displayProperty=nameWithType>|
|`decimal`|<span data-ttu-id="42013-121">±1,0 x 10<sup>-28</sup> to ±7,9228 x 10<sup>28</sup></span><span class="sxs-lookup"><span data-stu-id="42013-121">±1.0 x 10<sup>-28</sup> to ±7.9228 x 10<sup>28</sup></span></span>|<span data-ttu-id="42013-122">28 à 29 chiffres</span><span class="sxs-lookup"><span data-stu-id="42013-122">28-29 digits</span></span>|<span data-ttu-id="42013-123">16 octets</span><span class="sxs-lookup"><span data-stu-id="42013-123">16 bytes</span></span>|<xref:System.Decimal?displayProperty=nameWithType>|

<span data-ttu-id="42013-124">Dans le tableau précédent, chaque mot clé de type C# de la colonne la plus à gauche est un alias pour le type .NET correspondant.</span><span class="sxs-lookup"><span data-stu-id="42013-124">In the preceding table, each C# type keyword from the leftmost column is an alias for the corresponding .NET type.</span></span> <span data-ttu-id="42013-125">Ils sont interchangeables.</span><span class="sxs-lookup"><span data-stu-id="42013-125">They are interchangeable.</span></span> <span data-ttu-id="42013-126">Par exemple, les déclarations suivantes déclarent des variables du même type :</span><span class="sxs-lookup"><span data-stu-id="42013-126">For example, the following declarations declare variables of the same type:</span></span>

```csharp
double a = 12.3;
System.Double b = 12.3;
```

<span data-ttu-id="42013-127">La valeur par défaut pour tous les types virgule flottante est zéro, `0`.</span><span class="sxs-lookup"><span data-stu-id="42013-127">The default value of each floating-point type is zero, `0`.</span></span> <span data-ttu-id="42013-128">Chacun des types à virgule flottante a les constantes `MinValue` et `MaxValue` qui fournissent la valeur finie minimale et maximale de ce type.</span><span class="sxs-lookup"><span data-stu-id="42013-128">Each of the floating-point types has the `MinValue` and `MaxValue` constants that provide the minimum and maximum finite value of that type.</span></span> <span data-ttu-id="42013-129">Les types `float` et `double` fournissent également des constantes qui représentent des valeurs NaN (Not-a-Number) et d’infini.</span><span class="sxs-lookup"><span data-stu-id="42013-129">The `float` and `double` types also provide constants that represent not-a-number and infinity values.</span></span> <span data-ttu-id="42013-130">Par exemple, le type `double` fournit les constantes suivantes : <xref:System.Double.NaN?displayProperty=nameWithType>, <xref:System.Double.NegativeInfinity?displayProperty=nameWithType> et <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="42013-130">For example, the `double` type provides the following constants: <xref:System.Double.NaN?displayProperty=nameWithType>, <xref:System.Double.NegativeInfinity?displayProperty=nameWithType>, and <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="42013-131">Le type `decimal` fournit une plus grande précision et une plage de valeurs plus petite que `float` et `double`, ce qui le rend particulièrement approprié aux calculs financiers et monétaires.</span><span class="sxs-lookup"><span data-stu-id="42013-131">Because the `decimal` type has more precision and a smaller range than both `float` and `double`, it's appropriate for financial and monetary calculations.</span></span>

<span data-ttu-id="42013-132">Vous pouvez combiner des types [intégraux](integral-numeric-types.md) et des types virgule flottante dans une expression.</span><span class="sxs-lookup"><span data-stu-id="42013-132">You can mix [integral](integral-numeric-types.md) types and floating-point types in an expression.</span></span> <span data-ttu-id="42013-133">Dans ce cas, les types intégraux sont convertis en types virgule flottante.</span><span class="sxs-lookup"><span data-stu-id="42013-133">In this case, the integral types are converted to floating-point types.</span></span> <span data-ttu-id="42013-134">L’évaluation de l’expression est exécutée d’après les règles suivantes :</span><span class="sxs-lookup"><span data-stu-id="42013-134">The evaluation of the expression is performed according to the following rules:</span></span>

- <span data-ttu-id="42013-135">Si l’un des types à virgule flottante est `double`, l’expression prend la valeur `double`, ou la valeur [bool](bool.md) dans les comparaisons d’égalité et relationnelles.</span><span class="sxs-lookup"><span data-stu-id="42013-135">If one of the floating-point types is `double`, the expression evaluates to `double`, or to [bool](bool.md) in relational and equality comparisons.</span></span>
- <span data-ttu-id="42013-136">S’il n’existe aucun type de `double` dans l’expression, l’expression prend la valeur `float`, ou la valeur [bool](bool.md) dans les comparaisons d’égalité et relationnelles.</span><span class="sxs-lookup"><span data-stu-id="42013-136">If there is no `double` type in the expression, the expression evaluates to `float`, or to [bool](bool.md) in relational and equality comparisons.</span></span>

<span data-ttu-id="42013-137">Une expression à virgule flottante peut contenir les ensembles de valeurs suivants :</span><span class="sxs-lookup"><span data-stu-id="42013-137">A floating-point expression can contain the following sets of values:</span></span>

- <span data-ttu-id="42013-138">Zéro positif et négatif</span><span class="sxs-lookup"><span data-stu-id="42013-138">Positive and negative zero</span></span>
- <span data-ttu-id="42013-139">Infini positif et négatif</span><span class="sxs-lookup"><span data-stu-id="42013-139">Positive and negative infinity</span></span>
- <span data-ttu-id="42013-140">Valeur NaN (N’est pas un nombre)</span><span class="sxs-lookup"><span data-stu-id="42013-140">Not-a-Number value (NaN)</span></span>
- <span data-ttu-id="42013-141">L’ensemble fini de valeurs différentes de zéro</span><span class="sxs-lookup"><span data-stu-id="42013-141">The finite set of nonzero values</span></span>

<span data-ttu-id="42013-142">Pour plus d’informations sur ces valeurs, consultez IEEE Standard for Binary Floating-Point Arithmetic, disponible sur le site web de [l’IEEE](https://www.ieee.org).</span><span class="sxs-lookup"><span data-stu-id="42013-142">For more information about these values, see IEEE Standard for Binary Floating-Point Arithmetic, available on the [IEEE](https://www.ieee.org) website.</span></span>

<span data-ttu-id="42013-143">Vous pouvez utiliser des [chaînes au format numérique standard](../../../standard/base-types/standard-numeric-format-strings.md) ou des [chaînes au format numérique personnalisées](../../../standard/base-types/custom-numeric-format-strings.md) pour mettre en forme une valeur à virgule flottante.</span><span class="sxs-lookup"><span data-stu-id="42013-143">You can use either [standard numeric format strings](../../../standard/base-types/standard-numeric-format-strings.md) or [custom numeric format strings](../../../standard/base-types/custom-numeric-format-strings.md) to format a floating-point value.</span></span>

## <a name="real-literals"></a><span data-ttu-id="42013-144">Littéraux réels</span><span class="sxs-lookup"><span data-stu-id="42013-144">Real literals</span></span>

<span data-ttu-id="42013-145">Le type d’un littéral réel est déterminé par son suffixe comme suit :</span><span class="sxs-lookup"><span data-stu-id="42013-145">The type of a real literal is determined by its suffix as follows:</span></span>

- <span data-ttu-id="42013-146">Le littéral sans suffixe ou avec le suffixe `d` ou `D` est de type `double`</span><span class="sxs-lookup"><span data-stu-id="42013-146">The literal without suffix or with the `d` or `D` suffix is of type `double`</span></span>
- <span data-ttu-id="42013-147">Le littéral avec le suffixe `f` ou `F` est de type `float`</span><span class="sxs-lookup"><span data-stu-id="42013-147">The literal with the `f` or `F` suffix is of type `float`</span></span>
- <span data-ttu-id="42013-148">Le littéral avec le suffixe `m` ou `M` est de type `decimal`</span><span class="sxs-lookup"><span data-stu-id="42013-148">The literal with the `m` or `M` suffix is of type `decimal`</span></span>

<span data-ttu-id="42013-149">Le code suivant illustre un exemple de chaque :</span><span class="sxs-lookup"><span data-stu-id="42013-149">The following code demonstrates an example of each:</span></span>

```csharp
double d = 3D;
d = 4d;
d = 3.934_001;

float f = 3_000.5F;
f = 5.4f;

decimal myMoney = 3_000.5m;
myMoney = 400.75M;
```

<span data-ttu-id="42013-150">L’exemple précédent illustre également l’utilisation de `_` comme *séparateur de chiffres*, pris en charge à C# partir de 7,0.</span><span class="sxs-lookup"><span data-stu-id="42013-150">The preceding example also shows the use of `_` as a *digit separator*, which is supported starting with C# 7.0.</span></span> <span data-ttu-id="42013-151">Vous pouvez utiliser le séparateur de chiffres avec tous les types de littéraux numériques.</span><span class="sxs-lookup"><span data-stu-id="42013-151">You can use the digit separator with all kinds of numeric literals.</span></span>

<span data-ttu-id="42013-152">Vous pouvez également utiliser la notation scientifique, c’est-à-dire spécifier une partie exposant d’un littéral réel, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="42013-152">You also can use scientific notation, that is, specify an exponent part of a real literal, as the following example shows:</span></span>

```csharp-interactive
double d = 0.42e2;
Console.WriteLine(d);  // output 42;

float f = 134.45E-2f;
Console.WriteLine(f);  // output: 1.3445

decimal m = 1.5E6m;
Console.WriteLine(m);  // output: 1500000
```

## <a name="conversions"></a><span data-ttu-id="42013-153">Conversions</span><span class="sxs-lookup"><span data-stu-id="42013-153">Conversions</span></span>

<span data-ttu-id="42013-154">Il n’existe qu’une seule conversion implicite entre les types numériques à virgule flottante : de `float` à `double`.</span><span class="sxs-lookup"><span data-stu-id="42013-154">There is only one implicit conversion between floating-point numeric types: from `float` to `double`.</span></span> <span data-ttu-id="42013-155">Toutefois, vous pouvez convertir n’importe quel type à virgule flottante en tout autre type à virgule flottante avec le [cast explicite](../operators/type-testing-and-cast.md#cast-operator-).</span><span class="sxs-lookup"><span data-stu-id="42013-155">However, you can convert any floating-point type to any other floating-point type with the [explicit cast](../operators/type-testing-and-cast.md#cast-operator-).</span></span> <span data-ttu-id="42013-156">Pour plus d’informations, consultez [conversions numériques intégrées](numeric-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="42013-156">For more information, see [Built-in numeric conversions](numeric-conversions.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="42013-157">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="42013-157">C# language specification</span></span>

<span data-ttu-id="42013-158">Pour plus d’informations, consultez les sections suivantes de la [spécification du langage C#](~/_csharplang/spec/introduction.md) :</span><span class="sxs-lookup"><span data-stu-id="42013-158">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="42013-159">Types virgule flottante</span><span class="sxs-lookup"><span data-stu-id="42013-159">Floating-point types</span></span>](~/_csharplang/spec/types.md#floating-point-types)
- [<span data-ttu-id="42013-160">Type décimal</span><span class="sxs-lookup"><span data-stu-id="42013-160">The decimal type</span></span>](~/_csharplang/spec/types.md#the-decimal-type)
- [<span data-ttu-id="42013-161">Littéraux réels</span><span class="sxs-lookup"><span data-stu-id="42013-161">Real literals</span></span>](~/_csharplang/spec/lexical-structure.md#real-literals)

## <a name="see-also"></a><span data-ttu-id="42013-162">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="42013-162">See also</span></span>

- [<span data-ttu-id="42013-163">Informations de référence sur C#</span><span class="sxs-lookup"><span data-stu-id="42013-163">C# reference</span></span>](../index.md)
- [<span data-ttu-id="42013-164">Types de valeur</span><span class="sxs-lookup"><span data-stu-id="42013-164">Value types</span></span>](value-types.md)
- [<span data-ttu-id="42013-165">Types intégraux</span><span class="sxs-lookup"><span data-stu-id="42013-165">Integral types</span></span>](integral-numeric-types.md)
- [<span data-ttu-id="42013-166">Chaînes de format numériques standard</span><span class="sxs-lookup"><span data-stu-id="42013-166">Standard numeric format strings</span></span>](../../../standard/base-types/standard-numeric-format-strings.md)
- [<span data-ttu-id="42013-167">Valeurs numériques dans .NET</span><span class="sxs-lookup"><span data-stu-id="42013-167">Numerics in .NET</span></span>](../../../standard/numerics.md)
- <xref:System.Numerics.Complex?displayProperty=nameWithType>
