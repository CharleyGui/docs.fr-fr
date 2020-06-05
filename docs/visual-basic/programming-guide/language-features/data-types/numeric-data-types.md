---
title: Types de données numériques
ms.date: 07/20/2015
helpviewer_keywords:
- integral types [Visual Basic], Visual Basic
- Short data type [Visual Basic], numeric data types
- Double data type [Visual Basic], numeric data types
- Long data type [Visual Basic], Visual Basic numeric data types
- numbers [Visual Basic], whole
- fractions
- numbers
- whole numbers
- integer numbers
- numbers [Visual Basic], integer
- fractional data types [Visual Basic]
- mantissas, of fractional numbers
- mantissas
- data types [Visual Basic], numeric
- Integer data type [Visual Basic], numeric data types
- exponent, of fractional numbers
- integers [Visual Basic]
- numeric data types [Visual Basic], Visual Basic
- Single data type [Visual Basic], numeric types
- Decimal data type [Visual Basic], numeric data types
ms.assetid: a27bd4d0-7e14-43eb-9cc4-b42eaab323c9
ms.openlocfilehash: 72cdca295e209935687f67ad290e816775d9fe13
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84393674"
---
# <a name="numeric-data-types-visual-basic"></a>Types de données numériques (Visual Basic)
Visual Basic fournit plusieurs *types de données numériques* pour gérer les nombres dans différentes représentations. Les types *intégraux* représentent uniquement des nombres entiers (positif, négatif et zéro), et les types non *intégraux* représentent des nombres avec des parties entières et fractionnaires.  
  
 Pour obtenir un tableau présentant une comparaison côte à côte des types de données Visual Basic, consultez [types de données](../../../language-reference/data-types/index.md).  
  
## <a name="integral-numeric-types"></a>Types numériques intégraux  
 Les *types de données intégraux* sont ceux qui représentent uniquement des nombres sans parties fractionnaires.  
  
 Les types de données intégraux *signés* sont le [type de données SByte](../../../language-reference/data-types/sbyte-data-type.md) (8 bits), le type de données [short](../../../language-reference/data-types/short-data-type.md) (16 bits), le [type de données Integer](../../../language-reference/data-types/integer-data-type.md) (32 bits) et le [type de données long](../../../language-reference/data-types/long-data-type.md) (64 bits). Si une variable stocke toujours des entiers plutôt que des nombres fractionnaires, déclarez-la comme l’un de ces types.  
  
 Les types intégraux *non signés* sont le [type](../../../language-reference/data-types/byte-data-type.md) de données Byte (8 bits), le [type de données UShort](../../../language-reference/data-types/ushort-data-type.md) (16 bits), le [type de données UInteger](../../../language-reference/data-types/uinteger-data-type.md) (32 bits) et le [type de données ulong](../../../language-reference/data-types/ulong-data-type.md) (64 bits). Si une variable contient des données binaires ou des données de nature inconnue, déclarez-les comme l’un de ces types.  
  
### <a name="performance"></a>Performances  
 Les opérations arithmétiques sont plus rapides avec des types intégraux qu’avec d’autres types de données. Ils sont plus rapides avec `Integer` les `UInteger` types et dans Visual Basic.  
  
### <a name="large-integers"></a>Entiers volumineux  
 Si vous devez conserver un entier plus grand que le `Integer` type de données peut contenir, vous pouvez utiliser le type de données à la `Long` place. `Long`les variables peuvent contenir des nombres compris entre-9223372036854775808 et 9 223 372 036 854 775 807. Les opérations avec `Long` sont légèrement plus lentes que avec `Integer` .  
  
 Si vous avez besoin de valeurs plus élevées, vous pouvez utiliser le [type de données decimal](../../../language-reference/data-types/decimal-data-type.md). Vous pouvez stocker les nombres de-79 228 et 79 228 335 dans une `Decimal` variable si vous n’utilisez pas de décimales. Toutefois, les opérations avec des `Decimal` nombres sont beaucoup plus lentes qu’avec tout autre type de données numérique.  
  
### <a name="small-integers"></a>Petits entiers  
 Si vous n’avez pas besoin de la plage complète du `Integer` type de données, vous pouvez utiliser le `Short` type de données, qui peut contenir des entiers compris entre-32 768 et 32 767. Pour la plus petite plage d’entiers, le `SByte` type de données contient des entiers compris entre-128 et 127. Si vous avez un très grand nombre de variables qui contiennent de petits entiers, le common language runtime peut parfois stocker `Short` vos `SByte` variables et de manière plus efficace et réduire la consommation de mémoire. Toutefois, les opérations avec `Short` et `SByte` sont un peu plus lentes que avec `Integer` .  
  
