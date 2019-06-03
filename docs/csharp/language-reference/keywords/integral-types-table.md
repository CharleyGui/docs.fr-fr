---
title: Tableau des types intégraux - Référence C#
ms.custom: seodec18
description: Vue d’ensemble des types intégraux C# intégrés
ms.date: 08/20/2018
helpviewer_keywords:
- integral types, C#
- Visual C#, integral types
- types [C#], integral types
- ranges of integral types [C#]
ms.assetid: 62e86126-46ff-40b0-9028-e61d7558268c
ms.openlocfilehash: b4a3a46ba98c0c621b747284ce39e03d68a5b62d
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66421729"
---
# <a name="integral-types-table-c-reference"></a>Tableau des types intégraux (référence C#)

Le tableau suivant indique les tailles et les plages des types intégraux, qui constituent un sous-ensemble des types simples.  
  
|Type|Plage|Size|  
|----------|-----------|----------|  
|[sbyte](sbyte.md)|-128 à 127|Entier 8 bits signé|  
|[byte](byte.md)|0 à 255|Entier 8 bits non signé|  
|[char](char.md)|U+0000 à U+ffff|Caractère Unicode 16 bits|  
|[short](short.md)|de -32 768 à 32 767|Entier 16 bits signé|  
|[ushort](ushort.md)|0 à 65 535|Entier 16 bits non signé|  
|[int](int.md)|-2,147,483,648 en 2,147,483,647|Entier 32 bits signé|  
|[uint](uint.md)|de 0 à 4 294 967 295|Entier 32 bits non signé|  
|[long](long.md)|-9 223 372 036 854 775 808 à 9 223 372 036 854 775 807|Entier 64 bits signé|  
|[ulong](ulong.md)|de 0 à 18 446 744 073 709 551 615|Entier 64 bits non signé|  

## <a name="remarks"></a>Remarques
  
Si la valeur représentée par un littéral entier dépasse <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, une erreur de compilation [CS1021](../../misc/cs1021.md) se produit.

Utilisez la structure <xref:System.Numerics.BigInteger?displayProperty=nameWithType> pour représenter un entier signé arbitrairement grand.
  
## <a name="see-also"></a>Voir aussi

- [Référence C#](../index.md)
- [Guide de programmation C#](../../programming-guide/index.md)
- [Mots clés C#](index.md)
- [Tableau des types à virgule flottante](floating-point-types-table.md)
- [Tableau des valeurs par défaut](default-values-table.md)
- [Tableau des formats des résultats numériques](formatting-numeric-results-table.md)
- [Tableaux des types intégrés](built-in-types-table.md)
- [Valeurs numériques dans .NET](../../../standard/numerics.md)
