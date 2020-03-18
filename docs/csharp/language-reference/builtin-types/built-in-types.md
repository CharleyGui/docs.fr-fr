---
title: Types intégrés - Référence C
description: Apprenez les types de valeur et de référence intégrés CMD
ms.date: 02/04/2020
helpviewer_keywords:
- types [C#], built-in
- built-in C# types
ms.assetid: 54f901f2-bf2f-472c-ae8d-73e8ecfc57fe
ms.openlocfilehash: 4f748373350ed0596a5f1d595c273243ae3227c3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77095308"
---
# <a name="built-in-types-c-reference"></a><span data-ttu-id="3726b-103">Types intégrés (référence C)</span><span class="sxs-lookup"><span data-stu-id="3726b-103">Built-in types (C# reference)</span></span>

<span data-ttu-id="3726b-104">Le tableau suivant répertorie les types de [valeur](value-types.md) intégrés CMD :</span><span class="sxs-lookup"><span data-stu-id="3726b-104">The following table lists the C# built-in [value](value-types.md) types:</span></span>

|<span data-ttu-id="3726b-105">Mot-clé de type C</span><span class="sxs-lookup"><span data-stu-id="3726b-105">C# type keyword</span></span>|<span data-ttu-id="3726b-106">Type .NET</span><span class="sxs-lookup"><span data-stu-id="3726b-106">.NET type</span></span>|
|--------------|-------------------------|
|[`bool`](bool.md)|<xref:System.Boolean?displayProperty=nameWithType>|
|[`byte`](integral-numeric-types.md)|<xref:System.Byte?displayProperty=nameWithType>|
|[`sbyte`](integral-numeric-types.md)|<xref:System.SByte?displayProperty=nameWithType>|
|[`char`](char.md)|<xref:System.Char?displayProperty=nameWithType>|
|[`decimal`](floating-point-numeric-types.md)|<xref:System.Decimal?displayProperty=nameWithType>|
|[`double`](floating-point-numeric-types.md)|<xref:System.Double?displayProperty=nameWithType>|
|[`float`](floating-point-numeric-types.md)|<xref:System.Single?displayProperty=nameWithType>|
|[`int`](integral-numeric-types.md)|<xref:System.Int32?displayProperty=nameWithType>|
|[`uint`](integral-numeric-types.md)|<xref:System.UInt32?displayProperty=nameWithType>|
|[`long`](integral-numeric-types.md)|<xref:System.Int64?displayProperty=nameWithType>|
|[`ulong`](integral-numeric-types.md)|<xref:System.UInt64?displayProperty=nameWithType>|
|[`short`](integral-numeric-types.md)|<xref:System.Int16?displayProperty=nameWithType>|
|[`ushort`](integral-numeric-types.md)|<xref:System.UInt16?displayProperty=nameWithType>|

<span data-ttu-id="3726b-107">Le tableau suivant répertorie les types de [référence](../keywords/reference-types.md) intégrés CMD :</span><span class="sxs-lookup"><span data-stu-id="3726b-107">The following table lists the C# built-in [reference](../keywords/reference-types.md) types:</span></span>

|<span data-ttu-id="3726b-108">Mot-clé de type C</span><span class="sxs-lookup"><span data-stu-id="3726b-108">C# type keyword</span></span>|<span data-ttu-id="3726b-109">Type .NET</span><span class="sxs-lookup"><span data-stu-id="3726b-109">.NET type</span></span>|
|--------------|-------------------------|
|[`object`](reference-types.md#the-object-type)|<xref:System.Object?displayProperty=nameWithType>|
|[`string`](reference-types.md#the-string-type)|<xref:System.String?displayProperty=nameWithType>|

<span data-ttu-id="3726b-110">Dans les tableaux précédents, chaque mot clé de type C de la colonne gauche est un alias pour le type .NET correspondant.</span><span class="sxs-lookup"><span data-stu-id="3726b-110">In the preceding tables, each C# type keyword from the left column is an alias for the corresponding .NET type.</span></span> <span data-ttu-id="3726b-111">Ils sont interchangeables.</span><span class="sxs-lookup"><span data-stu-id="3726b-111">They are interchangeable.</span></span> <span data-ttu-id="3726b-112">Par exemple, les déclarations suivantes déclarent des variables du même type :</span><span class="sxs-lookup"><span data-stu-id="3726b-112">For example, the following declarations declare variables of the same type:</span></span>

```csharp
int a = 123;
System.Int32 b = 123;
```

## <a name="see-also"></a><span data-ttu-id="3726b-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3726b-113">See also</span></span>

- [<span data-ttu-id="3726b-114">Référence C#</span><span class="sxs-lookup"><span data-stu-id="3726b-114">C# reference</span></span>](../index.md)
- [<span data-ttu-id="3726b-115">Valeurs par défaut des types C</span><span class="sxs-lookup"><span data-stu-id="3726b-115">Default values of C# types</span></span>](default-values.md)
- [<span data-ttu-id="3726b-116">`dynamic`Mot-clé</span><span class="sxs-lookup"><span data-stu-id="3726b-116">`dynamic` keyword</span></span>](reference-types.md#the-dynamic-type)
