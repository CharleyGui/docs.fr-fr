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
# <a name="built-in-types-table-c-reference"></a>Tableau des types intégrés (référence C#)

Le tableau suivant liste les mots clés des types C# intégrés, qui sont des alias des types prédéfinis de l’espace de noms <xref:System>.  
  
|Type C#|Type .NET|  
|--------------|-------------------------|  
|[bool](bool.md)|<xref:System.Boolean?displayProperty=nameWithType>|  
|[byte](byte.md)|<xref:System.Byte?displayProperty=nameWithType>|  
|[sbyte](sbyte.md)|<xref:System.SByte?displayProperty=nameWithType>|  
|[char](char.md)|<xref:System.Char?displayProperty=nameWithType>|  
|[decimal](decimal.md)|<xref:System.Decimal?displayProperty=nameWithType>|  
|[double](double.md)|<xref:System.Double?displayProperty=nameWithType>|  
|[float](float.md)|<xref:System.Single?displayProperty=nameWithType>|  
|[int](int.md)|<xref:System.Int32?displayProperty=nameWithType>|  
|[uint](uint.md)|<xref:System.UInt32?displayProperty=nameWithType>|  
|[long](long.md)|<xref:System.Int64?displayProperty=nameWithType>|  
|[ulong](ulong.md)|<xref:System.UInt64?displayProperty=nameWithType>|  
|[object](object.md)|<xref:System.Object?displayProperty=nameWithType>|  
|[short](short.md)|<xref:System.Int16?displayProperty=nameWithType>|  
|[ushort](ushort.md)|<xref:System.UInt16?displayProperty=nameWithType>|  
|[string](string.md)|<xref:System.String?displayProperty=nameWithType>|  
  
## <a name="remarks"></a>Remarques

Hormis les types `object` et `string`, tous les types listés dans le tableau sont considérés comme des types simples.  
  
Les mots clés des types C# et leurs alias sont interchangeables. Par exemple, vous pouvez déclarer une variable de type entier à l’aide de l’une des deux déclarations suivantes :  

```csharp
int x = 123;
System.Int32 y = 123;
```

Utilisez l’opérateur [typeof](typeof.md) pour obtenir l’instance de <xref:System.Type?displayProperty=nameWithType>, qui représente le type spécifié :

```csharp
Type stringType = typeof(string);
Console.WriteLine(stringType.FullName);

Type doubleType = typeof(System.Double);
Console.WriteLine(doubleType.FullName);

// Output:
// System.String
// System.Double
```

## <a name="see-also"></a>Voir aussi

- [Référence C#](../../../csharp/language-reference/index.md)
- [Guide de programmation C#](../../../csharp/programming-guide/index.md)
- [Mots clés C#](index.md)
- [Types valeur](value-types.md)
- [Types référence](reference-types.md)
- [Tableau des valeurs par défaut](default-values-table.md)
- [dynamic](dynamic.md)
