---
title: type de caractère C# -référence
ms.date: 11/22/2019
f1_keywords:
- char
- char_CSharpKeyword
helpviewer_keywords:
- char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
ms.openlocfilehash: b7ea52eaccda4599969a5d1e3b683d2d842b0d82
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77093238"
---
# <a name="char-c-reference"></a><span data-ttu-id="deab1-102">Char (C# référence)</span><span class="sxs-lookup"><span data-stu-id="deab1-102">char (C# reference)</span></span>

<span data-ttu-id="deab1-103">Le mot clé `char` type est un alias pour le type de structure .NET <xref:System.Char?displayProperty=nameWithType> qui représente un caractère Unicode UTF-16.</span><span class="sxs-lookup"><span data-stu-id="deab1-103">The `char` type keyword is an alias for the .NET <xref:System.Char?displayProperty=nameWithType> structure type that represents a Unicode UTF-16 character.</span></span>

|<span data-ttu-id="deab1-104">Type</span><span class="sxs-lookup"><span data-stu-id="deab1-104">Type</span></span>|<span data-ttu-id="deab1-105">Plage</span><span class="sxs-lookup"><span data-stu-id="deab1-105">Range</span></span>|<span data-ttu-id="deab1-106">Size</span><span class="sxs-lookup"><span data-stu-id="deab1-106">Size</span></span>|<span data-ttu-id="deab1-107">Type .NET</span><span class="sxs-lookup"><span data-stu-id="deab1-107">.NET type</span></span>|
|----------|-----------|----------|-------------------------|
|`char`|<span data-ttu-id="deab1-108">U+0000 à U+FFFF</span><span class="sxs-lookup"><span data-stu-id="deab1-108">U+0000 to U+FFFF</span></span>|<span data-ttu-id="deab1-109">16 bits</span><span class="sxs-lookup"><span data-stu-id="deab1-109">16 bit</span></span>|<xref:System.Char?displayProperty=nameWithType>|

<span data-ttu-id="deab1-110">La valeur par défaut du type de `char` est `\0`, c’est-à-dire U + 0000.</span><span class="sxs-lookup"><span data-stu-id="deab1-110">The default value of the `char` type is `\0`, that is, U+0000.</span></span>

