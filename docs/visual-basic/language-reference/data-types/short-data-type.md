---
title: Short, type de données
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
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343935"
---
# <a name="short-data-type-visual-basic"></a>Short, type de données (Visual Basic)

Contient des entiers 16 bits (2 octets) signés dont la valeur est comprise entre-32 768 et 32 767.  
  
## <a name="remarks"></a>Notes  

 Utilisez le type de données `Short` pour contenir des valeurs entières qui ne nécessitent pas la largeur totale des données de `Integer`. Dans certains cas, l’common language runtime peut regrouper étroitement vos variables `Short` et économiser la consommation de mémoire.  
  
 La valeur par défaut de `Short` est 0.  
  
## <a name="literal-assignments"></a>Affectations littérales

Vous pouvez déclarer et initialiser une variable `Short` en lui assignant un littéral décimal, un littéral hexadécimal, un littéral octal ou (à partir de Visual Basic 2017) un littéral binaire. Si le littéral entier est en dehors de la plage de `Short` (autrement dit, s’il est inférieur à <xref:System.Int16.MinValue?displayProperty=nameWithType> ou supérieur à <xref:System.Int16.MaxValue?displayProperty=nameWithType>, une erreur de compilation se produit.

Dans l’exemple suivant, les entiers égaux à 1 034 représentés comme des littéraux décimaux, hexadécimaux et binaires sont convertis implicitement d’un [entier](integer-data-type.md) en valeurs `Short`.

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Short)]

> [!NOTE]
> Vous utilisez le préfixe `&h` ou `&H` pour désigner un littéral hexadécimal, le préfixe `&b` ou `&B` pour désigner un littéral binaire, et le préfixe `&o` ou `&O` pour désigner un littéral octal. Les littéraux décimaux n’ont pas de préfixe.

À compter de Visual Basic 2017, vous pouvez également utiliser le trait de soulignement, `_`, comme séparateur de chiffres pour améliorer la lisibilité, comme le montre l’exemple suivant.

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ShortS)]

À compter de Visual Basic 15,5, vous pouvez également utiliser le caractère de soulignement (`_`) comme séparateur de début entre le préfixe et les chiffres hexadécimaux, binaires ou octaux. Exemple :

```vb
Dim number As Short = &H_3264
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Les littéraux numériques peuvent également inclure le [caractère de type](../../programming-guide/language-features/data-types/type-characters.md) `S` pour désigner le type de données `Short`, comme le montre l’exemple suivant.

```vb
Dim number = &H_3264S
```

## <a name="programming-tips"></a>Conseils de programmation

- **Étendue.** Le type de données `Short` s’étend à `Integer`, `Long`, `Decimal`, `Single`ou `Double`. Cela signifie que vous pouvez convertir `Short` en l'un de ces types sans rencontrer d'erreur <xref:System.OverflowException?displayProperty=nameWithType>.  
  
- **Caractères de type.** L'ajout du caractère de type littéral `S` à un littéral force ce dernier en type de données `Short`. `Short` n’a pas de caractère de type d’identificateur.  
  
- **Type de Framework.** Le type correspondant dans le .NET Framework est la structure <xref:System.Int16?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Int16?displayProperty=nameWithType>
- [Types de données](../../../visual-basic/language-reference/data-types/index.md)
- [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Liste des conversions](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Integer (type de données)](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [Long (type de données)](../../../visual-basic/language-reference/data-types/long-data-type.md)
- [Utilisation efficace des types de données](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
