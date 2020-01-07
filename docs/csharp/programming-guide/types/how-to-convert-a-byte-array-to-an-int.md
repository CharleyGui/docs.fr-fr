---
title: Comment convertir un tableau d’octets en un guide de C# programmation int
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- conversions [C#], byte array to int
- byte arrays [C#], converting to int
ms.assetid: d6ac20e2-448e-4aea-99b9-faf04c6f1e79
ms.openlocfilehash: a553d8778997a2323c54c72be8e68aff590a7c7d
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635052"
---
# <a name="how-to-convert-a-byte-array-to-an-int-c-programming-guide"></a>Comment convertir un tableau d’octets en int (C# Guide de programmation)

Cet exemple montre comment utiliser la classe <xref:System.BitConverter> pour convertir un tableau d’octets en valeur [int](../../language-reference/builtin-types/integral-numeric-types.md), puis la reconvertir en tableau d’octets. Vous devrez peut-être convertir des octets en un type de données intégré après avoir lu les octets sur le réseau. En plus de la méthode [ToInt32 (Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) dans l’exemple, le tableau suivant répertorie les méthodes de la classe <xref:System.BitConverter> qui convertissent des octets (d’un tableau d’octets) en d’autres types intégrés.

|Type retourné|Méthode|
|-------------------|------------|
|`bool`|[ToBoolean (Byte\[\], Int32)](xref:System.BitConverter.ToBoolean(System.Byte[],System.Int32))|
|`char`|[ToChar (Byte\[\], Int32)](xref:System.BitConverter.ToChar(System.Byte[],System.Int32))|
|`double`|[ToDouble (Byte\[\], Int32)](xref:System.BitConverter.ToDouble(System.Byte[],System.Int32))|
|`short`|[Toint16 ((Byte\[\], Int32)](xref:System.BitConverter.ToInt16(System.Byte[],System.Int32))|
|`int`|[ToInt32 (Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))|
|`long`|[Toint64 ((Byte\[\], Int32)](xref:System.BitConverter.ToInt64(System.Byte[],System.Int32))|
|`float`|[ToSingle (Byte\[\], Int32)](xref:System.BitConverter.ToSingle(System.Byte[],System.Int32))|
|`ushort`|[Touint16 ((Byte\[\], Int32)](xref:System.BitConverter.ToUInt16(System.Byte[],System.Int32))|
|`uint`|[Touint32 ((Byte\[\], Int32)](xref:System.BitConverter.ToUInt32(System.Byte[],System.Int32))|
|`ulong`|[Touint64 ((Byte\[\], Int32)](xref:System.BitConverter.ToUInt64(System.Byte[],System.Int32))|

## <a name="example"></a>Exemple

Cet exemple Initialise un tableau d’octets, inverse le tableau si l’architecture de l’ordinateur est Little-endian (autrement dit, l’octet le moins significatif est stocké en premier), puis appelle la méthode [ToInt32 (byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) pour convertir quatre octets du tableau en un `int`. Le deuxième argument de [ToInt32 (Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) spécifie l’index de début du tableau d’octets.

> [!NOTE]
> La sortie peut différer selon le endianness de l’architecture de votre ordinateur.

[!code-csharp[csProgGuideTypes#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#22)]

## <a name="example"></a>Exemple

Dans cet exemple, la méthode <xref:System.BitConverter.GetBytes%28System.Int32%29> de la classe <xref:System.BitConverter> est appelée pour convertir une valeur `int` en tableau d’octets.

> [!NOTE]
> La sortie peut différer selon le endianness de l’architecture de votre ordinateur.

[!code-csharp[csProgGuideTypes#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#23)]

## <a name="see-also"></a>Voir aussi

- <xref:System.BitConverter>
- <xref:System.BitConverter.IsLittleEndian>
- [Types](./index.md)
