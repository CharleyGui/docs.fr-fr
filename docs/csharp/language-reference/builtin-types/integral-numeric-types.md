---
title: Types numériques intégraux - Référence C#
description: Découvrez la plage, la taille de stockage et les différentes utilisations associés à chacun des types numériques intégraux.
ms.date: 10/22/2019
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
ms.openlocfilehash: 394a809a9a2f45f4aee652d0eca892f62f0f2e54
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77093199"
---
# <a name="integral-numeric-types--c-reference"></a><span data-ttu-id="950c3-103">Types numériques intégraux (référence C#)</span><span class="sxs-lookup"><span data-stu-id="950c3-103">Integral numeric types  (C# reference)</span></span>

<span data-ttu-id="950c3-104">Les *types numériques intégraux* représentent des nombres entiers.</span><span class="sxs-lookup"><span data-stu-id="950c3-104">The *integral numeric types* represent integer numbers.</span></span> <span data-ttu-id="950c3-105">Tous les types numériques intégraux sont des [types valeur](value-types.md).</span><span class="sxs-lookup"><span data-stu-id="950c3-105">All integral numeric types are [value types](value-types.md).</span></span> <span data-ttu-id="950c3-106">Il s’agit également de [types simples](value-types.md#built-in-value-types) qui peuvent être initialisés avec des [littéraux](#integer-literals).</span><span class="sxs-lookup"><span data-stu-id="950c3-106">They are also [simple types](value-types.md#built-in-value-types) and can be initialized with [literals](#integer-literals).</span></span> <span data-ttu-id="950c3-107">Tous les types numériques intégraux prennent en charge les opérateurs [arithmétiques](../operators/arithmetic-operators.md), de comparaison [logique](../operators/bitwise-and-shift-operators.md), de [comparaison](../operators/comparison-operators.md)et d' [égalité](../operators/equality-operators.md) .</span><span class="sxs-lookup"><span data-stu-id="950c3-107">All integral numeric types support [arithmetic](../operators/arithmetic-operators.md), [bitwise logical](../operators/bitwise-and-shift-operators.md), [comparison](../operators/comparison-operators.md), and [equality](../operators/equality-operators.md) operators.</span></span>

## <a name="characteristics-of-the-integral-types"></a><span data-ttu-id="950c3-108">Caractéristiques des types intégraux</span><span class="sxs-lookup"><span data-stu-id="950c3-108">Characteristics of the integral types</span></span>

<span data-ttu-id="950c3-109">C# prend en charge les types intégraux prédéfinis suivants :</span><span class="sxs-lookup"><span data-stu-id="950c3-109">C# supports the following predefined integral types:</span></span>

|<span data-ttu-id="950c3-110">C# type/mot clé</span><span class="sxs-lookup"><span data-stu-id="950c3-110">C# type/keyword</span></span>|<span data-ttu-id="950c3-111">Plage</span><span class="sxs-lookup"><span data-stu-id="950c3-111">Range</span></span>|<span data-ttu-id="950c3-112">Size</span><span class="sxs-lookup"><span data-stu-id="950c3-112">Size</span></span>|<span data-ttu-id="950c3-113">Type .NET</span><span class="sxs-lookup"><span data-stu-id="950c3-113">.NET type</span></span>|
|----------|-----------|----------|-------------|
|`sbyte`|<span data-ttu-id="950c3-114">-128 à 127</span><span class="sxs-lookup"><span data-stu-id="950c3-114">-128 to 127</span></span>|<span data-ttu-id="950c3-115">Entier 8 bits signé</span><span class="sxs-lookup"><span data-stu-id="950c3-115">Signed 8-bit integer</span></span>|<xref:System.SByte?displayProperty=nameWithType>|
|`byte`|<span data-ttu-id="950c3-116">0 à 255</span><span class="sxs-lookup"><span data-stu-id="950c3-116">0 to 255</span></span>|<span data-ttu-id="950c3-117">Entier 8 bits non signé</span><span class="sxs-lookup"><span data-stu-id="950c3-117">Unsigned 8-bit integer</span></span>|<xref:System.Byte?displayProperty=nameWithType>|
|`short`|<span data-ttu-id="950c3-118">-32 768 à 32 767</span><span class="sxs-lookup"><span data-stu-id="950c3-118">-32,768 to 32,767</span></span>|<span data-ttu-id="950c3-119">Entier 16 bits signé</span><span class="sxs-lookup"><span data-stu-id="950c3-119">Signed 16-bit integer</span></span>|<xref:System.Int16?displayProperty=nameWithType>|
|`ushort`|<span data-ttu-id="950c3-120">0 à 65 535</span><span class="sxs-lookup"><span data-stu-id="950c3-120">0 to 65,535</span></span>|<span data-ttu-id="950c3-121">Entier 16 bits non signé</span><span class="sxs-lookup"><span data-stu-id="950c3-121">Unsigned 16-bit integer</span></span>|<xref:System.UInt16?displayProperty=nameWithType>|
|`int`|<span data-ttu-id="950c3-122">-2 147 483 648 à 2 147 483 647</span><span class="sxs-lookup"><span data-stu-id="950c3-122">-2,147,483,648 to 2,147,483,647</span></span>|<span data-ttu-id="950c3-123">Entier 32 bits signé</span><span class="sxs-lookup"><span data-stu-id="950c3-123">Signed 32-bit integer</span></span>|<xref:System.Int32?displayProperty=nameWithType>|
|`uint`|<span data-ttu-id="950c3-124">de 0 à 4 294 967 295</span><span class="sxs-lookup"><span data-stu-id="950c3-124">0 to 4,294,967,295</span></span>|<span data-ttu-id="950c3-125">Entier 32 bits non signé</span><span class="sxs-lookup"><span data-stu-id="950c3-125">Unsigned 32-bit integer</span></span>|<xref:System.UInt32?displayProperty=nameWithType>|
|`long`|<span data-ttu-id="950c3-126">-9 223 372 036 854 775 808 à 9 223 372 036 854 775 807</span><span class="sxs-lookup"><span data-stu-id="950c3-126">-9,223,372,036,854,775,808 to 9,223,372,036,854,775,807</span></span>|<span data-ttu-id="950c3-127">Entier 64 bits signé</span><span class="sxs-lookup"><span data-stu-id="950c3-127">Signed 64-bit integer</span></span>|<xref:System.Int64?displayProperty=nameWithType>|
|`ulong`|<span data-ttu-id="950c3-128">de 0 à 18 446 744 073 709 551 615</span><span class="sxs-lookup"><span data-stu-id="950c3-128">0 to 18,446,744,073,709,551,615</span></span>|<span data-ttu-id="950c3-129">Entier 64 bits non signé</span><span class="sxs-lookup"><span data-stu-id="950c3-129">Unsigned 64-bit integer</span></span>|<xref:System.UInt64?displayProperty=nameWithType>|

<span data-ttu-id="950c3-130">Dans le tableau précédent, chaque mot clé de type C# de la colonne la plus à gauche est un alias pour le type .NET correspondant.</span><span class="sxs-lookup"><span data-stu-id="950c3-130">In the preceding table, each C# type keyword from the leftmost column is an alias for the corresponding .NET type.</span></span> <span data-ttu-id="950c3-131">Ils sont interchangeables.</span><span class="sxs-lookup"><span data-stu-id="950c3-131">They are interchangeable.</span></span> <span data-ttu-id="950c3-132">Par exemple, les déclarations suivantes déclarent des variables du même type :</span><span class="sxs-lookup"><span data-stu-id="950c3-132">For example, the following declarations declare variables of the same type:</span></span>

```csharp
int a = 123;
System.Int32 b = 123;
```

<span data-ttu-id="950c3-133">La valeur par défaut pour chaque type intégral est zéro, `0`.</span><span class="sxs-lookup"><span data-stu-id="950c3-133">The default value of each integral type is zero, `0`.</span></span> <span data-ttu-id="950c3-134">Chacun des types intégraux a les constantes `MinValue` et `MaxValue` qui fournissent la valeur minimale et maximale de ce type.</span><span class="sxs-lookup"><span data-stu-id="950c3-134">Each of the integral types has the `MinValue` and `MaxValue` constants that provide the minimum and maximum value of that type.</span></span>

<span data-ttu-id="950c3-135">Utilisez la structure <xref:System.Numerics.BigInteger?displayProperty=nameWithType> pour représenter un entier signé sans limites supérieures ou inférieures.</span><span class="sxs-lookup"><span data-stu-id="950c3-135">Use the <xref:System.Numerics.BigInteger?displayProperty=nameWithType> structure to represent a signed integer with no upper or lower bounds.</span></span>

## <a name="integer-literals"></a><span data-ttu-id="950c3-136">Littéraux d'entier</span><span class="sxs-lookup"><span data-stu-id="950c3-136">Integer literals</span></span>

<span data-ttu-id="950c3-137">Les littéraux entiers peuvent être</span><span class="sxs-lookup"><span data-stu-id="950c3-137">Integer literals can be</span></span>

- <span data-ttu-id="950c3-138">*Decimal*: sans préfixe</span><span class="sxs-lookup"><span data-stu-id="950c3-138">*decimal*: without any prefix</span></span>
- <span data-ttu-id="950c3-139">*hexadécimal*: avec le préfixe `0x` ou `0X`</span><span class="sxs-lookup"><span data-stu-id="950c3-139">*hexadecimal*: with the `0x` or `0X` prefix</span></span>
- <span data-ttu-id="950c3-140">*Binary*: avec le préfixe `0b` ou `0B` (disponible C# dans 7,0 et versions ultérieures)</span><span class="sxs-lookup"><span data-stu-id="950c3-140">*binary*: with the `0b` or `0B` prefix (available in C# 7.0 and later)</span></span>

<span data-ttu-id="950c3-141">Le code suivant illustre un exemple de chaque :</span><span class="sxs-lookup"><span data-stu-id="950c3-141">The following code demonstrates an example of each:</span></span>

```csharp
var decimalLiteral = 42;
var hexLiteral = 0x2A;
var binaryLiteral = 0b_0010_1010;
```

<span data-ttu-id="950c3-142">L’exemple précédent illustre également l’utilisation de `_` comme *séparateur de chiffres*, pris en charge à C# partir de 7,0.</span><span class="sxs-lookup"><span data-stu-id="950c3-142">The preceding example also shows the use of `_` as a *digit separator*, which is supported starting with C# 7.0.</span></span> <span data-ttu-id="950c3-143">Vous pouvez utiliser le séparateur de chiffres avec tous les types de littéraux numériques.</span><span class="sxs-lookup"><span data-stu-id="950c3-143">You can use the digit separator with all kinds of numeric literals.</span></span>

<span data-ttu-id="950c3-144">Le type d’un littéral entier est déterminé par son suffixe comme suit :</span><span class="sxs-lookup"><span data-stu-id="950c3-144">The type of an integer literal is determined by its suffix as follows:</span></span>

- <span data-ttu-id="950c3-145">Si le littéral n’a pas de suffixe, son type est le premier des types suivants dans lesquels sa valeur peut être représentée : `int`, `uint`, `long`, `ulong`.</span><span class="sxs-lookup"><span data-stu-id="950c3-145">If the literal has no suffix, its type is the first of the following types in which its value can be represented: `int`, `uint`, `long`, `ulong`.</span></span>
- <span data-ttu-id="950c3-146">Si le littéral est précédé d’un suffixe `U` ou `u`, son type est le premier des types suivants dans lesquels sa valeur peut être représentée : `uint`, `ulong`.</span><span class="sxs-lookup"><span data-stu-id="950c3-146">If the literal is suffixed by `U` or `u`, its type is the first of the following types in which its value can be represented: `uint`, `ulong`.</span></span>
- <span data-ttu-id="950c3-147">Si le littéral est précédé d’un suffixe `L` ou `l`, son type est le premier des types suivants dans lesquels sa valeur peut être représentée : `long`, `ulong`.</span><span class="sxs-lookup"><span data-stu-id="950c3-147">If the literal is suffixed by `L` or `l`, its type is the first of the following types in which its value can be represented: `long`, `ulong`.</span></span>

  > [!NOTE]
  > <span data-ttu-id="950c3-148">Vous pouvez utiliser la lettre minuscule `l` comme suffixe.</span><span class="sxs-lookup"><span data-stu-id="950c3-148">You can use the lowercase letter `l` as a suffix.</span></span> <span data-ttu-id="950c3-149">Toutefois, cela génère un avertissement du compilateur, car la lettre `l` peut être confondue avec le chiffre `1`.</span><span class="sxs-lookup"><span data-stu-id="950c3-149">However, this generates a compiler warning because the letter `l` can be confused with the digit `1`.</span></span> <span data-ttu-id="950c3-150">Utilisez `L` pour plus de clarté.</span><span class="sxs-lookup"><span data-stu-id="950c3-150">Use `L` for clarity.</span></span>

- <span data-ttu-id="950c3-151">Si le littéral est précédé d’un suffixe `UL`, `Ul`, `uL`, `ul`, `LU`, `Lu`, `lU`ou `lu`, son type est `ulong`.</span><span class="sxs-lookup"><span data-stu-id="950c3-151">If the literal is suffixed by `UL`, `Ul`, `uL`, `ul`, `LU`, `Lu`, `lU`, or `lu`, its type is `ulong`.</span></span>

<span data-ttu-id="950c3-152">Si la valeur représentée par un littéral entier dépasse <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, une erreur de compilation [CS1021](../../misc/cs1021.md) se produit.</span><span class="sxs-lookup"><span data-stu-id="950c3-152">If the value represented by an integer literal exceeds <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, a compiler error [CS1021](../../misc/cs1021.md) occurs.</span></span>

<span data-ttu-id="950c3-153">Si le type déterminé d’un littéral d’entier est `int` et que la valeur représentée par le littéral est comprise dans la plage du type de destination, la valeur peut être convertie implicitement en `sbyte`, `byte`, `short`, `ushort`, `uint`ou `ulong`:</span><span class="sxs-lookup"><span data-stu-id="950c3-153">If the determined type of an integer literal is `int` and the value represented by the literal is within the range of the destination type, the value can be implicitly converted to `sbyte`, `byte`, `short`, `ushort`, `uint`, or `ulong`:</span></span>

```csharp
byte a = 17;
byte b = 300;   // CS0031: Constant value '300' cannot be converted to a 'byte'
```

<span data-ttu-id="950c3-154">Comme le montre l’exemple précédent, si la valeur du littéral n’est pas comprise dans la plage du type de destination, une erreur de compilateur [CS0031](../../misc/cs0031.md) se produit.</span><span class="sxs-lookup"><span data-stu-id="950c3-154">As the preceding example shows, if the literal's value is not within the range of the destination type, a compiler error [CS0031](../../misc/cs0031.md) occurs.</span></span>

<span data-ttu-id="950c3-155">Vous pouvez également utiliser un cast pour convertir la valeur représentée par un littéral entier en type autre que le type déterminé du littéral :</span><span class="sxs-lookup"><span data-stu-id="950c3-155">You also can use a cast to convert the value represented by an integer literal to the type other than the determined type of the literal:</span></span>

```csharp
var signedByte = (sbyte)42;
var longVariable = (long)42;
```

## <a name="conversions"></a><span data-ttu-id="950c3-156">Conversions</span><span class="sxs-lookup"><span data-stu-id="950c3-156">Conversions</span></span>

<span data-ttu-id="950c3-157">Vous pouvez convertir n’importe quel type numérique intégral en tout autre type numérique intégral.</span><span class="sxs-lookup"><span data-stu-id="950c3-157">You can convert any integral numeric type to any other integral numeric type.</span></span> <span data-ttu-id="950c3-158">Si le type de destination peut stocker toutes les valeurs du type source, la conversion est implicite.</span><span class="sxs-lookup"><span data-stu-id="950c3-158">If the destination type can store all values of the source type, the conversion is implicit.</span></span> <span data-ttu-id="950c3-159">Dans le cas contraire, vous devez utiliser l' [opérateur de cast `()`](../operators/type-testing-and-cast.md#cast-operator-) pour appeler une conversion explicite.</span><span class="sxs-lookup"><span data-stu-id="950c3-159">Otherwise, you need to use the [cast operator `()`](../operators/type-testing-and-cast.md#cast-operator-) to invoke an explicit conversion.</span></span> <span data-ttu-id="950c3-160">Pour plus d’informations, consultez [conversions numériques intégrées](numeric-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="950c3-160">For more information, see [Built-in numeric conversions](numeric-conversions.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="950c3-161">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="950c3-161">C# language specification</span></span>

<span data-ttu-id="950c3-162">Pour plus d’informations, consultez les sections suivantes de la [spécification du langage C#](~/_csharplang/spec/introduction.md) :</span><span class="sxs-lookup"><span data-stu-id="950c3-162">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="950c3-163">Types intégraux</span><span class="sxs-lookup"><span data-stu-id="950c3-163">Integral types</span></span>](~/_csharplang/spec/types.md#integral-types)
- [<span data-ttu-id="950c3-164">Littéraux entiers</span><span class="sxs-lookup"><span data-stu-id="950c3-164">Integer literals</span></span>](~/_csharplang/spec/lexical-structure.md#integer-literals)

## <a name="see-also"></a><span data-ttu-id="950c3-165">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="950c3-165">See also</span></span>

- [<span data-ttu-id="950c3-166">Informations de référence sur C#</span><span class="sxs-lookup"><span data-stu-id="950c3-166">C# reference</span></span>](../index.md)
- [<span data-ttu-id="950c3-167">Types de valeur</span><span class="sxs-lookup"><span data-stu-id="950c3-167">Value types</span></span>](value-types.md)
- [<span data-ttu-id="950c3-168">Types virgule flottante</span><span class="sxs-lookup"><span data-stu-id="950c3-168">Floating-point types</span></span>](floating-point-numeric-types.md)
- [<span data-ttu-id="950c3-169">Chaînes de format numériques standard</span><span class="sxs-lookup"><span data-stu-id="950c3-169">Standard numeric format strings</span></span>](../../../standard/base-types/standard-numeric-format-strings.md)
- [<span data-ttu-id="950c3-170">Valeurs numériques dans .NET</span><span class="sxs-lookup"><span data-stu-id="950c3-170">Numerics in .NET</span></span>](../../../standard/numerics.md)
