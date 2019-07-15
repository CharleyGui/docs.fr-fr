---
title: Tableau des types intégrés - Référence C#
ms.custom: seodec18
description: Mots clés pour les types C# intégrés
ms.date: 08/17/2018
helpviewer_keywords:
- types [C#], built-in
- built-in C# types
ms.assetid: 54f901f2-bf2f-472c-ae8d-73e8ecfc57fe
ms.openlocfilehash: e770c305afe098e633700b039efb51770c77ada7
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67661449"
---
# <a name="built-in-types-table-c-reference"></a>Tableau des types intégrés (référence C#)

Le tableau suivant liste les mots clés des types C# intégrés, qui sont des alias des types prédéfinis de l’espace de noms <xref:System>.  
  
|Type C#|Type .NET|  
|--------------|-------------------------|  
|[bool](bool.md)|<xref:System.Boolean?displayProperty=nameWithType>|  
|[byte](../builtin-types/integral-numeric-types.md)|<xref:System.Byte?displayProperty=nameWithType>|  
|[sbyte](../builtin-types/integral-numeric-types.md)|<xref:System.SByte?displayProperty=nameWithType>|  
|[char](char.md)|<xref:System.Char?displayProperty=nameWithType>|  
|[decimal](../builtin-types/floating-point-numeric-types.md)|<xref:System.Decimal?displayProperty=nameWithType>|  
|[double](../builtin-types/floating-point-numeric-types.md)|<xref:System.Double?displayProperty=nameWithType>|  
|[float](../builtin-types/floating-point-numeric-types.md)|<xref:System.Single?displayProperty=nameWithType>|  
|[int](../builtin-types/integral-numeric-types.md)|<xref:System.Int32?displayProperty=nameWithType>|  
|[uint](../builtin-types/integral-numeric-types.md)|<xref:System.UInt32?displayProperty=nameWithType>|  
|[long](../builtin-types/integral-numeric-types.md)|<xref:System.Int64?displayProperty=nameWithType>|  
|[ulong](../builtin-types/integral-numeric-types.md)|<xref:System.UInt64?displayProperty=nameWithType>|  
|[object](object.md)|<xref:System.Object?displayProperty=nameWithType>|  
|[short](../builtin-types/integral-numeric-types.md)|<xref:System.Int16?displayProperty=nameWithType>|  
|[ushort](../builtin-types/integral-numeric-types.md)|<xref:System.UInt16?displayProperty=nameWithType>|  
|[string](string.md)|<xref:System.String?displayProperty=nameWithType>|  
  
## <a name="remarks"></a>Remarques

Hormis les types `object` et `string`, tous les types listés dans le tableau sont considérés comme des types simples.  
  
Les mots clés des types C# et leurs alias sont interchangeables. Par exemple, vous pouvez déclarer une variable de type entier à l’aide de l’une des deux déclarations suivantes :  

```csharp
int x = 123;
System.Int32 y = 123;
```

Utilisez l’opérateur [typeof](../operators/type-testing-and-conversion-operators.md#typeof-operator) pour obtenir l’instance de <xref:System.Type?displayProperty=nameWithType>, qui représente le type spécifié :

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
