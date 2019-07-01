---
title: Tableau des types valeur - Référence C#
ms.custom: seodec18
ms.date: 08/24/2018
helpviewer_keywords:
- value types [C#], table
- types [C#], value types
- types [C#], suffixes
ms.assetid: 67d8f631-b6e3-4d83-9910-5ec497f8c5f3
ms.openlocfilehash: 98829f30c2c25c0710cf3fe044359d3c7538fe76
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67424038"
---
# <a name="value-types-table-c-reference"></a>Tableau des types valeur (référence C#)

Le tableau suivant présente les types valeur dans C# :

|Type de valeur|Category|Suffixe du type|
|----------------|--------------|-----------------|
|[bool](bool.md)|Booléen||
|[byte](../builtin-types/integral-numeric-types.md)|Non signé, numérique, [intégral](../builtin-types/integral-numeric-types.md)||
|[char](char.md)|Non signé, numérique, [intégral](../builtin-types/integral-numeric-types.md)
)||
|[decimal](decimal.md)|Numérique, [virgule flottante](floating-point-types-table.md)|M ou m|
|[double](double.md)|Numérique, [virgule flottante](floating-point-types-table.md)|D ou d|
|[enum](enum.md)|Énumération||
|[float](float.md)|Numérique, [virgule flottante](floating-point-types-table.md)|F ou f|
|[int](../builtin-types/integral-numeric-types.md)|Signé, numérique, [intégral](../builtin-types/integral-numeric-types.md)||
|[long](../builtin-types/integral-numeric-types.md)|Signé, numérique, [intégral](../builtin-types/integral-numeric-types.md)|L ou l|
|[sbyte](../builtin-types/integral-numeric-types.md)|Signé, numérique, [intégral](../builtin-types/integral-numeric-types.md)||
|[short](../builtin-types/integral-numeric-types.md)|Signé, numérique, [intégral](../builtin-types/integral-numeric-types.md)||
|[struct](struct.md)|Structure définie par l’utilisateur||
|[uint](../builtin-types/integral-numeric-types.md)|Non signé, numérique, [intégral](../builtin-types/integral-numeric-types.md)|U ou u|
|[ulong](../builtin-types/integral-numeric-types.md)|Non signé, numérique, [intégral](../builtin-types/integral-numeric-types.md)|UL, Ul, uL, ul, LU, Lu, lU ou lu|
|[ushort](../builtin-types/integral-numeric-types.md)|Non signé, numérique, [intégral](../builtin-types/integral-numeric-types.md)||

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
