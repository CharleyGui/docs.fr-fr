---
title: char, mot clé - Référence C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- char
- char_CSharpKeyword
helpviewer_keywords:
- char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
ms.openlocfilehash: 63f8871926e8c279678c59a2256bef46b2ff514e
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698774"
---
# <a name="char-c-reference"></a><span data-ttu-id="22296-102">char (référence C#)</span><span class="sxs-lookup"><span data-stu-id="22296-102">char (C# Reference)</span></span>

<span data-ttu-id="22296-103">Le mot clé `char` permet de déclarer une instance de la structure <xref:System.Char?displayProperty=nameWithType> utilisée par le .NET Framework pour représenter un caractère Unicode.</span><span class="sxs-lookup"><span data-stu-id="22296-103">The `char` keyword is used to declare an instance of the <xref:System.Char?displayProperty=nameWithType> structure that the .NET Framework uses to represent a Unicode character.</span></span> <span data-ttu-id="22296-104">La valeur d’un objet `Char` est une valeur numérique 16 bits (ordinale).</span><span class="sxs-lookup"><span data-stu-id="22296-104">The value of a `Char` object is a 16-bit numeric (ordinal) value.</span></span>

 <span data-ttu-id="22296-105">Les caractères Unicode sont utilisés pour représenter la plupart des langues écrites dans le monde.</span><span class="sxs-lookup"><span data-stu-id="22296-105">Unicode characters are used to represent most of the written languages throughout the world.</span></span>

|<span data-ttu-id="22296-106">Type</span><span class="sxs-lookup"><span data-stu-id="22296-106">Type</span></span>|<span data-ttu-id="22296-107">Plage</span><span class="sxs-lookup"><span data-stu-id="22296-107">Range</span></span>|<span data-ttu-id="22296-108">Size</span><span class="sxs-lookup"><span data-stu-id="22296-108">Size</span></span>|<span data-ttu-id="22296-109">Type .NET</span><span class="sxs-lookup"><span data-stu-id="22296-109">.NET type</span></span>|
|----------|-----------|----------|-------------------------|
|`char`|<span data-ttu-id="22296-110">U+0000 à U+FFFF</span><span class="sxs-lookup"><span data-stu-id="22296-110">U+0000 to U+FFFF</span></span>|<span data-ttu-id="22296-111">Caractère Unicode 16 bits</span><span class="sxs-lookup"><span data-stu-id="22296-111">Unicode 16-bit character</span></span>|<xref:System.Char?displayProperty=nameWithType>|

## <a name="literals"></a><span data-ttu-id="22296-112">Littéraux</span><span class="sxs-lookup"><span data-stu-id="22296-112">Literals</span></span>

<span data-ttu-id="22296-113">Les constantes de type `char` peuvent être représentées sous la forme de littéraux de caractères, d’une séquence d’échappement hexadécimale ou d’une représentation Unicode.</span><span class="sxs-lookup"><span data-stu-id="22296-113">Constants of the `char` type can be written as character literals, hexadecimal escape sequence, or Unicode representation.</span></span> <span data-ttu-id="22296-114">Vous pouvez également effectuer un cast des codes de caractères de type intégral.</span><span class="sxs-lookup"><span data-stu-id="22296-114">You can also cast the integral character codes.</span></span> <span data-ttu-id="22296-115">Dans l’exemple suivant, les quatre éléments d’un tableau de `char` sont initialisés avec le même caractère `X` :</span><span class="sxs-lookup"><span data-stu-id="22296-115">In the following example, the four elements of an array of `char` are initialized with the same character `X`:</span></span>

[!code-csharp[csrefKeywordsTypes#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#19)]

## <a name="conversions"></a><span data-ttu-id="22296-116">Conversions</span><span class="sxs-lookup"><span data-stu-id="22296-116">Conversions</span></span>

<span data-ttu-id="22296-117">Vous pouvez convertir implicitement un `char` en [ushort](../builtin-types/integral-numeric-types.md), [int](../builtin-types/integral-numeric-types.md), [uint](../builtin-types/integral-numeric-types.md), [double](../builtin-types/floating-point-numeric-types.md) ou [decimal](../builtin-types/floating-point-numeric-types.md).</span><span class="sxs-lookup"><span data-stu-id="22296-117">A `char` can be implicitly converted to [ushort](../builtin-types/integral-numeric-types.md), [int](../builtin-types/integral-numeric-types.md), [uint](../builtin-types/integral-numeric-types.md), [double](../builtin-types/floating-point-numeric-types.md), or [decimal](../builtin-types/floating-point-numeric-types.md).</span></span> <span data-ttu-id="22296-118">Par contre, vous ne pouvez pas convertir implicitement d’autres types en type `char`.</span><span class="sxs-lookup"><span data-stu-id="22296-118">However, there are no implicit conversions from other types to the `char` type.</span></span>

<span data-ttu-id="22296-119">Le type <xref:System.Char?displayProperty=nameWithType> fournit plusieurs méthodes statiques à utiliser avec des valeurs `char`.</span><span class="sxs-lookup"><span data-stu-id="22296-119">The <xref:System.Char?displayProperty=nameWithType> type provides several static methods for working with `char` values.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="22296-120">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="22296-120">C# language specification</span></span>  

<span data-ttu-id="22296-121">Pour plus d’informations, consultez [Types intégraux](~/_csharplang/spec/types.md#integral-types) dans la [spécification du langage C#](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="22296-121">For more information, see [Integral types](~/_csharplang/spec/types.md#integral-types) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="22296-122">La spécification du langage est la source de référence pour la syntaxe C# et son utilisation.</span><span class="sxs-lookup"><span data-stu-id="22296-122">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="22296-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="22296-123">See also</span></span>

- <xref:System.Char>
- [<span data-ttu-id="22296-124">Référence C#</span><span class="sxs-lookup"><span data-stu-id="22296-124">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="22296-125">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="22296-125">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="22296-126">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="22296-126">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="22296-127">Types intégraux</span><span class="sxs-lookup"><span data-stu-id="22296-127">Integral types</span></span>](../builtin-types/integral-numeric-types.md)
- [<span data-ttu-id="22296-128">Tableau des types intégrés</span><span class="sxs-lookup"><span data-stu-id="22296-128">Built-In Types Table</span></span>](./built-in-types-table.md)
- [<span data-ttu-id="22296-129">Tableau des conversions numériques implicites</span><span class="sxs-lookup"><span data-stu-id="22296-129">Implicit Numeric Conversions Table</span></span>](./implicit-numeric-conversions-table.md)
- [<span data-ttu-id="22296-130">Tableau des conversions numériques explicites</span><span class="sxs-lookup"><span data-stu-id="22296-130">Explicit Numeric Conversions Table</span></span>](./explicit-numeric-conversions-table.md)
- [<span data-ttu-id="22296-131">Chaînes</span><span class="sxs-lookup"><span data-stu-id="22296-131">Strings</span></span>](../../programming-guide/strings/index.md)
