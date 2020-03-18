---
title: type d’omble - Référence C
ms.date: 11/22/2019
f1_keywords:
- char
- char_CSharpKeyword
helpviewer_keywords:
- char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
ms.openlocfilehash: c4e29e6437edfe549b36a04a2050f63caa0d3d2a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78846520"
---
# <a name="char-c-reference"></a><span data-ttu-id="6ef39-102">char (référence C)</span><span class="sxs-lookup"><span data-stu-id="6ef39-102">char (C# reference)</span></span>

<span data-ttu-id="6ef39-103">Le `char` mot clé de type <xref:System.Char?displayProperty=nameWithType> est un alias pour le type de structure .NET qui représente un caractère Unicode UTF-16.</span><span class="sxs-lookup"><span data-stu-id="6ef39-103">The `char` type keyword is an alias for the .NET <xref:System.Char?displayProperty=nameWithType> structure type that represents a Unicode UTF-16 character.</span></span>

|<span data-ttu-id="6ef39-104">Type</span><span class="sxs-lookup"><span data-stu-id="6ef39-104">Type</span></span>|<span data-ttu-id="6ef39-105">Plage</span><span class="sxs-lookup"><span data-stu-id="6ef39-105">Range</span></span>|<span data-ttu-id="6ef39-106">Size</span><span class="sxs-lookup"><span data-stu-id="6ef39-106">Size</span></span>|<span data-ttu-id="6ef39-107">Type .NET</span><span class="sxs-lookup"><span data-stu-id="6ef39-107">.NET type</span></span>|
|----------|-----------|----------|-------------------------|
|`char`|<span data-ttu-id="6ef39-108">U+0000 à U+FFFF</span><span class="sxs-lookup"><span data-stu-id="6ef39-108">U+0000 to U+FFFF</span></span>|<span data-ttu-id="6ef39-109">16 bits</span><span class="sxs-lookup"><span data-stu-id="6ef39-109">16 bit</span></span>|<xref:System.Char?displayProperty=nameWithType>|

<span data-ttu-id="6ef39-110">La valeur par `char` défaut `\0`du type est, c’est-à-dire, U-0000.</span><span class="sxs-lookup"><span data-stu-id="6ef39-110">The default value of the `char` type is `\0`, that is, U+0000.</span></span>

