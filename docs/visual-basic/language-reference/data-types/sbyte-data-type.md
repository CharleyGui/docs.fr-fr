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
ms.openlocfilehash: 01a0a4a261213d7e6e2016bf49128092e5b22308
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400791"
---
# <a name="sbyte-data-type-visual-basic"></a>Type de données SByte (Visual Basic)

Détient signé 8 bits (1-byte) integers qui varient en valeur de -128 à 127.

## <a name="remarks"></a>Notes 

Utilisez `SByte` le type de données pour contenir des valeurs integer qui ne nécessitent pas la largeur de données complète de `Integer` ou même la moitié de la largeur de données de `Short`. Dans certains cas, le temps d’exécution `SByte` de langue commun pourrait être en mesure d’emballer vos variables étroitement ensemble et d’économiser la consommation de mémoire.

La valeur par défaut de `SByte` est 0.

## <a name="literal-assignments"></a>Affectations littérales

Vous pouvez déclarer et `SByte` initialiser une variable en lui assignant un littéal décimal, un littéal hexadecimal, un littéral octal, ou (à partir de Visual Basic 2017) un littéral binaire.

Dans l’exemple suivant, les intégristes sont égaux à -102 qui sont représentés comme décimales, hexadecimal, et les littérals binaires sont attribués aux `SByte` valeurs. Cet exemple exige que vous `/removeintchecks` compiliez avec le commutateur de compilateur.

[!code-vb[SByte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#SByte)]

> [!NOTE]
> Vous utilisez le `&h` `&H` préfixe ou pour désigner un littératal hexadecimal, le `&b` préfixe ou `&B` pour désigner un littératique binaire, et le préfixe `&o` ou `&O` pour désigner un littéral octal. Les littéraux décimaux n’ont pas de préfixe.

En commençant par Visual Basic 2017, vous `_`pouvez également utiliser le personnage de soulignement, , comme séparateur à chiffres pour améliorer la lisibilité, comme le montre l’exemple suivant.

[!code-vb[SByteSeparator](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#SByteS)]

En commençant par Visual Basic 15.5, vous`_`pouvez également utiliser le caractère de soulignement ( ) comme séparateur de premier plan entre le préfixe et les chiffres hexadecimal, binaire ou octal. Par exemple :

```vb
Dim number As SByte = &H_F9
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Si le littéral entier est en dehors de la plage de `SByte` (autrement dit, s’il est inférieur à <xref:System.SByte.MinValue?displayProperty=nameWithType> ou supérieur à <xref:System.SByte.MaxValue?displayProperty=nameWithType>, une erreur de compilation se produit. Lorsqu’un littéral integer n’a pas de suffixe, un [Integer](integer-data-type.md) est déduit. Si l’integer littéral est `Integer` en dehors de la portée du type, un [Long](long-data-type.md) est déduit. Cela signifie que, dans les exemples `0x9A` précédents, les littérals numériques et `0b10011010` sont interprétés comme des intégraux signés 32 bits d’une valeur de 156, ce qui dépasse <xref:System.SByte.MaxValue?displayProperty=nameWithType>. Pour compiler avec succès le code comme celui-ci qui `SByte`attribue un intégrateur non décimal à un , vous pouvez faire l’un des éléments suivants:

- Désactiver les limites integer vérifie en `/removeintchecks` compilant avec le commutateur de compilateur.

- Utilisez un [personnage de type](../../programming-guide/language-features/data-types/type-characters.md) pour définir explicitement la `SByte`valeur littérale que vous souhaitez attribuer à la . L’exemple suivant attribue une `Short` valeur `SByte`littérale négative à un . Notez que, pour les chiffres négatifs, le peu de haut ordre du mot de haute commande du littéral numérique doit être défini. Dans le cas de notre exemple, c’est `Short` un peu 15 de la valeur littérale.

   [!code-vb[SByteTypeChars](../../../../samples/snippets/visualbasic/language-reference/data-types/sbyte-assignment.vb#1)]

## <a name="programming-tips"></a>Conseils de programmation

- **Conformité CLS.** Le `SByte` type de données ne fait pas partie de la [spécification de langue commune](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), de sorte que le code conforme à CLS ne peut pas consommer un composant qui l’utilise.

- **Élargissement.** Le `SByte` type de `Short`données `Integer` `Long`s’élargit à , , , `Decimal`, `Single`et `Double`. Cela signifie que `SByte` vous pouvez convertir à <xref:System.OverflowException?displayProperty=nameWithType> l’un de ces types sans rencontrer une erreur.

- **Personnages de type.** `SByte`n’a pas de caractère de type littéral ou de caractère de type identifiant.

- **Type .NET Framework.** Le type correspondant dans le .NET Framework est la structure <xref:System.SByte?displayProperty=nameWithType>.

## <a name="see-also"></a>Voir aussi

- <xref:System.SByte?displayProperty=nameWithType>
- [Types de données](../../../visual-basic/language-reference/data-types/index.md)
- [Fonctions de conversion de types](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Liste des conversions](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Short (type de données)](../../../visual-basic/language-reference/data-types/short-data-type.md)
- [Type de données integer](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [Long (type de données)](../../../visual-basic/language-reference/data-types/long-data-type.md)
- [Utilisation efficace des types de données](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
