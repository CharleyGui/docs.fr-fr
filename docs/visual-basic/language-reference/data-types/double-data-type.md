---
title: Double, type de données (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Double
helpviewer_keywords:
- 'identifier type characters [Visual Basic], #'
- trailing zeros
- real numbers
- trailing 0 characters [Visual Basic]
- 0 characters [Visual Basic], trailing
- literal type characters [Visual Basic], R
- data types [Visual Basic], assigning
- Double data type [Visual Basic]
- '# identifier type character'
- double-precision numbers
- floating-point numbers [Visual Basic], Double data type
- R literal type character [Visual Basic]
- zeros, trailing
- Double data type
ms.assetid: 0c5670f7-fcb1-453a-bef1-374730cd38fd
ms.openlocfilehash: 92adb26702d94dee08e51decd845d019c797e195
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630100"
---
# <a name="double-data-type-visual-basic"></a>Double, type de données (Visual Basic)

Contient des nombres à virgule flottante double précision IEEE 64 bits (8 octets) qui comprises dans la valeur de-1.79769313486231570 E + 308 à-4.94065645841246544 E-324 pour les valeurs négatives et de 4.94065645841246544 E-324 à 1.79769313486231570 E + 308 pour valeurs positives. Les nombres à double précision stockent une approximation d’un nombre réel.

## <a name="remarks"></a>Notes

Le `Double` type de données fournit les plus grandes et les plus petites amplitudes possibles pour un nombre.

La valeur par défaut de `Double` est 0.

## <a name="programming-tips"></a>Conseils de programmation

- **Précision.** Lorsque vous utilisez des nombres à virgule flottante, n’oubliez pas qu’ils n’ont pas toujours une représentation précise en mémoire. Cela peut entraîner des résultats inattendus de certaines opérations, telles que la comparaison `Mod` de valeurs et l’opérateur. Pour plus d’informations, consultez [Dépannage des types de données](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).

- **Zéros de fin.** Les types de données à virgule flottante n’ont pas de représentation interne des zéros de fin. Par exemple, ils ne font pas la distinction entre 4,2000 et 4,2. Par conséquent, aucun caractère de fin ne s’affiche lorsque vous affichez ou imprimez des valeurs à virgule flottante.

- **Caractères de type.** L'ajout du caractère de type littéral `R` à un littéral force ce dernier en type de données `Double`. Par exemple, si une valeur entière est suivie de `R`, la valeur est remplacée `Double`par.

  ```vb
  ' Visual Basic expands the 4 in the statement Dim dub As Double = 4R to 4.0:
  Dim dub As Double = 4.0R
  ```

  L'ajout du caractère de type identificateur `#` à un identificateur force ce dernier en type `Double`. Dans l’exemple suivant, la variable `num` est de type: `Double`

  ```vb
  Dim num# = 3
  ```

- **Type de Framework.** Le type correspondant dans le .NET Framework est la structure <xref:System.Double?displayProperty=nameWithType>.

## <a name="see-also"></a>Voir aussi

- <xref:System.Double?displayProperty=nameWithType>
- [Types de données](../../../visual-basic/language-reference/data-types/index.md)
- [Decimal (type de données)](../../../visual-basic/language-reference/data-types/decimal-data-type.md)
- [Single (type de données)](../../../visual-basic/language-reference/data-types/single-data-type.md)
- [Fonctions de conversion de types](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Liste des conversions](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Utilisation efficace des types de données](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [Dépannage des types de données](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Caractères de type](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
