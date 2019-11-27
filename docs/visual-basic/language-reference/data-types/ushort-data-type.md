---
title: UShort, type de données
ms.date: 01/31/2018
f1_keywords:
- vb.ushort
helpviewer_keywords:
- numbers [Visual Basic], whole
- literal type characters [Visual Basic], US
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- UShort data type
- US literal type characters [Visual Basic]
ms.assetid: 138db892-665d-4ba8-9cae-d8d91c4a8f39
ms.openlocfilehash: 7cdbd5fb192fd5cc1be6260dcdcdb1f30cf3f865
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343852"
---
# <a name="ushort-data-type-visual-basic"></a>UShort, type de données (Visual Basic)

Contient des entiers 16 bits (2 octets) non signés dont la valeur est comprise entre 0 et 65 535.  
  
## <a name="remarks"></a>Notes

 Utilisez le type de données `UShort` pour contenir des données binaires trop volumineuses pour les `Byte`.  
  
 La valeur par défaut de `UShort` est 0.  

## <a name="literal-assignments"></a>Affectations littérales

Vous pouvez déclarer et initialiser une variable `UShort` en lui assignant un littéral décimal, un littéral hexadécimal, un littéral octal ou (à partir de Visual Basic 2017) un littéral binaire. Si le littéral entier est en dehors de la plage de `UShort` (autrement dit, s’il est inférieur à <xref:System.UInt16.MinValue?displayProperty=nameWithType> ou supérieur à <xref:System.UInt16.MaxValue?displayProperty=nameWithType>, une erreur de compilation se produit.

Dans l’exemple suivant, les entiers égaux à 65 034 représentés comme des littéraux décimaux, hexadécimaux et binaires sont assignés à des valeurs `UShort`.
  
[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShort)]

> [!NOTE]
> Vous utilisez le préfixe `&h` ou `&H` pour désigner un littéral hexadécimal, le préfixe `&b` ou `&B` pour désigner un littéral binaire, et le préfixe `&o` ou `&O` pour désigner un littéral octal. Les littéraux décimaux n’ont pas de préfixe.

À compter de Visual Basic 2017, vous pouvez également utiliser le trait de soulignement, `_`, comme séparateur de chiffres pour améliorer la lisibilité, comme le montre l’exemple suivant.

[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShortS)]

À compter de Visual Basic 15,5, vous pouvez également utiliser le caractère de soulignement (`_`) comme séparateur de début entre le préfixe et les chiffres hexadécimaux, binaires ou octaux. Exemple :

```vb
Dim number As UShort = &H_FF8C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Les littéraux numériques peuvent également inclure le caractère de [type](../../programming-guide/language-features/data-types/type-characters.md) `US` ou `us` pour désigner le type de données `UShort`, comme le montre l’exemple suivant.

```vb
Dim number = &H_5826us
```

## <a name="programming-tips"></a>Conseils de programmation
  
- **Nombres négatifs.** Étant donné que `UShort` est un type non signé, il ne peut pas représenter un nombre négatif. Si vous utilisez l’opérateur moins unaire (`-`) sur une expression qui prend la valeur du type `UShort`, Visual Basic convertit d’abord l’expression en `Integer`.  
  
- **Conformité CLS.** Le type de données `UShort` ne faisant pas partie du [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), le code conforme CLS ne peut pas consommer un composant qui l’utilise.
  
- **Étendue.** Le type de données `UShort` s’étend à `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`et `Double`. Cela signifie que vous pouvez convertir `UShort` en l’un de ces types sans rencontrer d’erreur de <xref:System.OverflowException?displayProperty=nameWithType>.  
  
- **Caractères de type.** L’ajout des caractères de type littéral `US` à un littéral force ce dernier en type de données `UShort`. `UShort` n’a pas de caractère de type d’identificateur.  
  
- **Type de Framework.** Le type correspondant dans le .NET Framework est la structure <xref:System.UInt16?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.UInt16>
- [Types de données](../../../visual-basic/language-reference/data-types/index.md)
- [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Liste des conversions](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Guide pratique : appeler une fonction Windows qui possède des types non signés](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [Utilisation efficace des types de données](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
