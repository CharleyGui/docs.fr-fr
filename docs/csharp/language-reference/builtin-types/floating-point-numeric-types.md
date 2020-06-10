---
title: Types numériques à virgule flottante - Référence C#
description: 'En savoir plus sur les types à virgule flottante C# intégrés : float, double et Decimal'
ms.date: 02/10/2020
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
ms.openlocfilehash: a1142d1aa04003ae1942902672cfc7a05edc99c0
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/10/2020
ms.locfileid: "84662665"
---
# <a name="floating-point-numeric-types-c-reference"></a><span data-ttu-id="87693-103">Types numériques à virgule flottante (Référence C#)</span><span class="sxs-lookup"><span data-stu-id="87693-103">Floating-point numeric types (C# reference)</span></span>

<span data-ttu-id="87693-104">Les *types numériques à virgule flottante* représentent des nombres réels.</span><span class="sxs-lookup"><span data-stu-id="87693-104">The *floating-point numeric types* represent real numbers.</span></span> <span data-ttu-id="87693-105">Tous les types numériques à virgule flottante sont des [types valeur](value-types.md).</span><span class="sxs-lookup"><span data-stu-id="87693-105">All floating-point numeric types are [value types](value-types.md).</span></span> <span data-ttu-id="87693-106">Il s’agit également de [types simples](value-types.md#built-in-value-types) qui peuvent être initialisés avec des [littéraux](#real-literals).</span><span class="sxs-lookup"><span data-stu-id="87693-106">They are also [simple types](value-types.md#built-in-value-types) and can be initialized with [literals](#real-literals).</span></span> <span data-ttu-id="87693-107">Tous les types numériques à virgule flottante prennent en charge les opérateurs [arithmétiques](../operators/arithmetic-operators.md), de [comparaison](../operators/comparison-operators.md)et d' [égalité](../operators/equality-operators.md) .</span><span class="sxs-lookup"><span data-stu-id="87693-107">All floating-point numeric types support [arithmetic](../operators/arithmetic-operators.md), [comparison](../operators/comparison-operators.md), and [equality](../operators/equality-operators.md) operators.</span></span>

## <a name="characteristics-of-the-floating-point-types"></a><span data-ttu-id="87693-108">Caractéristiques des types à virgule flottante</span><span class="sxs-lookup"><span data-stu-id="87693-108">Characteristics of the floating-point types</span></span>

<span data-ttu-id="87693-109">C# prend en charge les types à virgule flottante prédéfinis suivants :</span><span class="sxs-lookup"><span data-stu-id="87693-109">C# supports the following predefined floating-point types:</span></span>
  
|<span data-ttu-id="87693-110">C# type/mot clé</span><span class="sxs-lookup"><span data-stu-id="87693-110">C# type/keyword</span></span>|<span data-ttu-id="87693-111">Plage approximative</span><span class="sxs-lookup"><span data-stu-id="87693-111">Approximate range</span></span>|<span data-ttu-id="87693-112">Precision</span><span class="sxs-lookup"><span data-stu-id="87693-112">Precision</span></span>|<span data-ttu-id="87693-113">Taille</span><span class="sxs-lookup"><span data-stu-id="87693-113">Size</span></span>|<span data-ttu-id="87693-114">Type .NET</span><span class="sxs-lookup"><span data-stu-id="87693-114">.NET type</span></span>|
|----------|-----------------------|---------------|--------------|--------------|
|`float`|<span data-ttu-id="87693-115">±1,5 x 10<sup>−45</sup> à ±3,4 x 10<sup>38</sup></span><span class="sxs-lookup"><span data-stu-id="87693-115">±1.5 x 10<sup>−45</sup> to ±3.4 x 10<sup>38</sup></span></span>|<span data-ttu-id="87693-116">~6-9 chiffres</span><span class="sxs-lookup"><span data-stu-id="87693-116">~6-9 digits</span></span>|<span data-ttu-id="87693-117">4 octets</span><span class="sxs-lookup"><span data-stu-id="87693-117">4 bytes</span></span>|<xref:System.Single?displayProperty=nameWithType>|
|`double`|<span data-ttu-id="87693-118">De ±5,0 × 10<sup>−324</sup> à ±1,7 × 10<sup>308</sup></span><span class="sxs-lookup"><span data-stu-id="87693-118">±5.0 × 10<sup>−324</sup> to ±1.7 × 10<sup>308</sup></span></span>|<span data-ttu-id="87693-119">~15-17 chiffres</span><span class="sxs-lookup"><span data-stu-id="87693-119">~15-17 digits</span></span>|<span data-ttu-id="87693-120">8 octets</span><span class="sxs-lookup"><span data-stu-id="87693-120">8 bytes</span></span>|<xref:System.Double?displayProperty=nameWithType>|
|`decimal`|<span data-ttu-id="87693-121">±1,0 x 10<sup>-28</sup> to ±7,9228 x 10<sup>28</sup></span><span class="sxs-lookup"><span data-stu-id="87693-121">±1.0 x 10<sup>-28</sup> to ±7.9228 x 10<sup>28</sup></span></span>|<span data-ttu-id="87693-122">28 à 29 chiffres</span><span class="sxs-lookup"><span data-stu-id="87693-122">28-29 digits</span></span>|<span data-ttu-id="87693-123">16 octets</span><span class="sxs-lookup"><span data-stu-id="87693-123">16 bytes</span></span>|<xref:System.Decimal?displayProperty=nameWithType>|

<span data-ttu-id="87693-124">Dans le tableau précédent, chaque mot clé de type C# de la colonne la plus à gauche est un alias pour le type .NET correspondant.</span><span class="sxs-lookup"><span data-stu-id="87693-124">In the preceding table, each C# type keyword from the leftmost column is an alias for the corresponding .NET type.</span></span> <span data-ttu-id="87693-125">Ils sont interchangeables.</span><span class="sxs-lookup"><span data-stu-id="87693-125">They are interchangeable.</span></span> <span data-ttu-id="87693-126">Par exemple, les déclarations suivantes déclarent des variables du même type :</span><span class="sxs-lookup"><span data-stu-id="87693-126">For example, the following declarations declare variables of the same type:</span></span>

```csharp
double a = 12.3;
System.Double b = 12.3;
```

<span data-ttu-id="87693-127">La valeur par défaut pour tous les types virgule flottante est zéro, `0`.</span><span class="sxs-lookup"><span data-stu-id="87693-127">The default value of each floating-point type is zero, `0`.</span></span> <span data-ttu-id="87693-128">Chacun des types à virgule flottante a les constantes `MinValue` et `MaxValue` qui fournissent la valeur finie minimale et maximale de ce type.</span><span class="sxs-lookup"><span data-stu-id="87693-128">Each of the floating-point types has the `MinValue` and `MaxValue` constants that provide the minimum and maximum finite value of that type.</span></span> <span data-ttu-id="87693-129">Les types `float` et `double` fournissent également des constantes qui représentent des valeurs NaN (Not-a-Number) et d’infini.</span><span class="sxs-lookup"><span data-stu-id="87693-129">The `float` and `double` types also provide constants that represent not-a-number and infinity values.</span></span> <span data-ttu-id="87693-130">Par exemple, le type `double` fournit les constantes suivantes : <xref:System.Double.NaN?displayProperty=nameWithType>, <xref:System.Double.NegativeInfinity?displayProperty=nameWithType> et <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="87693-130">For example, the `double` type provides the following constants: <xref:System.Double.NaN?displayProperty=nameWithType>, <xref:System.Double.NegativeInfinity?displayProperty=nameWithType>, and <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="87693-131">Le type `decimal` fournit une plus grande précision et une plage de valeurs plus petite que `float` et `double`, ce qui le rend particulièrement approprié aux calculs financiers et monétaires.</span><span class="sxs-lookup"><span data-stu-id="87693-131">Because the `decimal` type has more precision and a smaller range than both `float` and `double`, it's appropriate for financial and monetary calculations.</span></span>

<span data-ttu-id="87693-132">Vous pouvez mélanger les types [intégraux](integral-numeric-types.md) et les `float` `double` types et dans une expression.</span><span class="sxs-lookup"><span data-stu-id="87693-132">You can mix [integral](integral-numeric-types.md) types and the `float` and `double` types in an expression.</span></span> <span data-ttu-id="87693-133">Dans ce cas, les types intégraux sont convertis implicitement en un des types à virgule flottante et, si nécessaire, le `float` type est implicitement converti en `double` .</span><span class="sxs-lookup"><span data-stu-id="87693-133">In this case, integral types are implicitly converted to one of the floating-point types and, if necessary, the `float` type is implicitly converted to `double`.</span></span> <span data-ttu-id="87693-134">L'expression est évaluée de la manière suivante :</span><span class="sxs-lookup"><span data-stu-id="87693-134">The expression is evaluated as follows:</span></span>

- <span data-ttu-id="87693-135">S’il existe `double` un type dans l’expression, l’expression prend la valeur `double` , ou [`bool`](bool.md) dans les comparaisons relationnelles et d’égalité.</span><span class="sxs-lookup"><span data-stu-id="87693-135">If there is `double` type in the expression, the expression evaluates to `double`, or to [`bool`](bool.md) in relational and equality comparisons.</span></span>
- <span data-ttu-id="87693-136">S’il n’y a aucun `double` type dans l’expression, l’expression prend la valeur `float` , ou `bool` dans les comparaisons relationnelles et d’égalité.</span><span class="sxs-lookup"><span data-stu-id="87693-136">If there is no `double` type in the expression, the expression evaluates to `float`, or to `bool` in relational and equality comparisons.</span></span>

<span data-ttu-id="87693-137">Vous pouvez également mélanger des types intégraux et le `decimal` type dans une expression.</span><span class="sxs-lookup"><span data-stu-id="87693-137">You can also mix integral types and the `decimal` type in an expression.</span></span> <span data-ttu-id="87693-138">Dans ce cas, les types intégraux sont convertis implicitement vers le `decimal` type et l’expression prend la valeur `decimal` , ou `bool` dans les comparaisons relationnelles et d’égalité.</span><span class="sxs-lookup"><span data-stu-id="87693-138">In this case, integral types are implicitly converted to the `decimal` type and the expression evaluates to `decimal`, or to `bool` in relational and equality comparisons.</span></span>

<span data-ttu-id="87693-139">Vous ne pouvez pas mélanger le `decimal` type `float` aux `double` types et dans une expression.</span><span class="sxs-lookup"><span data-stu-id="87693-139">You cannot mix the `decimal` type with the `float` and `double` types in an expression.</span></span> <span data-ttu-id="87693-140">Dans ce cas, si vous souhaitez effectuer des opérations arithmétiques, de comparaison ou d’égalité, vous devez convertir explicitement les opérandes à partir de ou vers le `decimal` type, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="87693-140">In this case, if you want to perform arithmetic, comparison, or equality operations, you must explicitly convert the operands either from or to the `decimal` type, as the following example shows:</span></span>

```csharp-interactive
double a = 1.0;
decimal b = 2.1m;
Console.WriteLine(a + (double)b);
Console.WriteLine((decimal)a + b);
```

<span data-ttu-id="87693-141">Vous pouvez utiliser des [chaînes au format numérique standard](../../../standard/base-types/standard-numeric-format-strings.md) ou des [chaînes au format numérique personnalisées](../../../standard/base-types/custom-numeric-format-strings.md) pour mettre en forme une valeur à virgule flottante.</span><span class="sxs-lookup"><span data-stu-id="87693-141">You can use either [standard numeric format strings](../../../standard/base-types/standard-numeric-format-strings.md) or [custom numeric format strings](../../../standard/base-types/custom-numeric-format-strings.md) to format a floating-point value.</span></span>

## <a name="real-literals"></a><span data-ttu-id="87693-142">Littéraux réels</span><span class="sxs-lookup"><span data-stu-id="87693-142">Real literals</span></span>

<span data-ttu-id="87693-143">Le type d’un littéral réel est déterminé par son suffixe comme suit :</span><span class="sxs-lookup"><span data-stu-id="87693-143">The type of a real literal is determined by its suffix as follows:</span></span>

- <span data-ttu-id="87693-144">Le littéral sans suffixe ou avec `d` le `D` suffixe ou est de type`double`</span><span class="sxs-lookup"><span data-stu-id="87693-144">The literal without suffix or with the `d` or `D` suffix is of type `double`</span></span>
- <span data-ttu-id="87693-145">Le littéral avec le `f` `F` suffixe ou est de type`float`</span><span class="sxs-lookup"><span data-stu-id="87693-145">The literal with the `f` or `F` suffix is of type `float`</span></span>
- <span data-ttu-id="87693-146">Le littéral avec le `m` `M` suffixe ou est de type`decimal`</span><span class="sxs-lookup"><span data-stu-id="87693-146">The literal with the `m` or `M` suffix is of type `decimal`</span></span>

<span data-ttu-id="87693-147">Le code suivant illustre un exemple de chaque :</span><span class="sxs-lookup"><span data-stu-id="87693-147">The following code demonstrates an example of each:</span></span>

```csharp
double d = 3D;
d = 4d;
d = 3.934_001;

float f = 3_000.5F;
f = 5.4f;

decimal myMoney = 3_000.5m;
myMoney = 400.75M;
```

<span data-ttu-id="87693-148">L’exemple précédent illustre également l’utilisation de `_` comme *séparateur de chiffres*, qui est pris en charge à partir de C# 7,0.</span><span class="sxs-lookup"><span data-stu-id="87693-148">The preceding example also shows the use of `_` as a *digit separator*, which is supported starting with C# 7.0.</span></span> <span data-ttu-id="87693-149">Vous pouvez utiliser le séparateur de chiffres avec tous les types de littéraux numériques.</span><span class="sxs-lookup"><span data-stu-id="87693-149">You can use the digit separator with all kinds of numeric literals.</span></span>

<span data-ttu-id="87693-150">Vous pouvez également utiliser la notation scientifique, c’est-à-dire spécifier une partie exposant d’un littéral réel, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="87693-150">You can also use scientific notation, that is, specify an exponent part of a real literal, as the following example shows:</span></span>

```csharp-interactive
double d = 0.42e2;
Console.WriteLine(d);  // output 42

float f = 134.45E-2f;
Console.WriteLine(f);  // output: 1.3445

decimal m = 1.5E6m;
Console.WriteLine(m);  // output: 1500000
```

## <a name="conversions"></a><span data-ttu-id="87693-151">Conversions</span><span class="sxs-lookup"><span data-stu-id="87693-151">Conversions</span></span>

<span data-ttu-id="87693-152">Il n’existe qu’une seule conversion implicite entre les types numériques à virgule flottante : de `float` à `double` .</span><span class="sxs-lookup"><span data-stu-id="87693-152">There is only one implicit conversion between floating-point numeric types: from `float` to `double`.</span></span> <span data-ttu-id="87693-153">Toutefois, vous pouvez convertir n’importe quel type à virgule flottante en tout autre type à virgule flottante avec le [cast explicite](../operators/type-testing-and-cast.md#cast-expression).</span><span class="sxs-lookup"><span data-stu-id="87693-153">However, you can convert any floating-point type to any other floating-point type with the [explicit cast](../operators/type-testing-and-cast.md#cast-expression).</span></span> <span data-ttu-id="87693-154">Pour plus d’informations, consultez [conversions numériques intégrées](numeric-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="87693-154">For more information, see [Built-in numeric conversions](numeric-conversions.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="87693-155">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="87693-155">C# language specification</span></span>

<span data-ttu-id="87693-156">Pour plus d’informations, consultez les sections suivantes de la [spécification du langage C#](~/_csharplang/spec/introduction.md) :</span><span class="sxs-lookup"><span data-stu-id="87693-156">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="87693-157">Types virgule flottante</span><span class="sxs-lookup"><span data-stu-id="87693-157">Floating-point types</span></span>](~/_csharplang/spec/types.md#floating-point-types)
- [<span data-ttu-id="87693-158">Type décimal</span><span class="sxs-lookup"><span data-stu-id="87693-158">The decimal type</span></span>](~/_csharplang/spec/types.md#the-decimal-type)
- [<span data-ttu-id="87693-159">Littéraux réels</span><span class="sxs-lookup"><span data-stu-id="87693-159">Real literals</span></span>](~/_csharplang/spec/lexical-structure.md#real-literals)

## <a name="see-also"></a><span data-ttu-id="87693-160">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="87693-160">See also</span></span>

- [<span data-ttu-id="87693-161">Informations de référence sur C#</span><span class="sxs-lookup"><span data-stu-id="87693-161">C# reference</span></span>](../index.md)
- [<span data-ttu-id="87693-162">Types valeur</span><span class="sxs-lookup"><span data-stu-id="87693-162">Value types</span></span>](value-types.md)
- [<span data-ttu-id="87693-163">Types intégraux</span><span class="sxs-lookup"><span data-stu-id="87693-163">Integral types</span></span>](integral-numeric-types.md)
- [<span data-ttu-id="87693-164">Chaînes de format numériques standard</span><span class="sxs-lookup"><span data-stu-id="87693-164">Standard numeric format strings</span></span>](../../../standard/base-types/standard-numeric-format-strings.md)
- [<span data-ttu-id="87693-165">Valeurs numériques dans .NET</span><span class="sxs-lookup"><span data-stu-id="87693-165">Numerics in .NET</span></span>](../../../standard/numerics.md)
- <xref:System.Numerics.Complex?displayProperty=nameWithType>
