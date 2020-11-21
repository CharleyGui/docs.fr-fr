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
# <a name="how-to-convert-a-byte-array-to-an-int-c-programming-guide"></a>Comment convertir un tableau d’octets en int (Guide de programmation C#)

Cet exemple montre comment utiliser la classe <xref:System.BitConverter> pour convertir un tableau d’octets en valeur [int](../../language-reference/builtin-types/integral-numeric-types.md), puis la reconvertir en tableau d’octets. Vous devrez peut-être convertir des octets en un type de données intégré après avoir lu les octets sur le réseau. En plus de la méthode [ToInt32 (Byte \[ \] , Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) dans l’exemple, le tableau suivant répertorie les méthodes de la <xref:System.BitConverter> classe qui convertissent des octets (d’un tableau d’octets) en d’autres types intégrés.

|Type retourné|Méthode|
|-------------------|------------|
|`bool`|[ToBoolean (Byte \[ \] , Int32)](xref:System.BitConverter.ToBoolean(System.Byte[],System.Int32))|
|`char`|[ToChar (Byte \[ \] , Int32)](xref:System.BitConverter.ToChar(System.Byte[],System.Int32))|
|`double`|[ToDouble (Byte \[ \] , Int32)](xref:System.BitConverter.ToDouble(System.Byte[],System.Int32))|
|`short`|[Toint16 ((Byte \[ \] , Int32)](xref:System.BitConverter.ToInt16(System.Byte[],System.Int32))|
|`int`|[ToInt32 (Byte \[ \] , Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))|
|`long`|[Toint64 ((Byte \[ \] , Int32)](xref:System.BitConverter.ToInt64(System.Byte[],System.Int32))|
|`float`|[ToSingle (Byte \[ \] , Int32)](xref:System.BitConverter.ToSingle(System.Byte[],System.Int32))|
|`ushort`|[Touint16 ((Byte \[ \] , Int32)](xref:System.BitConverter.ToUInt16(System.Byte[],System.Int32))|
|`uint`|[Touint32 ((Byte \[ \] , Int32)](xref:System.BitConverter.ToUInt32(System.Byte[],System.Int32))|
|`ulong`|[Touint64 ((Byte \[ \] , Int32)](xref:System.BitConverter.ToUInt64(System.Byte[],System.Int32))|

## <a name="example"></a>Exemple

Cet exemple Initialise un tableau d’octets, inverse le tableau si l’architecture de l’ordinateur est Little-endian (autrement dit, l’octet le moins significatif est stocké en premier), puis appelle la méthode [ToInt32 (Byte \[ \] , Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) pour convertir quatre octets dans le tableau en un `int` . Le deuxième argument de [ToInt32 (Byte \[ \] , Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) spécifie l’index de début du tableau d’octets.

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
