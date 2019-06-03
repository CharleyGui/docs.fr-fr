---
title: Tableau des types intégrés - Référence C#
ms.custom: seodec18
description: Mots clés pour les types C# intégrés
ms.date: 08/17/2018
helpviewer_keywords:
- types [C#], built-in
- built-in C# types
ms.assetid: 54f901f2-bf2f-472c-ae8d-73e8ecfc57fe
ms.openlocfilehash: bd8c52cd798496a4df3086411dfe3be6241fbff5
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66422348"
---
# <a name="built-in-types-table-c-reference"></a><span data-ttu-id="7760d-103">Tableau des types intégrés (référence C#)</span><span class="sxs-lookup"><span data-stu-id="7760d-103">Built-in types table (C# Reference)</span></span>

<span data-ttu-id="7760d-104">Le tableau suivant liste les mots clés des types C# intégrés, qui sont des alias des types prédéfinis de l’espace de noms <xref:System>.</span><span class="sxs-lookup"><span data-stu-id="7760d-104">The following table shows the keywords for built-in C# types, which are aliases of predefined types in the <xref:System> namespace.</span></span>  
  
|<span data-ttu-id="7760d-105">Type C#</span><span class="sxs-lookup"><span data-stu-id="7760d-105">C# type</span></span>|<span data-ttu-id="7760d-106">Type .NET</span><span class="sxs-lookup"><span data-stu-id="7760d-106">.NET type</span></span>|  
|--------------|-------------------------|  
|[<span data-ttu-id="7760d-107">bool</span><span class="sxs-lookup"><span data-stu-id="7760d-107">bool</span></span>](bool.md)|<xref:System.Boolean?displayProperty=nameWithType>|  
|[<span data-ttu-id="7760d-108">byte</span><span class="sxs-lookup"><span data-stu-id="7760d-108">byte</span></span>](byte.md)|<xref:System.Byte?displayProperty=nameWithType>|  
|[<span data-ttu-id="7760d-109">sbyte</span><span class="sxs-lookup"><span data-stu-id="7760d-109">sbyte</span></span>](sbyte.md)|<xref:System.SByte?displayProperty=nameWithType>|  
|[<span data-ttu-id="7760d-110">char</span><span class="sxs-lookup"><span data-stu-id="7760d-110">char</span></span>](char.md)|<xref:System.Char?displayProperty=nameWithType>|  
|[<span data-ttu-id="7760d-111">decimal</span><span class="sxs-lookup"><span data-stu-id="7760d-111">decimal</span></span>](decimal.md)|<xref:System.Decimal?displayProperty=nameWithType>|  
|[<span data-ttu-id="7760d-112">double</span><span class="sxs-lookup"><span data-stu-id="7760d-112">double</span></span>](double.md)|<xref:System.Double?displayProperty=nameWithType>|  
|[<span data-ttu-id="7760d-113">float</span><span class="sxs-lookup"><span data-stu-id="7760d-113">float</span></span>](float.md)|<xref:System.Single?displayProperty=nameWithType>|  
|[<span data-ttu-id="7760d-114">int</span><span class="sxs-lookup"><span data-stu-id="7760d-114">int</span></span>](int.md)|<xref:System.Int32?displayProperty=nameWithType>|  
|[<span data-ttu-id="7760d-115">uint</span><span class="sxs-lookup"><span data-stu-id="7760d-115">uint</span></span>](uint.md)|<xref:System.UInt32?displayProperty=nameWithType>|  
|[<span data-ttu-id="7760d-116">long</span><span class="sxs-lookup"><span data-stu-id="7760d-116">long</span></span>](long.md)|<xref:System.Int64?displayProperty=nameWithType>|  
|[<span data-ttu-id="7760d-117">ulong</span><span class="sxs-lookup"><span data-stu-id="7760d-117">ulong</span></span>](ulong.md)|<xref:System.UInt64?displayProperty=nameWithType>|  
|[<span data-ttu-id="7760d-118">object</span><span class="sxs-lookup"><span data-stu-id="7760d-118">object</span></span>](object.md)|<xref:System.Object?displayProperty=nameWithType>|  
|[<span data-ttu-id="7760d-119">short</span><span class="sxs-lookup"><span data-stu-id="7760d-119">short</span></span>](short.md)|<xref:System.Int16?displayProperty=nameWithType>|  
|[<span data-ttu-id="7760d-120">ushort</span><span class="sxs-lookup"><span data-stu-id="7760d-120">ushort</span></span>](ushort.md)|<xref:System.UInt16?displayProperty=nameWithType>|  
|[<span data-ttu-id="7760d-121">string</span><span class="sxs-lookup"><span data-stu-id="7760d-121">string</span></span>](string.md)|<xref:System.String?displayProperty=nameWithType>|  
  
## <a name="remarks"></a><span data-ttu-id="7760d-122">Remarques</span><span class="sxs-lookup"><span data-stu-id="7760d-122">Remarks</span></span>

<span data-ttu-id="7760d-123">Hormis les types `object` et `string`, tous les types listés dans le tableau sont considérés comme des types simples.</span><span class="sxs-lookup"><span data-stu-id="7760d-123">All of the types in the table, except `object` and `string`, are referred to as simple types.</span></span>  
  
<span data-ttu-id="7760d-124">Les mots clés des types C# et leurs alias sont interchangeables.</span><span class="sxs-lookup"><span data-stu-id="7760d-124">The C# type keywords and their aliases are interchangeable.</span></span> <span data-ttu-id="7760d-125">Par exemple, vous pouvez déclarer une variable de type entier à l’aide de l’une des deux déclarations suivantes :</span><span class="sxs-lookup"><span data-stu-id="7760d-125">For example, you can declare an integer variable by using either of the following declarations:</span></span>  

```csharp
int x = 123;
System.Int32 y = 123;
```

<span data-ttu-id="7760d-126">Utilisez l’opérateur [typeof](typeof.md) pour obtenir l’instance de <xref:System.Type?displayProperty=nameWithType>, qui représente le type spécifié :</span><span class="sxs-lookup"><span data-stu-id="7760d-126">Use the [typeof](typeof.md) operator to get the <xref:System.Type?displayProperty=nameWithType> instance that represents the specified type:</span></span>

```csharp
Type stringType = typeof(string);
Console.WriteLine(stringType.FullName);

Type doubleType = typeof(System.Double);
Console.WriteLine(doubleType.FullName);

// Output:
// System.String
// System.Double
```

## <a name="see-also"></a><span data-ttu-id="7760d-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7760d-127">See also</span></span>

- [<span data-ttu-id="7760d-128">Référence C#</span><span class="sxs-lookup"><span data-stu-id="7760d-128">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="7760d-129">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="7760d-129">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="7760d-130">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="7760d-130">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="7760d-131">Types valeur</span><span class="sxs-lookup"><span data-stu-id="7760d-131">Value types</span></span>](value-types.md)
- [<span data-ttu-id="7760d-132">Types référence</span><span class="sxs-lookup"><span data-stu-id="7760d-132">Reference types</span></span>](reference-types.md)
- [<span data-ttu-id="7760d-133">Tableau des valeurs par défaut</span><span class="sxs-lookup"><span data-stu-id="7760d-133">Default values table</span></span>](default-values-table.md)
- [<span data-ttu-id="7760d-134">dynamic</span><span class="sxs-lookup"><span data-stu-id="7760d-134">dynamic</span></span>](dynamic.md)