<span data-ttu-id="6ef39-111">Le type [de chaîne](reference-types.md#the-string-type) représente `char` le texte comme une séquence de valeurs.</span><span class="sxs-lookup"><span data-stu-id="6ef39-111">The [string](reference-types.md#the-string-type) type represents text as a sequence of `char` values.</span></span>

## <a name="literals"></a><span data-ttu-id="6ef39-112">Littéraux</span><span class="sxs-lookup"><span data-stu-id="6ef39-112">Literals</span></span>

<span data-ttu-id="6ef39-113">Vous pouvez `char` spécifier une valeur avec :</span><span class="sxs-lookup"><span data-stu-id="6ef39-113">You can specify a `char` value with:</span></span>

- <span data-ttu-id="6ef39-114">un personnage littéral.</span><span class="sxs-lookup"><span data-stu-id="6ef39-114">a character literal.</span></span>
- <span data-ttu-id="6ef39-115">une séquence d’évasion `\u` Unicode, qui est suivie par la représentation héxadecimale à quatre symboles d’un code de caractère.</span><span class="sxs-lookup"><span data-stu-id="6ef39-115">a Unicode escape sequence, which is `\u` followed by the four-symbol hexadecimal representation of a character code.</span></span>
- <span data-ttu-id="6ef39-116">une séquence d’évasion hexadecimal, qui est `\x` suivie par la représentation héxadecimale d’un code de caractère.</span><span class="sxs-lookup"><span data-stu-id="6ef39-116">a hexadecimal escape sequence, which is `\x` followed by the hexadecimal representation of a character code.</span></span>

[!code-csharp-interactive[char literals](snippets/CharType.cs#Literals)]

<span data-ttu-id="6ef39-117">Comme l’exemple précédent l’indique, vous pouvez également `char` jeter la valeur d’un code de caractère dans la valeur correspondante.</span><span class="sxs-lookup"><span data-stu-id="6ef39-117">As the preceding example shows, you also can cast the value of a character code into the corresponding `char` value.</span></span>

> [!NOTE]
> <span data-ttu-id="6ef39-118">Dans le cas d’une séquence d’évasion Unicode, vous devez spécifier les quatre chiffres hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="6ef39-118">In the case of a Unicode escape sequence, you must specify all four hexadecimal digits.</span></span> <span data-ttu-id="6ef39-119">C’est-à-dire, `\u006A` est `\u06A` `\u6A` une séquence d’évasion valide, tandis que et ne sont pas valides.</span><span class="sxs-lookup"><span data-stu-id="6ef39-119">That is, `\u006A` is a valid escape sequence, while `\u06A` and `\u6A` are not valid.</span></span>
>
> <span data-ttu-id="6ef39-120">Dans le cas d’une séquence d’évasion hexadecimal, vous pouvez omettre les zéros de premier plan.</span><span class="sxs-lookup"><span data-stu-id="6ef39-120">In the case of a hexadecimal escape sequence, you can omit the leading zeros.</span></span> <span data-ttu-id="6ef39-121">C’est-à-dire, le `\x006A`, `\x06A`, et `\x6A` les séquences d’évasion sont valides et correspondent au même caractère.</span><span class="sxs-lookup"><span data-stu-id="6ef39-121">That is, the `\x006A`, `\x06A`, and `\x6A` escape sequences are valid and correspond to the same character.</span></span>

## <a name="conversions"></a><span data-ttu-id="6ef39-122">Conversions</span><span class="sxs-lookup"><span data-stu-id="6ef39-122">Conversions</span></span>

<span data-ttu-id="6ef39-123">Le `char` type est implicitement convertible aux `int`types `uint` `long` [intégrals](integral-numeric-types.md) suivants: `ushort`, , , et `ulong`.</span><span class="sxs-lookup"><span data-stu-id="6ef39-123">The `char` type is implicitly convertible to the following [integral](integral-numeric-types.md) types: `ushort`, `int`, `uint`, `long`, and `ulong`.</span></span> <span data-ttu-id="6ef39-124">Il est également implicitement convertible pour les types numériques `double` [flottants](floating-point-numeric-types.md) intégrés: `float`, , et `decimal`.</span><span class="sxs-lookup"><span data-stu-id="6ef39-124">It's also implicitly convertible to the built-in [floating-point](floating-point-numeric-types.md) numeric types: `float`, `double`, and `decimal`.</span></span> <span data-ttu-id="6ef39-125">Il est explicitement `sbyte`convertible `byte`à `short` , , et les types intégrales.</span><span class="sxs-lookup"><span data-stu-id="6ef39-125">It's explicitly convertible to `sbyte`, `byte`, and `short` integral types.</span></span>

<span data-ttu-id="6ef39-126">Il n’y a pas de `char` conversions implicites d’autres types à ce type.</span><span class="sxs-lookup"><span data-stu-id="6ef39-126">There are no implicit conversions from other types to the `char` type.</span></span> <span data-ttu-id="6ef39-127">Cependant, tout type numérique [intégral](integral-numeric-types.md) ou à `char`point [flottant](floating-point-numeric-types.md) est explicitement convertible à .</span><span class="sxs-lookup"><span data-stu-id="6ef39-127">However, any [integral](integral-numeric-types.md) or [floating-point](floating-point-numeric-types.md) numeric type is explicitly convertible to `char`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="6ef39-128">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="6ef39-128">C# language specification</span></span>

<span data-ttu-id="6ef39-129">Pour plus d’informations, consultez la section [des types intégrales](~/_csharplang/spec/types.md#integral-types) de la [spécification linguistique C.](~/_csharplang/spec/introduction.md)</span><span class="sxs-lookup"><span data-stu-id="6ef39-129">For more information, see the [Integral types](~/_csharplang/spec/types.md#integral-types) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6ef39-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6ef39-130">See also</span></span>

- [<span data-ttu-id="6ef39-131">Référence C#</span><span class="sxs-lookup"><span data-stu-id="6ef39-131">C# reference</span></span>](../index.md)
- [<span data-ttu-id="6ef39-132">Types de valeur</span><span class="sxs-lookup"><span data-stu-id="6ef39-132">Value types</span></span>](value-types.md)
- [<span data-ttu-id="6ef39-133">Cordes</span><span class="sxs-lookup"><span data-stu-id="6ef39-133">Strings</span></span>](../../programming-guide/strings/index.md)
- <xref:System.Text.Rune?displayProperty=nameWithType>
