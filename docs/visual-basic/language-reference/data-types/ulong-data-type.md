---
title: ULong (type de données)
ms.date: 01/31/2018
f1_keywords:
- vb.ulong
helpviewer_keywords:
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- literal type characters [Visual Basic], UL
- ULong data type
- UL literal type characters [Visual Basic]
ms.assetid: 017e0702-774e-44ae-bedc-786b424ca84e
ms.openlocfilehash: 3c6cd4086e08b808c158948756b4806f098196b9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400700"
---
# <a name="ulong-data-type-visual-basic"></a>Type de données ULong (Visual Basic)

Détient des intégrés non signés 64 bits (8-byte) dont la valeur varie de 0 à 18 446 744 073 709 551 615 (plus de 1,84 fois 10 à 19).

## <a name="remarks"></a>Notes 

Utilisez `ULong` le type de données pour `UInteger`contenir des données binaires trop grandes pour, ou les plus grandes valeurs insignées possibles.

La valeur par défaut de `ULong` est 0.

## <a name="literal-assignments"></a>Affectations littérales

Vous pouvez déclarer et `ULong` initialiser une variable en lui assignant un littéal décimal, un littéal hexadecimal, un littéral octal, ou (à partir de Visual Basic 2017) un littéral binaire. Si le littéral entier est en dehors de la plage de `ULong` (autrement dit, s’il est inférieur à <xref:System.UInt64.MinValue?displayProperty=nameWithType> ou supérieur à <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, une erreur de compilation se produit.

Dans l’exemple suivant, les entiers égaux à 7 934 076 125 représentés comme des littéraux décimaux, hexadécimaux et binaires sont assignés aux valeurs `ULong`.

[!code-vb[ULong](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ULong)]

> [!NOTE]
> Vous utilisez le `&h` `&H` préfixe ou pour désigner un littératal hexadecimal, le `&b` préfixe ou `&B` pour désigner un littératique binaire, et le préfixe `&o` ou `&O` pour désigner un littéral octal. Les littéraux décimaux n’ont pas de préfixe.

En commençant par Visual Basic 2017, vous `_`pouvez également utiliser le personnage de soulignement, , comme séparateur à chiffres pour améliorer la lisibilité, comme le montre l’exemple suivant.

[!code-vb[ULong](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#LongS)]

En commençant par Visual Basic 15.5, vous`_`pouvez également utiliser le caractère de soulignement ( ) comme séparateur de premier plan entre le préfixe et les chiffres hexadecimal, binaire ou octal. Par exemple :

```vb
Dim number As ULong = &H_F9AC_0326_1489_D68C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Les littérals numériques `ul` peuvent également inclure `ULong` le caractère ou le `UL` [type](../../programming-guide/language-features/data-types/type-characters.md) pour désigner le type de données, comme le montre l’exemple suivant.

```vb
Dim number = &H_00_00_0A_96_2F_AC_14_D7ul
```

## <a name="programming-tips"></a>Conseils de programmation

- **Nombres négatifs.** Parce `ULong` qu’il s’agit d’un type non signé, il ne peut pas représenter un nombre négatif. Si vous utilisez l’opérateur unary moins (`-`) `ULong`sur une expression qui `Decimal` évalue au type, Visual Basic convertit l’expression en premier.

- **Conformité CLS.** Le `ULong` type de données ne fait pas partie de la [spécification de langue commune](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), de sorte que le code conforme à CLS ne peut pas consommer un composant qui l’utilise.

- **Considérations sur l'interopérabilité.** Si vous entrelacez avec des composants non écrits pour le cadre .NET, par exemple `ulong` des objets Automation ou COM, gardez à l’esprit que les types tels que peuvent avoir une largeur de données différente (32 bits) dans d’autres environnements. Si vous passez un argument 32 bits à `UInteger` un `ULong` tel composant, déclarez-le comme au lieu de dans votre code de base visuel géré.

  En outre, Automation ne prend pas en charge les intégrants 64 bits sur Windows 95, Windows 98, Windows ME ou Windows 2000. Vous ne pouvez pas `ULong` passer un argument de base visuelle à un composant d’automatisation sur ces plates-formes.

- **Élargissement.** Le `ULong` type de `Decimal`données `Single`s’élargit à , , et `Double`. Cela signifie que `ULong` vous pouvez convertir à <xref:System.OverflowException?displayProperty=nameWithType> l’un de ces types sans rencontrer une erreur.

- **Personnages de type.** Appending les caractères `UL` de type littéral `ULong` à un littéral le force au type de données. `ULong`n’a pas de caractère de type identificateur.

- **Type .NET Framework.** Le type correspondant dans le .NET Framework est la structure <xref:System.UInt64?displayProperty=nameWithType>.

## <a name="see-also"></a>Voir aussi

- <xref:System.UInt64>
- [Types de données](../../../visual-basic/language-reference/data-types/index.md)
- [Fonctions de conversion de types](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Liste des conversions](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Guide pratique : appeler une fonction Windows qui possède des types non signés](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [Utilisation efficace des types de données](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
