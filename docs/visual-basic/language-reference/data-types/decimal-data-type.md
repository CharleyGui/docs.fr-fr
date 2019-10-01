---
title: Decimal, type de données (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Decimal
helpviewer_keywords:
- literal type characters [Visual Basic], D
- trailing zeros
- real numbers
- trailing 0 characters [Visual Basic]
- Decimal data type
- D literal type character [Visual Basic]
- decimals, Decimal data type
- 0 characters [Visual Basic], trailing
- data types [Visual Basic], assigning
- decimal keyword [Visual Basic]
- numbers [Visual Basic], real
- variable-precision numbers
- zeros, trailing
- '@ identifier type character'
- identifier type characters [Visual Basic], @
ms.assetid: 1d855b45-afe2-45b0-a623-96b6f63a43d5
ms.openlocfilehash: 892824b61cfb6a0172361d220c638cab0a78565d
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700875"
---
# <a name="decimal-data-type-visual-basic"></a>Decimal, type de données (Visual Basic)

Contient des valeurs 128 bits (16 octets) signées représentant des nombres entiers 96 bits (12 octets) mis à l’échelle à l’aide d’une puissance variable de 10. Le facteur d’échelle spécifie le nombre de chiffres à droite de la virgule décimale ; elle est comprise entre 0 et 28. Avec une échelle de 0 (pas de décimale), la plus grande valeur possible est +/-79 228 162 514 264 337 593 543 950 335 (+/-7.9228162514264337593543950335E + 28). Avec 28 décimales, la plus grande valeur est +/-7,9228162514264337593543950335 et la plus petite valeur différente de zéro est +/-0,0000000000000000000000000001 (+/-1E-28).

## <a name="remarks"></a>Notes

Le type de données `Decimal` fournit le plus grand nombre de chiffres significatifs pour un nombre. Il prend en charge jusqu’à 29 chiffres significatifs et peut représenter des valeurs dépassant 7,9228 x 10 ^ 28. Elle est particulièrement adaptée aux calculs, tels que Financial, qui requièrent un grand nombre de chiffres, mais ne tolèrent pas les erreurs d’arrondi.

La valeur par défaut de `Decimal` est 0.

## <a name="programming-tips"></a>Conseils de programmation

- **Précision.** `Decimal` n’est pas un type de données à virgule flottante. La structure `Decimal` contient une valeur entière binaire, ainsi qu’un bit de signe et un facteur d’échelle d’entier qui spécifie quelle partie de la valeur est une fraction décimale. Pour cette raison, les nombres `Decimal` ont une représentation plus précise en mémoire que les types à virgule flottante (`Single` et `Double`).

- **Performances** Le type de données `Decimal` est le plus lent de tous les types numériques. Vous devez évaluer l’importance de la précision par rapport aux performances avant de choisir un type de données.

- **Étendue.** Le type de données `Decimal` s’étend à `Single` ou `Double`. Cela signifie que vous pouvez convertir `Decimal` en l’un de ces types sans rencontrer une erreur <xref:System.OverflowException?displayProperty=nameWithType>.

- **Zéros de fin.** Visual Basic ne stocke pas les zéros de fin dans un littéral `Decimal`. Toutefois, une variable `Decimal` préserve les zéros de fin acquis au calcul. L'exemple suivant illustre ce comportement.

  ```vb
  Dim d1, d2, d3, d4 As Decimal
  d1 = 2.375D
  d2 = 1.625D
  d3 = d1 + d2
  d4 = 4.000D
  MsgBox("d1 = " & CStr(d1) & ", d2 = " & CStr(d2) &
        ", d3 = " & CStr(d3) & ", d4 = " & CStr(d4))
  ```

  La sortie de `MsgBox` dans l’exemple précédent est la suivante :

  ```console
  d1 = 2.375, d2 = 1.625, d3 = 4.000, d4 = 4
  ```

- **Caractères de type.** L'ajout du caractère de type littéral `D` à un littéral force ce dernier en type de données `Decimal`. L'ajout du caractère de type identificateur `@` à un identificateur force ce dernier en type `Decimal`.

- **Type de Framework.** Le type correspondant dans le .NET Framework est la structure <xref:System.Decimal?displayProperty=nameWithType>.

## <a name="range"></a>Plage
 Vous devrez peut-être utiliser le caractère de type `D` pour affecter une valeur élevée à une variable ou une constante `Decimal`. Cette exigence est due au fait que le compilateur interprète un littéral comme `Long`, sauf si un caractère de type littéral suit le littéral, comme le montre l’exemple suivant.

```vb
Dim bigDec1 As Decimal = 9223372036854775807   ' No overflow.
Dim bigDec2 As Decimal = 9223372036854775808   ' Overflow.
Dim bigDec3 As Decimal = 9223372036854775808D  ' No overflow.
```

La déclaration pour `bigDec1` ne génère pas de dépassement de capacité, car la valeur qui lui est assignée est comprise dans la plage de `Long`. La valeur `Long` peut être assignée à la variable `Decimal`.

La déclaration pour `bigDec2` génère une erreur de dépassement de capacité, car la valeur qui lui est assignée est trop grande pour `Long`. Étant donné que le littéral numérique ne peut pas être d’abord interprété comme un `Long`, il ne peut pas être assigné à la variable `Decimal`.

Par `bigDec3`, le caractère de type de littéral `D` résout le problème en forçant le compilateur à interpréter le littéral comme un `Decimal` plutôt que comme un `Long`.

## <a name="see-also"></a>Voir aussi

- <xref:System.Decimal?displayProperty=nameWithType>
- <xref:System.Decimal.%23ctor%2A?displayProperty=nameWithType>
- <xref:System.Math.Round%2A?displayProperty=nameWithType>
- [Types de données](../../../visual-basic/language-reference/data-types/index.md)
- [Single (type de données)](../../../visual-basic/language-reference/data-types/single-data-type.md)
- [Double (type de données)](../../../visual-basic/language-reference/data-types/double-data-type.md)
- [Fonctions de conversion de types](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Liste des conversions](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Utilisation efficace des types de données](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
