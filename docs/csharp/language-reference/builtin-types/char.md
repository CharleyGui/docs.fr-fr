---
title: char type - C# reference
ms.date: 11/22/2019
f1_keywords:
- char
- char_CSharpKeyword
helpviewer_keywords:
- char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
ms.openlocfilehash: 3b2eec4f0e17aa329fe3865fb3ef453ee030c6a7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74451163"
---
# <a name="char-c-reference"></a><span data-ttu-id="e7e53-102">char (C# reference)</span><span class="sxs-lookup"><span data-stu-id="e7e53-102">char (C# reference)</span></span>

<span data-ttu-id="e7e53-103">The `char` type keyword is an alias for the .NET <xref:System.Char?displayProperty=nameWithType> structure type that represents a Unicode UTF-16 character.</span><span class="sxs-lookup"><span data-stu-id="e7e53-103">The `char` type keyword is an alias for the .NET <xref:System.Char?displayProperty=nameWithType> structure type that represents a Unicode UTF-16 character.</span></span>

|<span data-ttu-id="e7e53-104">Tapez</span><span class="sxs-lookup"><span data-stu-id="e7e53-104">Type</span></span>|<span data-ttu-id="e7e53-105">Range</span><span class="sxs-lookup"><span data-stu-id="e7e53-105">Range</span></span>|<span data-ttu-id="e7e53-106">Size</span><span class="sxs-lookup"><span data-stu-id="e7e53-106">Size</span></span>|<span data-ttu-id="e7e53-107">Type .NET</span><span class="sxs-lookup"><span data-stu-id="e7e53-107">.NET type</span></span>|
|----------|-----------|----------|-------------------------|
|`char`|<span data-ttu-id="e7e53-108">U+0000 à U+FFFF</span><span class="sxs-lookup"><span data-stu-id="e7e53-108">U+0000 to U+FFFF</span></span>|<span data-ttu-id="e7e53-109">16 bit</span><span class="sxs-lookup"><span data-stu-id="e7e53-109">16 bit</span></span>|<xref:System.Char?displayProperty=nameWithType>|

