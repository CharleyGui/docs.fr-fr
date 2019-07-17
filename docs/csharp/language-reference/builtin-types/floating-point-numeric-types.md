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
ms.openlocfilehash: 738368abd9db75fbd97d1913324cab3b6e869c56
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67664189"
---
# <a name="floating-point-numeric-types-c-reference"></a><span data-ttu-id="f9bdc-103">Types numériques à virgule flottante (Référence C#)</span><span class="sxs-lookup"><span data-stu-id="f9bdc-103">Floating-point numeric types (C# reference)</span></span>

<span data-ttu-id="f9bdc-104">Les **types numériques à virgule flottante** sont un sous-ensemble des **types simples** et peuvent être initialisés avec des [*littéraux*](#floating-point-literals).</span><span class="sxs-lookup"><span data-stu-id="f9bdc-104">The **floating-point types** are a subset of the **simple types** and can be initialized with [*literals*](#floating-point-literals).</span></span> <span data-ttu-id="f9bdc-105">Tous les types virgule flottante sont également des types valeur.</span><span class="sxs-lookup"><span data-stu-id="f9bdc-105">All floating-point types are also value types.</span></span> <span data-ttu-id="f9bdc-106">Tous les types numériques à virgule flottante prennent en charge les opérateurs [arithmétiques](../operators/arithmetic-operators.md) et les opérateurs de [comparaison et d’égalité](../operators/equality-operators.md).</span><span class="sxs-lookup"><span data-stu-id="f9bdc-106">All floating-point numeric types support [arithmetic](../operators/arithmetic-operators.md) [comparison, and equality](../operators/equality-operators.md) operators.</span></span>

<span data-ttu-id="f9bdc-107">Le tableau suivant indique la plage de valeurs approximative et la précision pour les types virgule flottante :</span><span class="sxs-lookup"><span data-stu-id="f9bdc-107">The following table shows the precision and approximate ranges for the floating-point types:</span></span>
  
|<span data-ttu-id="f9bdc-108">Type</span><span class="sxs-lookup"><span data-stu-id="f9bdc-108">Type</span></span>|<span data-ttu-id="f9bdc-109">Plage approximative</span><span class="sxs-lookup"><span data-stu-id="f9bdc-109">Approximate range</span></span>|<span data-ttu-id="f9bdc-110">Précision</span><span class="sxs-lookup"><span data-stu-id="f9bdc-110">Precision</span></span>|  
|----------|-----------------------|---------------|  
|`float`|<span data-ttu-id="f9bdc-111">±1,5 x 10<sup>−45</sup> à ±3,4 x 10<sup>38</sup></span><span class="sxs-lookup"><span data-stu-id="f9bdc-111">±1.5 x 10<sup>−45</sup> to ±3.4 x 10<sup>38</sup></span></span>|<span data-ttu-id="f9bdc-112">~6-9 chiffres</span><span class="sxs-lookup"><span data-stu-id="f9bdc-112">~6-9 digits</span></span>|  
|`double`|<span data-ttu-id="f9bdc-113">De ±5,0 × 10<sup>−324</sup> à ±1,7 × 10<sup>308</sup></span><span class="sxs-lookup"><span data-stu-id="f9bdc-113">±5.0 × 10<sup>−324</sup> to ±1.7 × 10<sup>308</sup></span></span>|<span data-ttu-id="f9bdc-114">~15-17 chiffres</span><span class="sxs-lookup"><span data-stu-id="f9bdc-114">~15-17 digits</span></span>|  
|`decimal`|<span data-ttu-id="f9bdc-115">±1,0 x 10<sup>-28</sup> to ±7,9228 x 10<sup>28</sup></span><span class="sxs-lookup"><span data-stu-id="f9bdc-115">±1.0 x 10<sup>-28</sup> to ±7.9228 x 10<sup>28</sup></span></span>|<span data-ttu-id="f9bdc-116">28 à 29 chiffres</span><span class="sxs-lookup"><span data-stu-id="f9bdc-116">28-29 digits</span></span>|  

<span data-ttu-id="f9bdc-117">La valeur par défaut pour tous les types virgule flottante est `0`.</span><span class="sxs-lookup"><span data-stu-id="f9bdc-117">The default value for all floating-point types is `0`.</span></span> <span data-ttu-id="f9bdc-118">Chaque type virgule flottante a des constantes nommées `MinValue` et `MaxValue` correspondant à la valeur minimale et à la valeur maximale.</span><span class="sxs-lookup"><span data-stu-id="f9bdc-118">Each of the floating-point types has constants named `MinValue` and `MaxValue` for the minimum and maximum value for that type.</span></span> <span data-ttu-id="f9bdc-119">Les types `float` et `double` ont des constantes supplémentaires pour `PositiveInfinity`, `NegativeInfinity` et `NaN` (pour « Pas un nombre »).</span><span class="sxs-lookup"><span data-stu-id="f9bdc-119">The `float` and `double` types have additional constants for `PositiveInfinity`, `NegativeInfinity`, and `NaN` (for "Not a Number").</span></span> <span data-ttu-id="f9bdc-120">Le type `decimal` contient des constantes pour `Zero`, `One` et `MinusOne`.</span><span class="sxs-lookup"><span data-stu-id="f9bdc-120">The `decimal` type includes constants for `Zero`, `One`, and `MinusOne`.</span></span>

<span data-ttu-id="f9bdc-121">Le type `decimal` fournit une plus grande précision et une plage de valeurs plus petite que `float` et `double`, ce qui le rend particulièrement approprié aux calculs financiers et monétaires.</span><span class="sxs-lookup"><span data-stu-id="f9bdc-121">The `decimal` type has more precision and a smaller range than both `float` and `double`, which makes it appropriate for financial and monetary calculations.</span></span>

<span data-ttu-id="f9bdc-122">Vous pouvez combiner des types intégraux et des types virgule flottante dans une expression.</span><span class="sxs-lookup"><span data-stu-id="f9bdc-122">You can mix integral types and floating-point types in an expression.</span></span> <span data-ttu-id="f9bdc-123">Dans ce cas, les types intégraux sont convertis en types virgule flottante.</span><span class="sxs-lookup"><span data-stu-id="f9bdc-123">In this case, the integral types are converted to floating-point types.</span></span> <span data-ttu-id="f9bdc-124">L’évaluation de l’expression est exécutée d’après les règles suivantes :</span><span class="sxs-lookup"><span data-stu-id="f9bdc-124">The evaluation of the expression is performed according to the following rules:</span></span>

- <span data-ttu-id="f9bdc-125">Si l’un des types virgule flottante est `double`, l’expression prend la valeur `double` ou [bool](../keywords/bool.md) dans les comparaisons relationnelles ou les comparaisons d’égalité.</span><span class="sxs-lookup"><span data-stu-id="f9bdc-125">If one of the floating-point types is `double`, the expression evaluates to `double`, or to [bool](../keywords/bool.md) in relational comparisons or comparisons for equality.</span></span>
- <span data-ttu-id="f9bdc-126">S’il n’y a aucun type `double` dans l’expression, celle-ci prend la valeur `float` ou [bool](../keywords/bool.md) dans les comparaisons relationnelles ou les comparaisons d’égalité.</span><span class="sxs-lookup"><span data-stu-id="f9bdc-126">If there is no `double` type in the expression, the expression evaluates to `float`, or to [bool](../keywords/bool.md) in relational comparisons or comparisons for equality.</span></span>

<span data-ttu-id="f9bdc-127">Une expression à virgule flottante peut contenir les ensembles de valeurs suivants :</span><span class="sxs-lookup"><span data-stu-id="f9bdc-127">A floating-point expression can contain the following sets of values:</span></span>

- <span data-ttu-id="f9bdc-128">Zéro positif et négatif</span><span class="sxs-lookup"><span data-stu-id="f9bdc-128">Positive and negative zero</span></span>
- <span data-ttu-id="f9bdc-129">Infini positif et négatif</span><span class="sxs-lookup"><span data-stu-id="f9bdc-129">Positive and negative infinity</span></span>
- <span data-ttu-id="f9bdc-130">Valeur NaN (N’est pas un nombre)</span><span class="sxs-lookup"><span data-stu-id="f9bdc-130">Not-a-Number value (NaN)</span></span>
- <span data-ttu-id="f9bdc-131">L’ensemble fini de valeurs différentes de zéro</span><span class="sxs-lookup"><span data-stu-id="f9bdc-131">The finite set of nonzero values</span></span>

<span data-ttu-id="f9bdc-132">Pour plus d’informations sur ces valeurs, consultez IEEE Standard for Binary Floating-Point Arithmetic, disponible sur le site web de [l’IEEE](https://www.ieee.org).</span><span class="sxs-lookup"><span data-stu-id="f9bdc-132">For more information about these values, see IEEE Standard for Binary Floating-Point Arithmetic, available on the [IEEE](https://www.ieee.org) website.</span></span>

<span data-ttu-id="f9bdc-133">Vous pouvez utiliser des [chaînes au format numérique standard](../../../standard/base-types/standard-numeric-format-strings.md) ou des [chaînes au format numérique personnalisées](../../../standard/base-types/custom-numeric-format-strings.md) pour mettre en forme une valeur à virgule flottante.</span><span class="sxs-lookup"><span data-stu-id="f9bdc-133">You can use either [standard numeric format strings](../../../standard/base-types/standard-numeric-format-strings.md) or [custom numeric format strings](../../../standard/base-types/custom-numeric-format-strings.md) to format a floating-point value.</span></span>

## <a name="floating-point-literals"></a><span data-ttu-id="f9bdc-134">Littéraux à virgule flottante</span><span class="sxs-lookup"><span data-stu-id="f9bdc-134">Floating-point literals</span></span>

<span data-ttu-id="f9bdc-135">Par défaut, un littéral numérique à virgule flottante sur le côté droit de l’opérateur d’assignation est traité comme `double`.</span><span class="sxs-lookup"><span data-stu-id="f9bdc-135">By default, a floating-point numeric literal on the right side of the assignment operator is treated as `double`.</span></span> <span data-ttu-id="f9bdc-136">Vous pouvez utiliser des suffixes pour convertir un littéral à virgule flottante ou intégral en un type spécifique :</span><span class="sxs-lookup"><span data-stu-id="f9bdc-136">You can use suffixes to convert a floating-point or integral literal to a specific type:</span></span>

- <span data-ttu-id="f9bdc-137">Le suffixe `d` ou `D` convertit un littéral en `double`.</span><span class="sxs-lookup"><span data-stu-id="f9bdc-137">The `d` or `D` suffix converts a literal to a `double`.</span></span>
- <span data-ttu-id="f9bdc-138">Le suffixe `f` ou `F` convertit un littéral en `float`.</span><span class="sxs-lookup"><span data-stu-id="f9bdc-138">The `f` or `F` suffix converts a literal to a `float`.</span></span>
- <span data-ttu-id="f9bdc-139">Le suffixe `m` ou `M` convertit un littéral en `decimal`.</span><span class="sxs-lookup"><span data-stu-id="f9bdc-139">The `m` or `M` suffix converts a literal to a `decimal`.</span></span>

<span data-ttu-id="f9bdc-140">Les exemples suivants montrent chaque suffixe :</span><span class="sxs-lookup"><span data-stu-id="f9bdc-140">The following examples show each suffix:</span></span>

```csharp
double d = 3D;
d = 4d;
float f = 3.5F;
f = 5.4f;
decimal myMoney = 300.5m;
myMoney = 400.75M;
```

## <a name="conversions"></a><span data-ttu-id="f9bdc-141">Conversions</span><span class="sxs-lookup"><span data-stu-id="f9bdc-141">Conversions</span></span>

<span data-ttu-id="f9bdc-142">Il existe une conversion implicite (appelée *conversion étendue*) de `float` en `double` parce que la plage de valeurs `float` est un sous-ensemble de `double` et qu’aucune perte de précision ne se produit de `float` en `double`.</span><span class="sxs-lookup"><span data-stu-id="f9bdc-142">There's an implicit conversion (called a *widening conversion*) from `float` to `double` because the range of `float` values is a proper subset of `double` and there is no loss of precision from `float` to `double`.</span></span> 

<span data-ttu-id="f9bdc-143">Vous devez utiliser un cast explicite pour convertir un type virgule flottante en un autre type virgule flottante, lorsqu’une conversion implicite n’est pas définie entre le type source et le type de destination.</span><span class="sxs-lookup"><span data-stu-id="f9bdc-143">You must use an explicit cast to convert one floating-point type to another floating-point type when an implicit conversion isn't defined from the source type to the destination type.</span></span> <span data-ttu-id="f9bdc-144">C’est ce qu’on appelle une *conversion restrictive*.</span><span class="sxs-lookup"><span data-stu-id="f9bdc-144">This is called a *narrowing conversion*.</span></span> <span data-ttu-id="f9bdc-145">Un scénario explicite est nécessaire, car la conversion peut entraîner une perte de données.</span><span class="sxs-lookup"><span data-stu-id="f9bdc-145">The explicit case is required because the conversion can result in data loss.</span></span> <span data-ttu-id="f9bdc-146">Il n’existe aucune conversion implicite entre les autres types virgule flottante et le type `decimal` parce que le type `decimal` a une plus grande précision que celle de `float` ou `double`.</span><span class="sxs-lookup"><span data-stu-id="f9bdc-146">There's no implicit conversion between other floating-point types and the `decimal` type because the `decimal` type has greater precision than either `float` or `double`.</span></span>

<span data-ttu-id="f9bdc-147">Pour plus d’informations sur les conversions numériques implicites, consultez [Tableau des conversions numériques implicites](../keywords/implicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="f9bdc-147">For more information about implicit numeric conversions, see [Implicit Numeric Conversions Table](../keywords/implicit-numeric-conversions-table.md).</span></span>

<span data-ttu-id="f9bdc-148">Pour plus d’informations sur les conversions numériques explicites, consultez [Tableau des conversions numériques explicites](../keywords/explicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="f9bdc-148">For more information about explicit numeric conversions, see [Explicit Numeric Conversions Table](../keywords/explicit-numeric-conversions-table.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f9bdc-149">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f9bdc-149">See also</span></span>

- [<span data-ttu-id="f9bdc-150">Référence C#</span><span class="sxs-lookup"><span data-stu-id="f9bdc-150">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="f9bdc-151">Types intégraux</span><span class="sxs-lookup"><span data-stu-id="f9bdc-151">Integral types</span></span>](integral-numeric-types.md)
- [<span data-ttu-id="f9bdc-152">Tableau des valeurs par défaut</span><span class="sxs-lookup"><span data-stu-id="f9bdc-152">Default values table</span></span>](../keywords/default-values-table.md)
- [<span data-ttu-id="f9bdc-153">Tableau des formats des résultats numériques</span><span class="sxs-lookup"><span data-stu-id="f9bdc-153">Formatting numeric results table</span></span>](../keywords/formatting-numeric-results-table.md)
- [<span data-ttu-id="f9bdc-154">Tableaux des types intégrés</span><span class="sxs-lookup"><span data-stu-id="f9bdc-154">Built-in types table</span></span>](../keywords/built-in-types-table.md)
- [<span data-ttu-id="f9bdc-155">Valeurs numériques dans .NET</span><span class="sxs-lookup"><span data-stu-id="f9bdc-155">Numerics in .NET</span></span>](../../../standard/numerics.md)
- [<span data-ttu-id="f9bdc-156">Cast et conversions de types</span><span class="sxs-lookup"><span data-stu-id="f9bdc-156">Casting and Type Conversions</span></span>](../../programming-guide/types/casting-and-type-conversions.md)
- [<span data-ttu-id="f9bdc-157">Tableau des conversions numériques implicites</span><span class="sxs-lookup"><span data-stu-id="f9bdc-157">Implicit Numeric Conversions Table</span></span>](../keywords/implicit-numeric-conversions-table.md)
- [<span data-ttu-id="f9bdc-158">Tableau des conversions numériques explicites</span><span class="sxs-lookup"><span data-stu-id="f9bdc-158">Explicit Numeric Conversions Table</span></span>](../keywords/explicit-numeric-conversions-table.md)
- <xref:System.Single?displayProperty=nameWithType>
- <xref:System.Double?displayProperty=nameWithType>
- <xref:System.Decimal?displayProperty=nameWithType>
- <xref:System.Numerics.Complex?displayProperty=nameWithType>
- [<span data-ttu-id="f9bdc-159">Standard Numeric Format Strings</span><span class="sxs-lookup"><span data-stu-id="f9bdc-159">Standard Numeric Format Strings</span></span>](../../../standard/base-types/standard-numeric-format-strings.md)
