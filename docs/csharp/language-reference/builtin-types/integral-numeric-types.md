---
title: Types numériques intégraux - Référence C#
description: Découvrez la plage, la taille de stockage et les différentes utilisations associés à chacun des types numériques intégraux.
ms.date: 10/18/2019
f1_keywords:
- byte
- byte_CSharpKeyword
- sbyte_CSharpKeyword
- sbyte
- short
- short_CSharpKeyword
- ushort
- ushort_CSharpKeyword
- int_CSharpKeyword
- int
- uint
- uint_CSharpKeyword
- long_CSharpKeyword
- long
- ulong_CSharpKeyword
- ulong
helpviewer_keywords:
- integral types, C#
- Visual C#, integral types
- types [C#], integral types
- ranges of integral types [C#]
- byte keyword [C#]
- sbyte keyword [C#]
- short keyword [C#]
- ushort keyword [C#]
- int keyword [C#]
- uint keyword [C#]
- long keyword [C#]
- ulong keyword [C#]
ms.openlocfilehash: 3d4f3164d67a000123417619f3be6be455d5ab87
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72579197"
---
# <a name="integral-numeric-types--c-reference"></a><span data-ttu-id="f1697-103">Types numériques intégraux (référence C#)</span><span class="sxs-lookup"><span data-stu-id="f1697-103">Integral numeric types  (C# reference)</span></span>

<span data-ttu-id="f1697-104">Les **types numériques intégraux** sont un sous-ensemble des **types simples** et peuvent être initialisés avec des [*littéraux*](#integer-literals).</span><span class="sxs-lookup"><span data-stu-id="f1697-104">The **integral numeric types** are a subset of the **simple types** and can be initialized with [*literals*](#integer-literals).</span></span> <span data-ttu-id="f1697-105">Tous les types intégraux sont également des types valeur.</span><span class="sxs-lookup"><span data-stu-id="f1697-105">All integral types are also value types.</span></span> <span data-ttu-id="f1697-106">Tous les types numériques intégraux prennent en charge les opérateurs [arithmétiques](../operators/arithmetic-operators.md), de comparaison [logique](../operators/bitwise-and-shift-operators.md), de [comparaison](../operators/comparison-operators.md)et d' [égalité](../operators/equality-operators.md) .</span><span class="sxs-lookup"><span data-stu-id="f1697-106">All integral numeric types support [arithmetic](../operators/arithmetic-operators.md), [bitwise logical](../operators/bitwise-and-shift-operators.md), [comparison](../operators/comparison-operators.md), and [equality](../operators/equality-operators.md) operators.</span></span>

## <a name="characteristics-of-the-integral-types"></a><span data-ttu-id="f1697-107">Caractéristiques des types intégraux</span><span class="sxs-lookup"><span data-stu-id="f1697-107">Characteristics of the integral types</span></span>

<span data-ttu-id="f1697-108">C# prend en charge les types intégraux prédéfinis suivants :</span><span class="sxs-lookup"><span data-stu-id="f1697-108">C# supports the following predefined integral types:</span></span>

|<span data-ttu-id="f1697-109">C# type/mot clé</span><span class="sxs-lookup"><span data-stu-id="f1697-109">C# type/keyword</span></span>|<span data-ttu-id="f1697-110">Range</span><span class="sxs-lookup"><span data-stu-id="f1697-110">Range</span></span>|<span data-ttu-id="f1697-111">Size</span><span class="sxs-lookup"><span data-stu-id="f1697-111">Size</span></span>|<span data-ttu-id="f1697-112">Type .NET</span><span class="sxs-lookup"><span data-stu-id="f1697-112">.NET type</span></span>|
|----------|-----------|----------|-------------|
|`sbyte`|<span data-ttu-id="f1697-113">-128 à 127</span><span class="sxs-lookup"><span data-stu-id="f1697-113">-128 to 127</span></span>|<span data-ttu-id="f1697-114">Entier 8 bits signé</span><span class="sxs-lookup"><span data-stu-id="f1697-114">Signed 8-bit integer</span></span>|<xref:System.SByte?displayProperty=nameWithType>|
|`byte`|<span data-ttu-id="f1697-115">0 à 255</span><span class="sxs-lookup"><span data-stu-id="f1697-115">0 to 255</span></span>|<span data-ttu-id="f1697-116">Entier 8 bits non signé</span><span class="sxs-lookup"><span data-stu-id="f1697-116">Unsigned 8-bit integer</span></span>|<xref:System.Byte?displayProperty=nameWithType>|
|`short`|<span data-ttu-id="f1697-117">de -32 768 à 32 767</span><span class="sxs-lookup"><span data-stu-id="f1697-117">-32,768 to 32,767</span></span>|<span data-ttu-id="f1697-118">Entier 16 bits signé</span><span class="sxs-lookup"><span data-stu-id="f1697-118">Signed 16-bit integer</span></span>|<xref:System.Int16?displayProperty=nameWithType>|
|`ushort`|<span data-ttu-id="f1697-119">0 à 65 535</span><span class="sxs-lookup"><span data-stu-id="f1697-119">0 to 65,535</span></span>|<span data-ttu-id="f1697-120">Entier 16 bits non signé</span><span class="sxs-lookup"><span data-stu-id="f1697-120">Unsigned 16-bit integer</span></span>|<xref:System.UInt16?displayProperty=nameWithType>|
|`int`|<span data-ttu-id="f1697-121">-2,147,483,648 en 2,147,483,647</span><span class="sxs-lookup"><span data-stu-id="f1697-121">-2,147,483,648 to 2,147,483,647</span></span>|<span data-ttu-id="f1697-122">Entier 32 bits signé</span><span class="sxs-lookup"><span data-stu-id="f1697-122">Signed 32-bit integer</span></span>|<xref:System.Int32?displayProperty=nameWithType>|
|`uint`|<span data-ttu-id="f1697-123">de 0 à 4 294 967 295</span><span class="sxs-lookup"><span data-stu-id="f1697-123">0 to 4,294,967,295</span></span>|<span data-ttu-id="f1697-124">Entier 32 bits non signé</span><span class="sxs-lookup"><span data-stu-id="f1697-124">Unsigned 32-bit integer</span></span>|<xref:System.UInt32?displayProperty=nameWithType>|
|`long`|<span data-ttu-id="f1697-125">-9 223 372 036 854 775 808 à 9 223 372 036 854 775 807</span><span class="sxs-lookup"><span data-stu-id="f1697-125">-9,223,372,036,854,775,808 to 9,223,372,036,854,775,807</span></span>|<span data-ttu-id="f1697-126">Entier 64 bits signé</span><span class="sxs-lookup"><span data-stu-id="f1697-126">Signed 64-bit integer</span></span>|<xref:System.Int64?displayProperty=nameWithType>|
|`ulong`|<span data-ttu-id="f1697-127">de 0 à 18 446 744 073 709 551 615</span><span class="sxs-lookup"><span data-stu-id="f1697-127">0 to 18,446,744,073,709,551,615</span></span>|<span data-ttu-id="f1697-128">Entier 64 bits non signé</span><span class="sxs-lookup"><span data-stu-id="f1697-128">Unsigned 64-bit integer</span></span>|<xref:System.UInt64?displayProperty=nameWithType>|

<span data-ttu-id="f1697-129">Dans le tableau précédent, chaque mot clé de type C# de la colonne la plus à gauche est un alias pour le type .NET correspondant.</span><span class="sxs-lookup"><span data-stu-id="f1697-129">In the preceding table, each C# type keyword from the leftmost column is an alias for the corresponding .NET type.</span></span> <span data-ttu-id="f1697-130">Ils sont interchangeables.</span><span class="sxs-lookup"><span data-stu-id="f1697-130">They are interchangeable.</span></span> <span data-ttu-id="f1697-131">Par exemple, les déclarations suivantes déclarent des variables du même type :</span><span class="sxs-lookup"><span data-stu-id="f1697-131">For example, the following declarations declare variables of the same type:</span></span>

```csharp
int a = 123;
System.Int32 b = 123;
```

<span data-ttu-id="f1697-132">La valeur par défaut pour chaque type intégral est zéro, `0`.</span><span class="sxs-lookup"><span data-stu-id="f1697-132">The default value of each integral type is zero, `0`.</span></span> <span data-ttu-id="f1697-133">Chacun des types intégraux a les constantes `MinValue` et `MaxValue` qui fournissent la valeur minimale et maximale de ce type.</span><span class="sxs-lookup"><span data-stu-id="f1697-133">Each of the integral types has the `MinValue` and `MaxValue` constants that provide the minimum and maximum value of that type.</span></span>

<span data-ttu-id="f1697-134">Utilisez la structure <xref:System.Numerics.BigInteger?displayProperty=nameWithType> pour représenter un entier signé sans limites supérieures ou inférieures.</span><span class="sxs-lookup"><span data-stu-id="f1697-134">Use the <xref:System.Numerics.BigInteger?displayProperty=nameWithType> structure to represent a signed integer with no upper or lower bounds.</span></span>

## <a name="integer-literals"></a><span data-ttu-id="f1697-135">Littéraux d'entier</span><span class="sxs-lookup"><span data-stu-id="f1697-135">Integer literals</span></span>

<span data-ttu-id="f1697-136">Les littéraux entiers peuvent être</span><span class="sxs-lookup"><span data-stu-id="f1697-136">Integer literals can be</span></span>

- <span data-ttu-id="f1697-137">*Decimal*: sans préfixe</span><span class="sxs-lookup"><span data-stu-id="f1697-137">*decimal*: without any prefix</span></span>
- <span data-ttu-id="f1697-138">*hexadécimal*: avec le préfixe `0x` ou `0X`</span><span class="sxs-lookup"><span data-stu-id="f1697-138">*hexadecimal*: with the `0x` or `0X` prefix</span></span>
- <span data-ttu-id="f1697-139">*Binary*: avec le préfixe `0b` ou `0B` (disponible C# dans 7,0 et versions ultérieures)</span><span class="sxs-lookup"><span data-stu-id="f1697-139">*binary*: with the `0b` or `0B` prefix (available in C# 7.0 and later)</span></span>

<span data-ttu-id="f1697-140">Le code suivant illustre un exemple de chaque :</span><span class="sxs-lookup"><span data-stu-id="f1697-140">The following code demonstrates an example of each:</span></span>

```csharp
var decimalLiteral = 42;
var hexLiteral = 0x2A;
var binaryLiteral = 0b_0010_1010;
```

<span data-ttu-id="f1697-141">L’exemple précédent illustre également l’utilisation de `_` comme *séparateur de chiffres*, pris en charge à C# partir de 7,0.</span><span class="sxs-lookup"><span data-stu-id="f1697-141">The preceding example also shows the use of `_` as a *digit separator*, which is supported starting with C# 7.0.</span></span> <span data-ttu-id="f1697-142">Vous pouvez utiliser le séparateur de chiffres avec tous les types de littéraux numériques.</span><span class="sxs-lookup"><span data-stu-id="f1697-142">You can use the digit separator with all kinds of numeric literals.</span></span>

<span data-ttu-id="f1697-143">Le type d’un littéral entier est déterminé par son suffixe comme suit :</span><span class="sxs-lookup"><span data-stu-id="f1697-143">The type of an integer literal is determined by its suffix as follows:</span></span>

- <span data-ttu-id="f1697-144">Si le littéral n’a pas de suffixe, son type est le premier des types suivants dans lesquels sa valeur peut être représentée : `int`, `uint`, `long`, `ulong`.</span><span class="sxs-lookup"><span data-stu-id="f1697-144">If the literal has no suffix, its type is the first of the following types in which its value can be represented: `int`, `uint`, `long`, `ulong`.</span></span>
- <span data-ttu-id="f1697-145">Si le littéral est précédé d’un suffixe `U` ou `u`, son type est le premier des types suivants dans lesquels sa valeur peut être représentée : `uint`, `ulong`.</span><span class="sxs-lookup"><span data-stu-id="f1697-145">If the literal is suffixed by `U` or `u`, its type is the first of the following types in which its value can be represented: `uint`, `ulong`.</span></span>
- <span data-ttu-id="f1697-146">Si le littéral est précédé d’un suffixe `L` ou `l`, son type est le premier des types suivants dans lesquels sa valeur peut être représentée : `long`, `ulong`.</span><span class="sxs-lookup"><span data-stu-id="f1697-146">If the literal is suffixed by `L` or `l`, its type is the first of the following types in which its value can be represented: `long`, `ulong`.</span></span>

  > [!NOTE]
  > <span data-ttu-id="f1697-147">Vous pouvez utiliser la lettre minuscule `l` comme suffixe.</span><span class="sxs-lookup"><span data-stu-id="f1697-147">You can use the lowercase letter `l` as a suffix.</span></span> <span data-ttu-id="f1697-148">Toutefois, cela génère un avertissement du compilateur, car la lettre `l` peut être confondue avec le chiffre `1`.</span><span class="sxs-lookup"><span data-stu-id="f1697-148">However, this generates a compiler warning because the letter `l` can be confused with the digit `1`.</span></span> <span data-ttu-id="f1697-149">Utilisez `L` pour plus de clarté.</span><span class="sxs-lookup"><span data-stu-id="f1697-149">Use `L` for clarity.</span></span>

- <span data-ttu-id="f1697-150">Si le littéral est précédé d’un suffixe `UL`, `Ul`, `uL`, `ul`, `LU`, `Lu`, `lU` ou `lu`, son type est `ulong`.</span><span class="sxs-lookup"><span data-stu-id="f1697-150">If the literal is suffixed by `UL`, `Ul`, `uL`, `ul`, `LU`, `Lu`, `lU`, or `lu`, its type is `ulong`.</span></span>

<span data-ttu-id="f1697-151">Si la valeur représentée par un littéral entier dépasse <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, une erreur de compilation [CS1021](../../misc/cs1021.md) se produit.</span><span class="sxs-lookup"><span data-stu-id="f1697-151">If the value represented by an integer literal exceeds <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, a compiler error [CS1021](../../misc/cs1021.md) occurs.</span></span>

<span data-ttu-id="f1697-152">La valeur représentée par un littéral entier peut être implicitement convertie en un type avec une plage plus petite que le type déterminé du littéral.</span><span class="sxs-lookup"><span data-stu-id="f1697-152">The value represented by an integer literal can be implicitly converted to a type with a smaller range than the determined type of the literal.</span></span> <span data-ttu-id="f1697-153">Cela est possible lorsque la valeur est comprise dans la plage du type de destination :</span><span class="sxs-lookup"><span data-stu-id="f1697-153">That's possible when the value is within the range of the destination type:</span></span>

```csharp
byte a = 17;
byte b = 300;   // CS0031: Constant value '300' cannot be converted to a 'byte'
```

<span data-ttu-id="f1697-154">Comme le montre l’exemple précédent, si la valeur du littéral n’est pas comprise dans la plage du type de destination, une erreur de compilateur [CS0031](../../misc/cs0031.md) se produit.</span><span class="sxs-lookup"><span data-stu-id="f1697-154">As the preceding example shows, if the literal's value is not within the range of the destination type, a compiler error [CS0031](../../misc/cs0031.md) occurs.</span></span>

<span data-ttu-id="f1697-155">Vous pouvez également utiliser un cast pour convertir la valeur représentée par un littéral entier en type autre que le type déterminé du littéral :</span><span class="sxs-lookup"><span data-stu-id="f1697-155">You also can use a cast to convert the value represented by an integer literal to the type other than the determined type of the literal:</span></span>

```csharp
var signedByte = (sbyte)42;
var longVariable = (long)42;
```

## <a name="conversions"></a><span data-ttu-id="f1697-156">Conversions</span><span class="sxs-lookup"><span data-stu-id="f1697-156">Conversions</span></span>

<span data-ttu-id="f1697-157">Entre deux types intégraux, il existe une conversion implicite (appelée *conversion étendue*) où le type de destination peut stocker toutes les valeurs du type source.</span><span class="sxs-lookup"><span data-stu-id="f1697-157">There's an implicit conversion (called a *widening conversion*) between any two integral types where the destination type can store all values of the source type.</span></span> <span data-ttu-id="f1697-158">Par exemple, il existe une conversion implicite de `int` vers `long`, car la plage de valeurs `int` est un sous-ensemble de `long`.</span><span class="sxs-lookup"><span data-stu-id="f1697-158">For example, there's an implicit conversion from `int` to `long` because the range of `int` values is a proper subset of `long`.</span></span> <span data-ttu-id="f1697-159">Il existe des conversions implicites entre un type intégral non signé plus petit et un type intégral signé plus grand.</span><span class="sxs-lookup"><span data-stu-id="f1697-159">There are implicit conversions from a smaller unsigned integral type to a larger signed integral type.</span></span> <span data-ttu-id="f1697-160">Il existe également une conversion implicite entre un type intégral et n’importe quel type à virgule flottante.</span><span class="sxs-lookup"><span data-stu-id="f1697-160">There's also an implicit conversion from any integral type to any floating-point type.</span></span>  <span data-ttu-id="f1697-161">Il existe une conversion implicite entre un type intégral signé et n’importe quel type intégral non signé.</span><span class="sxs-lookup"><span data-stu-id="f1697-161">There's no implicit conversion from any signed integral type to any unsigned integral type.</span></span>

<span data-ttu-id="f1697-162">Vous devez utiliser un cast explicite pour convertir un type intégral en un autre type intégral, lorsqu’une conversion implicite n’est pas définie entre le type source et le type de destination.</span><span class="sxs-lookup"><span data-stu-id="f1697-162">You must use an explicit cast to convert one integral type to another integral type when an implicit conversion is not defined from the source type to the destination type.</span></span> <span data-ttu-id="f1697-163">C’est ce qu’on appelle une *conversion restrictive*.</span><span class="sxs-lookup"><span data-stu-id="f1697-163">This is called a *narrowing conversion*.</span></span> <span data-ttu-id="f1697-164">Un scénario explicite est nécessaire, car la conversion peut entraîner une perte de données.</span><span class="sxs-lookup"><span data-stu-id="f1697-164">The explicit case is required because the conversion can result in data loss.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="f1697-165">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="f1697-165">C# language specification</span></span>

<span data-ttu-id="f1697-166">Pour plus d’informations, consultez les sections suivantes de la [spécification du langage C#](~/_csharplang/spec/introduction.md) :</span><span class="sxs-lookup"><span data-stu-id="f1697-166">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="f1697-167">Types intégraux</span><span class="sxs-lookup"><span data-stu-id="f1697-167">Integral types</span></span>](~/_csharplang/spec/types.md#integral-types)
- [<span data-ttu-id="f1697-168">Littéraux entiers</span><span class="sxs-lookup"><span data-stu-id="f1697-168">Integer literals</span></span>](~/_csharplang/spec/lexical-structure.md#integer-literals)

## <a name="see-also"></a><span data-ttu-id="f1697-169">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f1697-169">See also</span></span>

- [<span data-ttu-id="f1697-170">Informations de référence sur C#</span><span class="sxs-lookup"><span data-stu-id="f1697-170">C# reference</span></span>](../index.md)
- [<span data-ttu-id="f1697-171">Types virgule flottante</span><span class="sxs-lookup"><span data-stu-id="f1697-171">Floating-point types</span></span>](floating-point-numeric-types.md)
- [<span data-ttu-id="f1697-172">Tableau des valeurs par défaut</span><span class="sxs-lookup"><span data-stu-id="f1697-172">Default values table</span></span>](../keywords/default-values-table.md)
- [<span data-ttu-id="f1697-173">Tableau des formats des résultats numériques</span><span class="sxs-lookup"><span data-stu-id="f1697-173">Formatting numeric results table</span></span>](../keywords/formatting-numeric-results-table.md)
- [<span data-ttu-id="f1697-174">Tableaux des types intégrés</span><span class="sxs-lookup"><span data-stu-id="f1697-174">Built-in types table</span></span>](../keywords/built-in-types-table.md)
- [<span data-ttu-id="f1697-175">Valeurs numériques dans .NET</span><span class="sxs-lookup"><span data-stu-id="f1697-175">Numerics in .NET</span></span>](../../../standard/numerics.md)