<span data-ttu-id="e7e53-110">The [string](reference-types.md#the-string-type) type represents text as a sequence of `char` values.</span><span class="sxs-lookup"><span data-stu-id="e7e53-110">The [string](reference-types.md#the-string-type) type represents text as a sequence of `char` values.</span></span>

## <a name="literals"></a><span data-ttu-id="e7e53-111">Littéraux</span><span class="sxs-lookup"><span data-stu-id="e7e53-111">Literals</span></span>

<span data-ttu-id="e7e53-112">You can specify a `char` value with:</span><span class="sxs-lookup"><span data-stu-id="e7e53-112">You can specify a `char` value with:</span></span>

- <span data-ttu-id="e7e53-113">a character literal.</span><span class="sxs-lookup"><span data-stu-id="e7e53-113">a character literal.</span></span>
- <span data-ttu-id="e7e53-114">a Unicode escape sequence, which is `\u` followed by the four-symbol hexadecimal representation of a character code.</span><span class="sxs-lookup"><span data-stu-id="e7e53-114">a Unicode escape sequence, which is `\u` followed by the four-symbol hexadecimal representation of a character code.</span></span>
- <span data-ttu-id="e7e53-115">a hexadecimal escape sequence, which is `\x` followed by the hexadecimal representation of a character code.</span><span class="sxs-lookup"><span data-stu-id="e7e53-115">a hexadecimal escape sequence, which is `\x` followed by the hexadecimal representation of a character code.</span></span>

[!code-csharp-interactive[char literals](~/samples/csharp/language-reference/builtin-types/CharType.cs#Literals)]

<span data-ttu-id="e7e53-116">As the preceding example shows, you also can cast the value of a character code into the corresponding `char` value.</span><span class="sxs-lookup"><span data-stu-id="e7e53-116">As the preceding example shows, you also can cast the value of a character code into the corresponding `char` value.</span></span>

> [!NOTE]
> <span data-ttu-id="e7e53-117">In the case of a Unicode escape sequence, you must specify all four hexadecimal digits.</span><span class="sxs-lookup"><span data-stu-id="e7e53-117">In the case of a Unicode escape sequence, you must specify all four hexadecimal digits.</span></span> <span data-ttu-id="e7e53-118">That is, `\u006A` is a valid escape sequence, while `\u06A` and `\u6A` are not valid.</span><span class="sxs-lookup"><span data-stu-id="e7e53-118">That is, `\u006A` is a valid escape sequence, while `\u06A` and `\u6A` are not valid.</span></span>
>
> <span data-ttu-id="e7e53-119">In the case of a hexadecimal escape sequence, you can omit the leading zeros.</span><span class="sxs-lookup"><span data-stu-id="e7e53-119">In the case of a hexadecimal escape sequence, you can omit the leading zeros.</span></span> <span data-ttu-id="e7e53-120">That is, the `\x006A`, `\x06A`, and `\x6A` escape sequences are valid and correspond to the same character.</span><span class="sxs-lookup"><span data-stu-id="e7e53-120">That is, the `\x006A`, `\x06A`, and `\x6A` escape sequences are valid and correspond to the same character.</span></span>

## <a name="conversions"></a><span data-ttu-id="e7e53-121">Conversions</span><span class="sxs-lookup"><span data-stu-id="e7e53-121">Conversions</span></span>

<span data-ttu-id="e7e53-122">The `char` type is implicitly convertible to the following [integral](integral-numeric-types.md) types: `ushort`, `int`, `uint`, `long`, and `ulong`.</span><span class="sxs-lookup"><span data-stu-id="e7e53-122">The `char` type is implicitly convertible to the following [integral](integral-numeric-types.md) types: `ushort`, `int`, `uint`, `long`, and `ulong`.</span></span> <span data-ttu-id="e7e53-123">It's also implicitly convertible to the built-in [floating-point](floating-point-numeric-types.md) numeric types: `float`, `double`, and `decimal`.</span><span class="sxs-lookup"><span data-stu-id="e7e53-123">It's also implicitly convertible to the built-in [floating-point](floating-point-numeric-types.md) numeric types: `float`, `double`, and `decimal`.</span></span> <span data-ttu-id="e7e53-124">It's explicitly convertible to `sbyte`, `byte`, and `short` integral types.</span><span class="sxs-lookup"><span data-stu-id="e7e53-124">It's explicitly convertible to `sbyte`, `byte`, and `short` integral types.</span></span>

<span data-ttu-id="e7e53-125">There are no implicit conversions from other types to the `char` type.</span><span class="sxs-lookup"><span data-stu-id="e7e53-125">There are no implicit conversions from other types to the `char` type.</span></span> <span data-ttu-id="e7e53-126">However, any [integral](integral-numeric-types.md) or [floating-point](floating-point-numeric-types.md) numeric type is explicitly convertible to `char`.</span><span class="sxs-lookup"><span data-stu-id="e7e53-126">However, any [integral](integral-numeric-types.md) or [floating-point](floating-point-numeric-types.md) numeric type is explicitly convertible to `char`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="e7e53-127">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="e7e53-127">C# language specification</span></span>

<span data-ttu-id="e7e53-128">For more information, see the [Integral types](~/_csharplang/spec/types.md#integral-types) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="e7e53-128">For more information, see the [Integral types](~/_csharplang/spec/types.md#integral-types) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e7e53-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e7e53-129">See also</span></span>

- [<span data-ttu-id="e7e53-130">Informations de référence sur C#</span><span class="sxs-lookup"><span data-stu-id="e7e53-130">C# reference</span></span>](../index.md)
- [<span data-ttu-id="e7e53-131">Tableaux des types intégrés</span><span class="sxs-lookup"><span data-stu-id="e7e53-131">Built-in types table</span></span>](../keywords/built-in-types-table.md)
- [<span data-ttu-id="e7e53-132">Chaînes</span><span class="sxs-lookup"><span data-stu-id="e7e53-132">Strings</span></span>](../../programming-guide/strings/index.md)
