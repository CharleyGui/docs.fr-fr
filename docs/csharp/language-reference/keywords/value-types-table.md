---
title: Tableau des types valeur - Référence C#
ms.custom: seodec18
ms.date: 08/24/2018
helpviewer_keywords:
- value types [C#], table
- types [C#], value types
- types [C#], suffixes
ms.assetid: 67d8f631-b6e3-4d83-9910-5ec497f8c5f3
ms.openlocfilehash: 2e2897ff647140b58b3a1812e153a44a6fcdaef7
ms.sourcegitcommit: 83ecdf731dc1920bca31f017b1556c917aafd7a0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/12/2019
ms.locfileid: "67859561"
---
# <a name="value-types-table-c-reference"></a>Tableau des types valeur (référence C#)

Le tableau suivant présente les types valeur dans C# :

|Type de valeur|Category|Suffixe du type|
|----------------|--------------|-----------------|
|[bool](bool.md)|Booléen||
|`byte`|Non signé, numérique, [intégral](../builtin-types/integral-numeric-types.md)||
|[char](char.md)|Non signé, numérique, [intégral](../builtin-types/integral-numeric-types.md)
|`decimal`|Numérique, [virgule flottante](../builtin-types/floating-point-numeric-types.md)|M ou m|
|`double`|Numérique, [virgule flottante](../builtin-types/floating-point-numeric-types.md)|D ou d|
|[enum](enum.md)|Énumération||
|`float`|Numérique, [virgule flottante](../builtin-types/floating-point-numeric-types.md)|F ou f|
|`int`|Signé, numérique, [intégral](../builtin-types/integral-numeric-types.md)||
|`long`|Signé, numérique, [intégral](../builtin-types/integral-numeric-types.md)|L ou l|
|`sbyte`|Signé, numérique, [intégral](../builtin-types/integral-numeric-types.md)||
|`short`|Signé, numérique, [intégral](../builtin-types/integral-numeric-types.md)||
|[struct](struct.md)|Structure définie par l’utilisateur||
|`uint`|Non signé, numérique, [intégral](../builtin-types/integral-numeric-types.md)|U ou u|
|`ulong`|Non signé, numérique, [intégral](../builtin-types/integral-numeric-types.md)|UL, Ul, uL, ul, LU, Lu, lU ou lu|
|`ushort`|Non signé, numérique, [intégral](../builtin-types/integral-numeric-types.md)||

## <a name="remarks"></a>Remarques

Utilisez un suffixe de type pour spécifier un type d’un littéral numérique. Par exemple :

```csharp
decimal a = 0.1M;
```

Quand un [littéral numérique entier](~/_csharplang/spec/lexical-structure.md#integer-literals) n’a pas de suffixe, il a le premier type parmi les types suivants où sa valeur peut être représentée : `int`, `uint`, `long`, `ulong`.

Si un [littéral numérique réel](~/_csharplang/spec/lexical-structure.md#real-literals) n’a pas de suffixe, il a le type `double`.

## <a name="see-also"></a>Voir aussi

- [Référence C#](../index.md)
- [Guide de programmation C#](../../programming-guide/index.md)
- [Tableau des valeurs par défaut](default-values-table.md)
- [Types valeur](value-types.md)
- [Tableau des formats des résultats numériques](formatting-numeric-results-table.md)
