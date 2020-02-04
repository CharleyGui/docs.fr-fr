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
ms.openlocfilehash: 2fb4d7185ac85b29f2cc2d2e7a29e192f91a0868
ms.sourcegitcommit: 19014f9c081ca2ff19652ca12503828db8239d48
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/04/2020
ms.locfileid: "76980143"
---
# <a name="integral-numeric-types--c-reference"></a><span data-ttu-id="b3d8a-103">Types numériques intégraux (référence C#)</span><span class="sxs-lookup"><span data-stu-id="b3d8a-103">Integral numeric types  (C# reference)</span></span>

<span data-ttu-id="b3d8a-104">Les **types numériques intégraux** sont un sous-ensemble des **types simples** et peuvent être initialisés avec des [*littéraux*](#integer-literals).</span><span class="sxs-lookup"><span data-stu-id="b3d8a-104">The **integral numeric types** are a subset of the **simple types** and can be initialized with [*literals*](#integer-literals).</span></span> <span data-ttu-id="b3d8a-105">Tous les types intégraux sont également des types valeur.</span><span class="sxs-lookup"><span data-stu-id="b3d8a-105">All integral types are also value types.</span></span> <span data-ttu-id="b3d8a-106">Tous les types numériques intégraux prennent en charge les opérateurs [arithmétiques](../operators/arithmetic-operators.md), de comparaison [logique](../operators/bitwise-and-shift-operators.md), de [comparaison](../operators/comparison-operators.md)et d' [égalité](../operators/equality-operators.md) .</span><span class="sxs-lookup"><span data-stu-id="b3d8a-106">All integral numeric types support [arithmetic](../operators/arithmetic-operators.md), [bitwise logical](../operators/bitwise-and-shift-operators.md), [comparison](../operators/comparison-operators.md), and [equality](../operators/equality-operators.md) operators.</span></span>

## <a name="characteristics-of-the-integral-types"></a><span data-ttu-id="b3d8a-107">Caractéristiques des types intégraux</span><span class="sxs-lookup"><span data-stu-id="b3d8a-107">Characteristics of the integral types</span></span>

<span data-ttu-id="b3d8a-108">C# prend en charge les types intégraux prédéfinis suivants :</span><span class="sxs-lookup"><span data-stu-id="b3d8a-108">C# supports the following predefined integral types:</span></span>

|<span data-ttu-id="b3d8a-109">C# type/mot clé</span><span class="sxs-lookup"><span data-stu-id="b3d8a-109">C# type/keyword</span></span>|<span data-ttu-id="b3d8a-110">Range</span><span class="sxs-lookup"><span data-stu-id="b3d8a-110">Range</span></span>|<span data-ttu-id="b3d8a-111">Taille</span><span class="sxs-lookup"><span data-stu-id="b3d8a-111">Size</span></span>|<span data-ttu-id="b3d8a-112">Type .NET</span><span class="sxs-lookup"><span data-stu-id="b3d8a-112">.NET type</span></span>|
|----------|-----------|----------|-------------|
|`sbyte`|<span data-ttu-id="b3d8a-113">-128 à 127</span><span class="sxs-lookup"><span data-stu-id="b3d8a-113">-128 to 127</span></span>|<span data-ttu-id="b3d8a-114">Entier 8 bits signé</span><span class="sxs-lookup"><span data-stu-id="b3d8a-114">Signed 8-bit integer</span></span>|<xref:System.SByte?displayProperty=nameWithType>|
|`byte`|<span data-ttu-id="b3d8a-115">0 à 255</span><span class="sxs-lookup"><span data-stu-id="b3d8a-115">0 to 255</span></span>|<span data-ttu-id="b3d8a-116">Entier 8 bits non signé</span><span class="sxs-lookup"><span data-stu-id="b3d8a-116">Unsigned 8-bit integer</span></span>|<xref:System.Byte?displayProperty=nameWithType>|
|`short`|<span data-ttu-id="b3d8a-117">de -32 768 à 32 767</span><span class="sxs-lookup"><span data-stu-id="b3d8a-117">-32,768 to 32,767</span></span>|<span data-ttu-id="b3d8a-118">Entier 16 bits signé</span><span class="sxs-lookup"><span data-stu-id="b3d8a-118">Signed 16-bit integer</span></span>|<xref:System.Int16?displayProperty=nameWithType>|
|`ushort`|<span data-ttu-id="b3d8a-119">0 à 65 535</span><span class="sxs-lookup"><span data-stu-id="b3d8a-119">0 to 65,535</span></span>|<span data-ttu-id="b3d8a-120">Entier 16 bits non signé</span><span class="sxs-lookup"><span data-stu-id="b3d8a-120">Unsigned 16-bit integer</span></span>|<xref:System.UInt16?displayProperty=nameWithType>|
|`int`|<span data-ttu-id="b3d8a-121">-2,147,483,648 en 2,147,483,647</span><span class="sxs-lookup"><span data-stu-id="b3d8a-121">-2,147,483,648 to 2,147,483,647</span></span>|<span data-ttu-id="b3d8a-122">Entier 32 bits signé</span><span class="sxs-lookup"><span data-stu-id="b3d8a-122">Signed 32-bit integer</span></span>|<xref:System.Int32?displayProperty=nameWithType>|
|`uint`|<span data-ttu-id="b3d8a-123">de 0 à 4 294 967 295</span><span class="sxs-lookup"><span data-stu-id="b3d8a-123">0 to 4,294,967,295</span></span>|<span data-ttu-id="b3d8a-124">Entier 32 bits non signé</span><span class="sxs-lookup"><span data-stu-id="b3d8a-124">Unsigned 32-bit integer</span></span>|<xref:System.UInt32?displayProperty=nameWithType>|
|`long`|<span data-ttu-id="b3d8a-125">-9 223 372 036 854 775 808 à 9 223 372 036 854 775 807</span><span class="sxs-lookup"><span data-stu-id="b3d8a-125">-9,223,372,036,854,775,808 to 9,223,372,036,854,775,807</span></span>|<span data-ttu-id="b3d8a-126">Entier 64 bits signé</span><span class="sxs-lookup"><span data-stu-id="b3d8a-126">Signed 64-bit integer</span></span>|<xref:System.Int64?displayProperty=nameWithType>|
|`ulong`|<span data-ttu-id="b3d8a-127">de 0 à 18 446 744 073 709 551 615</span><span class="sxs-lookup"><span data-stu-id="b3d8a-127">0 to 18,446,744,073,709,551,615</span></span>|<span data-ttu-id="b3d8a-128">Entier 64 bits non signé</span><span class="sxs-lookup"><span data-stu-id="b3d8a-128">Unsigned 64-bit integer</span></span>|<xref:System.UInt64?displayProperty=nameWithType>|

<span data-ttu-id="b3d8a-129">Dans le tableau précédent, chaque mot clé de type C# de la colonne la plus à gauche est un alias pour le type .NET correspondant.</span><span class="sxs-lookup"><span data-stu-id="b3d8a-129">In the preceding table, each C# type keyword from the leftmost column is an alias for the corresponding .NET type.</span></span> <span data-ttu-id="b3d8a-130">Ils sont interchangeables.</span><span class="sxs-lookup"><span data-stu-id="b3d8a-130">They are interchangeable.</span></span> <span data-ttu-id="b3d8a-131">Par exemple, les déclarations suivantes déclarent des variables du même type :</span><span class="sxs-lookup"><span data-stu-id="b3d8a-131">For example, the following declarations declare variables of the same type:</span></span>

```csharp
int a = 123;
System.Int32 b = 123;
```

<span data-ttu-id="b3d8a-132">La valeur par défaut pour chaque type intégral est zéro, `0`.</span><span class="sxs-lookup"><span data-stu-id="b3d8a-132">The default value of each integral type is zero, `0`.</span></span> <span data-ttu-id="b3d8a-133">Chacun des types intégraux a les constantes `MinValue` et `MaxValue` qui fournissent la valeur minimale et maximale de ce type.</span><span class="sxs-lookup"><span data-stu-id="b3d8a-133">Each of the integral types has the `MinValue` and `MaxValue` constants that provide the minimum and maximum value of that type.</span></span>

<span data-ttu-id="b3d8a-134">Utilisez la structure <xref:System.Numerics.BigInteger?displayProperty=nameWithType> pour représenter un entier signé sans limites supérieures ou inférieures.</span><span class="sxs-lookup"><span data-stu-id="b3d8a-134">Use the <xref:System.Numerics.BigInteger?displayProperty=nameWithType> structure to represent a signed integer with no upper or lower bounds.</span></span>

## <a name="integer-literals"></a><span data-ttu-id="b3d8a-135">Littéraux d'entier</span><span class="sxs-lookup"><span data-stu-id="b3d8a-135">Integer literals</span></span>

<span data-ttu-id="b3d8a-136">Les littéraux entiers peuvent être</span><span class="sxs-lookup"><span data-stu-id="b3d8a-136">Integer literals can be</span></span>

- <span data-ttu-id="b3d8a-137">*Decimal*: sans préfixe</span><span class="sxs-lookup"><span data-stu-id="b3d8a-137">*decimal*: without any prefix</span></span>
- <span data-ttu-id="b3d8a-138">*hexadécimal*: avec le préfixe `0x` ou `0X`</span><span class="sxs-lookup"><span data-stu-id="b3d8a-138">*hexadecimal*: with the `0x` or `0X` prefix</span></span>
- <span data-ttu-id="b3d8a-139">*Binary*: avec le préfixe `0b` ou `0B` (disponible C# dans 7,0 et versions ultérieures)</span><span class="sxs-lookup"><span data-stu-id="b3d8a-139">*binary*: with the `0b` or `0B` prefix (available in C# 7.0 and later)</span></span>

<span data-ttu-id="b3d8a-140">Le code suivant illustre un exemple de chaque :</span><span class="sxs-lookup"><span data-stu-id="b3d8a-140">The following code demonstrates an example of each:</span></span>

```csharp
var decimalLiteral = 42;
var hexLiteral = 0x2A;
var binaryLiteral = 0b_0010_1010;
```

<span data-ttu-id="b3d8a-141">L’exemple précédent illustre également l’utilisation de `_` comme *séparateur de chiffres*, pris en charge à C# partir de 7,0.</span><span class="sxs-lookup"><span data-stu-id="b3d8a-141">The preceding example also shows the use of `_` as a *digit separator*, which is supported starting with C# 7.0.</span></span> <span data-ttu-id="b3d8a-142">Vous pouvez utiliser le séparateur de chiffres avec tous les types de littéraux numériques.</span><span class="sxs-lookup"><span data-stu-id="b3d8a-142">You can use the digit separator with all kinds of numeric literals.</span></span>

<span data-ttu-id="b3d8a-143">Le type d’un littéral entier est déterminé par son suffixe comme suit :</span><span class="sxs-lookup"><span data-stu-id="b3d8a-143">The type of an integer literal is determined by its suffix as follows:</span></span>

- <span data-ttu-id="b3d8a-144">Si le littéral n’a pas de suffixe, son type est le premier des types suivants dans lesquels sa valeur peut être représentée : `int`, `uint`, `long`, `ulong`.</span><span class="sxs-lookup"><span data-stu-id="b3d8a-144">If the literal has no suffix, its type is the first of the following types in which its value can be represented: `int`, `uint`, `long`, `ulong`.</span></span>
- <span data-ttu-id="b3d8a-145">Si le littéral est précédé d’un suffixe `U` ou `u`, son type est le premier des types suivants dans lesquels sa valeur peut être représentée : `uint`, `ulong`.</span><span class="sxs-lookup"><span data-stu-id="b3d8a-145">If the literal is suffixed by `U` or `u`, its type is the first of the following types in which its value can be represented: `uint`, `ulong`.</span></span>
- <span data-ttu-id="b3d8a-146">Si le littéral est précédé d’un suffixe `L` ou `l`, son type est le premier des types suivants dans lesquels sa valeur peut être représentée : `long`, `ulong`.</span><span class="sxs-lookup"><span data-stu-id="b3d8a-146">If the literal is suffixed by `L` or `l`, its type is the first of the following types in which its value can be represented: `long`, `ulong`.</span></span>

  > [!NOTE]
  > <span data-ttu-id="b3d8a-147">Vous pouvez utiliser la lettre minuscule `l` comme suffixe.</span><span class="sxs-lookup"><span data-stu-id="b3d8a-147">You can use the lowercase letter `l` as a suffix.</span></span> <span data-ttu-id="b3d8a-148">Toutefois, cela génère un avertissement du compilateur, car la lettre `l` peut être confondue avec le chiffre `1`.</span><span class="sxs-lookup"><span data-stu-id="b3d8a-148">However, this generates a compiler warning because the letter `l` can be confused with the digit `1`.</span></span> <span data-ttu-id="b3d8a-149">Utilisez `L` pour plus de clarté.</span><span class="sxs-lookup"><span data-stu-id="b3d8a-149">Use `L` for clarity.</span></span>

- <span data-ttu-id="b3d8a-150">Si le littéral est précédé d’un suffixe `UL`, `Ul`, `uL`, `ul`, `LU`, `Lu`, `lU`ou `lu`, son type est `ulong`.</span><span class="sxs-lookup"><span data-stu-id="b3d8a-150">If the literal is suffixed by `UL`, `Ul`, `uL`, `ul`, `LU`, `Lu`, `lU`, or `lu`, its type is `ulong`.</span></span>

<span data-ttu-id="b3d8a-151">Si la valeur représentée par un littéral entier dépasse <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, une erreur de compilation [CS1021](../../misc/cs1021.md) se produit.</span><span class="sxs-lookup"><span data-stu-id="b3d8a-151">If the value represented by an integer literal exceeds <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, a compiler error [CS1021](../../misc/cs1021.md) occurs.</span></span>

<span data-ttu-id="b3d8a-152">Si le type déterminé d’un littéral d’entier est `int` et que la valeur représentée par le littéral est comprise dans la plage du type de destination, la valeur peut être convertie implicitement en `sbyte`, `byte`, `short`, `ushort`, `uint`ou `ulong`:</span><span class="sxs-lookup"><span data-stu-id="b3d8a-152">If the determined type of an integer literal is `int` and the value represented by the literal is within the range of the destination type, the value can be implicitly converted to `sbyte`, `byte`, `short`, `ushort`, `uint`, or `ulong`:</span></span>

```csharp
byte a = 17;
byte b = 300;   // CS0031: Constant value '300' cannot be converted to a 'byte'
```

<span data-ttu-id="b3d8a-153">Comme le montre l’exemple précédent, si la valeur du littéral n’est pas comprise dans la plage du type de destination, une erreur de compilateur [CS0031](../../misc/cs0031.md) se produit.</span><span class="sxs-lookup"><span data-stu-id="b3d8a-153">As the preceding example shows, if the literal's value is not within the range of the destination type, a compiler error [CS0031](../../misc/cs0031.md) occurs.</span></span>

<span data-ttu-id="b3d8a-154">Vous pouvez également utiliser un cast pour convertir la valeur représentée par un littéral entier en type autre que le type déterminé du littéral :</span><span class="sxs-lookup"><span data-stu-id="b3d8a-154">You also can use a cast to convert the value represented by an integer literal to the type other than the determined type of the literal:</span></span>

```csharp
var signedByte = (sbyte)42;
var longVariable = (long)42;
```

## <a name="conversions"></a><span data-ttu-id="b3d8a-155">Conversions</span><span class="sxs-lookup"><span data-stu-id="b3d8a-155">Conversions</span></span>

<span data-ttu-id="b3d8a-156">Vous pouvez convertir n’importe quel type numérique intégral en tout autre type numérique intégral.</span><span class="sxs-lookup"><span data-stu-id="b3d8a-156">You can convert any integral numeric type to any other integral numeric type.</span></span> <span data-ttu-id="b3d8a-157">Si le type de destination peut stocker toutes les valeurs du type source, la conversion est implicite.</span><span class="sxs-lookup"><span data-stu-id="b3d8a-157">If the destination type can store all values of the source type, the conversion is implicit.</span></span> <span data-ttu-id="b3d8a-158">Dans le cas contraire, vous devez utiliser l' [opérateur de cast `()`](../operators/type-testing-and-cast.md#cast-operator-) pour appeler une conversion explicite.</span><span class="sxs-lookup"><span data-stu-id="b3d8a-158">Otherwise, you need to use the [cast operator `()`](../operators/type-testing-and-cast.md#cast-operator-) to invoke an explicit conversion.</span></span> <span data-ttu-id="b3d8a-159">Pour plus d’informations, consultez [conversions numériques intégrées](numeric-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="b3d8a-159">For more information, see [Built-in numeric conversions](numeric-conversions.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="b3d8a-160">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="b3d8a-160">C# language specification</span></span>

<span data-ttu-id="b3d8a-161">Pour plus d’informations, consultez les sections suivantes de la [spécification du langage C#](~/_csharplang/spec/introduction.md) :</span><span class="sxs-lookup"><span data-stu-id="b3d8a-161">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="b3d8a-162">Types intégraux</span><span class="sxs-lookup"><span data-stu-id="b3d8a-162">Integral types</span></span>](~/_csharplang/spec/types.md#integral-types)
- [<span data-ttu-id="b3d8a-163">Littéraux entiers</span><span class="sxs-lookup"><span data-stu-id="b3d8a-163">Integer literals</span></span>](~/_csharplang/spec/lexical-structure.md#integer-literals)

## <a name="see-also"></a><span data-ttu-id="b3d8a-164">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b3d8a-164">See also</span></span>

- [<span data-ttu-id="b3d8a-165">Informations de référence sur C#</span><span class="sxs-lookup"><span data-stu-id="b3d8a-165">C# reference</span></span>](../index.md)
- [<span data-ttu-id="b3d8a-166">Tableaux des types intégrés</span><span class="sxs-lookup"><span data-stu-id="b3d8a-166">Built-in types table</span></span>](../keywords/built-in-types-table.md)
- [<span data-ttu-id="b3d8a-167">Types virgule flottante</span><span class="sxs-lookup"><span data-stu-id="b3d8a-167">Floating-point types</span></span>](floating-point-numeric-types.md)
- [<span data-ttu-id="b3d8a-168">Chaînes de format numériques standard</span><span class="sxs-lookup"><span data-stu-id="b3d8a-168">Standard numeric format strings</span></span>](../../../standard/base-types/standard-numeric-format-strings.md)
- [<span data-ttu-id="b3d8a-169">Valeurs numériques dans .NET</span><span class="sxs-lookup"><span data-stu-id="b3d8a-169">Numerics in .NET</span></span>](../../../standard/numerics.md)
