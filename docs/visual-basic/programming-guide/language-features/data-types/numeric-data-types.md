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
ms.openlocfilehash: dc8b630eebc48e5733344a00664b453360769c0b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346308"
---
# <a name="numeric-data-types-visual-basic"></a>Types de données numériques (Visual Basic)
Visual Basic fournit plusieurs *types de données numériques* pour gérer les nombres dans différentes représentations. Les types *intégraux* représentent uniquement des nombres entiers (positif, négatif et zéro), et les types non *intégraux* représentent des nombres avec des parties entières et fractionnaires.  
  
 Pour obtenir un tableau présentant une comparaison côte à côte des types de données Visual Basic, consultez [types de données](../../../../visual-basic/language-reference/data-types/index.md).  
  
## <a name="integral-numeric-types"></a>Types numériques intégraux  
 Les *types de données intégraux* sont ceux qui représentent uniquement des nombres sans parties fractionnaires.  
  
 Les types de données intégraux *signés* sont le [type de données SByte](../../../../visual-basic/language-reference/data-types/sbyte-data-type.md) (8 bits), le type de données [short](../../../../visual-basic/language-reference/data-types/short-data-type.md) (16 bits), le [type de données Integer](../../../../visual-basic/language-reference/data-types/integer-data-type.md) (32 bits) et le [type de données long](../../../../visual-basic/language-reference/data-types/long-data-type.md) (64 bits). Si une variable stocke toujours des entiers plutôt que des nombres fractionnaires, déclarez-la comme l’un de ces types.  
  
 Les types intégraux *non signés* sont le [type](../../../../visual-basic/language-reference/data-types/byte-data-type.md) de données Byte (8 bits), le [type de données UShort](../../../../visual-basic/language-reference/data-types/ushort-data-type.md) (16 bits), le [type de données UInteger](../../../../visual-basic/language-reference/data-types/uinteger-data-type.md) (32 bits) et le [type de données ulong](../../../../visual-basic/language-reference/data-types/ulong-data-type.md) (64 bits). Si une variable contient des données binaires ou des données de nature inconnue, déclarez-les comme l’un de ces types.  
  
### <a name="performance"></a>Performances  
 Les opérations arithmétiques sont plus rapides avec des types intégraux qu’avec d’autres types de données. Ils sont plus rapides avec les types de `Integer` et de `UInteger` dans Visual Basic.  
  
### <a name="large-integers"></a>Entiers volumineux  
 Si vous devez conserver un entier plus grand que le type de données `Integer` peut contenir, vous pouvez utiliser le type de données `Long` à la place. les variables de `Long` peuvent contenir des nombres compris entre-9223372036854775808 et 9 223 372 036 854 775 807. Les opérations avec des `Long` sont légèrement plus lentes qu’avec `Integer`.  
  
 Si vous avez besoin de valeurs plus élevées, vous pouvez utiliser le [type de données decimal](../../../../visual-basic/language-reference/data-types/decimal-data-type.md). Vous pouvez stocker les nombres de-79 228 et 79 228 335 dans une variable `Decimal` si vous n’utilisez pas de décimales. Toutefois, les opérations avec des nombres `Decimal` sont beaucoup plus lentes qu’avec tout autre type de données numérique.  
  
### <a name="small-integers"></a>Petits entiers  
 Si vous n’avez pas besoin de la plage complète du type de données `Integer`, vous pouvez utiliser le type de données `Short`, qui peut contenir des entiers compris entre-32 768 et 32 767. Pour la plus petite plage d’entiers, le type de données `SByte` contient des entiers compris entre-128 et 127. Si vous avez un très grand nombre de variables qui contiennent de petits entiers, le common language runtime peut parfois stocker vos variables de `Short` et de `SByte` de manière plus efficace et réduire la consommation de mémoire. Toutefois, les opérations avec `Short` et `SByte` sont un peu plus lentes qu’avec `Integer`.  
  
