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
ms.openlocfilehash: 11070f6c7f3259b8c34528eb54d99b031b68f9f9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415542"
---
# <a name="uinteger-data-type"></a>UInteger (type de données)

Contient des entiers non signés de 32 bits (4 octets) dont la valeur est comprise entre 0 et 4 294 967 295.

## <a name="remarks"></a>Notes

Le `UInteger` type de données fournit la plus grande valeur non signée dans la largeur de données la plus efficace.

La valeur par défaut de `UInteger` est 0.

## <a name="literal-assignments"></a>Affectations littérales

Vous pouvez déclarer et initialiser une `UInteger` variable en lui assignant un littéral décimal, un littéral hexadécimal, un littéral octal ou (à partir de Visual Basic 2017) un littéral binaire. Si le littéral entier est en dehors de la plage de `UInteger` (autrement dit, s’il est inférieur à <xref:System.UInt32.MinValue?displayProperty=nameWithType> ou supérieur à <xref:System.UInt32.MaxValue?displayProperty=nameWithType>, une erreur de compilation se produit.

Dans l’exemple suivant, les entiers égaux à 3 000 000 000 représentés comme des littéraux décimaux, hexadécimaux et binaires sont assignés aux valeurs `UInteger`.

[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UInt)]

> [!NOTE]
> Vous utilisez le préfixe `&h` ou `&H` pour désigner un littéral hexadécimal, le préfixe `&b` ou `&B` pour désigner un littéral binaire, et le préfixe `&o` ou `&O` pour désigner un littéral octal. Les littéraux décimaux n’ont pas de préfixe.

À compter de Visual Basic 2017, vous pouvez également utiliser le caractère de soulignement, `_` , comme séparateur de chiffres pour améliorer la lisibilité, comme le montre l’exemple suivant.

[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UIntS)]

À compter de Visual Basic 15,5, vous pouvez également utiliser le trait de soulignement ( `_` ) comme séparateur de début entre le préfixe et les chiffres hexadécimaux, binaires ou octaux. Par exemple :

```vb
Dim number As UInteger = &H_0F8C_0326
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Les littéraux numériques peuvent également inclure `UI` le `ui` [caractère de type](../../programming-guide/language-features/data-types/type-characters.md) ou pour désigner le `UInteger` type de données, comme le montre l’exemple suivant.

```vb
Dim number = &H_0FAC_14D7ui
```

## <a name="programming-tips"></a>Conseils de programmation

Les `UInteger` `Integer` types de données et offrent des performances optimales sur un processeur 32 bits, étant donné que les types d’entiers plus petits ( `UShort` , `Short` , `Byte` et `SByte` ), même s’ils utilisent moins de bits, prennent plus de temps pour le chargement, le stockage et l’extraction.

- **Nombres négatifs.** Étant donné que `UInteger` est un type non signé, il ne peut pas représenter un nombre négatif. Si vous utilisez l’opérateur moins unaire ( `-` ) sur une expression qui prend la valeur type `UInteger` , Visual Basic convertit d’abord l’expression en `Long` premier.

- **Conformité CLS.** Le `UInteger` type de données ne faisant pas partie du [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), le code conforme CLS ne peut pas consommer un composant qui l’utilise.

- **Considérations sur l'interopérabilité.** Si vous utilisez des composants non écrits pour le .NET Framework, par exemple des objets Automation ou COM, n’oubliez pas que les types tels que `uint` peuvent avoir une largeur de données différente (16 bits) dans d’autres environnements. Si vous passez un argument de 16 bits à un tel composant, déclarez-le comme `UShort` au lieu de `UInteger` dans votre code Visual Basic managé.

- **Étendue.** Le `UInteger` type de données s’étend à `Long` , `ULong` ,, `Decimal` `Single` et `Double` . Cela signifie que vous pouvez `UInteger` effectuer une conversion vers l’un de ces types sans rencontrer d' <xref:System.OverflowException?displayProperty=nameWithType> erreur.

- **Caractères de type.** L’ajout des caractères de type littéral `UI` à un littéral force ce dernier en `UInteger` type de données. `UInteger`n’a pas de caractère de type d’identificateur.

- **Type .NET Framework.** Le type correspondant dans le .NET Framework est la structure <xref:System.UInt32?displayProperty=nameWithType>.

## <a name="see-also"></a>Voir aussi

- <xref:System.UInt32>
- [Types de données](index.md)
- [Type Conversion Functions](../functions/type-conversion-functions.md)
- [Liste des conversions](../keywords/conversion-summary.md)
- [Procédure : Appeler une fonction Windows qui accepte des types non signés](../../programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [Utilisation efficace des types de données](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
