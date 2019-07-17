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
ms.openlocfilehash: 0a1ed01d9e6cb86ea177e8b947627f9dc02eedae
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67744216"
---
# <a name="integral-numeric-types--c-reference"></a><span data-ttu-id="1b90e-103">Types numériques intégraux (référence C#)</span><span class="sxs-lookup"><span data-stu-id="1b90e-103">Integral numeric types  (C# reference)</span></span>

<span data-ttu-id="1b90e-104">Les **types numériques intégraux** sont un sous-ensemble des **types simples** et peuvent être initialisés avec des [*littéraux*](#integral-literals).</span><span class="sxs-lookup"><span data-stu-id="1b90e-104">The **integral numeric types** are a subset of the **simple types** and can be initialized with [*literals*](#integral-literals).</span></span> <span data-ttu-id="1b90e-105">Tous les types intégraux sont également des types valeur.</span><span class="sxs-lookup"><span data-stu-id="1b90e-105">All integral types are also value types.</span></span>

<span data-ttu-id="1b90e-106">Tous les types numériques intégraux prennent en charge les opérateurs [arithmétiques](../operators/arithmetic-operators.md), les opérateurs [logiques au niveau du bit](../operators/bitwise-and-shift-operators.md), ainsi que les opérateurs [de comparaison et d’égalité](../operators/equality-operators.md).</span><span class="sxs-lookup"><span data-stu-id="1b90e-106">All integral numeric types support [arithmetic](../operators/arithmetic-operators.md), [bitwise logical](../operators/bitwise-and-shift-operators.md), [comparison, and equality](../operators/equality-operators.md) operators.</span></span>

## <a name="sizes-and-ranges"></a><span data-ttu-id="1b90e-107">Tailles et plages</span><span class="sxs-lookup"><span data-stu-id="1b90e-107">Sizes and ranges</span></span>

<span data-ttu-id="1b90e-108">Le tableau suivant indique les tailles et les plages des types intégraux :</span><span class="sxs-lookup"><span data-stu-id="1b90e-108">The following table shows the sizes and ranges of the integral types:</span></span>

|<span data-ttu-id="1b90e-109">Type</span><span class="sxs-lookup"><span data-stu-id="1b90e-109">Type</span></span>|<span data-ttu-id="1b90e-110">Plage</span><span class="sxs-lookup"><span data-stu-id="1b90e-110">Range</span></span>|<span data-ttu-id="1b90e-111">Size</span><span class="sxs-lookup"><span data-stu-id="1b90e-111">Size</span></span>|  
|----------|-----------|----------|  
|`sbyte`|<span data-ttu-id="1b90e-112">-128 à 127</span><span class="sxs-lookup"><span data-stu-id="1b90e-112">-128 to 127</span></span>|<span data-ttu-id="1b90e-113">Entier 8 bits signé</span><span class="sxs-lookup"><span data-stu-id="1b90e-113">Signed 8-bit integer</span></span>|  
|`byte`|<span data-ttu-id="1b90e-114">0 à 255</span><span class="sxs-lookup"><span data-stu-id="1b90e-114">0 to 255</span></span>|<span data-ttu-id="1b90e-115">Entier 8 bits non signé</span><span class="sxs-lookup"><span data-stu-id="1b90e-115">Unsigned 8-bit integer</span></span>|  
|`short`|<span data-ttu-id="1b90e-116">de -32 768 à 32 767</span><span class="sxs-lookup"><span data-stu-id="1b90e-116">-32,768 to 32,767</span></span>|<span data-ttu-id="1b90e-117">Entier 16 bits signé</span><span class="sxs-lookup"><span data-stu-id="1b90e-117">Signed 16-bit integer</span></span>|  
|`ushort`|<span data-ttu-id="1b90e-118">0 à 65 535</span><span class="sxs-lookup"><span data-stu-id="1b90e-118">0 to 65,535</span></span>|<span data-ttu-id="1b90e-119">Entier 16 bits non signé</span><span class="sxs-lookup"><span data-stu-id="1b90e-119">Unsigned 16-bit integer</span></span>|  
|`int`|<span data-ttu-id="1b90e-120">-2,147,483,648 en 2,147,483,647</span><span class="sxs-lookup"><span data-stu-id="1b90e-120">-2,147,483,648 to 2,147,483,647</span></span>|<span data-ttu-id="1b90e-121">Entier 32 bits signé</span><span class="sxs-lookup"><span data-stu-id="1b90e-121">Signed 32-bit integer</span></span>|  
|`uint`|<span data-ttu-id="1b90e-122">de 0 à 4 294 967 295</span><span class="sxs-lookup"><span data-stu-id="1b90e-122">0 to 4,294,967,295</span></span>|<span data-ttu-id="1b90e-123">Entier 32 bits non signé</span><span class="sxs-lookup"><span data-stu-id="1b90e-123">Unsigned 32-bit integer</span></span>|  
|`long`|<span data-ttu-id="1b90e-124">-9 223 372 036 854 775 808 à 9 223 372 036 854 775 807</span><span class="sxs-lookup"><span data-stu-id="1b90e-124">-9,223,372,036,854,775,808 to 9,223,372,036,854,775,807</span></span>|<span data-ttu-id="1b90e-125">Entier 64 bits signé</span><span class="sxs-lookup"><span data-stu-id="1b90e-125">Signed 64-bit integer</span></span>|  
|`ulong`|<span data-ttu-id="1b90e-126">de 0 à 18 446 744 073 709 551 615</span><span class="sxs-lookup"><span data-stu-id="1b90e-126">0 to 18,446,744,073,709,551,615</span></span>|<span data-ttu-id="1b90e-127">Entier 64 bits non signé</span><span class="sxs-lookup"><span data-stu-id="1b90e-127">Unsigned 64-bit integer</span></span>|  

<span data-ttu-id="1b90e-128">`0` est la valeur par défaut de tous les types intégraux.</span><span class="sxs-lookup"><span data-stu-id="1b90e-128">The default value for all integral types is `0`.</span></span> <span data-ttu-id="1b90e-129">Chaque type intégral a des constantes nommées `MinValue` et `MaxValue` correspondant à la valeur minimale et à la valeur maximale.</span><span class="sxs-lookup"><span data-stu-id="1b90e-129">Each of the integral types has constants named `MinValue` and `MaxValue` for the minimum and maximum value for that type.</span></span>

<span data-ttu-id="1b90e-130">Utilisez la structure <xref:System.Numerics.BigInteger?displayProperty=nameWithType> pour représenter un entier signé sans limites supérieures ou inférieures.</span><span class="sxs-lookup"><span data-stu-id="1b90e-130">Use the <xref:System.Numerics.BigInteger?displayProperty=nameWithType> structure to represent a signed integer with no upper or lower bounds.</span></span>

## <a name="integral-literals"></a><span data-ttu-id="1b90e-131">Littéraux intégraux</span><span class="sxs-lookup"><span data-stu-id="1b90e-131">Integral literals</span></span>

<span data-ttu-id="1b90e-132">Vous pouvez spécifier les littéraux intégraux en tant que *littéraux décimaux*, *littéraux hexadécimaux* ou *littéraux binaires*.</span><span class="sxs-lookup"><span data-stu-id="1b90e-132">Integral literals can be specified as *decimal literals*, *hexadecimal literals*, or *binary literals*.</span></span> <span data-ttu-id="1b90e-133">Voici un exemple de chacun de ces littéraux :</span><span class="sxs-lookup"><span data-stu-id="1b90e-133">An example of each is shown below:</span></span>

```csharp
var decimalLiteral = 42;
var hexLiteral = 0x2A;
var binaryLiteral = 0b_0010_1010;
```

<span data-ttu-id="1b90e-134">Les littéraux décimaux ne nécessitent aucun préfixe.</span><span class="sxs-lookup"><span data-stu-id="1b90e-134">Decimal literals don't require any prefix.</span></span> <span data-ttu-id="1b90e-135">Les préfixes `x` ou `X` correspondent à un *littéral hexadécimal*.</span><span class="sxs-lookup"><span data-stu-id="1b90e-135">The `x` or `X` prefix signifies a *hexadecimal literal*.</span></span> <span data-ttu-id="1b90e-136">Les préfixes `b` ou `B` correspondent à un *littéral binaire*.</span><span class="sxs-lookup"><span data-stu-id="1b90e-136">The `b` or `B` prefix signifies a *binary literal*.</span></span> <span data-ttu-id="1b90e-137">La déclaration de `binaryLiteral` illustre l’utilisation de `_` comme un *séparateur numérique*.</span><span class="sxs-lookup"><span data-stu-id="1b90e-137">The declaration of `binaryLiteral` demonstrates the use of `_` as a *digit separator*.</span></span> <span data-ttu-id="1b90e-138">Vous pouvez aussi utiliser le séparateur numérique avec tous les littéraux numériques.</span><span class="sxs-lookup"><span data-stu-id="1b90e-138">The digit separator can be used with all numeric literals.</span></span> <span data-ttu-id="1b90e-139">Les littéraux binaires et le séparateur numérique `_` sont pris en charge dans C# 7.0.</span><span class="sxs-lookup"><span data-stu-id="1b90e-139">Binary literals and the digit separator `_` are supported starting with C# 7.0.</span></span>

### <a name="literal-suffixes"></a><span data-ttu-id="1b90e-140">Suffixes littéraux</span><span class="sxs-lookup"><span data-stu-id="1b90e-140">Literal suffixes</span></span> 

<span data-ttu-id="1b90e-141">Les suffixes `l` ou `L` indiquent que le littéral intégral doit être de type `long`.</span><span class="sxs-lookup"><span data-stu-id="1b90e-141">The `l` or `L` suffix specifies that the integral literal should be of the `long` type.</span></span> <span data-ttu-id="1b90e-142">Les suffixes `ul` et `UL` spécifient le type `ulong`.</span><span class="sxs-lookup"><span data-stu-id="1b90e-142">The `ul` or `UL` suffix specifies the `ulong` type.</span></span> <span data-ttu-id="1b90e-143">Si le suffixe `L` est utilisé sur un littéral qui est supérieur à 9 223 372 036 854 775 807 (la valeur maximale de `long`), la valeur est convertie vers le type `ulong`.</span><span class="sxs-lookup"><span data-stu-id="1b90e-143">If the `L` suffix is used on a literal that is greater than 9,223,372,036,854,775,807 (the maximum value of `long`), the value is converted to the `ulong` type.</span></span> <span data-ttu-id="1b90e-144">Si la valeur représentée par un littéral entier dépasse <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, une erreur de compilation [CS1021](../../misc/cs1021.md) se produit.</span><span class="sxs-lookup"><span data-stu-id="1b90e-144">If the value represented by an integral literal exceeds <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, a compiler error [CS1021](../../misc/cs1021.md) occurs.</span></span> 

> [!NOTE]
> <span data-ttu-id="1b90e-145">Vous pouvez utiliser la lettre minuscule « l » comme suffixe.</span><span class="sxs-lookup"><span data-stu-id="1b90e-145">You can use the lowercase letter "l" as a suffix.</span></span> <span data-ttu-id="1b90e-146">Toutefois, ceci génère un avertissement du compilateur, car la lettre « l » peut être facilement confondue avec le chiffre « 1 ».</span><span class="sxs-lookup"><span data-stu-id="1b90e-146">However, this generates a compiler warning because the letter "l" is easily confused with the digit "1."</span></span> <span data-ttu-id="1b90e-147">Utilisez « L » pour plus de clarté.</span><span class="sxs-lookup"><span data-stu-id="1b90e-147">Use "L" for clarity.</span></span>

### <a name="type-of-an-integral-literal"></a><span data-ttu-id="1b90e-148">Type d’un littéral intégral</span><span class="sxs-lookup"><span data-stu-id="1b90e-148">Type of an integral literal</span></span>

<span data-ttu-id="1b90e-149">Quand un littéral intégral n’a pas de suffixe, son type est le premier des types suivants dans lesquels sa valeur peut être représentée :</span><span class="sxs-lookup"><span data-stu-id="1b90e-149">If an integral literal has no suffix, its type is the first of the following types in which its value can be represented:</span></span>

1. `int`
1. `uint`
1. `long`
1. `ulong`

<span data-ttu-id="1b90e-150">Vous pouvez convertir un littéral intégral en un type ayant une plage plus petite que celle par défaut, à l’aide d’une affectation ou d’un cast :</span><span class="sxs-lookup"><span data-stu-id="1b90e-150">You can convert an integral literal to a type with a smaller range than the default using either an assignment or a cast:</span></span>

```csharp
byte byteVariable = 42; // type is byte
var signedByte = (sbyte)42; // type is sbyte.
```

<span data-ttu-id="1b90e-151">Vous pouvez convertir un littéral intégral en un type ayant une plage plus grande que celle par défaut, à l’aide d’une affectation, d’un cast ou d’un suffixe appliqué au littéral :</span><span class="sxs-lookup"><span data-stu-id="1b90e-151">You can convert an integral literal to a type with a larger range than the default using either assignment, a cast, or a suffix on the literal:</span></span>

```csharp
var unsignedLong = 42UL;
var longVariable = 42L;
ulong anotherUnsignedLong = 42;
var anotherLong = (long)42;
```

## <a name="conversions"></a><span data-ttu-id="1b90e-152">Conversions</span><span class="sxs-lookup"><span data-stu-id="1b90e-152">Conversions</span></span>

<span data-ttu-id="1b90e-153">Entre deux types intégraux, il existe une conversion implicite (appelée *conversion étendue*) où le type de destination peut stocker toutes les valeurs du type source.</span><span class="sxs-lookup"><span data-stu-id="1b90e-153">There's an implicit conversion (called a *widening conversion*) between any two integral types where the destination type can store all values of the source type.</span></span> <span data-ttu-id="1b90e-154">Par exemple, il existe une conversion implicite de `int` vers `long`, car la plage de valeurs `int` est un sous-ensemble de `long`.</span><span class="sxs-lookup"><span data-stu-id="1b90e-154">For example, there's an implicit conversion from `int` to `long` because the range of `int` values is a proper subset of `long`.</span></span> <span data-ttu-id="1b90e-155">Il existe des conversions implicites entre un type intégral non signé plus petit et un type intégral signé plus grand.</span><span class="sxs-lookup"><span data-stu-id="1b90e-155">There are implicit conversions from a smaller unsigned integral type to a larger signed integral type.</span></span> <span data-ttu-id="1b90e-156">Il existe également une conversion implicite entre un type intégral et n’importe quel type à virgule flottante.</span><span class="sxs-lookup"><span data-stu-id="1b90e-156">There's also an implicit conversion from any integral type to any floating-point type.</span></span>  <span data-ttu-id="1b90e-157">Il existe une conversion implicite entre un type intégral signé et n’importe quel type intégral non signé.</span><span class="sxs-lookup"><span data-stu-id="1b90e-157">There's no implicit conversion from any signed integral type to any unsigned integral type.</span></span>

<span data-ttu-id="1b90e-158">Vous devez utiliser un cast explicite pour convertir un type intégral en un autre type intégral, lorsqu’une conversion implicite n’est pas définie entre le type source et le type de destination.</span><span class="sxs-lookup"><span data-stu-id="1b90e-158">You must use an explicit cast to convert one integral type to another integral type when an implicit conversion is not defined from the source type to the destination type.</span></span> <span data-ttu-id="1b90e-159">C’est ce qu’on appelle une *conversion restrictive*.</span><span class="sxs-lookup"><span data-stu-id="1b90e-159">This is called a *narrowing conversion*.</span></span> <span data-ttu-id="1b90e-160">Un scénario explicite est nécessaire, car la conversion peut entraîner une perte de données.</span><span class="sxs-lookup"><span data-stu-id="1b90e-160">The explicit case is required because the conversion can result in data loss.</span></span>

## <a name="see-also"></a><span data-ttu-id="1b90e-161">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1b90e-161">See also</span></span>

- [<span data-ttu-id="1b90e-162">Spécification du langage C# - Types intégraux</span><span class="sxs-lookup"><span data-stu-id="1b90e-162">C# language specification - Integral types</span></span>](~/_csharplang/spec/types.md#integral-types)
- [<span data-ttu-id="1b90e-163">Informations de référence sur C#</span><span class="sxs-lookup"><span data-stu-id="1b90e-163">C# reference</span></span>](../index.md)
- [<span data-ttu-id="1b90e-164">Types virgule flottante</span><span class="sxs-lookup"><span data-stu-id="1b90e-164">Floating-point types</span></span>](floating-point-numeric-types.md)
- [<span data-ttu-id="1b90e-165">Tableau des valeurs par défaut</span><span class="sxs-lookup"><span data-stu-id="1b90e-165">Default values table</span></span>](../keywords/default-values-table.md)
- [<span data-ttu-id="1b90e-166">Tableau des formats des résultats numériques</span><span class="sxs-lookup"><span data-stu-id="1b90e-166">Formatting numeric results table</span></span>](../keywords/formatting-numeric-results-table.md)
- [<span data-ttu-id="1b90e-167">Tableaux des types intégrés</span><span class="sxs-lookup"><span data-stu-id="1b90e-167">Built-in types table</span></span>](../keywords/built-in-types-table.md)
- [<span data-ttu-id="1b90e-168">Valeurs numériques dans .NET</span><span class="sxs-lookup"><span data-stu-id="1b90e-168">Numerics in .NET</span></span>](../../../standard/numerics.md)
- <xref:System.Byte?displayProperty=nameWithType>
- <xref:System.SByte?displayProperty=nameWithType>
- <xref:System.Int16?displayProperty=nameWithType>
- <xref:System.UInt16?displayProperty=nameWithType>
- <xref:System.Int32?displayProperty=nameWithType>
- <xref:System.UInt32?displayProperty=nameWithType>
- <xref:System.Int64?displayProperty=nameWithType>
- <xref:System.UInt64?displayProperty=nameWithType>
