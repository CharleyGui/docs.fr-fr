---
title: ULong, type de données
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
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343883"
---
# <a name="ulong-data-type-visual-basic"></a>ULong, type de données (Visual Basic)

Contient des entiers non signés de 64 bits (8 octets) dont la valeur est comprise entre 0 et 18 446 744 073 709 551 615 (plus de 1,84 fois 10 ^ 19).

## <a name="remarks"></a>Notes

Utilisez le type de données `ULong` pour contenir des données binaires trop volumineuses pour `UInteger`ou les plus grandes valeurs entières non signées.

La valeur par défaut de `ULong` est 0.

## <a name="literal-assignments"></a>Affectations littérales

Vous pouvez déclarer et initialiser une variable `ULong` en lui assignant un littéral décimal, un littéral hexadécimal, un littéral octal ou (à partir de Visual Basic 2017) un littéral binaire. Si le littéral entier est en dehors de la plage de `ULong` (autrement dit, s’il est inférieur à <xref:System.UInt64.MinValue?displayProperty=nameWithType> ou supérieur à <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, une erreur de compilation se produit.

Dans l’exemple suivant, les entiers égaux à 7 934 076 125 représentés comme des littéraux décimaux, hexadécimaux et binaires sont assignés aux valeurs `ULong`.

[!code-vb[ULong](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ULong)]

> [!NOTE]
> Vous utilisez le préfixe `&h` ou `&H` pour désigner un littéral hexadécimal, le préfixe `&b` ou `&B` pour désigner un littéral binaire, et le préfixe `&o` ou `&O` pour désigner un littéral octal. Les littéraux décimaux n’ont pas de préfixe.

À compter de Visual Basic 2017, vous pouvez également utiliser le trait de soulignement, `_`, comme séparateur de chiffres pour améliorer la lisibilité, comme le montre l’exemple suivant.

[!code-vb[ULong](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#LongS)]

À compter de Visual Basic 15,5, vous pouvez également utiliser le caractère de soulignement (`_`) comme séparateur de début entre le préfixe et les chiffres hexadécimaux, binaires ou octaux. Exemple :

```vb
Dim number As ULong = &H_F9AC_0326_1489_D68C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Les littéraux numériques peuvent également inclure le caractère de [type](../../programming-guide/language-features/data-types/type-characters.md) `UL` ou `ul` pour désigner le type de données `ULong`, comme le montre l’exemple suivant.

```vb
Dim number = &H_00_00_0A_96_2F_AC_14_D7ul
```

## <a name="programming-tips"></a>Conseils de programmation

- **Nombres négatifs.** Étant donné que `ULong` est un type non signé, il ne peut pas représenter un nombre négatif. Si vous utilisez l’opérateur moins unaire (`-`) sur une expression qui prend la valeur du type `ULong`, Visual Basic convertit d’abord l’expression en `Decimal`.

- **Conformité CLS.** Le type de données `ULong` ne faisant pas partie du [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), le code conforme CLS ne peut pas consommer un composant qui l’utilise.

- **Considérations relatives à l’interopérabilité.** Si vous utilisez des composants non écrits pour le .NET Framework, par exemple des objets Automation ou COM, n’oubliez pas que les types tels que `ulong` peuvent avoir une largeur de données différente (32 bits) dans d’autres environnements. Si vous passez un argument 32 bits à un tel composant, déclarez-le comme `UInteger` au lieu de `ULong` dans le code de votre Visual Basic managé.

  En outre, Automation ne prend pas en charge les entiers 64 bits sur Windows 95, Windows 98, Windows ME ou Windows 2000. Vous ne pouvez pas passer un argument Visual Basic `ULong` à un composant Automation sur ces plateformes.

- **Étendue.** Le type de données `ULong` s’étend à `Decimal`, `Single`et `Double`. Cela signifie que vous pouvez convertir `ULong` en l’un de ces types sans rencontrer d’erreur de <xref:System.OverflowException?displayProperty=nameWithType>.

- **Caractères de type.** L’ajout des caractères de type littéral `UL` à un littéral force ce dernier en type de données `ULong`. `ULong` n’a pas de caractère de type d’identificateur.

- **Type de Framework.** Le type correspondant dans le .NET Framework est la structure <xref:System.UInt64?displayProperty=nameWithType>.

## <a name="see-also"></a>Voir aussi

- <xref:System.UInt64>
- [Types de données](../../../visual-basic/language-reference/data-types/index.md)
- [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Liste des conversions](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Guide pratique : appeler une fonction Windows qui possède des types non signés](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [Utilisation efficace des types de données](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
