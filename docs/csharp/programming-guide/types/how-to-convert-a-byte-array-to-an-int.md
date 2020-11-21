---
title: Comment convertir un tableau d’octets en Guide de programmation int-C#
description: Découvrez comment convertir un tableau d’octets en int. Consultez des exemples de code et affichez des ressources disponibles supplémentaires.
ms.date: 07/20/2015
helpviewer_keywords:
- conversions [C#], byte array to int
- byte arrays [C#], converting to int
ms.topic: how-to
ms.custom: contperfq2
ms.assetid: d6ac20e2-448e-4aea-99b9-faf04c6f1e79
ms.openlocfilehash: a339766313678590cb80263ba5b2ff328c018a58
ms.sourcegitcommit: 30e9e11dfd90112b8eec6406186ba3533f21eba1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2020
ms.locfileid: "95099183"
---
# <a name="how-to-convert-a-byte-array-to-an-int-c-programming-guide"></a><span data-ttu-id="c66a2-103">Comment convertir un tableau d’octets en int (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="c66a2-103">How to convert a byte array to an int (C# Programming Guide)</span></span>

<span data-ttu-id="c66a2-104">Cet exemple montre comment utiliser la classe <xref:System.BitConverter> pour convertir un tableau d’octets en valeur [int](../../language-reference/builtin-types/integral-numeric-types.md), puis la reconvertir en tableau d’octets.</span><span class="sxs-lookup"><span data-stu-id="c66a2-104">This example shows you how to use the <xref:System.BitConverter> class to convert an array of bytes to an [int](../../language-reference/builtin-types/integral-numeric-types.md) and back to an array of bytes.</span></span> <span data-ttu-id="c66a2-105">Vous devrez peut-être convertir des octets en un type de données intégré après avoir lu les octets sur le réseau.</span><span class="sxs-lookup"><span data-stu-id="c66a2-105">You may have to convert from bytes to a built-in data type after you read bytes off the network, for example.</span></span> <span data-ttu-id="c66a2-106">En plus de la méthode [ToInt32 (Byte \[ \] , Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) dans l’exemple, le tableau suivant répertorie les méthodes de la <xref:System.BitConverter> classe qui convertissent des octets (d’un tableau d’octets) en d’autres types intégrés.</span><span class="sxs-lookup"><span data-stu-id="c66a2-106">In addition to the [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) method in the example, the following table lists methods in the <xref:System.BitConverter> class that convert bytes (from an array of bytes) to other built-in types.</span></span>

|<span data-ttu-id="c66a2-107">Type retourné</span><span class="sxs-lookup"><span data-stu-id="c66a2-107">Type returned</span></span>|<span data-ttu-id="c66a2-108">Méthode</span><span class="sxs-lookup"><span data-stu-id="c66a2-108">Method</span></span>|
|-------------------|------------|
|`bool`|<span data-ttu-id="c66a2-109">[ToBoolean (Byte \[ \] , Int32)](xref:System.BitConverter.ToBoolean(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="c66a2-109">[ToBoolean(Byte\[\], Int32)](xref:System.BitConverter.ToBoolean(System.Byte[],System.Int32))</span></span>|
|`char`|<span data-ttu-id="c66a2-110">[ToChar (Byte \[ \] , Int32)](xref:System.BitConverter.ToChar(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="c66a2-110">[ToChar(Byte\[\], Int32)](xref:System.BitConverter.ToChar(System.Byte[],System.Int32))</span></span>|
|`double`|<span data-ttu-id="c66a2-111">[ToDouble (Byte \[ \] , Int32)](xref:System.BitConverter.ToDouble(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="c66a2-111">[ToDouble(Byte\[\], Int32)](xref:System.BitConverter.ToDouble(System.Byte[],System.Int32))</span></span>|
|`short`|<span data-ttu-id="c66a2-112">[Toint16 ((Byte \[ \] , Int32)](xref:System.BitConverter.ToInt16(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="c66a2-112">[ToInt16(Byte\[\], Int32)](xref:System.BitConverter.ToInt16(System.Byte[],System.Int32))</span></span>|
|`int`|<span data-ttu-id="c66a2-113">[ToInt32 (Byte \[ \] , Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="c66a2-113">[ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))</span></span>|
|`long`|<span data-ttu-id="c66a2-114">[Toint64 ((Byte \[ \] , Int32)](xref:System.BitConverter.ToInt64(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="c66a2-114">[ToInt64(Byte\[\], Int32)](xref:System.BitConverter.ToInt64(System.Byte[],System.Int32))</span></span>|
|`float`|<span data-ttu-id="c66a2-115">[ToSingle (Byte \[ \] , Int32)](xref:System.BitConverter.ToSingle(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="c66a2-115">[ToSingle(Byte\[\], Int32)](xref:System.BitConverter.ToSingle(System.Byte[],System.Int32))</span></span>|
|`ushort`|<span data-ttu-id="c66a2-116">[Touint16 ((Byte \[ \] , Int32)](xref:System.BitConverter.ToUInt16(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="c66a2-116">[ToUInt16(Byte\[\], Int32)](xref:System.BitConverter.ToUInt16(System.Byte[],System.Int32))</span></span>|
|`uint`|<span data-ttu-id="c66a2-117">[Touint32 ((Byte \[ \] , Int32)](xref:System.BitConverter.ToUInt32(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="c66a2-117">[ToUInt32(Byte\[\], Int32)](xref:System.BitConverter.ToUInt32(System.Byte[],System.Int32))</span></span>|
|`ulong`|<span data-ttu-id="c66a2-118">[Touint64 ((Byte \[ \] , Int32)](xref:System.BitConverter.ToUInt64(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="c66a2-118">[ToUInt64(Byte\[\], Int32)](xref:System.BitConverter.ToUInt64(System.Byte[],System.Int32))</span></span>|

## <a name="example"></a><span data-ttu-id="c66a2-119">Exemple</span><span class="sxs-lookup"><span data-stu-id="c66a2-119">Example</span></span>

<span data-ttu-id="c66a2-120">Cet exemple Initialise un tableau d’octets, inverse le tableau si l’architecture de l’ordinateur est Little-endian (autrement dit, l’octet le moins significatif est stocké en premier), puis appelle la méthode [ToInt32 (Byte \[ \] , Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) pour convertir quatre octets dans le tableau en un `int` .</span><span class="sxs-lookup"><span data-stu-id="c66a2-120">This example initializes an array of bytes, reverses the array if the computer architecture is little-endian (that is, the least significant byte is stored first), and then calls the [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) method to convert four bytes in the array to an `int`.</span></span> <span data-ttu-id="c66a2-121">Le deuxième argument de [ToInt32 (Byte \[ \] , Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) spécifie l’index de début du tableau d’octets.</span><span class="sxs-lookup"><span data-stu-id="c66a2-121">The second argument to [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) specifies the start index of the array of bytes.</span></span>

> [!NOTE]
> <span data-ttu-id="c66a2-122">La sortie peut différer selon le endianness de l’architecture de votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="c66a2-122">The output may differ depending on the endianness of your computer's architecture.</span></span>

[!code-csharp[csProgGuideTypes#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#22)]

## <a name="example"></a><span data-ttu-id="c66a2-123">Exemple</span><span class="sxs-lookup"><span data-stu-id="c66a2-123">Example</span></span>

<span data-ttu-id="c66a2-124">Dans cet exemple, la méthode <xref:System.BitConverter.GetBytes%28System.Int32%29> de la classe <xref:System.BitConverter> est appelée pour convertir une valeur `int` en tableau d’octets.</span><span class="sxs-lookup"><span data-stu-id="c66a2-124">In this example, the <xref:System.BitConverter.GetBytes%28System.Int32%29> method of the <xref:System.BitConverter> class is called to convert an `int` to an array of bytes.</span></span>

> [!NOTE]
> <span data-ttu-id="c66a2-125">La sortie peut différer selon le endianness de l’architecture de votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="c66a2-125">The output may differ depending on the endianness of your computer's architecture.</span></span>

[!code-csharp[csProgGuideTypes#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#23)]

## <a name="see-also"></a><span data-ttu-id="c66a2-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c66a2-126">See also</span></span>

- <xref:System.BitConverter>
- <xref:System.BitConverter.IsLittleEndian>
- [<span data-ttu-id="c66a2-127">Types</span><span class="sxs-lookup"><span data-stu-id="c66a2-127">Types</span></span>](./index.md)
