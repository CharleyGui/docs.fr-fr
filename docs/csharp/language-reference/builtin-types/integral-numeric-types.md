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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77093199"
---
# <a name="integral-numeric-types--c-reference"></a><span data-ttu-id="aec05-103">Types numériques intégraux (référence C#)</span><span class="sxs-lookup"><span data-stu-id="aec05-103">Integral numeric types  (C# reference)</span></span>

<span data-ttu-id="aec05-104">Les *types numériques intégrals* représentent les nombres d’intégraires.</span><span class="sxs-lookup"><span data-stu-id="aec05-104">The *integral numeric types* represent integer numbers.</span></span> <span data-ttu-id="aec05-105">Tous les types numériques intégral sont [des types de valeur](value-types.md).</span><span class="sxs-lookup"><span data-stu-id="aec05-105">All integral numeric types are [value types](value-types.md).</span></span> <span data-ttu-id="aec05-106">Ils sont également [des types simples](value-types.md#built-in-value-types) et peuvent être parascés avec des [littérals](#integer-literals).</span><span class="sxs-lookup"><span data-stu-id="aec05-106">They are also [simple types](value-types.md#built-in-value-types) and can be initialized with [literals](#integer-literals).</span></span> <span data-ttu-id="aec05-107">Tous les types numériques intégral prennent en charge [l’arithmétique,](../operators/arithmetic-operators.md) [la logique bitwise,](../operators/bitwise-and-shift-operators.md) [la comparaison,](../operators/comparison-operators.md)et les opérateurs [d’égalité.](../operators/equality-operators.md)</span><span class="sxs-lookup"><span data-stu-id="aec05-107">All integral numeric types support [arithmetic](../operators/arithmetic-operators.md), [bitwise logical](../operators/bitwise-and-shift-operators.md), [comparison](../operators/comparison-operators.md), and [equality](../operators/equality-operators.md) operators.</span></span>

## <a name="characteristics-of-the-integral-types"></a><span data-ttu-id="aec05-108">Caractéristiques des types intégraux</span><span class="sxs-lookup"><span data-stu-id="aec05-108">Characteristics of the integral types</span></span>

<span data-ttu-id="aec05-109">C# prend en charge les types intégraux prédéfinis suivants :</span><span class="sxs-lookup"><span data-stu-id="aec05-109">C# supports the following predefined integral types:</span></span>

|<span data-ttu-id="aec05-110">C# type/mot clé</span><span class="sxs-lookup"><span data-stu-id="aec05-110">C# type/keyword</span></span>|<span data-ttu-id="aec05-111">Plage</span><span class="sxs-lookup"><span data-stu-id="aec05-111">Range</span></span>|<span data-ttu-id="aec05-112">Size</span><span class="sxs-lookup"><span data-stu-id="aec05-112">Size</span></span>|<span data-ttu-id="aec05-113">Type .NET</span><span class="sxs-lookup"><span data-stu-id="aec05-113">.NET type</span></span>|
|----------|-----------|----------|-------------|
|`sbyte`|<span data-ttu-id="aec05-114">-128 à 127</span><span class="sxs-lookup"><span data-stu-id="aec05-114">-128 to 127</span></span>|<span data-ttu-id="aec05-115">Entier 8 bits signé</span><span class="sxs-lookup"><span data-stu-id="aec05-115">Signed 8-bit integer</span></span>|<xref:System.SByte?displayProperty=nameWithType>|
|`byte`|<span data-ttu-id="aec05-116">0 à 255</span><span class="sxs-lookup"><span data-stu-id="aec05-116">0 to 255</span></span>|<span data-ttu-id="aec05-117">Entier 8 bits non signé</span><span class="sxs-lookup"><span data-stu-id="aec05-117">Unsigned 8-bit integer</span></span>|<xref:System.Byte?displayProperty=nameWithType>|
|`short`|<span data-ttu-id="aec05-118">-32 768 à 32 767</span><span class="sxs-lookup"><span data-stu-id="aec05-118">-32,768 to 32,767</span></span>|<span data-ttu-id="aec05-119">Entier 16 bits signé</span><span class="sxs-lookup"><span data-stu-id="aec05-119">Signed 16-bit integer</span></span>|<xref:System.Int16?displayProperty=nameWithType>|
|`ushort`|<span data-ttu-id="aec05-120">0 à 65 535</span><span class="sxs-lookup"><span data-stu-id="aec05-120">0 to 65,535</span></span>|<span data-ttu-id="aec05-121">Entier 16 bits non signé</span><span class="sxs-lookup"><span data-stu-id="aec05-121">Unsigned 16-bit integer</span></span>|<xref:System.UInt16?displayProperty=nameWithType>|
|`int`|<span data-ttu-id="aec05-122">-2 147 483 648 à 2 147 483 647</span><span class="sxs-lookup"><span data-stu-id="aec05-122">-2,147,483,648 to 2,147,483,647</span></span>|<span data-ttu-id="aec05-123">Entier 32 bits signé</span><span class="sxs-lookup"><span data-stu-id="aec05-123">Signed 32-bit integer</span></span>|<xref:System.Int32?displayProperty=nameWithType>|
|`uint`|<span data-ttu-id="aec05-124">de 0 à 4 294 967 295</span><span class="sxs-lookup"><span data-stu-id="aec05-124">0 to 4,294,967,295</span></span>|<span data-ttu-id="aec05-125">Entier 32 bits non signé</span><span class="sxs-lookup"><span data-stu-id="aec05-125">Unsigned 32-bit integer</span></span>|<xref:System.UInt32?displayProperty=nameWithType>|
|`long`|<span data-ttu-id="aec05-126">-9 223 372 036 854 775 808 à 9 223 372 036 854 775 807</span><span class="sxs-lookup"><span data-stu-id="aec05-126">-9,223,372,036,854,775,808 to 9,223,372,036,854,775,807</span></span>|<span data-ttu-id="aec05-127">Entier 64 bits signé</span><span class="sxs-lookup"><span data-stu-id="aec05-127">Signed 64-bit integer</span></span>|<xref:System.Int64?displayProperty=nameWithType>|
|`ulong`|<span data-ttu-id="aec05-128">de 0 à 18 446 744 073 709 551 615</span><span class="sxs-lookup"><span data-stu-id="aec05-128">0 to 18,446,744,073,709,551,615</span></span>|<span data-ttu-id="aec05-129">Entier 64 bits non signé</span><span class="sxs-lookup"><span data-stu-id="aec05-129">Unsigned 64-bit integer</span></span>|<xref:System.UInt64?displayProperty=nameWithType>|

<span data-ttu-id="aec05-130">Dans le tableau précédent, chaque mot clé de type C# de la colonne la plus à gauche est un alias pour le type .NET correspondant.</span><span class="sxs-lookup"><span data-stu-id="aec05-130">In the preceding table, each C# type keyword from the leftmost column is an alias for the corresponding .NET type.</span></span> <span data-ttu-id="aec05-131">Ils sont interchangeables.</span><span class="sxs-lookup"><span data-stu-id="aec05-131">They are interchangeable.</span></span> <span data-ttu-id="aec05-132">Par exemple, les déclarations suivantes déclarent des variables du même type :</span><span class="sxs-lookup"><span data-stu-id="aec05-132">For example, the following declarations declare variables of the same type:</span></span>

```csharp
int a = 123;
System.Int32 b = 123;
```

<span data-ttu-id="aec05-133">La valeur par défaut pour chaque type intégral est zéro, `0`.</span><span class="sxs-lookup"><span data-stu-id="aec05-133">The default value of each integral type is zero, `0`.</span></span> <span data-ttu-id="aec05-134">Chacun des types intégraux a les constantes `MinValue` et `MaxValue` qui fournissent la valeur minimale et maximale de ce type.</span><span class="sxs-lookup"><span data-stu-id="aec05-134">Each of the integral types has the `MinValue` and `MaxValue` constants that provide the minimum and maximum value of that type.</span></span>

<span data-ttu-id="aec05-135">Utilisez la structure <xref:System.Numerics.BigInteger?displayProperty=nameWithType> pour représenter un entier signé sans limites supérieures ou inférieures.</span><span class="sxs-lookup"><span data-stu-id="aec05-135">Use the <xref:System.Numerics.BigInteger?displayProperty=nameWithType> structure to represent a signed integer with no upper or lower bounds.</span></span>

## <a name="integer-literals"></a><span data-ttu-id="aec05-136">Littéraux d'entier</span><span class="sxs-lookup"><span data-stu-id="aec05-136">Integer literals</span></span>

<span data-ttu-id="aec05-137">Les littérals integer peuvent être</span><span class="sxs-lookup"><span data-stu-id="aec05-137">Integer literals can be</span></span>

- <span data-ttu-id="aec05-138">*décimale*: sans préfixe</span><span class="sxs-lookup"><span data-stu-id="aec05-138">*decimal*: without any prefix</span></span>
- <span data-ttu-id="aec05-139">*hexadecimal*: `0x` avec `0X` le préfixe ou le préfixe</span><span class="sxs-lookup"><span data-stu-id="aec05-139">*hexadecimal*: with the `0x` or `0X` prefix</span></span>
- <span data-ttu-id="aec05-140">*binaire*: `0b` avec `0B` le ou le préfixe (disponible en C 7.0 et plus tard)</span><span class="sxs-lookup"><span data-stu-id="aec05-140">*binary*: with the `0b` or `0B` prefix (available in C# 7.0 and later)</span></span>

<span data-ttu-id="aec05-141">Le code suivant montre un exemple de chacun :</span><span class="sxs-lookup"><span data-stu-id="aec05-141">The following code demonstrates an example of each:</span></span>

```csharp
var decimalLiteral = 42;
var hexLiteral = 0x2A;
var binaryLiteral = 0b_0010_1010;
```

<span data-ttu-id="aec05-142">L’exemple précédent montre `_` également l’utilisation d’un *séparateur à chiffres*, qui est pris en charge à partir de C 7.0.</span><span class="sxs-lookup"><span data-stu-id="aec05-142">The preceding example also shows the use of `_` as a *digit separator*, which is supported starting with C# 7.0.</span></span> <span data-ttu-id="aec05-143">Vous pouvez utiliser le séparateur de chiffre avec toutes sortes de littéral numériques.</span><span class="sxs-lookup"><span data-stu-id="aec05-143">You can use the digit separator with all kinds of numeric literals.</span></span>

<span data-ttu-id="aec05-144">Le type d’un littéral integer est déterminé par son suffixe comme suit:</span><span class="sxs-lookup"><span data-stu-id="aec05-144">The type of an integer literal is determined by its suffix as follows:</span></span>

- <span data-ttu-id="aec05-145">Si le littéral n’a pas de suffixe, son type est le `int` `uint`premier `long` `ulong`des types suivants dans lesquels sa valeur peut être représentée: , , , .</span><span class="sxs-lookup"><span data-stu-id="aec05-145">If the literal has no suffix, its type is the first of the following types in which its value can be represented: `int`, `uint`, `long`, `ulong`.</span></span>
- <span data-ttu-id="aec05-146">Si le littéral est `U` `u`suffixe par ou, son type est le premier des `uint` `ulong`types suivants dans lesquels sa valeur peut être représentée: , .</span><span class="sxs-lookup"><span data-stu-id="aec05-146">If the literal is suffixed by `U` or `u`, its type is the first of the following types in which its value can be represented: `uint`, `ulong`.</span></span>
- <span data-ttu-id="aec05-147">Si le littéral est `L` `l`suffixe par ou, son type est le premier des `long` `ulong`types suivants dans lesquels sa valeur peut être représentée: , .</span><span class="sxs-lookup"><span data-stu-id="aec05-147">If the literal is suffixed by `L` or `l`, its type is the first of the following types in which its value can be represented: `long`, `ulong`.</span></span>

  > [!NOTE]
  > <span data-ttu-id="aec05-148">Vous pouvez utiliser la `l` lettre minuscule comme suffixe.</span><span class="sxs-lookup"><span data-stu-id="aec05-148">You can use the lowercase letter `l` as a suffix.</span></span> <span data-ttu-id="aec05-149">Cependant, cela génère un avertissement compilateur parce que la lettre `l` peut être confondue avec le chiffre `1`.</span><span class="sxs-lookup"><span data-stu-id="aec05-149">However, this generates a compiler warning because the letter `l` can be confused with the digit `1`.</span></span> <span data-ttu-id="aec05-150">Utiliser `L` pour plus de clarté.</span><span class="sxs-lookup"><span data-stu-id="aec05-150">Use `L` for clarity.</span></span>

- <span data-ttu-id="aec05-151">Si le littéral est `UL` `Ul`suffixe par `Lu`, `lu`, `ulong`, `uL` `ul`, `LU`, , `lU`, , ou , son type est .</span><span class="sxs-lookup"><span data-stu-id="aec05-151">If the literal is suffixed by `UL`, `Ul`, `uL`, `ul`, `LU`, `Lu`, `lU`, or `lu`, its type is `ulong`.</span></span>

<span data-ttu-id="aec05-152">Si la valeur représentée par un littéral entier dépasse <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, une erreur de compilation [CS1021](../../misc/cs1021.md) se produit.</span><span class="sxs-lookup"><span data-stu-id="aec05-152">If the value represented by an integer literal exceeds <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, a compiler error [CS1021](../../misc/cs1021.md) occurs.</span></span>

<span data-ttu-id="aec05-153">Si le type déterminé d’un `int` littéral integer est et la valeur représentée par le littéral est `sbyte` `byte`dans `short` `ushort`la gamme du type de destination, la valeur peut être implicitement convertie en , , , , `uint`, ou: `ulong`</span><span class="sxs-lookup"><span data-stu-id="aec05-153">If the determined type of an integer literal is `int` and the value represented by the literal is within the range of the destination type, the value can be implicitly converted to `sbyte`, `byte`, `short`, `ushort`, `uint`, or `ulong`:</span></span>

```csharp
byte a = 17;
byte b = 300;   // CS0031: Constant value '300' cannot be converted to a 'byte'
```

<span data-ttu-id="aec05-154">Comme l’exemple précédent le montre, si la valeur du littéral n’est pas dans la plage du type de destination, une erreur de compilateur [CS0031](../../misc/cs0031.md) se produit.</span><span class="sxs-lookup"><span data-stu-id="aec05-154">As the preceding example shows, if the literal's value is not within the range of the destination type, a compiler error [CS0031](../../misc/cs0031.md) occurs.</span></span>

<span data-ttu-id="aec05-155">Vous pouvez également utiliser un plâtre pour convertir la valeur représentée par un littéral integer au type autre que le type déterminé de littéral:</span><span class="sxs-lookup"><span data-stu-id="aec05-155">You also can use a cast to convert the value represented by an integer literal to the type other than the determined type of the literal:</span></span>

```csharp
var signedByte = (sbyte)42;
var longVariable = (long)42;
```

## <a name="conversions"></a><span data-ttu-id="aec05-156">Conversions</span><span class="sxs-lookup"><span data-stu-id="aec05-156">Conversions</span></span>

<span data-ttu-id="aec05-157">Vous pouvez convertir n’importe quel type numérique intégral à n’importe quel autre type numérique intégral.</span><span class="sxs-lookup"><span data-stu-id="aec05-157">You can convert any integral numeric type to any other integral numeric type.</span></span> <span data-ttu-id="aec05-158">Si le type de destination peut stocker toutes les valeurs du type source, la conversion est implicite.</span><span class="sxs-lookup"><span data-stu-id="aec05-158">If the destination type can store all values of the source type, the conversion is implicit.</span></span> <span data-ttu-id="aec05-159">Sinon, vous devez utiliser [l’opérateur `()` de distribution](../operators/type-testing-and-cast.md#cast-operator-) pour invoquer une conversion explicite.</span><span class="sxs-lookup"><span data-stu-id="aec05-159">Otherwise, you need to use the [cast operator `()`](../operators/type-testing-and-cast.md#cast-operator-) to invoke an explicit conversion.</span></span> <span data-ttu-id="aec05-160">Pour plus d’informations, voir [conversions numériques intégrées](numeric-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="aec05-160">For more information, see [Built-in numeric conversions](numeric-conversions.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="aec05-161">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="aec05-161">C# language specification</span></span>

<span data-ttu-id="aec05-162">Pour plus d’informations, consultez les sections suivantes de la [spécification du langage C#](~/_csharplang/spec/introduction.md) :</span><span class="sxs-lookup"><span data-stu-id="aec05-162">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="aec05-163">Types intégraux</span><span class="sxs-lookup"><span data-stu-id="aec05-163">Integral types</span></span>](~/_csharplang/spec/types.md#integral-types)
- [<span data-ttu-id="aec05-164">Littéraux d'entier</span><span class="sxs-lookup"><span data-stu-id="aec05-164">Integer literals</span></span>](~/_csharplang/spec/lexical-structure.md#integer-literals)

## <a name="see-also"></a><span data-ttu-id="aec05-165">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aec05-165">See also</span></span>

- [<span data-ttu-id="aec05-166">Référence C#</span><span class="sxs-lookup"><span data-stu-id="aec05-166">C# reference</span></span>](../index.md)
- [<span data-ttu-id="aec05-167">Types de valeur</span><span class="sxs-lookup"><span data-stu-id="aec05-167">Value types</span></span>](value-types.md)
- [<span data-ttu-id="aec05-168">Types virgule flottante</span><span class="sxs-lookup"><span data-stu-id="aec05-168">Floating-point types</span></span>](floating-point-numeric-types.md)
- [<span data-ttu-id="aec05-169">Chaînes de format numérique standard</span><span class="sxs-lookup"><span data-stu-id="aec05-169">Standard numeric format strings</span></span>](../../../standard/base-types/standard-numeric-format-strings.md)
- [<span data-ttu-id="aec05-170">Valeurs numériques dans .NET</span><span class="sxs-lookup"><span data-stu-id="aec05-170">Numerics in .NET</span></span>](../../../standard/numerics.md)
