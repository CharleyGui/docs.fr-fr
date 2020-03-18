---
title: Comment convertir un tableau d’ente en un guide de programmation int - C
ms.date: 07/20/2015
helpviewer_keywords:
- conversions [C#], byte array to int
- byte arrays [C#], converting to int
ms.assetid: d6ac20e2-448e-4aea-99b9-faf04c6f1e79
ms.openlocfilehash: 9f477649dba1b42d7a10d521c010977707daf3ec
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75698753"
---
# <a name="how-to-convert-a-byte-array-to-an-int-c-programming-guide"></a><span data-ttu-id="92706-102">Comment convertir un tableau d’en-l’et l’autre en un guide de programmation int (C)</span><span class="sxs-lookup"><span data-stu-id="92706-102">How to convert a byte array to an int (C# Programming Guide)</span></span>

<span data-ttu-id="92706-103">Cet exemple montre comment utiliser la classe <xref:System.BitConverter> pour convertir un tableau d’octets en valeur [int](../../language-reference/builtin-types/integral-numeric-types.md), puis la reconvertir en tableau d’octets.</span><span class="sxs-lookup"><span data-stu-id="92706-103">This example shows you how to use the <xref:System.BitConverter> class to convert an array of bytes to an [int](../../language-reference/builtin-types/integral-numeric-types.md) and back to an array of bytes.</span></span> <span data-ttu-id="92706-104">Vous devrez peut-être convertir des octets en un type de données intégré après avoir lu les octets sur le réseau.</span><span class="sxs-lookup"><span data-stu-id="92706-104">You may have to convert from bytes to a built-in data type after you read bytes off the network, for example.</span></span> <span data-ttu-id="92706-105">En plus de la méthode [ToInt32 (Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) dans <xref:System.BitConverter> l’exemple, le tableau suivant répertorie les méthodes de la classe qui convertissent les octets (d’une gamme d’octets) à d’autres types intégrés.</span><span class="sxs-lookup"><span data-stu-id="92706-105">In addition to the [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) method in the example, the following table lists methods in the <xref:System.BitConverter> class that convert bytes (from an array of bytes) to other built-in types.</span></span>

|<span data-ttu-id="92706-106">Type retourné</span><span class="sxs-lookup"><span data-stu-id="92706-106">Type returned</span></span>|<span data-ttu-id="92706-107">Méthode</span><span class="sxs-lookup"><span data-stu-id="92706-107">Method</span></span>|
|-------------------|------------|
|`bool`|<span data-ttu-id="92706-108">[ToBoolean (Byte\[\], Int32)](xref:System.BitConverter.ToBoolean(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="92706-108">[ToBoolean(Byte\[\], Int32)](xref:System.BitConverter.ToBoolean(System.Byte[],System.Int32))</span></span>|
|`char`|<span data-ttu-id="92706-109">[ToChar (Byte\[\], Int32)](xref:System.BitConverter.ToChar(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="92706-109">[ToChar(Byte\[\], Int32)](xref:System.BitConverter.ToChar(System.Byte[],System.Int32))</span></span>|
|`double`|<span data-ttu-id="92706-110">[ToDouble (Byte\[\], Int32)](xref:System.BitConverter.ToDouble(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="92706-110">[ToDouble(Byte\[\], Int32)](xref:System.BitConverter.ToDouble(System.Byte[],System.Int32))</span></span>|
|`short`|<span data-ttu-id="92706-111">[ToInt16 (Byte\[\], Int32)](xref:System.BitConverter.ToInt16(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="92706-111">[ToInt16(Byte\[\], Int32)](xref:System.BitConverter.ToInt16(System.Byte[],System.Int32))</span></span>|
|`int`|<span data-ttu-id="92706-112">[ToInt32 (Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="92706-112">[ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))</span></span>|
|`long`|<span data-ttu-id="92706-113">[ToInt64 (Byte\[\], Int32)](xref:System.BitConverter.ToInt64(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="92706-113">[ToInt64(Byte\[\], Int32)](xref:System.BitConverter.ToInt64(System.Byte[],System.Int32))</span></span>|
|`float`|<span data-ttu-id="92706-114">[ToSingle (Byte\[\], Int32)](xref:System.BitConverter.ToSingle(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="92706-114">[ToSingle(Byte\[\], Int32)](xref:System.BitConverter.ToSingle(System.Byte[],System.Int32))</span></span>|
|`ushort`|<span data-ttu-id="92706-115">[ToUInt16 (Byte\[\], Int32)](xref:System.BitConverter.ToUInt16(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="92706-115">[ToUInt16(Byte\[\], Int32)](xref:System.BitConverter.ToUInt16(System.Byte[],System.Int32))</span></span>|
|`uint`|<span data-ttu-id="92706-116">[ToUInt32 (Byte\[\], Int32)](xref:System.BitConverter.ToUInt32(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="92706-116">[ToUInt32(Byte\[\], Int32)](xref:System.BitConverter.ToUInt32(System.Byte[],System.Int32))</span></span>|
|`ulong`|<span data-ttu-id="92706-117">[ToUInt64 (Byte\[\], Int32)](xref:System.BitConverter.ToUInt64(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="92706-117">[ToUInt64(Byte\[\], Int32)](xref:System.BitConverter.ToUInt64(System.Byte[],System.Int32))</span></span>|

## <a name="example"></a><span data-ttu-id="92706-118"> Exemple</span><span class="sxs-lookup"><span data-stu-id="92706-118">Example</span></span>

<span data-ttu-id="92706-119">Cet exemple initialise un tableau d’octets, inverse le tableau si l’architecture informatique est peu-endienne (c’est-à-dire, le octet le moins significatif est stocké en `int`premier), puis appelle la méthode [ToInt32 (Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) pour convertir quatre octets dans le tableau en un .</span><span class="sxs-lookup"><span data-stu-id="92706-119">This example initializes an array of bytes, reverses the array if the computer architecture is little-endian (that is, the least significant byte is stored first), and then calls the [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) method to convert four bytes in the array to an `int`.</span></span> <span data-ttu-id="92706-120">Le deuxième argument à [ToInt32 (Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) spécifie l’indice de départ de la gamme d’octets.</span><span class="sxs-lookup"><span data-stu-id="92706-120">The second argument to [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) specifies the start index of the array of bytes.</span></span>

> [!NOTE]
> <span data-ttu-id="92706-121">La sortie peut différer en fonction de l’endianness de l’architecture de votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="92706-121">The output may differ depending on the endianness of your computer's architecture.</span></span>

[!code-csharp[csProgGuideTypes#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#22)]

## <a name="example"></a><span data-ttu-id="92706-122"> Exemple</span><span class="sxs-lookup"><span data-stu-id="92706-122">Example</span></span>

<span data-ttu-id="92706-123">Dans cet exemple, la méthode <xref:System.BitConverter.GetBytes%28System.Int32%29> de la classe <xref:System.BitConverter> est appelée pour convertir une valeur `int` en tableau d’octets.</span><span class="sxs-lookup"><span data-stu-id="92706-123">In this example, the <xref:System.BitConverter.GetBytes%28System.Int32%29> method of the <xref:System.BitConverter> class is called to convert an `int` to an array of bytes.</span></span>

> [!NOTE]
> <span data-ttu-id="92706-124">La sortie peut différer en fonction de l’endianness de l’architecture de votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="92706-124">The output may differ depending on the endianness of your computer's architecture.</span></span>

[!code-csharp[csProgGuideTypes#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#23)]

## <a name="see-also"></a><span data-ttu-id="92706-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="92706-125">See also</span></span>

- <xref:System.BitConverter>
- <xref:System.BitConverter.IsLittleEndian>
- [<span data-ttu-id="92706-126">Types</span><span class="sxs-lookup"><span data-stu-id="92706-126">Types</span></span>](./index.md)
