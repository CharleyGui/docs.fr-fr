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
ms.openlocfilehash: 7cdbd5fb192fd5cc1be6260dcdcdb1f30cf3f865
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400693"
---
# <a name="ushort-data-type-visual-basic"></a>Type de données UShort (Visual Basic)

Détient des 16 pouces non signés (2-byte) d’une valeur allant de 0 à 65 535.  
  
## <a name="remarks"></a>Notes 

 Utilisez `UShort` le type de données pour `Byte`contenir des données binaires trop grandes pour .  
  
 La valeur par défaut de `UShort` est 0.  

## <a name="literal-assignments"></a>Affectations littérales

Vous pouvez déclarer et `UShort` initialiser une variable en lui assignant un littéal décimal, un littéal hexadecimal, un littéral octal, ou (à partir de Visual Basic 2017) un littéral binaire. Si le littéral entier est en dehors de la plage de `UShort` (autrement dit, s’il est inférieur à <xref:System.UInt16.MinValue?displayProperty=nameWithType> ou supérieur à <xref:System.UInt16.MaxValue?displayProperty=nameWithType>, une erreur de compilation se produit.

Dans l’exemple suivant, les intégristes sont égaux à 65 034 qui sont représentés comme décimales, hexadecimal, et les littérals binaires sont attribués aux `UShort` valeurs.
  
[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShort)]

> [!NOTE]
> Vous utilisez le `&h` `&H` préfixe ou pour désigner un littératal hexadecimal, le `&b` préfixe ou `&B` pour désigner un littératique binaire, et le préfixe `&o` ou `&O` pour désigner un littéral octal. Les littéraux décimaux n’ont pas de préfixe.

En commençant par Visual Basic 2017, vous `_`pouvez également utiliser le personnage de soulignement, , comme séparateur à chiffres pour améliorer la lisibilité, comme le montre l’exemple suivant.

[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShortS)]

En commençant par Visual Basic 15.5, vous`_`pouvez également utiliser le caractère de soulignement ( ) comme séparateur de premier plan entre le préfixe et les chiffres hexadecimal, binaire ou octal. Par exemple :

```vb
Dim number As UShort = &H_FF8C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Les littérals numériques `us` peuvent également inclure `UShort` le caractère ou le `US` [type](../../programming-guide/language-features/data-types/type-characters.md) pour désigner le type de données, comme le montre l’exemple suivant.

```vb
Dim number = &H_5826us
```

## <a name="programming-tips"></a>Conseils de programmation
  
- **Nombres négatifs.** Parce `UShort` qu’il s’agit d’un type non signé, il ne peut pas représenter un nombre négatif. Si vous utilisez l’opérateur unary moins (`-`) `UShort`sur une expression qui `Integer` évalue au type, Visual Basic convertit l’expression en premier.  
  
- **Conformité CLS.** Le `UShort` type de données ne fait pas partie de la [spécification de langue commune](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), de sorte que le code conforme à CLS ne peut pas consommer un composant qui l’utilise.
  
- **Élargissement.** Le `UShort` type de `Integer`données `UInteger` `Long`s’élargit à , , `ULong`, , `Decimal`, `Single`et `Double`. Cela signifie que `UShort` vous pouvez convertir à <xref:System.OverflowException?displayProperty=nameWithType> l’un de ces types sans rencontrer une erreur.  
  
- **Personnages de type.** Appending les caractères `US` de type littéral `UShort` à un littéral le force au type de données. `UShort`n’a pas de caractère de type identificateur.  
  
- **Type .NET Framework.** Le type correspondant dans le .NET Framework est la structure <xref:System.UInt16?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.UInt16>
- [Types de données](../../../visual-basic/language-reference/data-types/index.md)
- [Fonctions de conversion de types](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Liste des conversions](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Guide pratique : appeler une fonction Windows qui possède des types non signés](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [Utilisation efficace des types de données](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
