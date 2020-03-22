---
title: Court (type de données)
ms.date: 01/31/2018
f1_keywords:
- vb.Short
helpviewer_keywords:
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- S literal type character [Visual Basic]
- Short data type
- literal type characters [Visual Basic], S
ms.assetid: 65fcbcf3-a841-400e-885e-301497729a8b
ms.openlocfilehash: 8dfdfb56de32e4b3a96729b09ccf46a6fee9a424
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400728"
---
# <a name="short-data-type-visual-basic"></a>Type de données courts (Visual Basic)

Détient signé 16 bits (2-byte) integers qui varient en valeur de -32 768 à 32 767.  
  
## <a name="remarks"></a>Notes   

 Utilisez `Short` le type de données pour contenir des valeurs integer qui ne nécessitent pas toute la largeur des données de `Integer`. Dans certains cas, le temps d’exécution de langage commun peut emballer vos `Short` variables étroitement ensemble et enregistrer la consommation de mémoire.  
  
 La valeur par défaut de `Short` est 0.  
  
## <a name="literal-assignments"></a>Affectations littérales

Vous pouvez déclarer et `Short` initialiser une variable en lui assignant un littéal décimal, un littéal hexadecimal, un littéral octal, ou (à partir de Visual Basic 2017) un littéral binaire. Si le littéral entier est en dehors de la plage de `Short` (autrement dit, s’il est inférieur à <xref:System.Int16.MinValue?displayProperty=nameWithType> ou supérieur à <xref:System.Int16.MaxValue?displayProperty=nameWithType>, une erreur de compilation se produit.

Dans l’exemple suivant, les intégristes sont égaux à 1 034 qui sont représentés comme décimales, hexadecimal, et les littérals binaires sont implicitement convertis d’Integer à des [Integer](integer-data-type.md) `Short` valeurs.

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Short)]

> [!NOTE]
> Vous utilisez le `&h` `&H` préfixe ou pour désigner un littératal hexadecimal, le `&b` préfixe ou `&B` pour désigner un littératique binaire, et le préfixe `&o` ou `&O` pour désigner un littéral octal. Les littéraux décimaux n’ont pas de préfixe.

En commençant par Visual Basic 2017, vous `_`pouvez également utiliser le personnage de soulignement, , comme séparateur à chiffres pour améliorer la lisibilité, comme le montre l’exemple suivant.

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ShortS)]

En commençant par Visual Basic 15.5, vous`_`pouvez également utiliser le caractère de soulignement ( ) comme séparateur de premier plan entre le préfixe et les chiffres hexadecimal, binaire ou octal. Par exemple :

```vb
Dim number As Short = &H_3264
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Les littérals numériques peuvent également inclure le `S` [caractère type](../../programming-guide/language-features/data-types/type-characters.md) pour désigner le `Short` type de données, comme le montre l’exemple suivant.

```vb
Dim number = &H_3264S
```

## <a name="programming-tips"></a>Conseils de programmation

- **Élargissement.** Le `Short` type de `Integer`données `Long` `Decimal`s’élargit à , , , `Single`ou `Double`. Cela signifie que vous pouvez convertir `Short` en l'un de ces types sans rencontrer d'erreur <xref:System.OverflowException?displayProperty=nameWithType>.  
  
- **Personnages de type.** L'ajout du caractère de type littéral `S` à un littéral force ce dernier en type de données `Short`. `Short`n’a pas de caractère de type identificateur.  
  
- **Type .NET Framework.** Le type correspondant dans le .NET Framework est la structure <xref:System.Int16?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Int16?displayProperty=nameWithType>
- [Types de données](../../../visual-basic/language-reference/data-types/index.md)
- [Fonctions de conversion de types](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Liste des conversions](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Type de données integer](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [Long (type de données)](../../../visual-basic/language-reference/data-types/long-data-type.md)
- [Utilisation efficace des types de données](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
