---
title: Opérateurs au niveau du bit
description: En savoir plus sur les opérateurs de bits qui sont disponibles dans le F# langage de programmation.
ms.date: 07/20/2018
ms.openlocfilehash: e4d61492ba94d26cfe8354c0ba89fbd732ed782e
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65645068"
---
# <a name="bitwise-operators"></a>Opérateurs au niveau du bit

Cette rubrique décrit les opérateurs au niveau du bit qui sont disponibles dans le F# langage.

## <a name="summary-of-bitwise-operators"></a>Résumé des opérateurs au niveau du bit

Le tableau suivant décrit les opérateurs au niveau du bit qui sont prises en charge pour les types intégrés unboxed dans le F# langage.

|Opérateur|Notes|
|--------|-----|
|`&&&`|Opérateur de bits AND. Dans le résultat ont la valeur 1 si et seulement si les bits correspondants dans les deux opérandes de source sont 1.|
|<code>&#124;&#124;&#124;</code>|Opérateur de bits OR. Dans le résultat ont la valeur 1 si des bits correspondants dans la source opérandes sont 1.|
|`^^^`|Au niveau du bit opérateur OR exclusif. Dans le résultat ont la valeur 1 si et seulement si les bits dans les opérandes source ont des valeurs différentes.|
|`~~~`|Opérateur de négation au niveau du bit. Ceci est un opérateur unaire et produit un résultat dans lequel tous les bits 0 dans l’opérande source sont convertis en bits 1 et tous les bits 1 sont convertis en bits 0.|
|`<<<`|Au niveau du bit opérateur de décalage vers la gauche. Le résultat est le premier opérande avec les bits décalés vers la gauche par le nombre de bits dans le second opérande. Les bits décalés à la position la plus significative n’ont pas pivotées dans la position la moins significative. Les bits les moins significatifs sont complétées avec des zéros. Le type du deuxième argument est `int32`.|
|`>>>`|Au niveau du bit opérateur de décalage vers la droite. Le résultat est le premier opérande avec les bits décalés vers la droite par le nombre de bits dans le second opérande. Les bits décalés à la position la moins significative n’ont pas pivotées dans la position la plus significative. Pour les types non signés, les bits les plus significatifs sont remplis avec des zéros. Pour les types signés avec des valeurs négatives, les bits les plus significatifs sont remplis avec celles. Le type du deuxième argument est `int32`.|

Les types suivants peuvent être utilisés avec des opérateurs au niveau du bit : `byte`, `sbyte`, `int16`, `uint16`, `int32 (int)`, `uint32`, `int64`, `uint64`, `nativeint`, et `unativeint`.

## <a name="see-also"></a>Voir aussi

- [Informations de référence des symboles et opérateurs](index.md)
- [Opérateurs arithmétiques](arithmetic-operators.md)
- [Opérateurs booléens](boolean-operators.md)
