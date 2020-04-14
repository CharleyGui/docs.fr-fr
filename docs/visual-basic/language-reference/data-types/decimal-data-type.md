---
title: Décimal (type de données)
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
ms.openlocfilehash: d4d868ba7c05cf3c2d538de1217231df91d4f43d
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243321"
---
# <a name="decimal-data-type-visual-basic"></a>Decimal, type de données (Visual Basic)

Contient des valeurs 128 bits (16 octets) signées représentant des nombres entiers 96 bits (12 octets) mis à l’échelle par une puissance de variable de 10. Le facteur d’échelle spécifie le nombre de chiffres à droite du point décimal; il varie de 0 à 28. Avec une échelle de 0 (pas de décimales), la valeur la plus importante possible est de 79 228 162 514 264 337 593,593,543 950 335 (-7,9228162514264375935439503333350335E 28E). Avec 28 décimales, la valeur la plus élevée est de 7,922816251426437593543950335, et la plus petite valeur nonzero est de 0,00000000000000000000000000000000 .

## <a name="remarks"></a>Notes

Le `Decimal` type de données fournit le plus grand nombre de chiffres significatifs pour un nombre. Il prend en charge jusqu’à 29 chiffres significatifs et peut représenter des valeurs supérieures à 7.9228 x 10-28. Il convient particulièrement aux calculs, tels que les finances, qui nécessitent un grand nombre de chiffres, mais ne peuvent tolérer les erreurs d’arrondissement.

La valeur par défaut de `Decimal` est 0.

## <a name="programming-tips"></a>Conseils de programmation

- **Précision.** `Decimal`n’est pas un type de données à point flottant. La `Decimal` structure détient une valeur binaire d’intégrage, avec un bit de signe et un facteur d’échelle d’intégrant qui spécifie quelle partie de la valeur est une fraction décimale. Pour cette `Decimal` raison, les chiffres ont une représentation plus`Single` `Double`précise dans la mémoire que les types de points flottants ( et ).

- **Performances.** Le `Decimal` type de données est le plus lent de tous les types numériques. Vous devez peser l’importance de la précision par rapport aux performances avant de choisir un type de données.

- **Élargissement.** Le `Decimal` type de `Single` données `Double`s’élargit à ou . Cela signifie que `Decimal` vous pouvez convertir à <xref:System.OverflowException?displayProperty=nameWithType> l’un de ces types sans rencontrer une erreur.

- **Zéros à la traîne.** Visual Basic ne stocke pas `Decimal` les zéros de fuite dans un littéral. Cependant, `Decimal` une variable préserve tous les zéros de fuite acquis de manière computationnelle. L'exemple suivant illustre ce comportement.

  ```vb
  Dim d1, d2, d3, d4 As Decimal
  d1 = 2.375D
  d2 = 1.625D
  d3 = d1 + d2
  d4 = 4.000D
  MsgBox("d1 = " & CStr(d1) & ", d2 = " & CStr(d2) &
        ", d3 = " & CStr(d3) & ", d4 = " & CStr(d4))
  ```

  La sortie `MsgBox` de l’exemple précédent est la suivante:

  ```console
  d1 = 2.375, d2 = 1.625, d3 = 4.000, d4 = 4
  ```

- **Personnages de type.** L'ajout du caractère de type littéral `D` à un littéral force ce dernier en type de données `Decimal`. L'ajout du caractère de type identificateur `@` à un identificateur force ce dernier en type `Decimal`.

- **Type .NET Framework.** Le type correspondant dans le .NET Framework est la structure <xref:System.Decimal?displayProperty=nameWithType>.

## <a name="range"></a>Plage

 Vous devrez peut-être utiliser le caractère `D` type `Decimal` pour attribuer une grande valeur à une variable ou constante. Cette exigence est parce que le compilateur interprète un littéral comme `Long` à moins qu’un caractère de type littéral suit le littéral, comme le montre l’exemple suivant.

```vb
Dim bigDec1 As Decimal = 9223372036854775807   ' No overflow.
Dim bigDec2 As Decimal = 9223372036854775808   ' Overflow.
Dim bigDec3 As Decimal = 9223372036854775808D  ' No overflow.
```

La déclaration `bigDec1` pour ne produit pas un débordement parce que la valeur `Long`qui lui est assignée tombe dans la gamme pour . La `Long` valeur peut être `Decimal` attribuée à la variable.

La déclaration `bigDec2` pour génère une erreur de débordement parce que la `Long`valeur qui lui est assignée est trop grande pour . Parce que le littéral numérique ne `Long`peut pas d’abord `Decimal` être interprété comme un , il ne peut pas être affecté à la variable.

Pour `bigDec3`, le caractère `D` de type littéral résout le problème `Decimal` en forçant `Long`le compilateur à interpréter le littéral comme un au lieu de comme un .

## <a name="see-also"></a>Voir aussi

- <xref:System.Decimal?displayProperty=nameWithType>
- <xref:System.Decimal.%23ctor%2A>
- <xref:System.Math.Round%2A?displayProperty=nameWithType>
- [Types de données](../../../visual-basic/language-reference/data-types/index.md)
- [Single (type de données)](../../../visual-basic/language-reference/data-types/single-data-type.md)
- [Double (type de données)](../../../visual-basic/language-reference/data-types/double-data-type.md)
- [Fonctions de conversion de types](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Liste des conversions](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Utilisation efficace des types de données](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
