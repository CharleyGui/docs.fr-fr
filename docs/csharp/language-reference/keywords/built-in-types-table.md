---
title: Tableau des types intégrés - Référence C#
description: Mots clés pour les types C# intégrés
ms.date: 08/17/2018
helpviewer_keywords:
- types [C#], built-in
- built-in C# types
ms.assetid: 54f901f2-bf2f-472c-ae8d-73e8ecfc57fe
ms.openlocfilehash: f26da848d58426472d2c2ab755ecadfd267b096a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734483"
---
# <a name="built-in-types-table-c-reference"></a>Tableau des types intégrés (référence C#)

Le tableau suivant présente les mots clés des C# types intégrés, qui sont des alias de types prédéfinis dans l’espace de noms <xref:System> :

|Type C#|Type .NET|  
|--------------|-------------------------|  
|[bool](../builtin-types/bool.md)|<xref:System.Boolean?displayProperty=nameWithType>|  
|[byte](../builtin-types/integral-numeric-types.md)|<xref:System.Byte?displayProperty=nameWithType>|  
|[sbyte](../builtin-types/integral-numeric-types.md)|<xref:System.SByte?displayProperty=nameWithType>|  
|[char](../builtin-types/char.md)|<xref:System.Char?displayProperty=nameWithType>|  
|[decimal](../builtin-types/floating-point-numeric-types.md)|<xref:System.Decimal?displayProperty=nameWithType>|  
|[double](../builtin-types/floating-point-numeric-types.md)|<xref:System.Double?displayProperty=nameWithType>|  
|[float](../builtin-types/floating-point-numeric-types.md)|<xref:System.Single?displayProperty=nameWithType>|  
|[int](../builtin-types/integral-numeric-types.md)|<xref:System.Int32?displayProperty=nameWithType>|  
|[uint](../builtin-types/integral-numeric-types.md)|<xref:System.UInt32?displayProperty=nameWithType>|  
|[long](../builtin-types/integral-numeric-types.md)|<xref:System.Int64?displayProperty=nameWithType>|  
|[ulong](../builtin-types/integral-numeric-types.md)|<xref:System.UInt64?displayProperty=nameWithType>|  
|[object](../builtin-types/reference-types.md)|<xref:System.Object?displayProperty=nameWithType>|  
|[short](../builtin-types/integral-numeric-types.md)|<xref:System.Int16?displayProperty=nameWithType>|  
|[ushort](../builtin-types/integral-numeric-types.md)|<xref:System.UInt16?displayProperty=nameWithType>|  
|[string](../builtin-types/reference-types.md)|<xref:System.String?displayProperty=nameWithType>|  
  
## <a name="remarks"></a>Notes

Hormis les types `object` et `string`, tous les types listés dans le tableau sont considérés comme des types simples.

Les types .NET et leurs alias de mots clés de type C# sont interchangeables. Par exemple, vous pouvez déclarer une variable de type entier à l’aide de l’une des deux déclarations suivantes :

```csharp
int x = 123;
System.Int32 y = 123;
```

Utilisez l’opérateur [typeof](../operators/type-testing-and-cast.md#typeof-operator) pour obtenir l’instance de <xref:System.Type?displayProperty=nameWithType>, qui représente le type spécifié :

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

- [Référence C#](../index.md)
- [Mots clés C#](index.md)
- [Types valeur](../builtin-types/value-types.md)
- [Types référence](reference-types.md)
- [Valeurs par défaut C# des types](../builtin-types/default-values.md)
- [dynamic](../builtin-types/reference-types.md#the-dynamic-type)
