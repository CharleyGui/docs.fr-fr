---
title: UShort (type de données)
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
ms.openlocfilehash: ee31156e00059699125fd72a7f091afbb21beab0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415477"
---
# <a name="ushort-data-type-visual-basic"></a>UShort, type de données (Visual Basic)

Contient des entiers 16 bits (2 octets) non signés dont la valeur est comprise entre 0 et 65 535.  
  
## <a name="remarks"></a>Notes

 Utilisez le `UShort` type de données pour contenir des données binaires trop volumineuses pour `Byte` .  
  
 La valeur par défaut de `UShort` est 0.  

## <a name="literal-assignments"></a>Affectations littérales

Vous pouvez déclarer et initialiser une `UShort` variable en lui assignant un littéral décimal, un littéral hexadécimal, un littéral octal ou (à partir de Visual Basic 2017) un littéral binaire. Si le littéral entier est en dehors de la plage de `UShort` (autrement dit, s’il est inférieur à <xref:System.UInt16.MinValue?displayProperty=nameWithType> ou supérieur à <xref:System.UInt16.MaxValue?displayProperty=nameWithType>, une erreur de compilation se produit.

Dans l’exemple suivant, les entiers égaux à 65 034 représentés comme des littéraux décimaux, hexadécimaux et binaires sont assignés aux `UShort` valeurs.
  
[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShort)]

> [!NOTE]
> Vous utilisez le préfixe `&h` ou `&H` pour désigner un littéral hexadécimal, le préfixe `&b` ou `&B` pour désigner un littéral binaire, et le préfixe `&o` ou `&O` pour désigner un littéral octal. Les littéraux décimaux n’ont pas de préfixe.

À compter de Visual Basic 2017, vous pouvez également utiliser le caractère de soulignement, `_` , comme séparateur de chiffres pour améliorer la lisibilité, comme le montre l’exemple suivant.

[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShortS)]

À compter de Visual Basic 15,5, vous pouvez également utiliser le trait de soulignement ( `_` ) comme séparateur de début entre le préfixe et les chiffres hexadécimaux, binaires ou octaux. Par exemple :

```vb
Dim number As UShort = &H_FF8C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Les littéraux numériques peuvent également inclure `US` le `us` [caractère de type](../../programming-guide/language-features/data-types/type-characters.md) ou pour désigner le `UShort` type de données, comme le montre l’exemple suivant.

```vb
Dim number = &H_5826us
```

## <a name="programming-tips"></a>Conseils de programmation
  
- **Nombres négatifs.** Étant donné que `UShort` est un type non signé, il ne peut pas représenter un nombre négatif. Si vous utilisez l’opérateur moins unaire ( `-` ) sur une expression qui prend la valeur type `UShort` , Visual Basic convertit d’abord l’expression en `Integer` premier.  
  
- **Conformité CLS.** Le `UShort` type de données ne faisant pas partie du [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), le code conforme CLS ne peut pas consommer un composant qui l’utilise.
  
- **Étendue.** Le `UShort` type de données s’étend à `Integer` , `UInteger` , `Long` , `ULong` , `Decimal` , `Single` et `Double` . Cela signifie que vous pouvez `UShort` effectuer une conversion vers l’un de ces types sans rencontrer d' <xref:System.OverflowException?displayProperty=nameWithType> erreur.  
  
- **Caractères de type.** L’ajout des caractères de type littéral `US` à un littéral force ce dernier en `UShort` type de données. `UShort`n’a pas de caractère de type d’identificateur.  
  
- **Type .NET Framework.** Le type correspondant dans le .NET Framework est la structure <xref:System.UInt16?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.UInt16>
- [Types de données](index.md)
- [Type Conversion Functions](../functions/type-conversion-functions.md)
- [Liste des conversions](../keywords/conversion-summary.md)
- [Procédure : Appeler une fonction Windows qui accepte des types non signés](../../programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [Utilisation efficace des types de données](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
