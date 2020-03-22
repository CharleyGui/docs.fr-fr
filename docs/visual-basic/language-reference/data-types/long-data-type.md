---
title: Long (type de données)
ms.date: 01/31/2018
f1_keywords:
- vb.Long
helpviewer_keywords:
- identifier type characters [Visual Basic], &
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- '& identifier type character'
- integer numbers
- literal type characters [Visual Basic], L
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- L literal type character [Visual Basic]
- integers [Visual Basic], types
- Long keyword [Visual Basic]
- data types [Visual Basic], integral
- data types [Visual Basic], assigning
- Long data type
ms.assetid: b4770c34-1804-4f8c-b512-c10b0893e516
ms.openlocfilehash: 16d7409c802e97b1f33474d810134db4d9f0ad6c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400812"
---
# <a name="long-data-type-visual-basic"></a>Type de données longue (Visual Basic)

Détient signé 64 bits (8-byte) integers allant de -9 223 372 036 854 775 808 à 9 223 372 036 854 775 807 (9,2...E-18).

## <a name="remarks"></a>Notes 

Utilisez `Long` le type de données pour contenir des nombres `Integer` d’intégrants trop grands pour s’adapter au type de données.

La valeur par défaut de `Long` est 0.

## <a name="literal-assignments"></a>Affectations littérales

Vous pouvez déclarer et `Long` initialiser une variable en lui assignant un littéal décimal, un littéal hexadecimal, un littéral octal, ou (à partir de Visual Basic 2017) un littéral binaire. Si le littéral entier est en dehors de la plage de `Long` (autrement dit, s’il est inférieur à <xref:System.Int64.MinValue?displayProperty=nameWithType> ou supérieur à <xref:System.Int64.MaxValue?displayProperty=nameWithType>, une erreur de compilation se produit.

Dans l’exemple suivant, les entiers égaux à 4 294 967 296 représentés comme des littéraux décimaux, hexadécimaux et binaires sont assignés aux valeurs `Long`.

[!code-vb[long](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Long)]

> [!NOTE]
> Vous utilisez le `&h` `&H` préfixe ou pour désigner un littératal hexadecimal, le `&b` préfixe ou `&B` pour désigner un littératique binaire, et le préfixe `&o` ou `&O` pour désigner un littéral octal. Les littéraux décimaux n’ont pas de préfixe.

En commençant par Visual Basic 2017, vous `_`pouvez également utiliser le personnage de soulignement, , comme séparateur à chiffres pour améliorer la lisibilité, comme le montre l’exemple suivant.

[!code-vb[long](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#LongS)]

En commençant par Visual Basic 15.5, vous`_`pouvez également utiliser le caractère de soulignement ( ) comme séparateur de premier plan entre le préfixe et les chiffres hexadecimal, binaire ou octal. Par exemple :

```vb
Dim number As Long = &H_0FAC_0326_1489_D68C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Les littérals numériques peuvent également inclure le `L` [caractère type](../../programming-guide/language-features/data-types/type-characters.md) pour désigner le `Long` type de données, comme le montre l’exemple suivant.

```vb
Dim number = &H_0FAC_0326_1489_D68CL
```

## <a name="programming-tips"></a>Conseils de programmation

- **Considérations sur l'interopérabilité.** Si vous entrelacez avec des composants non écrits pour le cadre .NET, par exemple des objets Automation ou COM, rappelez-vous que `Long` la largeur des données est différente (32 bits) dans d’autres environnements. Si vous passez un argument 32 bits à `Integer` un `Long` tel composant, déclarez-le comme au lieu de dans votre nouveau code de base visuelle.

- **Élargissement.** Le `Long` type de `Decimal`données `Single`s’élargit à , , ou `Double`. Cela signifie que vous pouvez convertir `Long` en l'un de ces types sans rencontrer d'erreur <xref:System.OverflowException?displayProperty=nameWithType>.

- **Personnages de type.** L'ajout du caractère de type littéral `L` à un littéral force ce dernier en type de données `Long`. L'ajout du caractère de type identificateur `&` à un identificateur force ce dernier en type `Long`.

- **Type .NET Framework.** Le type correspondant dans le .NET Framework est la structure <xref:System.Int64?displayProperty=nameWithType>.

## <a name="see-also"></a>Voir aussi

- <xref:System.Int64>
- [Types de données](../../../visual-basic/language-reference/data-types/index.md)
- [Type de données integer](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [Short (type de données)](../../../visual-basic/language-reference/data-types/short-data-type.md)
- [Fonctions de conversion de types](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Liste des conversions](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Utilisation efficace des types de données](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
