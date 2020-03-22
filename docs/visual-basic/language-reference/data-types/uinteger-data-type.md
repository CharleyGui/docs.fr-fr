---
title: UInteger (type de données)
ms.date: 01/31/2018
f1_keywords:
- vb.uinteger
helpviewer_keywords:
- numbers [Visual Basic], whole
- UInteger data type
- literal type characters [Visual Basic], UI
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- UI literal type characters [Visual Basic]
- data types [Visual Basic], integral
ms.assetid: db7ddd34-4f23-46f5-84dd-8b0f83bb8729
ms.openlocfilehash: ccff61608aed797734cb4f5ca0571d7ed73ba98b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400784"
---
# <a name="uinteger-data-type"></a>UInteger (type de données)

Détient des intégrés 32 bits non signés (4-byte) dont la valeur varie de 0 à 4 294 967 295.

## <a name="remarks"></a>Notes 

Le `UInteger` type de données fournit la plus grande valeur non signée dans la largeur de données la plus efficace.

La valeur par défaut de `UInteger` est 0.

## <a name="literal-assignments"></a>Affectations littérales

Vous pouvez déclarer et `UInteger` initialiser une variable en lui assignant un littéal décimal, un littéal hexadecimal, un littéral octal, ou (à partir de Visual Basic 2017) un littéral binaire. Si le littéral entier est en dehors de la plage de `UInteger` (autrement dit, s’il est inférieur à <xref:System.UInt32.MinValue?displayProperty=nameWithType> ou supérieur à <xref:System.UInt32.MaxValue?displayProperty=nameWithType>, une erreur de compilation se produit.

Dans l’exemple suivant, les entiers égaux à 3 000 000 000 représentés comme des littéraux décimaux, hexadécimaux et binaires sont assignés aux valeurs `UInteger`.

[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UInt)]

> [!NOTE]
> Vous utilisez le `&h` `&H` préfixe ou pour désigner un littératal hexadecimal, le `&b` préfixe ou `&B` pour désigner un littératique binaire, et le préfixe `&o` ou `&O` pour désigner un littéral octal. Les littéraux décimaux n’ont pas de préfixe.

En commençant par Visual Basic 2017, vous `_`pouvez également utiliser le personnage de soulignement, , comme séparateur à chiffres pour améliorer la lisibilité, comme le montre l’exemple suivant.

[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UIntS)]

En commençant par Visual Basic 15.5, vous`_`pouvez également utiliser le caractère de soulignement ( ) comme séparateur de premier plan entre le préfixe et les chiffres hexadecimal, binaire ou octal. Par exemple :

```vb
Dim number As UInteger = &H_0F8C_0326
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Les littérals numériques `ui` peuvent également inclure `UInteger` le caractère ou le `UI` [type](../../programming-guide/language-features/data-types/type-characters.md) pour désigner le type de données, comme le montre l’exemple suivant.

```vb
Dim number = &H_0FAC_14D7ui
```

## <a name="programming-tips"></a>Conseils de programmation

Les `UInteger` `Integer` types et les types de données offrent des performances optimales sur`UShort` `Short`un `Byte`processeur `SByte`32 bits, parce que les petits types d’intégreurs ( , , , , et ), même s’ils utilisent moins de bits, prendre plus de temps pour charger, stocker, et aller chercher.

- **Nombres négatifs.** Parce `UInteger` qu’il s’agit d’un type non signé, il ne peut pas représenter un nombre négatif. Si vous utilisez l’opérateur unary moins (`-`) `UInteger`sur une expression qui `Long` évalue au type, Visual Basic convertit l’expression en premier.

- **Conformité CLS.** Le `UInteger` type de données ne fait pas partie de la [spécification de langue commune](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), de sorte que le code conforme à CLS ne peut pas consommer un composant qui l’utilise.

- **Considérations sur l'interopérabilité.** Si vous entrelacez avec des composants non écrits pour le cadre .NET, par exemple `uint` des objets Automation ou COM, gardez à l’esprit que les types tels que peuvent avoir une largeur de données différente (16 bits) dans d’autres environnements. Si vous passez un argument 16 bits à `UShort` un `UInteger` tel composant, déclarez-le comme au lieu de dans votre code de base visuel géré.

- **Élargissement.** Le `UInteger` type de `Long`données `ULong` `Decimal`s’élargit à , , , `Single`et `Double`. Cela signifie que `UInteger` vous pouvez convertir à <xref:System.OverflowException?displayProperty=nameWithType> l’un de ces types sans rencontrer une erreur.

- **Personnages de type.** Appending les caractères `UI` de type littéral `UInteger` à un littéral le force au type de données. `UInteger`n’a pas de caractère de type identificateur.

- **Type .NET Framework.** Le type correspondant dans le .NET Framework est la structure <xref:System.UInt32?displayProperty=nameWithType>.

## <a name="see-also"></a>Voir aussi

- <xref:System.UInt32>
- [Types de données](../../../visual-basic/language-reference/data-types/index.md)
- [Fonctions de conversion de types](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Liste des conversions](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Guide pratique : appeler une fonction Windows qui possède des types non signés](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [Utilisation efficace des types de données](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