<span data-ttu-id="deab1-111">Le type [String](reference-types.md#the-string-type) représente du texte sous la forme d’une séquence de valeurs `char`.</span><span class="sxs-lookup"><span data-stu-id="deab1-111">The [string](reference-types.md#the-string-type) type represents text as a sequence of `char` values.</span></span>

## <a name="literals"></a><span data-ttu-id="deab1-112">Littéraux</span><span class="sxs-lookup"><span data-stu-id="deab1-112">Literals</span></span>

<span data-ttu-id="deab1-113">Vous pouvez spécifier une valeur de `char` avec :</span><span class="sxs-lookup"><span data-stu-id="deab1-113">You can specify a `char` value with:</span></span>

- <span data-ttu-id="deab1-114">littéral de caractère.</span><span class="sxs-lookup"><span data-stu-id="deab1-114">a character literal.</span></span>
- <span data-ttu-id="deab1-115">séquence d’échappement Unicode, `\u` suivie de la représentation hexadécimale à quatre symboles d’un code de caractère.</span><span class="sxs-lookup"><span data-stu-id="deab1-115">a Unicode escape sequence, which is `\u` followed by the four-symbol hexadecimal representation of a character code.</span></span>
- <span data-ttu-id="deab1-116">séquence d’échappement hexadécimale, `\x` suivie de la représentation hexadécimale d’un code de caractère.</span><span class="sxs-lookup"><span data-stu-id="deab1-116">a hexadecimal escape sequence, which is `\x` followed by the hexadecimal representation of a character code.</span></span>

[!code-csharp-interactive[char literals](~/samples/csharp/language-reference/builtin-types/CharType.cs#Literals)]

<span data-ttu-id="deab1-117">Comme le montre l’exemple précédent, vous pouvez également effectuer un cast de la valeur d’un code de caractère dans la valeur `char` correspondante.</span><span class="sxs-lookup"><span data-stu-id="deab1-117">As the preceding example shows, you also can cast the value of a character code into the corresponding `char` value.</span></span>

> [!NOTE]
> <span data-ttu-id="deab1-118">Dans le cas d’une séquence d’échappement Unicode, vous devez spécifier les quatre chiffres hexadécimaux.</span><span class="sxs-lookup"><span data-stu-id="deab1-118">In the case of a Unicode escape sequence, you must specify all four hexadecimal digits.</span></span> <span data-ttu-id="deab1-119">Autrement dit, `\u006A` est une séquence d’échappement valide, tandis que `\u06A` et `\u6A` ne sont pas valides.</span><span class="sxs-lookup"><span data-stu-id="deab1-119">That is, `\u006A` is a valid escape sequence, while `\u06A` and `\u6A` are not valid.</span></span>
>
> <span data-ttu-id="deab1-120">Dans le cas d’une séquence d’échappement hexadécimale, vous pouvez omettre les zéros non significatifs.</span><span class="sxs-lookup"><span data-stu-id="deab1-120">In the case of a hexadecimal escape sequence, you can omit the leading zeros.</span></span> <span data-ttu-id="deab1-121">Autrement dit, les séquences d’échappement `\x006A`, `\x06A`et `\x6A` sont valides et correspondent au même caractère.</span><span class="sxs-lookup"><span data-stu-id="deab1-121">That is, the `\x006A`, `\x06A`, and `\x6A` escape sequences are valid and correspond to the same character.</span></span>

## <a name="conversions"></a><span data-ttu-id="deab1-122">Conversions</span><span class="sxs-lookup"><span data-stu-id="deab1-122">Conversions</span></span>

<span data-ttu-id="deab1-123">Le type de `char` est implicitement convertible en types [intégraux](integral-numeric-types.md) suivants : `ushort`, `int`, `uint`, `long`et `ulong`.</span><span class="sxs-lookup"><span data-stu-id="deab1-123">The `char` type is implicitly convertible to the following [integral](integral-numeric-types.md) types: `ushort`, `int`, `uint`, `long`, and `ulong`.</span></span> <span data-ttu-id="deab1-124">Il est également implicitement convertible en types numériques à [virgule flottante](floating-point-numeric-types.md) intégrés : `float`, `double`et `decimal`.</span><span class="sxs-lookup"><span data-stu-id="deab1-124">It's also implicitly convertible to the built-in [floating-point](floating-point-numeric-types.md) numeric types: `float`, `double`, and `decimal`.</span></span> <span data-ttu-id="deab1-125">Elle est explicitement convertible en `sbyte`, `byte`et `short` types intégraux.</span><span class="sxs-lookup"><span data-stu-id="deab1-125">It's explicitly convertible to `sbyte`, `byte`, and `short` integral types.</span></span>

<span data-ttu-id="deab1-126">Il n’existe pas de conversion implicite d’autres types en type `char`.</span><span class="sxs-lookup"><span data-stu-id="deab1-126">There are no implicit conversions from other types to the `char` type.</span></span> <span data-ttu-id="deab1-127">Toutefois, tout type numérique [intégral](integral-numeric-types.md) ou à [virgule flottante](floating-point-numeric-types.md) est explicitement convertible en `char`.</span><span class="sxs-lookup"><span data-stu-id="deab1-127">However, any [integral](integral-numeric-types.md) or [floating-point](floating-point-numeric-types.md) numeric type is explicitly convertible to `char`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="deab1-128">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="deab1-128">C# language specification</span></span>

<span data-ttu-id="deab1-129">Pour plus d’informations, consultez la section [types intégraux](~/_csharplang/spec/types.md#integral-types) de la [ C# spécification du langage](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="deab1-129">For more information, see the [Integral types](~/_csharplang/spec/types.md#integral-types) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="deab1-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="deab1-130">See also</span></span>

- [<span data-ttu-id="deab1-131">Informations de référence sur C#</span><span class="sxs-lookup"><span data-stu-id="deab1-131">C# reference</span></span>](../index.md)
- [<span data-ttu-id="deab1-132">Types de valeur</span><span class="sxs-lookup"><span data-stu-id="deab1-132">Value types</span></span>](value-types.md)
- [<span data-ttu-id="deab1-133">Chaînes</span><span class="sxs-lookup"><span data-stu-id="deab1-133">Strings</span></span>](../../programming-guide/strings/index.md)
- <xref:System.Text.Rune?displayProperty=nameWithType>