### <a name="unsigned-integers"></a>Entiers non signés  
 Si vous savez que votre variable n’a jamais besoin de contenir un nombre négatif, vous pouvez utiliser les *types non signés*`Byte`, `UShort`, `UInteger`et `ULong`. Chacun de ces types de données peut contenir un entier positif deux fois plus grand que son type signé correspondant (`SByte`, `Short`, `Integer`et `Long`). En termes de performances, chaque type non signé est exactement aussi efficace que son type signé correspondant. En particulier, `UInteger` partage avec `Integer` la distinction entre les types de données numériques élémentaires.  
  
## <a name="nonintegral-numeric-types"></a>Types numériques non intégraux  
 Les *types de données non intégraux* sont ceux qui représentent des nombres avec des parties entières et fractionnaires.  
  
 Les types de données numériques non intégraux sont `Decimal` (virgule fixe 128 bits), [un type de données unique](../../../../visual-basic/language-reference/data-types/single-data-type.md) (virgule flottante de 32 bits) et un [type de données double](../../../../visual-basic/language-reference/data-types/double-data-type.md) (virgule flottante 64 bits). Il s’agit de tous les types signés. Si une variable peut contenir une fraction, déclarez-la comme l’un de ces types.  
  
 `Decimal` n’est pas un type de données à virgule flottante. les nombres `Decimal` ont une valeur d’entier binaire et un facteur d’échelle d’entier qui spécifie quelle partie de la valeur est une fraction décimale.  
  
 Vous pouvez utiliser des variables de `Decimal` pour les valeurs monétaires. L’avantage est la précision des valeurs. Le type de données `Double` est plus rapide et requiert moins de mémoire, mais il est soumis à des erreurs d’arrondi. Le type de données `Decimal` conserve une précision totale à 28 décimales.  
  
 Les nombres à virgule flottante (`Single` et `Double`) ont des plages plus larges que les nombres `Decimal` mais peuvent être soumis à des erreurs d’arrondi. Les types à virgule flottante prennent en charge moins de chiffres significatifs que `Decimal` mais peuvent représenter des valeurs d’une plus grande amplitude.  
  
 Les valeurs numériques non intégrales peuvent être exprimées sous la forme mmmEeee, où MMM est la *mantisse* (chiffres significatifs) et EEE est l' *exposant* (une puissance de 10). Les valeurs positives les plus élevées des types non intégraux sont 7,9228162514264337593543950335 E + 28 pour `Decimal`, 3.4028235 E + 38 pour `Single`et 1.79769313486231570 E + 308 pour `Double`.  
  
### <a name="performance"></a>Performances  
 `Double` est le plus efficace des types de données fractionnaires, car les processeurs sur les plateformes actuelles effectuent des opérations à virgule flottante en double précision. Toutefois, les opérations avec `Double` ne sont pas aussi rapides qu’avec les types intégraux tels que `Integer`.  
  
### <a name="small-magnitudes"></a>Petites amplitudes  
 Pour les nombres ayant la plus petite amplitude possible (le plus proche de 0), les variables `Double` peuvent contenir des nombres aussi petits que 4.94065645841246544 E-324 pour les valeurs négatives et 4.94065645841246544 E-324 pour les valeurs positives.  
  
### <a name="small-fractional-numbers"></a>Petits nombres fractionnaires  
 Si vous n’avez pas besoin de la plage complète du type de données `Double`, vous pouvez utiliser le type de données `Single`, qui peut contenir des nombres à virgule flottante de-3.4028235 E + 38 à 3.4028235 E + 38. Les plus petites amplitudes pour `Single` variables sont-1.401298 E-45 pour les valeurs négatives et 1.401298 E-45 pour les valeurs positives. Si vous avez un très grand nombre de variables qui contiennent des nombres à virgule flottante réduits, le common language runtime peut parfois stocker vos variables `Single` plus efficacement et économiser la consommation de mémoire.  
  
## <a name="see-also"></a>Voir aussi

- [Types de données élémentaires](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [Types de données caractère](../../../../visual-basic/programming-guide/language-features/data-types/character-data-types.md)
- [Types de données divers](../../../../visual-basic/programming-guide/language-features/data-types/miscellaneous-data-types.md)
- [Dépannage des types de données](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Guide pratique : appeler une fonction Windows qui possède des types non signés](../../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
