---
title: Integer, type de données
ms.date: 01/31/2018
f1_keywords:
- vb.Integer
- Integer
helpviewer_keywords:
- numbers [Visual Basic], whole
- enumerated values [Visual Basic]
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- literal type characters [Visual Basic], I
- integers [Visual Basic], types
- data types [Visual Basic], integral
- '% identifier type character'
- data types [Visual Basic], assigning
- identifier type characters [Visual Basic], %
- I literal type character [Visual Basic]
- Integer data type
ms.assetid: a8f233b4-4be3-455c-861b-05af2fbb6c60
ms.openlocfilehash: c5b1041b8ef0ca9898a846fea03888537bb4abbf
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343981"
---
# <a name="integer-data-type-visual-basic"></a>Integer data type (Visual Basic)

Contient des entiers 32 bits (4 octets) signés dont la valeur est comprise entre -2 147 483 648 et 2 147 483 647.  
  
## <a name="remarks"></a>Notes

 Le type de données `Integer` offre des performances optimales sur un processeur 32 bits. Les autres types intégraux sont plus lents à charger et à stocker en provenance et à destination de la mémoire.  
  
 La valeur par défaut de `Integer` est 0.  

## <a name="literal-assignments"></a>Literal assignments

You can declare and initialize an `Integer` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal. Si le littéral entier est en dehors de la plage de `Integer` (autrement dit, s’il est inférieur à <xref:System.Int32.MinValue?displayProperty=nameWithType> ou supérieur à <xref:System.Int32.MaxValue?displayProperty=nameWithType>, une erreur de compilation se produit.

Dans l’exemple suivant, les entiers égaux à 90 946 représentés comme des littéraux décimaux, hexadécimaux et binaires sont assignés aux valeurs `Integer`.

[!code-vb[integer](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Int)]  

> [!NOTE]
> You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal. Les littéraux décimaux n’ont pas de préfixe.

Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.

[!code-vb[integer](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#IntS)]  

Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits. Exemple :

```vb
Dim number As Integer = &H_C305_F860
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Numeric literals can also include the `I` [type character](../../programming-guide/language-features/data-types/type-characters.md) to denote the `Integer` data type, as the following example shows.

```vb
Dim number = &H_035826I
```

## <a name="programming-tips"></a>Conseils de programmation

- **Interop Considerations.** If you are interfacing with components not written for the .NET Framework, such as Automation or COM objects, remember that `Integer` has a different data width (16 bits) in other environments. Si vous passez un argument de 16 bits à un tel composant, déclarez-le en tant que type de données `Short` et non `Integer` dans votre nouveau code Visual Basic.  
  
- **Widening.** Le type de données `Integer` s'étend à `Long`, `Decimal`, `Single` ou `Double`. Cela signifie que vous pouvez convertir `Integer` en l'un de ces types sans rencontrer d'erreur <xref:System.OverflowException?displayProperty=nameWithType>.  
  
- **Type Characters.** L'ajout du caractère de type littéral `I` à un littéral force ce dernier en type de données `Integer`. L'ajout du caractère de type identificateur `%` à un identificateur force ce dernier en type `Integer`.  
  
- **Framework Type.** Le type correspondant dans le .NET Framework est la structure <xref:System.Int32?displayProperty=nameWithType>.  
  
## <a name="range"></a>Range

Si vous essayez d'assigner à une variable de type intégral un nombre situé hors de la plage de ce type, une erreur se produit. Si vous essayez de lui assigner une fraction, le nombre est arrondi à la valeur entière supérieure ou inférieure la plus proche. Si le nombre est proche à l'identique de deux valeurs entières, la valeur est arrondie à l'entier pair le plus proche. Ce comportement réduit les erreurs d'arrondi qui résultent de l'arrondissement cohérent d'une valeur du milieu dans un seul sens. Le code suivant présente des exemples d'arrondi.  

```vb  
' The valid range of an Integer variable is -2147483648 through +2147483647.  
Dim k As Integer  
' The following statement causes an error because the value is too large.  
k = 2147483648  
' The following statement sets k to 6.  
k = 5.9  
' The following statement sets k to 4  
k = 4.5  
' The following statement sets k to 6  
' Note, Visual Basic uses banker’s rounding (toward nearest even number)  
k = 5.5  
```

## <a name="see-also"></a>Voir aussi

- <xref:System.Int32?displayProperty=nameWithType>
- [Types de données](../../../visual-basic/language-reference/data-types/index.md)
- [Long (type de données)](../../../visual-basic/language-reference/data-types/long-data-type.md)
- [Short (type de données)](../../../visual-basic/language-reference/data-types/short-data-type.md)
- [Fonctions de conversion de types](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Liste des conversions](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Utilisation efficace des types de données](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
