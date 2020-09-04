---
description: 'En savoir plus sur le type de caractère intégré en C #'
title: type char-référence C#
ms.date: 05/11/2020
f1_keywords:
- char
- char_CSharpKeyword
helpviewer_keywords:
- char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
ms.openlocfilehash: 636e032ac22b48ebc471780ffa85148bf952cdd2
ms.sourcegitcommit: e7acba36517134238065e4d50bb4a1cfe47ebd06
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2020
ms.locfileid: "89465089"
---
# <a name="char-c-reference"></a><span data-ttu-id="73d44-103">Char (référence C#)</span><span class="sxs-lookup"><span data-stu-id="73d44-103">char (C# reference)</span></span>

<span data-ttu-id="73d44-104">Le `char` mot clé type est un alias pour le <xref:System.Char?displayProperty=nameWithType> type de structure .net qui représente un caractère Unicode UTF-16.</span><span class="sxs-lookup"><span data-stu-id="73d44-104">The `char` type keyword is an alias for the .NET <xref:System.Char?displayProperty=nameWithType> structure type that represents a Unicode UTF-16 character.</span></span>

|<span data-ttu-id="73d44-105">Type</span><span class="sxs-lookup"><span data-stu-id="73d44-105">Type</span></span>|<span data-ttu-id="73d44-106">Plage</span><span class="sxs-lookup"><span data-stu-id="73d44-106">Range</span></span>|<span data-ttu-id="73d44-107">Size</span><span class="sxs-lookup"><span data-stu-id="73d44-107">Size</span></span>|<span data-ttu-id="73d44-108">Type .NET</span><span class="sxs-lookup"><span data-stu-id="73d44-108">.NET type</span></span>|
|----------|-----------|----------|-------------------------|
|`char`|<span data-ttu-id="73d44-109">U+0000 à U+FFFF</span><span class="sxs-lookup"><span data-stu-id="73d44-109">U+0000 to U+FFFF</span></span>|<span data-ttu-id="73d44-110">16 bits</span><span class="sxs-lookup"><span data-stu-id="73d44-110">16 bit</span></span>|<xref:System.Char?displayProperty=nameWithType>|

<span data-ttu-id="73d44-111">La valeur par défaut du `char` type est `\0` , c’est-à-dire U + 0000.</span><span class="sxs-lookup"><span data-stu-id="73d44-111">The default value of the `char` type is `\0`, that is, U+0000.</span></span>

