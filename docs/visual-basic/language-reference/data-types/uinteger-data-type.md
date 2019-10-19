---
title: UInteger, type de données (Visual Basic)
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
ms.openlocfilehash: 1ae0cbd3a518bf863a3c57f50934837a486d2901
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583136"
---
# <a name="uinteger-data-type"></a>UInteger (type de données)

Contient des entiers non signés de 32 bits (4 octets) dont la valeur est comprise entre 0 et 4 294 967 295.

## <a name="remarks"></a>Notes

Le type de données `UInteger` fournit la plus grande valeur non signée dans la largeur de données la plus efficace.

La valeur par défaut de `UInteger` est 0.

## <a name="literal-assignments"></a>Affectations littérales

Vous pouvez déclarer et initialiser une variable `UInteger` en lui assignant un littéral décimal, un littéral hexadécimal, un littéral octal ou (à partir de Visual Basic 2017) un littéral binaire. Si le littéral entier est en dehors de la plage de `UInteger` (autrement dit, s’il est inférieur à <xref:System.UInt32.MinValue?displayProperty=nameWithType> ou supérieur à <xref:System.UInt32.MaxValue?displayProperty=nameWithType>, une erreur de compilation se produit.

Dans l’exemple suivant, les entiers égaux à 3 000 000 000 représentés comme des littéraux décimaux, hexadécimaux et binaires sont assignés aux valeurs `UInteger`.

[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UInt)]

> [!NOTE]
> Vous utilisez le préfixe `&h` ou `&H` pour désigner un littéral hexadécimal, le préfixe `&b` ou `&B` pour désigner un littéral binaire, et le préfixe `&o` ou `&O` pour désigner un littéral octal. Les littéraux décimaux n’ont pas de préfixe.

À compter de Visual Basic 2017, vous pouvez également utiliser le trait de soulignement, `_`, comme séparateur de chiffres pour améliorer la lisibilité, comme le montre l’exemple suivant.

[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UIntS)]

À compter de Visual Basic 15,5, vous pouvez également utiliser le caractère de soulignement (`_`) comme séparateur de début entre le préfixe et les chiffres hexadécimaux, binaires ou octaux. Exemple :

```vb
Dim number As UInteger = &H_0F8C_0326
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Les littéraux numériques peuvent également inclure le caractère de [type](../../programming-guide/language-features/data-types/type-characters.md) `UI` ou `ui` pour désigner le type de données `UInteger`, comme le montre l’exemple suivant.

```vb
Dim number = &H_0FAC_14D7ui
```

## <a name="programming-tips"></a>Conseils de programmation

Les types de données `UInteger` et `Integer` offrent des performances optimales sur un processeur 32 bits, étant donné que les types d’entiers plus petits (`UShort`, `Short`, `Byte` et `SByte`), même s’ils utilisent moins de bits, prennent plus de temps pour le chargement , Store et FETCH.

- **Nombres négatifs.** Étant donné que `UInteger` est un type non signé, il ne peut pas représenter un nombre négatif. Si vous utilisez l’opérateur moins unaire (`-`) sur une expression qui prend la valeur du type `UInteger`, Visual Basic convertit d’abord l’expression en `Long`.

- **Conformité CLS.** Le type de données `UInteger` ne faisant pas partie du [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), le code conforme CLS ne peut pas consommer un composant qui l’utilise.

- **Considérations relatives à l’interopérabilité.** Si vous utilisez des composants non écrits pour le .NET Framework, par exemple des objets Automation ou COM, n’oubliez pas que les types tels que `uint` peuvent avoir une largeur de données différente (16 bits) dans d’autres environnements. Si vous passez un argument de 16 bits à un tel composant, déclarez-le comme `UShort` au lieu de `UInteger` dans le code de votre Visual Basic managé.

- **Étendue.** Le type de données `UInteger` s’étend à `Long`, `ULong`, `Decimal`, `Single` et `Double`. Cela signifie que vous pouvez convertir `UInteger` en l’un de ces types sans rencontrer d’erreur de <xref:System.OverflowException?displayProperty=nameWithType>.

- **Caractères de type.** L’ajout des caractères de type littéral `UI` à un littéral force ce dernier en type de données `UInteger`. `UInteger` n’a pas de caractère de type d’identificateur.

- **Type de Framework.** Le type correspondant dans le .NET Framework est la structure <xref:System.UInt32?displayProperty=nameWithType>.

## <a name="see-also"></a>Voir aussi

- <xref:System.UInt32>
- [Types de données](../../../visual-basic/language-reference/data-types/index.md)
- [Fonctions de conversion de types](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Liste des conversions](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Guide pratique : appeler une fonction Windows qui possède des types non signés](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [Utilisation efficace des types de données](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