### <a name="unsigned-integers"></a>Entiers non signés  
 Si vous savez que votre variable n’a jamais besoin de contenir un nombre négatif, vous pouvez utiliser les *types non signés* `Byte` ,, `UShort` `UInteger` et `ULong` . Chacun de ces types de données peut contenir un entier positif deux fois plus grand que son type signé correspondant ( `SByte` , `Short` , `Integer` et `Long` ). En termes de performances, chaque type non signé est exactement aussi efficace que son type signé correspondant. En particulier, les `UInteger` partages avec `Integer` la distinction sont les plus efficaces de tous les types de données numériques élémentaires.  
  
## <a name="nonintegral-numeric-types"></a>Types numériques non intégraux  
 Les *types de données non intégraux* sont ceux qui représentent des nombres avec des parties entières et fractionnaires.  
  
 Les types de données numériques non intégraux sont `Decimal` (point fixe 128 bits), [un type de données unique](../../../language-reference/data-types/single-data-type.md) (virgule flottante de 32 bits) et le [type de données double](../../../language-reference/data-types/double-data-type.md) (virgule flottante 64 bits). Il s’agit de tous les types signés. Si une variable peut contenir une fraction, déclarez-la comme l’un de ces types.  
  
 `Decimal`n’est pas un type de données à virgule flottante. `Decimal`les nombres ont une valeur d’entier binaire et un facteur d’échelle d’entier qui spécifie quelle partie de la valeur est une fraction décimale.  
  
 Vous pouvez utiliser `Decimal` des variables pour les valeurs monétaires. L’avantage est la précision des valeurs. Le `Double` type de données est plus rapide et requiert moins de mémoire, mais il est soumis à des erreurs d’arrondi. Le `Decimal` type de données conserve une précision complète à 28 décimales.  
  
 Les nombres à virgule flottante ( `Single` et `Double` ) ont des plages plus larges que les `Decimal` nombres, mais ils peuvent être soumis à des erreurs d’arrondi. Les types à virgule flottante prennent en charge moins de chiffres significatifs que `Decimal` , mais peuvent représenter des valeurs d’une plus grande amplitude.  
  
 Les valeurs numériques non intégrales peuvent être exprimées sous la forme mmmEeee, où MMM est la *mantisse* (chiffres significatifs) et EEE est l' *exposant* (une puissance de 10). Les valeurs positives les plus élevées des types non intégraux sont 7,9228162514264337593543950335 E + 28 pour `Decimal` , 3.4028235 e + 38 pour `Single` et 1.79769313486231570 e + 308 pour `Double` .  
  
### <a name="performance"></a>Performances  
 `Double`est le plus efficace des types de données fractionnaires, car les processeurs sur les plateformes actuelles effectuent des opérations à virgule flottante en double précision. Toutefois, les opérations avec `Double` ne sont pas aussi rapides que les types intégraux tels que `Integer` .  
  
### <a name="small-magnitudes"></a>Petites amplitudes  
 Pour les nombres ayant la plus petite amplitude possible (le plus proche de 0), les `Double` variables peuvent contenir des nombres aussi petits que 4.94065645841246544 e-324 pour les valeurs négatives et 4.94065645841246544 e-324 pour les valeurs positives.  
  
### <a name="small-fractional-numbers"></a>Petits nombres fractionnaires  
 Si vous n’avez pas besoin de la plage complète du `Double` type de données, vous pouvez utiliser le `Single` type de données, qui peut contenir des nombres à virgule flottante compris entre-3.4028235 e + 38 et 3.4028235 e + 38. Les plus petites amplitudes pour les `Single` variables sont-1.401298 e-45 pour les valeurs négatives et 1.401298 e-45 pour les valeurs positives. Si vous avez un très grand nombre de variables qui contiennent des nombres à virgule flottante réduits, le common language runtime peut parfois stocker vos `Single` variables plus efficacement et économiser de la consommation de mémoire.  
  
## <a name="see-also"></a>Voir aussi

- [Types de données élémentaires](elementary-data-types.md)
- [Types de données caractères](character-data-types.md)
- [Types de données divers](miscellaneous-data-types.md)
- [Dépannage des types de données](troubleshooting-data-types.md)
- [Procédure : Appeler une fonction Windows qui accepte des types non signés](../../com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
