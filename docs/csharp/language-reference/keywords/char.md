---
title: Char, mot C# clé-référence
ms.custom: seodec18
ms.date: 10/22/2019
f1_keywords:
- char
- char_CSharpKeyword
helpviewer_keywords:
- char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
ms.openlocfilehash: 1b9f8d1bb205a6cbfe521830a11bd8878ccde991
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72771797"
---
# <a name="char-c-reference"></a><span data-ttu-id="8b9d3-102">Char (C# référence)</span><span class="sxs-lookup"><span data-stu-id="8b9d3-102">char (C# reference)</span></span>

<span data-ttu-id="8b9d3-103">Le mot clé `char` type est un alias pour le type de structure .NET <xref:System.Char?displayProperty=nameWithType> qui représente un caractère Unicode UTF-16 :</span><span class="sxs-lookup"><span data-stu-id="8b9d3-103">The `char` type keyword is an alias for the .NET <xref:System.Char?displayProperty=nameWithType> structure type that represents a Unicode UTF-16 character:</span></span>

|<span data-ttu-id="8b9d3-104">Tapez</span><span class="sxs-lookup"><span data-stu-id="8b9d3-104">Type</span></span>|<span data-ttu-id="8b9d3-105">Range</span><span class="sxs-lookup"><span data-stu-id="8b9d3-105">Range</span></span>|<span data-ttu-id="8b9d3-106">Size</span><span class="sxs-lookup"><span data-stu-id="8b9d3-106">Size</span></span>|<span data-ttu-id="8b9d3-107">Type .NET</span><span class="sxs-lookup"><span data-stu-id="8b9d3-107">.NET type</span></span>|
|----------|-----------|----------|-------------------------|
|`char`|<span data-ttu-id="8b9d3-108">U+0000 à U+FFFF</span><span class="sxs-lookup"><span data-stu-id="8b9d3-108">U+0000 to U+FFFF</span></span>|<span data-ttu-id="8b9d3-109">16 bits</span><span class="sxs-lookup"><span data-stu-id="8b9d3-109">16 bit</span></span>|<xref:System.Char?displayProperty=nameWithType>|

## <a name="literals"></a><span data-ttu-id="8b9d3-110">Littéraux</span><span class="sxs-lookup"><span data-stu-id="8b9d3-110">Literals</span></span>

<span data-ttu-id="8b9d3-111">Les constantes de type `char` peuvent être représentées sous la forme de littéraux de caractères, d’une séquence d’échappement hexadécimale ou d’une représentation Unicode.</span><span class="sxs-lookup"><span data-stu-id="8b9d3-111">Constants of the `char` type can be written as character literals, hexadecimal escape sequence, or Unicode representation.</span></span> <span data-ttu-id="8b9d3-112">Vous pouvez également convertir un code de caractère intégral en valeur `char` correspondante.</span><span class="sxs-lookup"><span data-stu-id="8b9d3-112">You can also cast an integral character code into the corresponding `char` value.</span></span> <span data-ttu-id="8b9d3-113">Dans l’exemple suivant, les quatre éléments d’un tableau de `char` sont initialisés avec le même `X` de caractères :</span><span class="sxs-lookup"><span data-stu-id="8b9d3-113">In the following example, the four elements of an array of `char` are initialized with the same character `X`:</span></span>

[!code-csharp[csrefKeywordsTypes#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#19)]

## <a name="conversions"></a><span data-ttu-id="8b9d3-114">Conversions</span><span class="sxs-lookup"><span data-stu-id="8b9d3-114">Conversions</span></span>

<span data-ttu-id="8b9d3-115">Le type de `char` est implicitement convertible en types [intégraux](../builtin-types/integral-numeric-types.md) suivants : `ushort`, `int`, `uint`, `long` et `ulong`.</span><span class="sxs-lookup"><span data-stu-id="8b9d3-115">The `char` type is implicitly convertible to the following [integral](../builtin-types/integral-numeric-types.md) types: `ushort`, `int`, `uint`, `long`, and `ulong`.</span></span> <span data-ttu-id="8b9d3-116">Il est également implicitement convertible en types numériques à [virgule flottante](../builtin-types/floating-point-numeric-types.md) intégrés : `float`, `double` et `decimal`.</span><span class="sxs-lookup"><span data-stu-id="8b9d3-116">It's also implicitly convertible to the built-in [floating-point](../builtin-types/floating-point-numeric-types.md) numeric types: `float`, `double`, and `decimal`.</span></span> <span data-ttu-id="8b9d3-117">Elle est explicitement convertible en `sbyte`, `byte` et `short` types intégraux.</span><span class="sxs-lookup"><span data-stu-id="8b9d3-117">It's explicitly convertible to `sbyte`, `byte`, and `short` integral types.</span></span>

<span data-ttu-id="8b9d3-118">Il n’existe pas de conversion implicite d’autres types en type `char`.</span><span class="sxs-lookup"><span data-stu-id="8b9d3-118">There are no implicit conversions from other types to the `char` type.</span></span> <span data-ttu-id="8b9d3-119">Toutefois, tout type numérique [intégral](../builtin-types/integral-numeric-types.md) ou à [virgule flottante](../builtin-types/floating-point-numeric-types.md) est explicitement convertible en `char`.</span><span class="sxs-lookup"><span data-stu-id="8b9d3-119">However, any [integral](../builtin-types/integral-numeric-types.md) or [floating-point](../builtin-types/floating-point-numeric-types.md) numeric type is explicitly convertible to `char`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="8b9d3-120">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="8b9d3-120">C# language specification</span></span>

<span data-ttu-id="8b9d3-121">Pour plus d’informations, consultez la section [types intégraux](~/_csharplang/spec/types.md#integral-types) de la [ C# spécification du langage](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="8b9d3-121">For more information, see the [Integral types](~/_csharplang/spec/types.md#integral-types) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8b9d3-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8b9d3-122">See also</span></span>

- [<span data-ttu-id="8b9d3-123">Informations de référence sur C#</span><span class="sxs-lookup"><span data-stu-id="8b9d3-123">C# reference</span></span>](../index.md)
- [<span data-ttu-id="8b9d3-124">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="8b9d3-124">C# keywords</span></span>](./index.md)
- [<span data-ttu-id="8b9d3-125">Tableaux des types intégrés</span><span class="sxs-lookup"><span data-stu-id="8b9d3-125">Built-in types table</span></span>](./built-in-types-table.md)
- [<span data-ttu-id="8b9d3-126">Chaînes</span><span class="sxs-lookup"><span data-stu-id="8b9d3-126">Strings</span></span>](../../programming-guide/strings/index.md)
- <xref:System.Char?displayProperty=nameWithType>
