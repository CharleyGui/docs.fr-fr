---
title: SByte, type de données
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
ms.openlocfilehash: 01a0a4a261213d7e6e2016bf49128092e5b22308
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343952"
---
# <a name="sbyte-data-type-visual-basic"></a>SByte, type de données (Visual Basic)

Contient des entiers 8 bits (1 octet) signés dont la valeur est comprise entre-128 et 127.

## <a name="remarks"></a>Notes

Utilisez le type de données `SByte` pour contenir des valeurs entières qui ne nécessitent pas la largeur totale des données de `Integer` ou même la demi-largeur des données de `Short`. Dans certains cas, le common language runtime peut être en mesure de regrouper étroitement vos variables `SByte` et de réduire la consommation de mémoire.

La valeur par défaut de `SByte` est 0.

## <a name="literal-assignments"></a>Affectations littérales

Vous pouvez déclarer et initialiser une variable `SByte` en lui assignant un littéral décimal, un littéral hexadécimal, un littéral octal ou (à partir de Visual Basic 2017) un littéral binaire.

Dans l’exemple suivant, les entiers égaux à-102 qui sont représentés comme des littéraux décimaux, hexadécimaux et binaires sont assignés à des valeurs `SByte`. Cet exemple requiert que vous compiliez avec le commutateur du compilateur `/removeintchecks`.

[!code-vb[SByte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#SByte)]

> [!NOTE]
> Vous utilisez le préfixe `&h` ou `&H` pour désigner un littéral hexadécimal, le préfixe `&b` ou `&B` pour désigner un littéral binaire, et le préfixe `&o` ou `&O` pour désigner un littéral octal. Les littéraux décimaux n’ont pas de préfixe.

À compter de Visual Basic 2017, vous pouvez également utiliser le trait de soulignement, `_`, comme séparateur de chiffres pour améliorer la lisibilité, comme le montre l’exemple suivant.

[!code-vb[SByteSeparator](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#SByteS)]

À compter de Visual Basic 15,5, vous pouvez également utiliser le caractère de soulignement (`_`) comme séparateur de début entre le préfixe et les chiffres hexadécimaux, binaires ou octaux. Exemple :

```vb
Dim number As SByte = &H_F9
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Si le littéral entier est en dehors de la plage de `SByte` (autrement dit, s’il est inférieur à <xref:System.SByte.MinValue?displayProperty=nameWithType> ou supérieur à <xref:System.SByte.MaxValue?displayProperty=nameWithType>, une erreur de compilation se produit. Lorsqu’un littéral entier n’a pas de suffixe, un [entier](integer-data-type.md) est déduit. Si le littéral entier est en dehors de la plage du type de `Integer`, une [valeur long](long-data-type.md) est déduite. Cela signifie que, dans les exemples précédents, les littéraux numériques `0x9A` et `0b10011010` sont interprétés comme des entiers signés 32 bits avec une valeur de 156, qui dépasse <xref:System.SByte.MaxValue?displayProperty=nameWithType>. Pour compiler correctement du code comme celui-ci, qui assigne un entier non décimal à un `SByte`, vous pouvez effectuer l’une des opérations suivantes :

- Désactivez les vérifications de limites d’entiers en compilant avec le commutateur de compilateur `/removeintchecks`.

- Utilisez un [caractère de type](../../programming-guide/language-features/data-types/type-characters.md) pour définir explicitement la valeur littérale que vous souhaitez assigner au `SByte`. L’exemple suivant affecte un littéral négatif `Short` valeur à une `SByte`. Notez que, pour les nombres négatifs, le bit de poids fort du mot de poids fort du littéral numérique doit être défini. Dans le cas de notre exemple, il s’agit du bit 15 de la valeur littérale `Short`.

   [!code-vb[SByteTypeChars](../../../../samples/snippets/visualbasic/language-reference/data-types/sbyte-assignment.vb#1)]

## <a name="programming-tips"></a>Conseils de programmation

- **Conformité CLS.** Le type de données `SByte` ne faisant pas partie du [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), le code conforme CLS ne peut pas consommer un composant qui l’utilise.

- **Étendue.** Le type de données `SByte` s’étend à `Short`, `Integer`, `Long`, `Decimal`, `Single`et `Double`. Cela signifie que vous pouvez convertir `SByte` en l’un de ces types sans rencontrer d’erreur de <xref:System.OverflowException?displayProperty=nameWithType>.

- **Caractères de type.** `SByte` n’a aucun caractère de type de littéral ou caractère de type d’identificateur.

- **Type de Framework.** Le type correspondant dans le .NET Framework est la structure <xref:System.SByte?displayProperty=nameWithType>.

## <a name="see-also"></a>Voir aussi

- <xref:System.SByte?displayProperty=nameWithType>
- [Types de données](../../../visual-basic/language-reference/data-types/index.md)
- [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Liste des conversions](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Short (type de données)](../../../visual-basic/language-reference/data-types/short-data-type.md)
- [Integer (type de données)](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [Long (type de données)](../../../visual-basic/language-reference/data-types/long-data-type.md)
- [Utilisation efficace des types de données](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
