---
title: Types numériques intégraux - Référence C#
description: Découvrez la plage, la taille de stockage et les différentes utilisations associés à chacun des types numériques intégraux.
ms.date: 06/25/2019
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
ms.openlocfilehash: dfb1298abaff0cfe8eae7536f94511a30012a4a9
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68236078"
---
# <a name="integral-numeric-types--c-reference"></a><span data-ttu-id="39bc5-103">Types numériques intégraux (référence C#)</span><span class="sxs-lookup"><span data-stu-id="39bc5-103">Integral numeric types  (C# reference)</span></span>

<span data-ttu-id="39bc5-104">Les **types numériques intégraux** sont un sous-ensemble des **types simples** et peuvent être initialisés avec des [*littéraux*](#integral-literals).</span><span class="sxs-lookup"><span data-stu-id="39bc5-104">The **integral numeric types** are a subset of the **simple types** and can be initialized with [*literals*](#integral-literals).</span></span> <span data-ttu-id="39bc5-105">Tous les types intégraux sont également des types valeur.</span><span class="sxs-lookup"><span data-stu-id="39bc5-105">All integral types are also value types.</span></span> <span data-ttu-id="39bc5-106">Tous les types numériques intégraux prennent en charge les opérateurs [arithmétiques](../operators/arithmetic-operators.md), les opérateurs [logiques au niveau du bit](../operators/bitwise-and-shift-operators.md), ainsi que les opérateurs [de comparaison et d’égalité](../operators/equality-operators.md).</span><span class="sxs-lookup"><span data-stu-id="39bc5-106">All integral numeric types support [arithmetic](../operators/arithmetic-operators.md), [bitwise logical](../operators/bitwise-and-shift-operators.md), [comparison, and equality](../operators/equality-operators.md) operators.</span></span>

## <a name="characteristics-of-the-integral-types"></a><span data-ttu-id="39bc5-107">Caractéristiques des types intégraux</span><span class="sxs-lookup"><span data-stu-id="39bc5-107">Characteristics of the integral types</span></span>

<span data-ttu-id="39bc5-108">C# prend en charge les types intégraux prédéfinis suivants :</span><span class="sxs-lookup"><span data-stu-id="39bc5-108">C# supports the following predefined integral types:</span></span>

|<span data-ttu-id="39bc5-109">C# type/mot clé</span><span class="sxs-lookup"><span data-stu-id="39bc5-109">C# type/keyword</span></span>|<span data-ttu-id="39bc5-110">Plage</span><span class="sxs-lookup"><span data-stu-id="39bc5-110">Range</span></span>|<span data-ttu-id="39bc5-111">Size</span><span class="sxs-lookup"><span data-stu-id="39bc5-111">Size</span></span>|<span data-ttu-id="39bc5-112">Type .NET</span><span class="sxs-lookup"><span data-stu-id="39bc5-112">.NET type</span></span>|
|----------|-----------|----------|-------------|
|`sbyte`|<span data-ttu-id="39bc5-113">-128 à 127</span><span class="sxs-lookup"><span data-stu-id="39bc5-113">-128 to 127</span></span>|<span data-ttu-id="39bc5-114">Entier 8 bits signé</span><span class="sxs-lookup"><span data-stu-id="39bc5-114">Signed 8-bit integer</span></span>|<xref:System.SByte?displayProperty=nameWithType>|
|`byte`|<span data-ttu-id="39bc5-115">0 à 255</span><span class="sxs-lookup"><span data-stu-id="39bc5-115">0 to 255</span></span>|<span data-ttu-id="39bc5-116">Entier 8 bits non signé</span><span class="sxs-lookup"><span data-stu-id="39bc5-116">Unsigned 8-bit integer</span></span>|<xref:System.Byte?displayProperty=nameWithType>|
|`short`|<span data-ttu-id="39bc5-117">de -32 768 à 32 767</span><span class="sxs-lookup"><span data-stu-id="39bc5-117">-32,768 to 32,767</span></span>|<span data-ttu-id="39bc5-118">Entier 16 bits signé</span><span class="sxs-lookup"><span data-stu-id="39bc5-118">Signed 16-bit integer</span></span>|<xref:System.Int16?displayProperty=nameWithType>|
|`ushort`|<span data-ttu-id="39bc5-119">0 à 65 535</span><span class="sxs-lookup"><span data-stu-id="39bc5-119">0 to 65,535</span></span>|<span data-ttu-id="39bc5-120">Entier 16 bits non signé</span><span class="sxs-lookup"><span data-stu-id="39bc5-120">Unsigned 16-bit integer</span></span>|<xref:System.UInt16?displayProperty=nameWithType>|
|`int`|<span data-ttu-id="39bc5-121">-2,147,483,648 en 2,147,483,647</span><span class="sxs-lookup"><span data-stu-id="39bc5-121">-2,147,483,648 to 2,147,483,647</span></span>|<span data-ttu-id="39bc5-122">Entier 32 bits signé</span><span class="sxs-lookup"><span data-stu-id="39bc5-122">Signed 32-bit integer</span></span>|<xref:System.Int32?displayProperty=nameWithType>|
|`uint`|<span data-ttu-id="39bc5-123">de 0 à 4 294 967 295</span><span class="sxs-lookup"><span data-stu-id="39bc5-123">0 to 4,294,967,295</span></span>|<span data-ttu-id="39bc5-124">Entier 32 bits non signé</span><span class="sxs-lookup"><span data-stu-id="39bc5-124">Unsigned 32-bit integer</span></span>|<xref:System.UInt32?displayProperty=nameWithType>|
|`long`|<span data-ttu-id="39bc5-125">-9 223 372 036 854 775 808 à 9 223 372 036 854 775 807</span><span class="sxs-lookup"><span data-stu-id="39bc5-125">-9,223,372,036,854,775,808 to 9,223,372,036,854,775,807</span></span>|<span data-ttu-id="39bc5-126">Entier 64 bits signé</span><span class="sxs-lookup"><span data-stu-id="39bc5-126">Signed 64-bit integer</span></span>|<xref:System.Int64?displayProperty=nameWithType>|
|`ulong`|<span data-ttu-id="39bc5-127">de 0 à 18 446 744 073 709 551 615</span><span class="sxs-lookup"><span data-stu-id="39bc5-127">0 to 18,446,744,073,709,551,615</span></span>|<span data-ttu-id="39bc5-128">Entier 64 bits non signé</span><span class="sxs-lookup"><span data-stu-id="39bc5-128">Unsigned 64-bit integer</span></span>|<xref:System.UInt64?displayProperty=nameWithType>|

<span data-ttu-id="39bc5-129">Dans le tableau précédent, chaque mot clé de type C# de la colonne la plus à gauche est un alias pour le type .NET correspondant.</span><span class="sxs-lookup"><span data-stu-id="39bc5-129">In the preceding table, each C# type keyword from the leftmost column is an alias for the corresponding .NET type.</span></span> <span data-ttu-id="39bc5-130">Ils sont interchangeables.</span><span class="sxs-lookup"><span data-stu-id="39bc5-130">They are interchangeable.</span></span> <span data-ttu-id="39bc5-131">Par exemple, les déclarations suivantes déclarent des variables du même type :</span><span class="sxs-lookup"><span data-stu-id="39bc5-131">For example, the following declarations declare variables of the same type:</span></span>

```csharp
int a = 123;
System.Int32 b = 123;
```

<span data-ttu-id="39bc5-132">La valeur par défaut pour chaque type intégral est zéro, `0`.</span><span class="sxs-lookup"><span data-stu-id="39bc5-132">The default value of each integral type is zero, `0`.</span></span> <span data-ttu-id="39bc5-133">Chacun des types intégraux a les constantes `MinValue` et `MaxValue` qui fournissent la valeur minimale et maximale de ce type.</span><span class="sxs-lookup"><span data-stu-id="39bc5-133">Each of the integral types has the `MinValue` and `MaxValue` constants that provide the minimum and maximum value of that type.</span></span>

<span data-ttu-id="39bc5-134">Utilisez la structure <xref:System.Numerics.BigInteger?displayProperty=nameWithType> pour représenter un entier signé sans limites supérieures ou inférieures.</span><span class="sxs-lookup"><span data-stu-id="39bc5-134">Use the <xref:System.Numerics.BigInteger?displayProperty=nameWithType> structure to represent a signed integer with no upper or lower bounds.</span></span>

## <a name="integral-literals"></a><span data-ttu-id="39bc5-135">Littéraux intégraux</span><span class="sxs-lookup"><span data-stu-id="39bc5-135">Integral literals</span></span>

<span data-ttu-id="39bc5-136">Vous pouvez spécifier les littéraux intégraux en tant que *littéraux décimaux*, *littéraux hexadécimaux* ou *littéraux binaires*.</span><span class="sxs-lookup"><span data-stu-id="39bc5-136">Integral literals can be specified as *decimal literals*, *hexadecimal literals*, or *binary literals*.</span></span> <span data-ttu-id="39bc5-137">Voici un exemple de chacun de ces littéraux :</span><span class="sxs-lookup"><span data-stu-id="39bc5-137">An example of each is shown below:</span></span>

```csharp
var decimalLiteral = 42;
var hexLiteral = 0x2A;
var binaryLiteral = 0b_0010_1010;
```

<span data-ttu-id="39bc5-138">Les littéraux décimaux ne nécessitent aucun préfixe.</span><span class="sxs-lookup"><span data-stu-id="39bc5-138">Decimal literals don't require any prefix.</span></span> <span data-ttu-id="39bc5-139">Les préfixes `x` ou `X` correspondent à un *littéral hexadécimal*.</span><span class="sxs-lookup"><span data-stu-id="39bc5-139">The `x` or `X` prefix signifies a *hexadecimal literal*.</span></span> <span data-ttu-id="39bc5-140">Les préfixes `b` ou `B` correspondent à un *littéral binaire*.</span><span class="sxs-lookup"><span data-stu-id="39bc5-140">The `b` or `B` prefix signifies a *binary literal*.</span></span> <span data-ttu-id="39bc5-141">La déclaration de `binaryLiteral` illustre l’utilisation de `_` comme un *séparateur numérique*.</span><span class="sxs-lookup"><span data-stu-id="39bc5-141">The declaration of `binaryLiteral` demonstrates the use of `_` as a *digit separator*.</span></span> <span data-ttu-id="39bc5-142">Vous pouvez aussi utiliser le séparateur numérique avec tous les littéraux numériques.</span><span class="sxs-lookup"><span data-stu-id="39bc5-142">The digit separator can be used with all numeric literals.</span></span> <span data-ttu-id="39bc5-143">Les littéraux binaires et le séparateur numérique `_` sont pris en charge dans C# 7.0.</span><span class="sxs-lookup"><span data-stu-id="39bc5-143">Binary literals and the digit separator `_` are supported starting with C# 7.0.</span></span>

### <a name="literal-suffixes"></a><span data-ttu-id="39bc5-144">Suffixes littéraux</span><span class="sxs-lookup"><span data-stu-id="39bc5-144">Literal suffixes</span></span>

<span data-ttu-id="39bc5-145">Les suffixes `l` ou `L` indiquent que le littéral intégral doit être de type `long`.</span><span class="sxs-lookup"><span data-stu-id="39bc5-145">The `l` or `L` suffix specifies that the integral literal should be of the `long` type.</span></span> <span data-ttu-id="39bc5-146">Les suffixes `ul` et `UL` spécifient le type `ulong`.</span><span class="sxs-lookup"><span data-stu-id="39bc5-146">The `ul` or `UL` suffix specifies the `ulong` type.</span></span> <span data-ttu-id="39bc5-147">Si le suffixe `L` est utilisé sur un littéral qui est supérieur à 9 223 372 036 854 775 807 (la valeur maximale de `long`), la valeur est convertie vers le type `ulong`.</span><span class="sxs-lookup"><span data-stu-id="39bc5-147">If the `L` suffix is used on a literal that is greater than 9,223,372,036,854,775,807 (the maximum value of `long`), the value is converted to the `ulong` type.</span></span> <span data-ttu-id="39bc5-148">Si la valeur représentée par un littéral entier dépasse <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, une erreur de compilation [CS1021](../../misc/cs1021.md) se produit.</span><span class="sxs-lookup"><span data-stu-id="39bc5-148">If the value represented by an integral literal exceeds <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, a compiler error [CS1021](../../misc/cs1021.md) occurs.</span></span> 

> [!NOTE]
> <span data-ttu-id="39bc5-149">Vous pouvez utiliser la lettre minuscule « l » comme suffixe.</span><span class="sxs-lookup"><span data-stu-id="39bc5-149">You can use the lowercase letter "l" as a suffix.</span></span> <span data-ttu-id="39bc5-150">Toutefois, ceci génère un avertissement du compilateur, car la lettre « l » peut être facilement confondue avec le chiffre « 1 ».</span><span class="sxs-lookup"><span data-stu-id="39bc5-150">However, this generates a compiler warning because the letter "l" is easily confused with the digit "1."</span></span> <span data-ttu-id="39bc5-151">Utilisez « L » pour plus de clarté.</span><span class="sxs-lookup"><span data-stu-id="39bc5-151">Use "L" for clarity.</span></span>

### <a name="type-of-an-integral-literal"></a><span data-ttu-id="39bc5-152">Type d’un littéral intégral</span><span class="sxs-lookup"><span data-stu-id="39bc5-152">Type of an integral literal</span></span>

<span data-ttu-id="39bc5-153">Quand un littéral intégral n’a pas de suffixe, son type est le premier des types suivants dans lesquels sa valeur peut être représentée :</span><span class="sxs-lookup"><span data-stu-id="39bc5-153">If an integral literal has no suffix, its type is the first of the following types in which its value can be represented:</span></span>

1. `int`
1. `uint`
1. `long`
1. `ulong`

<span data-ttu-id="39bc5-154">Vous pouvez convertir un littéral intégral en un type ayant une plage plus petite que celle par défaut, à l’aide d’une affectation ou d’un cast :</span><span class="sxs-lookup"><span data-stu-id="39bc5-154">You can convert an integral literal to a type with a smaller range than the default using either an assignment or a cast:</span></span>

```csharp
byte byteVariable = 42; // type is byte
var signedByte = (sbyte)42; // type is sbyte.
```

<span data-ttu-id="39bc5-155">Vous pouvez convertir un littéral intégral en un type ayant une plage plus grande que celle par défaut, à l’aide d’une affectation, d’un cast ou d’un suffixe appliqué au littéral :</span><span class="sxs-lookup"><span data-stu-id="39bc5-155">You can convert an integral literal to a type with a larger range than the default using either assignment, a cast, or a suffix on the literal:</span></span>

```csharp
var unsignedLong = 42UL;
var longVariable = 42L;
ulong anotherUnsignedLong = 42;
var anotherLong = (long)42;
```

## <a name="conversions"></a><span data-ttu-id="39bc5-156">Conversions</span><span class="sxs-lookup"><span data-stu-id="39bc5-156">Conversions</span></span>

<span data-ttu-id="39bc5-157">Entre deux types intégraux, il existe une conversion implicite (appelée *conversion étendue*) où le type de destination peut stocker toutes les valeurs du type source.</span><span class="sxs-lookup"><span data-stu-id="39bc5-157">There's an implicit conversion (called a *widening conversion*) between any two integral types where the destination type can store all values of the source type.</span></span> <span data-ttu-id="39bc5-158">Par exemple, il existe une conversion implicite de `int` vers `long`, car la plage de valeurs `int` est un sous-ensemble de `long`.</span><span class="sxs-lookup"><span data-stu-id="39bc5-158">For example, there's an implicit conversion from `int` to `long` because the range of `int` values is a proper subset of `long`.</span></span> <span data-ttu-id="39bc5-159">Il existe des conversions implicites entre un type intégral non signé plus petit et un type intégral signé plus grand.</span><span class="sxs-lookup"><span data-stu-id="39bc5-159">There are implicit conversions from a smaller unsigned integral type to a larger signed integral type.</span></span> <span data-ttu-id="39bc5-160">Il existe également une conversion implicite entre un type intégral et n’importe quel type à virgule flottante.</span><span class="sxs-lookup"><span data-stu-id="39bc5-160">There's also an implicit conversion from any integral type to any floating-point type.</span></span>  <span data-ttu-id="39bc5-161">Il existe une conversion implicite entre un type intégral signé et n’importe quel type intégral non signé.</span><span class="sxs-lookup"><span data-stu-id="39bc5-161">There's no implicit conversion from any signed integral type to any unsigned integral type.</span></span>

<span data-ttu-id="39bc5-162">Vous devez utiliser un cast explicite pour convertir un type intégral en un autre type intégral, lorsqu’une conversion implicite n’est pas définie entre le type source et le type de destination.</span><span class="sxs-lookup"><span data-stu-id="39bc5-162">You must use an explicit cast to convert one integral type to another integral type when an implicit conversion is not defined from the source type to the destination type.</span></span> <span data-ttu-id="39bc5-163">C’est ce qu’on appelle une *conversion restrictive*.</span><span class="sxs-lookup"><span data-stu-id="39bc5-163">This is called a *narrowing conversion*.</span></span> <span data-ttu-id="39bc5-164">Un scénario explicite est nécessaire, car la conversion peut entraîner une perte de données.</span><span class="sxs-lookup"><span data-stu-id="39bc5-164">The explicit case is required because the conversion can result in data loss.</span></span>

## <a name="see-also"></a><span data-ttu-id="39bc5-165">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="39bc5-165">See also</span></span>

- [<span data-ttu-id="39bc5-166">Spécification du langage C# - Types intégraux</span><span class="sxs-lookup"><span data-stu-id="39bc5-166">C# language specification - Integral types</span></span>](~/_csharplang/spec/types.md#integral-types)
- [<span data-ttu-id="39bc5-167">Informations de référence sur C#</span><span class="sxs-lookup"><span data-stu-id="39bc5-167">C# reference</span></span>](../index.md)
- [<span data-ttu-id="39bc5-168">Types virgule flottante</span><span class="sxs-lookup"><span data-stu-id="39bc5-168">Floating-point types</span></span>](floating-point-numeric-types.md)
- [<span data-ttu-id="39bc5-169">Tableau des valeurs par défaut</span><span class="sxs-lookup"><span data-stu-id="39bc5-169">Default values table</span></span>](../keywords/default-values-table.md)
- [<span data-ttu-id="39bc5-170">Tableau des formats des résultats numériques</span><span class="sxs-lookup"><span data-stu-id="39bc5-170">Formatting numeric results table</span></span>](../keywords/formatting-numeric-results-table.md)
- [<span data-ttu-id="39bc5-171">Tableaux des types intégrés</span><span class="sxs-lookup"><span data-stu-id="39bc5-171">Built-in types table</span></span>](../keywords/built-in-types-table.md)
- [<span data-ttu-id="39bc5-172">Valeurs numériques dans .NET</span><span class="sxs-lookup"><span data-stu-id="39bc5-172">Numerics in .NET</span></span>](../../../standard/numerics.md)
