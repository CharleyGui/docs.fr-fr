---
title: SByte (type de données)
ms.date: 04/20/2017
f1_keywords:
- vb.sbyte
helpviewer_keywords:
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- SByte data type
ms.assetid: 5c38374a-18a1-4cc2-b493-299e3dcaa60f
ms.openlocfilehash: e7d45c74056ce5b6aa66674c99e48b5ab60015f0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415568"
---
# <a name="sbyte-data-type-visual-basic"></a>SByte, type de données (Visual Basic)

Contient des entiers 8 bits (1 octet) signés dont la valeur est comprise entre-128 et 127.

## <a name="remarks"></a>Notes

Utilisez le `SByte` type de données pour contenir des valeurs entières qui ne nécessitent pas la largeur complète des données `Integer` ou même la demi-largeur des données `Short` . Dans certains cas, le common language runtime peut être en mesure de `SByte` regrouper vos variables de près et d’économiser la consommation de mémoire.

La valeur par défaut de `SByte` est 0.

## <a name="literal-assignments"></a>Affectations littérales

Vous pouvez déclarer et initialiser une `SByte` variable en lui assignant un littéral décimal, un littéral hexadécimal, un littéral octal ou (à partir de Visual Basic 2017) un littéral binaire.

Dans l’exemple suivant, les entiers égaux à-102 qui sont représentés comme des littéraux décimaux, hexadécimaux et binaires sont assignés aux `SByte` valeurs. Cet exemple requiert que vous compiliez avec le `/removeintchecks` commutateur du compilateur.

[!code-vb[SByte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#SByte)]

> [!NOTE]
> Vous utilisez le préfixe `&h` ou `&H` pour désigner un littéral hexadécimal, le préfixe `&b` ou `&B` pour désigner un littéral binaire, et le préfixe `&o` ou `&O` pour désigner un littéral octal. Les littéraux décimaux n’ont pas de préfixe.

À compter de Visual Basic 2017, vous pouvez également utiliser le caractère de soulignement, `_` , comme séparateur de chiffres pour améliorer la lisibilité, comme le montre l’exemple suivant.

[!code-vb[SByteSeparator](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#SByteS)]

À compter de Visual Basic 15,5, vous pouvez également utiliser le trait de soulignement ( `_` ) comme séparateur de début entre le préfixe et les chiffres hexadécimaux, binaires ou octaux. Par exemple :

```vb
Dim number As SByte = &H_F9
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Si le littéral entier est en dehors de la plage de `SByte` (autrement dit, s’il est inférieur à <xref:System.SByte.MinValue?displayProperty=nameWithType> ou supérieur à <xref:System.SByte.MaxValue?displayProperty=nameWithType>, une erreur de compilation se produit. Lorsqu’un littéral entier n’a pas de suffixe, un [entier](integer-data-type.md) est déduit. Si le littéral entier est en dehors de la plage du `Integer` type, une [valeur long](long-data-type.md) est déduite. Cela signifie que, dans les exemples précédents, les littéraux numériques `0x9A` et `0b10011010` sont interprétés comme des entiers signés 32 bits avec une valeur de 156, ce qui dépasse <xref:System.SByte.MaxValue?displayProperty=nameWithType> . Pour compiler correctement du code comme celui-ci, qui assigne un entier non décimal à un `SByte` , vous pouvez effectuer l’une des opérations suivantes :

- Désactivez les vérifications de limites d’entiers en compilant avec le `/removeintchecks` commutateur du compilateur.

- Utilisez un [caractère de type](../../programming-guide/language-features/data-types/type-characters.md) pour définir explicitement la valeur littérale que vous souhaitez assigner à `SByte` . L’exemple suivant assigne une valeur littérale négative `Short` à un `SByte` . Notez que, pour les nombres négatifs, le bit de poids fort du mot de poids fort du littéral numérique doit être défini. Dans le cas de notre exemple, il s’agit du bit 15 de la valeur littérale `Short` .

   [!code-vb[SByteTypeChars](../../../../samples/snippets/visualbasic/language-reference/data-types/sbyte-assignment.vb#1)]

## <a name="programming-tips"></a>Conseils de programmation

- **Conformité CLS.** Le `SByte` type de données ne faisant pas partie du [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), le code conforme CLS ne peut pas consommer un composant qui l’utilise.

- **Étendue.** Le `SByte` type de données s’étend à `Short` , `Integer` ,,, `Long` `Decimal` `Single` et `Double` . Cela signifie que vous pouvez `SByte` effectuer une conversion vers l’un de ces types sans rencontrer d' <xref:System.OverflowException?displayProperty=nameWithType> erreur.

- **Caractères de type.** `SByte`n’a aucun caractère de type de littéral ou caractère de type d’identificateur.

- **Type .NET Framework.** Le type correspondant dans le .NET Framework est la structure <xref:System.SByte?displayProperty=nameWithType>.

## <a name="see-also"></a>Voir aussi

- <xref:System.SByte?displayProperty=nameWithType>
- [Types de données](index.md)
- [Type Conversion Functions](../functions/type-conversion-functions.md)
- [Liste des conversions](../keywords/conversion-summary.md)
- [Court (type de données)](short-data-type.md)
- [Entier (type de données)](integer-data-type.md)
- [Long (type de données)](long-data-type.md)
- [Utilisation efficace des types de données](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