<span data-ttu-id="73d44-112">Le `char` type prend en charge les opérateurs de [comparaison](../operators/comparison-operators.md), d' [égalité](../operators/equality-operators.md), d' [incrémentation](../operators/arithmetic-operators.md#increment-operator-)et de [décrémentation](../operators/arithmetic-operators.md#decrement-operator---) .</span><span class="sxs-lookup"><span data-stu-id="73d44-112">The `char` type supports [comparison](../operators/comparison-operators.md), [equality](../operators/equality-operators.md), [increment](../operators/arithmetic-operators.md#increment-operator-), and [decrement](../operators/arithmetic-operators.md#decrement-operator---) operators.</span></span> <span data-ttu-id="73d44-113">En outre, pour les `char` opérandes, les opérateurs [logiques](../operators/bitwise-and-shift-operators.md) [arithmétiques](../operators/arithmetic-operators.md) et au niveau du bit effectuent une opération sur les codes de caractères correspondants et produisent le résultat du `int` type.</span><span class="sxs-lookup"><span data-stu-id="73d44-113">Moreover, for `char` operands, [arithmetic](../operators/arithmetic-operators.md) and [bitwise logical](../operators/bitwise-and-shift-operators.md) operators perform an operation on the corresponding character codes and produce the result of the `int` type.</span></span>

<span data-ttu-id="73d44-114">Le type [String](reference-types.md#the-string-type) représente du texte sous la forme d’une séquence de `char` valeurs.</span><span class="sxs-lookup"><span data-stu-id="73d44-114">The [string](reference-types.md#the-string-type) type represents text as a sequence of `char` values.</span></span>

## <a name="literals"></a><span data-ttu-id="73d44-115">Littéraux</span><span class="sxs-lookup"><span data-stu-id="73d44-115">Literals</span></span>

<span data-ttu-id="73d44-116">Vous pouvez spécifier une `char` valeur avec :</span><span class="sxs-lookup"><span data-stu-id="73d44-116">You can specify a `char` value with:</span></span>

- <span data-ttu-id="73d44-117">littéral de caractère.</span><span class="sxs-lookup"><span data-stu-id="73d44-117">a character literal.</span></span>
- <span data-ttu-id="73d44-118">séquence d’échappement Unicode, suivie de `\u` la représentation hexadécimale à quatre symboles d’un code de caractère.</span><span class="sxs-lookup"><span data-stu-id="73d44-118">a Unicode escape sequence, which is `\u` followed by the four-symbol hexadecimal representation of a character code.</span></span>
- <span data-ttu-id="73d44-119">séquence d’échappement hexadécimale, `\x` suivie de la représentation hexadécimale d’un code de caractère.</span><span class="sxs-lookup"><span data-stu-id="73d44-119">a hexadecimal escape sequence, which is `\x` followed by the hexadecimal representation of a character code.</span></span>

[!code-csharp-interactive[char literals](snippets/CharType.cs#Literals)]

<span data-ttu-id="73d44-120">Comme le montre l’exemple précédent, vous pouvez également effectuer un cast de la valeur d’un code de caractère dans la `char` valeur correspondante.</span><span class="sxs-lookup"><span data-stu-id="73d44-120">As the preceding example shows, you can also cast the value of a character code into the corresponding `char` value.</span></span>

> [!NOTE]
> <span data-ttu-id="73d44-121">Dans le cas d’une séquence d’échappement Unicode, vous devez spécifier les quatre chiffres hexadécimaux.</span><span class="sxs-lookup"><span data-stu-id="73d44-121">In the case of a Unicode escape sequence, you must specify all four hexadecimal digits.</span></span> <span data-ttu-id="73d44-122">Autrement dit, `\u006A` est une séquence d’échappement valide, tandis que `\u06A` et `\u6A` ne sont pas valides.</span><span class="sxs-lookup"><span data-stu-id="73d44-122">That is, `\u006A` is a valid escape sequence, while `\u06A` and `\u6A` are not valid.</span></span>
>
> <span data-ttu-id="73d44-123">Dans le cas d’une séquence d’échappement hexadécimale, vous pouvez omettre les zéros non significatifs.</span><span class="sxs-lookup"><span data-stu-id="73d44-123">In the case of a hexadecimal escape sequence, you can omit the leading zeros.</span></span> <span data-ttu-id="73d44-124">Autrement dit, les `\x006A` `\x06A` `\x6A` séquences d’échappement, et sont valides et correspondent au même caractère.</span><span class="sxs-lookup"><span data-stu-id="73d44-124">That is, the `\x006A`, `\x06A`, and `\x6A` escape sequences are valid and correspond to the same character.</span></span>

## <a name="conversions"></a><span data-ttu-id="73d44-125">Conversions</span><span class="sxs-lookup"><span data-stu-id="73d44-125">Conversions</span></span>

<span data-ttu-id="73d44-126">Le `char` type est implicitement convertible en types [intégraux](integral-numeric-types.md) suivants : `ushort` , `int` , `uint` , `long` et `ulong` .</span><span class="sxs-lookup"><span data-stu-id="73d44-126">The `char` type is implicitly convertible to the following [integral](integral-numeric-types.md) types: `ushort`, `int`, `uint`, `long`, and `ulong`.</span></span> <span data-ttu-id="73d44-127">Il est également implicitement convertible en types numériques à [virgule flottante](floating-point-numeric-types.md) intégrés : `float` , `double` et `decimal` .</span><span class="sxs-lookup"><span data-stu-id="73d44-127">It's also implicitly convertible to the built-in [floating-point](floating-point-numeric-types.md) numeric types: `float`, `double`, and `decimal`.</span></span> <span data-ttu-id="73d44-128">Il est explicitement convertible en `sbyte` `byte` types, et en `short` types intégraux.</span><span class="sxs-lookup"><span data-stu-id="73d44-128">It's explicitly convertible to `sbyte`, `byte`, and `short` integral types.</span></span>

<span data-ttu-id="73d44-129">Il n’existe pas de conversion implicite d’autres types vers le `char` type.</span><span class="sxs-lookup"><span data-stu-id="73d44-129">There are no implicit conversions from other types to the `char` type.</span></span> <span data-ttu-id="73d44-130">Toutefois, tous les types numériques [intégraux](integral-numeric-types.md) ou à [virgule flottante](floating-point-numeric-types.md) sont explicitement convertibles en `char` .</span><span class="sxs-lookup"><span data-stu-id="73d44-130">However, any [integral](integral-numeric-types.md) or [floating-point](floating-point-numeric-types.md) numeric type is explicitly convertible to `char`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="73d44-131">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="73d44-131">C# language specification</span></span>

<span data-ttu-id="73d44-132">Pour plus d’informations, consultez la section [types intégraux](~/_csharplang/spec/types.md#integral-types) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="73d44-132">For more information, see the [Integral types](~/_csharplang/spec/types.md#integral-types) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="73d44-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="73d44-133">See also</span></span>

- [<span data-ttu-id="73d44-134">Informations de référence sur C#</span><span class="sxs-lookup"><span data-stu-id="73d44-134">C# reference</span></span>](../index.md)
- [<span data-ttu-id="73d44-135">Types de valeur</span><span class="sxs-lookup"><span data-stu-id="73d44-135">Value types</span></span>](value-types.md)
- [<span data-ttu-id="73d44-136">Chaînes</span><span class="sxs-lookup"><span data-stu-id="73d44-136">Strings</span></span>](../../programming-guide/strings/index.md)
- <xref:System.Text.Rune?displayProperty=nameWithType>
- [<span data-ttu-id="73d44-137">Encodage de caractères dans .NET</span><span class="sxs-lookup"><span data-stu-id="73d44-137">Character encoding in .NET</span></span>](../../../standard/base-types/character-encoding-introduction.md)
