---
title: Types numériques à virgule flottante - Référence C#
description: Vue d’ensemble des types virgule flottante C# intégrés
ms.date: 06/30/2019
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
- types [C#], floating-point types
- float keyword [C#]
- floating-point numbers [C#], float keyword
- double data type [C#]
- decimal keyword [C#]
ms.openlocfilehash: 0d97b3ffd587e8398e5572706a47937716a6e709
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68236058"
---
# <a name="floating-point-numeric-types-c-reference"></a><span data-ttu-id="6d7a1-103">Types numériques à virgule flottante (Référence C#)</span><span class="sxs-lookup"><span data-stu-id="6d7a1-103">Floating-point numeric types (C# reference)</span></span>

<span data-ttu-id="6d7a1-104">Les **types numériques à virgule flottante** sont un sous-ensemble des **types simples** et peuvent être initialisés avec des [*littéraux*](#floating-point-literals).</span><span class="sxs-lookup"><span data-stu-id="6d7a1-104">The **floating-point types** are a subset of the **simple types** and can be initialized with [*literals*](#floating-point-literals).</span></span> <span data-ttu-id="6d7a1-105">Tous les types virgule flottante sont également des types valeur.</span><span class="sxs-lookup"><span data-stu-id="6d7a1-105">All floating-point types are also value types.</span></span> <span data-ttu-id="6d7a1-106">Tous les types numériques à virgule flottante prennent en charge les opérateurs [arithmétiques](../operators/arithmetic-operators.md) et les opérateurs de [comparaison et d’égalité](../operators/equality-operators.md).</span><span class="sxs-lookup"><span data-stu-id="6d7a1-106">All floating-point numeric types support [arithmetic](../operators/arithmetic-operators.md), [comparison, and equality](../operators/equality-operators.md) operators.</span></span>

## <a name="characteristics-of-the-floating-point-types"></a><span data-ttu-id="6d7a1-107">Caractéristiques des types à virgule flottante</span><span class="sxs-lookup"><span data-stu-id="6d7a1-107">Characteristics of the floating-point types</span></span>

<span data-ttu-id="6d7a1-108">C# prend en charge les types à virgule flottante prédéfinis suivants :</span><span class="sxs-lookup"><span data-stu-id="6d7a1-108">C# supports the following predefined floating-point types:</span></span>
  
|<span data-ttu-id="6d7a1-109">C# type/mot clé</span><span class="sxs-lookup"><span data-stu-id="6d7a1-109">C# type/keyword</span></span>|<span data-ttu-id="6d7a1-110">Plage approximative</span><span class="sxs-lookup"><span data-stu-id="6d7a1-110">Approximate range</span></span>|<span data-ttu-id="6d7a1-111">Precision</span><span class="sxs-lookup"><span data-stu-id="6d7a1-111">Precision</span></span>|<span data-ttu-id="6d7a1-112">Type .NET</span><span class="sxs-lookup"><span data-stu-id="6d7a1-112">.NET type</span></span>|
|----------|-----------------------|---------------|--------------|
|`float`|<span data-ttu-id="6d7a1-113">±1,5 x 10<sup>−45</sup> à ±3,4 x 10<sup>38</sup></span><span class="sxs-lookup"><span data-stu-id="6d7a1-113">±1.5 x 10<sup>−45</sup> to ±3.4 x 10<sup>38</sup></span></span>|<span data-ttu-id="6d7a1-114">~6-9 chiffres</span><span class="sxs-lookup"><span data-stu-id="6d7a1-114">~6-9 digits</span></span>|<xref:System.Single?displayProperty=nameWithType>|
|`double`|<span data-ttu-id="6d7a1-115">De ±5,0 × 10<sup>−324</sup> à ±1,7 × 10<sup>308</sup></span><span class="sxs-lookup"><span data-stu-id="6d7a1-115">±5.0 × 10<sup>−324</sup> to ±1.7 × 10<sup>308</sup></span></span>|<span data-ttu-id="6d7a1-116">~15-17 chiffres</span><span class="sxs-lookup"><span data-stu-id="6d7a1-116">~15-17 digits</span></span>|<xref:System.Double?displayProperty=nameWithType>|
|`decimal`|<span data-ttu-id="6d7a1-117">±1,0 x 10<sup>-28</sup> to ±7,9228 x 10<sup>28</sup></span><span class="sxs-lookup"><span data-stu-id="6d7a1-117">±1.0 x 10<sup>-28</sup> to ±7.9228 x 10<sup>28</sup></span></span>|<span data-ttu-id="6d7a1-118">28 à 29 chiffres</span><span class="sxs-lookup"><span data-stu-id="6d7a1-118">28-29 digits</span></span>|<xref:System.Decimal?displayProperty=nameWithType>|

<span data-ttu-id="6d7a1-119">Dans le tableau précédent, chaque mot clé de type C# de la colonne la plus à gauche est un alias pour le type .NET correspondant.</span><span class="sxs-lookup"><span data-stu-id="6d7a1-119">In the preceding table, each C# type keyword from the leftmost column is an alias for the corresponding .NET type.</span></span> <span data-ttu-id="6d7a1-120">Ils sont interchangeables.</span><span class="sxs-lookup"><span data-stu-id="6d7a1-120">They are interchangeable.</span></span> <span data-ttu-id="6d7a1-121">Par exemple, les déclarations suivantes déclarent des variables du même type :</span><span class="sxs-lookup"><span data-stu-id="6d7a1-121">For example, the following declarations declare variables of the same type:</span></span>

```csharp
double a = 12.3;
System.Double b = 12.3;
```

<span data-ttu-id="6d7a1-122">La valeur par défaut pour tous les types virgule flottante est zéro, `0`.</span><span class="sxs-lookup"><span data-stu-id="6d7a1-122">The default value of each floating-point type is zero, `0`.</span></span> <span data-ttu-id="6d7a1-123">Chacun des types à virgule flottante a les constantes `MinValue` et `MaxValue` qui fournissent la valeur finie minimale et maximale de ce type.</span><span class="sxs-lookup"><span data-stu-id="6d7a1-123">Each of the floating-point types has the `MinValue` and `MaxValue` constants that provide the minimum and maximum finite value of that type.</span></span> <span data-ttu-id="6d7a1-124">Les types `float` et `double` fournissent également des constantes qui représentent des valeurs NaN (Not-a-Number) et d’infini.</span><span class="sxs-lookup"><span data-stu-id="6d7a1-124">The `float` and `double` types also provide constants that represent not-a-number and infinity values.</span></span> <span data-ttu-id="6d7a1-125">Par exemple, le type `double` fournit les constantes suivantes : <xref:System.Double.NaN?displayProperty=nameWithType>, <xref:System.Double.NegativeInfinity?displayProperty=nameWithType> et <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6d7a1-125">For example, the `double` type provides the following constants: <xref:System.Double.NaN?displayProperty=nameWithType>, <xref:System.Double.NegativeInfinity?displayProperty=nameWithType>, and <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="6d7a1-126">Le type `decimal` fournit une plus grande précision et une plage de valeurs plus petite que `float` et `double`, ce qui le rend particulièrement approprié aux calculs financiers et monétaires.</span><span class="sxs-lookup"><span data-stu-id="6d7a1-126">Because the `decimal` type has more precision and a smaller range than both `float` and `double`, it's appropriate for financial and monetary calculations.</span></span>

<span data-ttu-id="6d7a1-127">Vous pouvez combiner des types [intégraux](integral-numeric-types.md) et des types virgule flottante dans une expression.</span><span class="sxs-lookup"><span data-stu-id="6d7a1-127">You can mix [integral](integral-numeric-types.md) types and floating-point types in an expression.</span></span> <span data-ttu-id="6d7a1-128">Dans ce cas, les types intégraux sont convertis en types virgule flottante.</span><span class="sxs-lookup"><span data-stu-id="6d7a1-128">In this case, the integral types are converted to floating-point types.</span></span> <span data-ttu-id="6d7a1-129">L’évaluation de l’expression est exécutée d’après les règles suivantes :</span><span class="sxs-lookup"><span data-stu-id="6d7a1-129">The evaluation of the expression is performed according to the following rules:</span></span>

- <span data-ttu-id="6d7a1-130">Si l’un des types virgule flottante est `double`, l’expression prend la valeur `double` ou [bool](../keywords/bool.md) dans les comparaisons relationnelles ou les comparaisons d’égalité.</span><span class="sxs-lookup"><span data-stu-id="6d7a1-130">If one of the floating-point types is `double`, the expression evaluates to `double`, or to [bool](../keywords/bool.md) in relational comparisons or comparisons for equality.</span></span>
- <span data-ttu-id="6d7a1-131">S’il n’y a aucun type `double` dans l’expression, celle-ci prend la valeur `float` ou [bool](../keywords/bool.md) dans les comparaisons relationnelles ou les comparaisons d’égalité.</span><span class="sxs-lookup"><span data-stu-id="6d7a1-131">If there is no `double` type in the expression, the expression evaluates to `float`, or to [bool](../keywords/bool.md) in relational comparisons or comparisons for equality.</span></span>

<span data-ttu-id="6d7a1-132">Une expression à virgule flottante peut contenir les ensembles de valeurs suivants :</span><span class="sxs-lookup"><span data-stu-id="6d7a1-132">A floating-point expression can contain the following sets of values:</span></span>

- <span data-ttu-id="6d7a1-133">Zéro positif et négatif</span><span class="sxs-lookup"><span data-stu-id="6d7a1-133">Positive and negative zero</span></span>
- <span data-ttu-id="6d7a1-134">Infini positif et négatif</span><span class="sxs-lookup"><span data-stu-id="6d7a1-134">Positive and negative infinity</span></span>
- <span data-ttu-id="6d7a1-135">Valeur NaN (N’est pas un nombre)</span><span class="sxs-lookup"><span data-stu-id="6d7a1-135">Not-a-Number value (NaN)</span></span>
- <span data-ttu-id="6d7a1-136">L’ensemble fini de valeurs différentes de zéro</span><span class="sxs-lookup"><span data-stu-id="6d7a1-136">The finite set of nonzero values</span></span>

<span data-ttu-id="6d7a1-137">Pour plus d’informations sur ces valeurs, consultez IEEE Standard for Binary Floating-Point Arithmetic, disponible sur le site web de [l’IEEE](https://www.ieee.org).</span><span class="sxs-lookup"><span data-stu-id="6d7a1-137">For more information about these values, see IEEE Standard for Binary Floating-Point Arithmetic, available on the [IEEE](https://www.ieee.org) website.</span></span>

<span data-ttu-id="6d7a1-138">Vous pouvez utiliser des [chaînes au format numérique standard](../../../standard/base-types/standard-numeric-format-strings.md) ou des [chaînes au format numérique personnalisées](../../../standard/base-types/custom-numeric-format-strings.md) pour mettre en forme une valeur à virgule flottante.</span><span class="sxs-lookup"><span data-stu-id="6d7a1-138">You can use either [standard numeric format strings](../../../standard/base-types/standard-numeric-format-strings.md) or [custom numeric format strings](../../../standard/base-types/custom-numeric-format-strings.md) to format a floating-point value.</span></span>

## <a name="floating-point-literals"></a><span data-ttu-id="6d7a1-139">Littéraux à virgule flottante</span><span class="sxs-lookup"><span data-stu-id="6d7a1-139">Floating-point literals</span></span>

<span data-ttu-id="6d7a1-140">Par défaut, un littéral numérique à virgule flottante sur le côté droit de l’opérateur d’assignation est traité comme `double`.</span><span class="sxs-lookup"><span data-stu-id="6d7a1-140">By default, a floating-point numeric literal on the right side of the assignment operator is treated as `double`.</span></span> <span data-ttu-id="6d7a1-141">Vous pouvez utiliser des suffixes pour convertir un littéral à virgule flottante ou intégral en un type spécifique :</span><span class="sxs-lookup"><span data-stu-id="6d7a1-141">You can use suffixes to convert a floating-point or integral literal to a specific type:</span></span>

- <span data-ttu-id="6d7a1-142">Le suffixe `d` ou `D` convertit un littéral en `double`.</span><span class="sxs-lookup"><span data-stu-id="6d7a1-142">The `d` or `D` suffix converts a literal to a `double`.</span></span>
- <span data-ttu-id="6d7a1-143">Le suffixe `f` ou `F` convertit un littéral en `float`.</span><span class="sxs-lookup"><span data-stu-id="6d7a1-143">The `f` or `F` suffix converts a literal to a `float`.</span></span>
- <span data-ttu-id="6d7a1-144">Le suffixe `m` ou `M` convertit un littéral en `decimal`.</span><span class="sxs-lookup"><span data-stu-id="6d7a1-144">The `m` or `M` suffix converts a literal to a `decimal`.</span></span>

<span data-ttu-id="6d7a1-145">Les exemples suivants montrent chaque suffixe :</span><span class="sxs-lookup"><span data-stu-id="6d7a1-145">The following examples show each suffix:</span></span>

```csharp
double d = 3D;
d = 4d;
float f = 3.5F;
f = 5.4f;
decimal myMoney = 300.5m;
myMoney = 400.75M;
```

## <a name="conversions"></a><span data-ttu-id="6d7a1-146">Conversions</span><span class="sxs-lookup"><span data-stu-id="6d7a1-146">Conversions</span></span>

<span data-ttu-id="6d7a1-147">Il existe une conversion implicite (appelée *conversion étendue*) de `float` en `double` parce que la plage de valeurs `float` est un sous-ensemble de `double` et qu’aucune perte de précision ne se produit de `float` en `double`.</span><span class="sxs-lookup"><span data-stu-id="6d7a1-147">There's an implicit conversion (called a *widening conversion*) from `float` to `double` because the range of `float` values is a proper subset of `double` and there is no loss of precision from `float` to `double`.</span></span>

<span data-ttu-id="6d7a1-148">Vous devez utiliser un cast explicite pour convertir un type virgule flottante en un autre type virgule flottante, lorsqu’une conversion implicite n’est pas définie entre le type source et le type de destination.</span><span class="sxs-lookup"><span data-stu-id="6d7a1-148">You must use an explicit cast to convert one floating-point type to another floating-point type when an implicit conversion isn't defined from the source type to the destination type.</span></span> <span data-ttu-id="6d7a1-149">C’est ce qu’on appelle une *conversion restrictive*.</span><span class="sxs-lookup"><span data-stu-id="6d7a1-149">This is called a *narrowing conversion*.</span></span> <span data-ttu-id="6d7a1-150">Un scénario explicite est nécessaire, car la conversion peut entraîner une perte de données.</span><span class="sxs-lookup"><span data-stu-id="6d7a1-150">The explicit case is required because the conversion can result in data loss.</span></span> <span data-ttu-id="6d7a1-151">Il n’existe aucune conversion implicite entre les autres types virgule flottante et le type `decimal` parce que le type `decimal` a une plus grande précision que celle de `float` ou `double`.</span><span class="sxs-lookup"><span data-stu-id="6d7a1-151">There's no implicit conversion between other floating-point types and the `decimal` type because the `decimal` type has greater precision than either `float` or `double`.</span></span>

<span data-ttu-id="6d7a1-152">Pour plus d’informations sur les conversions numériques implicites, consultez [Tableau des conversions numériques implicites](../keywords/implicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="6d7a1-152">For more information about implicit numeric conversions, see [Implicit Numeric Conversions Table](../keywords/implicit-numeric-conversions-table.md).</span></span>

<span data-ttu-id="6d7a1-153">Pour plus d’informations sur les conversions numériques explicites, consultez [Tableau des conversions numériques explicites](../keywords/explicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="6d7a1-153">For more information about explicit numeric conversions, see [Explicit Numeric Conversions Table](../keywords/explicit-numeric-conversions-table.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6d7a1-154">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6d7a1-154">See also</span></span>

- [<span data-ttu-id="6d7a1-155">Référence C#</span><span class="sxs-lookup"><span data-stu-id="6d7a1-155">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="6d7a1-156">Types intégraux</span><span class="sxs-lookup"><span data-stu-id="6d7a1-156">Integral types</span></span>](integral-numeric-types.md)
- [<span data-ttu-id="6d7a1-157">Tableaux des types intégrés</span><span class="sxs-lookup"><span data-stu-id="6d7a1-157">Built-in types table</span></span>](../keywords/built-in-types-table.md)
- [<span data-ttu-id="6d7a1-158">Valeurs numériques dans .NET</span><span class="sxs-lookup"><span data-stu-id="6d7a1-158">Numerics in .NET</span></span>](../../../standard/numerics.md)
- [<span data-ttu-id="6d7a1-159">Cast et conversions de types</span><span class="sxs-lookup"><span data-stu-id="6d7a1-159">Casting and Type Conversions</span></span>](../../programming-guide/types/casting-and-type-conversions.md)
- [<span data-ttu-id="6d7a1-160">Tableau des conversions numériques implicites</span><span class="sxs-lookup"><span data-stu-id="6d7a1-160">Implicit Numeric Conversions Table</span></span>](../keywords/implicit-numeric-conversions-table.md)
- [<span data-ttu-id="6d7a1-161">Tableau des conversions numériques explicites</span><span class="sxs-lookup"><span data-stu-id="6d7a1-161">Explicit Numeric Conversions Table</span></span>](../keywords/explicit-numeric-conversions-table.md)
- <xref:System.Numerics.Complex?displayProperty=nameWithType>
- [<span data-ttu-id="6d7a1-162">Tableau des formats des résultats numériques</span><span class="sxs-lookup"><span data-stu-id="6d7a1-162">Formatting numeric results table</span></span>](../keywords/formatting-numeric-results-table.md)
- [<span data-ttu-id="6d7a1-163">Standard Numeric Format Strings</span><span class="sxs-lookup"><span data-stu-id="6d7a1-163">Standard Numeric Format Strings</span></span>](../../../standard/base-types/standard-numeric-format-strings.md)
